---
layout: page
title: "Event Study Copilot"
description: "A public-data copilot for framing event windows, pulling market data, and drafting caveated event-study notes."
importance: 4
category: applied-ai
related_publications: false
---

<p><span class="status-badge status-badge--blueprint">Public-safe blueprint</span></p>

_Updated: 2026-06-14_

A public-data copilot for framing event windows, pulling market data, and drafting caveated event-study notes.

## Why This Matters

Event analysis requires careful window selection, benchmark choice, data validation, charting, and caveat writing.

## System Approach

The copilot guides event framing, validates public price data, computes basic windows, and produces charts plus caveated draft notes.

## What The Demo Shows

- Select a public event and define pre/post windows.
- Load public price data and run validation checks.
- Generate charts and a caveated memo.
- Show how assumptions change the interpretation.

## Architecture Highlights

- Event definition and timeline builder.
- Public price data intake and validation.
- Window calculation and benchmark comparison.
- Chart and caveat generation.
- Human review gate before using outputs in any decision.

## Safety And Evals

- Test missing-date and stale-price handling.
- Compare calculations against a small hand-checked fixture.
- Require caveats for confounding events and benchmark choice.
- Keep recommendations separate from analytical observations.

## Public-Safe Boundary

Use only personal, public, or synthetic examples. Do not use employer, client, litigation, confidential, or internal work material.

This project page is intentionally written from personal, public, or synthetic examples only.
