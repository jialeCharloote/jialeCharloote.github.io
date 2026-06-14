---
layout: page
title: "Charlotte Orbit"
description: "A local-first assistant control plane that routes personal, career, wellness, market, and operations requests through specialized agents with approval gates."
importance: 1
category: applied-ai
related_publications: false
---

**Status:** Working prototype  
**Updated:** 2026-06-14

A local-first assistant control plane that routes personal, career, wellness, market, and operations requests through specialized agents with approval gates.

## Why This Matters

Personal AI workflows become messy when every tool has its own memory, risk model, and notification loop.

## System Approach

Charlotte Orbit creates one front door, then routes requests to specialist agents for messages, market research, wellness, career planning, coding, and approvals.

## What The Demo Shows

- Initialize the local control plane and seed CharlotteOS folders.
- Route one career request, one grocery request, and one market-research request.
- Ingest fixture Slack or Discord messages and show signal scoring.
- Generate the weekly command center and inspect pending approval items.

## Architecture Highlights

- Sol routes natural-language requests into agent-owned workflows.
- Mercury scores Slack and Discord messages before escalating high-value signals.
- Jupiter turns ticker evidence into source-backed research memo tasks.
- Ceres creates wellness and grocery plans from user-approved local context.
- Pallas generates career plans, resume bullets, LinkedIn drafts, and job trackers.
- Saturn enforces approval gates for sending, buying, booking, trading, applying, or publishing.

## Safety And Evals

- Route tests confirm that career, grocery, market, and irreversible requests go to the right agent.
- Approval tests confirm high-risk actions become needs_approval tasks.
- Digest tests confirm noisy message streams only surface scored signals.
- Brief tests confirm generated reports include evidence, status, and open tasks.

## Public-Safe Boundary

Use only personal, public, or synthetic examples. Do not use employer, client, litigation, confidential, or internal work material.

This project page is intentionally written from personal, public, or synthetic examples only.
