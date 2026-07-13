---
layout: page
title: "听写 Tingxie — Local Voice Dictation"
description: "Offline zh/en voice dictation for macOS. Hold a key, speak, and the text lands in whatever app you're in. Nothing leaves the machine."
importance: 1
category: applied-ai
github: https://github.com/jialeCharloote/tingxie
related_publications: false
---

<p><span class="status-badge status-badge--built">Built · in daily use</span></p>

_Updated: 2026-07_

I talk in a mix of Chinese and English, and every dictation tool I tried made me pick one. Whisper Flow is good but it ships my voice to someone else's server, and I didn't want my notes and messages going through a cloud API. So I built my own. Hold the fn key, speak, let go, and the text is pasted into whatever app has focus. Nothing ever leaves my laptop.

## See It Run

<video controls playsinline preload="metadata" poster="/assets/img/tingxie-poster.png" class="rounded z-depth-1" style="max-width: 400px; width: 100%; display: block; margin: 0 auto 1rem;">
  <source src="/assets/video/tingxie-demo.mp4" type="video/mp4">
  Your browser doesn't support embedded video —
  <a href="/assets/video/tingxie-demo.mp4">download the demo</a> instead.
</video>

<p style="text-align: center;"><small>Speaking mixed 中文/English with filler words — live transcript rolls in the pill, raw text pastes instantly, the polished version swaps in. Second take: shift+fn pastes the English translation. Sound on 🔊</small></p>

The whole pipeline runs on-device: microphone at 16kHz, Silero VAD to find where speech starts and stops, SenseVoice for the transcription, a local LLM to clean up the result, then paste. On my machine a 5.6-second Chinese clip transcribes in 0.07 seconds, so it feels instant. **Source:** [github.com/jialeCharloote/tingxie](https://github.com/jialeCharloote/tingxie).

## What Works Now

- **Code-switched speech.** SenseVoice-Small (via sherpa-onnx) was trained for 中英混杂 speech, so it handles a sentence that starts in Chinese and ends in English without dropping half of it. Whisper stays available as an alternate backend if I want to compare.
- **Push-to-talk and hands-free.** Tap and it keeps recording until you stop talking. Hold and it records until you let go. Silero VAD decides when a hands-free take is over.
- **Local cleanup.** A local Qwen model on Ollama strips the filler (嗯, 呃, um, uh), fixes punctuation, and is few-shot prompted to leave the Chinese/English mixing exactly as spoken instead of quietly translating it. Costs about a second, and it's a one-line toggle to turn off.
- **A personal dictionary.** The model kept hearing "cloud code" when I said Claude Code. Now there's a rules file I can edit while the app is running, and the fix applies on the next dictation.
- **Menu bar app** with a floating recording indicator, sound cues, and a LaunchAgent if you want it running at login.

## Why I Like This One

It's a small tool, but it's the whole loop: pick the model that actually fits the problem instead of the famous one, measure whether it's fast enough to feel good, then find the failure cases and fix them where they belong. The dictionary exists because I watched what it got wrong. The few-shot cleanup prompt exists because the first version kept translating my Chinese into English, which is exactly the kind of confidently-wrong output I spend my working life trying to catch.
