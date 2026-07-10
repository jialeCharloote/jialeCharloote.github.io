---
layout: page
title: "Charla — AI Reply Copilot"
description: "A macOS copilot that reads your current iMessage/Slack conversation and drafts replies in your voice — local-first, bilingual, human-confirmed."
importance: 2
category: applied-ai
related_publications: false
---

**Status:** Built — working CLI core loop
**Updated:** 2026-07

A Mac desktop copilot that reads the current iMessage or Slack conversation and drafts reply candidates in your voice. Local-first by design: your style profile and feedback log live on your machine.

## Why This Matters

Replying well is a judgment task: tone, language, context, and relationships all matter. Most AI reply tools ignore voice and privacy — Charla treats both as the product.

## What Works Now

- Read-only readers for local iMessage (`chat.db`, including modern `attributedBody` decoding) and Slack (Web API), reconstructed into one conversation model.
- Reply generation: a one-line understanding of the thread plus three distinct reply candidates, tuned by a local personal style profile.
- Bilingual by default — replies match the conversation's language, with natural Chinese/English mixing.
- Safety: a sensitive-content reminder (financial/medical/legal/credentials, EN + ZH) before any context reaches a cloud model; sending always requires human confirmation, with `--dry-run` support.
- An end-to-end `reply` command: read → generate → pick or edit → confirm → send. A feedback log closes the evaluation loop.

## Product Practice

Charla started as a bilingual PRD and a positioning doc before any code — spec first, then a tested CLI core loop. Reply behavior is iterated the same way I approach AI quality elsewhere: define what "good" sounds like, generate candidates, collect feedback, adjust the prompts and profile.
