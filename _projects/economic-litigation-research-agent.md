---
layout: page
title: "Economic Litigation Research Agent"
description: "A research agent that turns public filings, company disclosures, news, and market data into a cited analytical memo."
importance: 3
category: applied-ai
related_publications: false
---

**Status:** Public-safe blueprint  
**Updated:** 2026-06-14

A research agent that turns public filings, company disclosures, news, and market data into a cited analytical memo.

## Why This Matters

Research workflows lose time when analysts jump between filings, news, market data, notes, and memo drafts without an evidence ledger.

## System Approach

The agent builds a public-source evidence ledger, separates facts from interpretation, and drafts a memo with citations, caveats, and open questions.

## What The Demo Shows

- Pick a public company or public legal/regulatory topic.
- Collect public sources and add them to the evidence ledger.
- Generate a cited memo with fact/interpretation separation.
- Review source coverage gaps and next research questions.

## Architecture Highlights

- Question framing and source plan.
- Public filing, news, and market-data source inventory.
- Evidence ledger with timestamps, links, and confidence notes.
- Memo generator with thesis, facts, risks, and open questions.
- Human review gate before publishing or relying on findings.

## Safety And Evals

- Check every factual claim for a source link or source note.
- Score source freshness and source type quality.
- Track unsupported claims and unresolved questions.
- Review whether the memo separates rumor, fact, inference, and recommendation.

## Public-Safe Boundary

Use only personal, public, or synthetic examples. Do not use employer, client, litigation, confidential, or internal work material.

This project page is intentionally written from personal, public, or synthetic examples only.
