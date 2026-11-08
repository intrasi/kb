---
type: decision
title: "Protect device makers' shipped algorithms (Samsung-type consumer and smart devices) against competitors reverse-engineering them with AI, priced per protected release build"
tags: [idea, pitch, security, market, customer, demo]
date: 2026-11-08
by: tea+claude
status: active
---

Decided by the team on 2026-11-08 (Tea owns the use case; Luka builds the tech). Replaces
[[0002-use-case-paid-professional-software]]. An earlier vehicle anti-tampering draft was withdrawn; its
evidence stays in the kb ([[re-euro-7-makes-ecu-software-anti-tampering-law-from-2027]]).

## Context

Device makers put much of a product's value into algorithms that ship inside the device: noise
cancelling, robot-vacuum navigation, camera processing, sleep scores, battery management, hair-dryer
heat control ([[consumer-products-can-contain-valuable-shipped-algorithms]]). A competitor that
reconstructs such an algorithm from the firmware skips years of R&D and sells a cheaper product.
AI agents make reading firmware cheaper ([[re-agents-route-around-obfuscation]], `RE-INC-026` in
[[re-incident-records]]).

What supports the fear:
- Patents protect device makers poorly: Dyson's key hair-dryer patents were invalidated in China after
  challenges from Dreame and Laifen; iRobot, DJI and Ecovacs fights ended in invalidations or settlements
  ([[re-no-public-case-of-clones-copying-algorithms-from-shipped-consumer-devices]]).
- Copying is concentrated: German machine makers report €4.1B a year in piracy damage, with China the
  origin in 82% of cases (VDMA 2024, [[re-machine-software-cloning-report-2026-11-08]]).
- Shipped models are taken in practice: researchers extracted on-device models from 66% of apps that
  tried to protect them ([[re-on-device-models-are-extractable-from-most-protected-apps]]).

What does not (say it before judges do):
- No public case shows a competitor taking an algorithm from a shipped Samsung, Dyson, iRobot, DJI or
  Xiaomi device. The big losses (Samsung chip leaks, Motorola v. Hytera) came from insiders, which
  protecting shipped code cannot stop ([[re-big-machine-software-theft-cases-started-with-insiders]]).
  Chinese-language court records are not yet searched.

## The choice

**Customer:** makers of consumer and smart devices whose differentiation is an on-device algorithm,
and the suppliers of those algorithm libraries (Bosch Sensortec-type). Start with audio, robotic and
measuring devices, where the algorithm can be isolated and its value measured. Samsung-scale makers are
the vision; mid-size makers and library suppliers are the first conversations.

**Pitch line:** "Your patents keep failing. Protect the know-how inside the device itself."

**Product:**
1. Protect: obfuscate the selected algorithm functions in the firmware.
2. Prove: the protected functions compute exactly the same outputs (Z3, integer and fixed-point code).
3. Measure: AI agents try to reconstruct the algorithm; report how much longer they need ("time bought").

**Pricing:** one unit = one protected release build per device model, inside an annual plan; price per
build scales with the share of functions protected; internal builds free; security-only releases at
half; a minimum and a cap per product line. Worked examples (untested assumptions): robot-vacuum maker
with 7 models about $30k a year; release volume is real because devices ship builds for years
([[re-devices-ship-many-release-builds-for-years-after-launch]],
[[re-protection-is-sold-per-app-per-year-not-per-build]]).

**Differentiator:** an open, rerunnable AI time-to-break measurement. The behaviour proof alone is not
unique for firmware ([[re-emproof-already-claims-proof-backed-firmware-obfuscation]]).
Free open-source hardening against AI analysers now exists for app and web formats, and it claims
verified runtime equivalence too, but it skips firmware and works by inflating files far beyond what
device flash allows ([[re-free-open-source-ai-hardening-exists-for-app-formats-but-skips-firmware]]).
That is another reason to sell into devices rather than apps.

**Out of scope, honestly:**
- Insider theft of source code.
- Copying the whole binary onto identical hardware (needs no understanding; hardware-bound licensing
  handles it).
- Blocking owners or repairers; we protect the code, not the device from its owner
  ([[re-eu-law-lets-owners-study-and-decompile-software-for-interoperability]],
  [[re-newag-train-locks-show-the-backlash-risk-for-protection-vendors]]).

## Demo brief for Luka

A small self-written device algorithm in C, fixed-point, for example a robot-vacuum coverage step or an
audio filter. Silent, 60 seconds:

1. An AI agent reconstructs the algorithm from the plain binary: minutes, cents.
2. Protect it; Z3 shows the protected function gives identical outputs.
3. The same agent on the protected binary: fails or needs many times the time and tokens.
4. A "time bought" chart.

Grade reconstruction by comparing the agent's version with the original on thousands of inputs
([[re-shipped-tests-miss-decompiler-divergence]]).

## Revisit when

- Interviews with device makers say competitors match their algorithms through people or patents, not
  by studying the shipped device.
- Two of three pricing conversations prefer a flat yearly price per product line over per-build.
- Luka's spike shows no measurable gap between plain and protected builds.
- A competitor already publishes an AI time-to-break score for firmware.
