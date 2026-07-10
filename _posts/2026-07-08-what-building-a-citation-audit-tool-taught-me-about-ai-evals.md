---
layout: post
title: "What Building a Citation-Audit Tool Taught Me About AI Evals"
date: 2026-07-08
description: "An economist's field notes on defining 'good' precisely enough to measure it."
tags: [applied-ai, evals, llm]
---

At work, part of my job involves the least glamorous task in economic consulting: auditing footnotes. Expert reports cite hundreds of sources — depositions, filings, spreadsheets, web pages — and every citation has to be complete, correctly styled, numerically consistent with the text, and backed by a real document. Opposing counsel will look for the one that isn't.

Last year I got tired of doing this by hand, so I built a tool: a Python CLI that indexes case documents into a searchable full-text database, suggests citation candidates for incomplete footnotes, and runs twenty-five deterministic checks — does the arithmetic in this footnote actually add up, does the quoted passage exist verbatim in any source document, did an entity name silently change between report versions. A small review UI lets humans approve or reject what the system proposes.

The tool works. But the most useful thing I got out of it wasn't the tool — it was what the evaluation loop taught me about AI quality in general. Three lessons.

## 1. A single accuracy number is almost useless

The first time I scored the system's auto-generated citation drafts against a ground-truth answer key, the source-match rate came back embarrassingly low. My first instinct was that the matcher was bad. It wasn't — or rather, I had no way of knowing whether it was, because "18% accurate" bundles together completely different failures.

So I built a miss-analysis step that classifies every failure by cause: the correct document was never in the corpus (an ops problem — go copy the files); the document was in the corpus but was a scanned PDF with no extractable text (an OCR problem); or the document was indexed, readable, and the matcher genuinely picked the wrong one (the only real algorithm bug). The same 18% decoded into roughly "80% corpus gaps, 15% scan issues, 5% matcher errors."

That decomposition changed everything: the lever wasn't a smarter matcher, it was boring corpus hygiene. I now believe this generalizes to LLM systems: an eval that outputs one number tells you that you have a problem; an eval that outputs a failure taxonomy tells you what to do on Monday morning.

## 2. Retrieval fails socially, not randomly

My favorite bug: one very long deposition transcript kept "absorbing" footnotes that had nothing to do with it, simply because it was long and lexically rich — a magnet document. BM25 loved it. The fix wasn't better ranking; it was recognizing that many citations *name their source* ("Smith Deposition at 36"), so the system should resolve named sources first and only fall back to search when nothing pins. And when a match couldn't be corroborated by a name the footnote actually cites, the right behavior was to *decline to answer* and flag for human review rather than emit a plausible-looking wrong answer.

If that sounds familiar, it's because it's the hallucination problem in miniature. The design lesson carried over directly to how I think about LLM products: the quality bar isn't "always produce something," it's "know when you shouldn't."

## 3. Define "good" before you automate, or you'll automate "plausible"

The checks that caught real errors were never clever. They were painfully specific: *this style guide forbids "Ibid."*, *a percentage in the sentence must match the percentage in the footnote within tolerance*, *a quotation must appear verbatim in at least one source document*. Writing them forced me to turn a vague professional instinct — "this footnote looks off" — into rules precise enough for a machine to apply and a reviewer to trust.

That translation step, I've come to think, *is* the job in AI quality work. Models are increasingly capable; the scarce skill is specifying what "good" means in a domain, building the measurement loop, and keeping humans in the loop where the cost of a confident error is high.

---

I came to this from economics, where we're trained to distrust our own numbers — every regression comes with the question "what would have to be true for this to be wrong?" Building this tool convinced me the same instinct is exactly what LLM systems need, and it's what I want to spend the next years working on: evaluation, model behavior, and the unglamorous machinery that makes AI outputs trustworthy.

*(All examples above are described at the workflow level; the tool and data are internal. The public-safe blueprint of the same ideas lives in my [Expert Report QA Assistant](/projects/expert-report-qa-assistant/) project.)*
