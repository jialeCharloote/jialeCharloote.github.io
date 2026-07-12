---
layout: post
title: "Magnet Documents: Why Retrieval Fails Socially, Not Randomly"
description: "A deep dive on the one failure mode that broke my citation matcher — and what it says about RAG in general."
tags: [applied-ai, evals, rag, llm]
# DRAFT — when ready: set a real `date:` (YYYY-MM-DD), then move this file to _posts/
# renamed as _posts/<date>-magnet-documents-retrieval-fails-socially.md
---

<!--
OUTLINE / SKELETON — expand each section into 2–4 paragraphs, keep the workflow-level,
public-safe framing you used in the evals post. Target ~800–1100 words.
-->

## The bug that didn't look like a bug

<!-- Set the scene: one long deposition transcript kept "absorbing" footnotes that had
     nothing to do with it. Nothing errored. Accuracy just quietly sagged. Explain what a
     "magnet document" is — long + lexically rich → BM25 loves it. -->

## Why lexical retrieval rewards the wrong document

<!-- The mechanism, in plain terms: term-frequency scoring, document length, why a big
     document out-competes the correct short one. Keep it intuitive, not mathy. One small
     concrete (synthetic) example of a footnote getting mis-matched. -->

## The fix wasn't better ranking

<!-- Named sources first: many citations literally name their source ("Smith Deposition at
     36"). Resolve the named entity, fall back to search only when nothing pins. Reframe:
     the ranking wasn't broken, the resolution *order* was. -->

## Know when to decline

<!-- When a match can't be corroborated by a name the footnote actually cites, decline and
     flag for a human instead of emitting a plausible wrong answer. Tie explicitly to the
     hallucination problem: the bar isn't "always answer," it's "know when you shouldn't." -->

## What this generalizes to in RAG

<!-- The payoff paragraph: magnet documents exist in any corpus (long wikis, catch-all docs,
     giant PDFs). Practical takeaways — entity-first resolution, length normalization,
     abstention as a first-class output. Close with the economics instinct: "what would have
     to be true for this retrieval to be wrong?" -->
