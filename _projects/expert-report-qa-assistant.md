---
layout: page
title: "Expert Report QA Assistant"
description: "A public-safe report QA workflow that checks citations, figures, assumptions, and internal consistency in synthetic expert-style reports."
importance: 3
category: applied-ai
related_publications: false
---

<p><span class="status-badge status-badge--blueprint">Public-safe blueprint</span></p>

_Updated: 2026-06-14_

A public-safe report QA workflow that checks citations, figures, assumptions, and internal consistency in synthetic expert-style reports.

## Why This Matters

Long analytical reports often require repetitive checks across citations, tables, assumptions, defined terms, and conclusion consistency.

## System Approach

A QA assistant ingests public or synthetic report packets, creates structured checks, flags issues, and produces a reviewer-ready punch list.

## What The Demo Shows

- Load a synthetic report packet and public source appendix.
- Run citation, figure, assumption, and conclusion checks.
- Generate a QA memo with severity, evidence reference, and reviewer action.
- Show how the same pattern could support legal or consulting workflows without using private data.

## Architecture Highlights

- Document intake with source inventory and page/section references.
- Citation and exhibit checklist with missing-source flags.
- Figure and table consistency review against stated assumptions.
- Claim extraction with evidence status and reviewer notes.
- Saturn gate before any public claim or external sharing.

## Safety And Evals

- Seed known citation defects into a synthetic report and measure recall.
- Seed unsupported claims and track whether each gets flagged.
- Use a reviewer checklist to classify false positives and false negatives.
- Require every flagged issue to include a source or section reference.

## Public-Safe Boundary

Use only personal, public, or synthetic examples. Do not use employer, client, litigation, confidential, or internal work material.

This project page is intentionally written from personal, public, or synthetic examples only.
