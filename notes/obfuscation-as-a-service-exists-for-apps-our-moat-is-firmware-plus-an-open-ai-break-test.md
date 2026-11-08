---
type: note
title: "Obfuscation as a service already exists for mobile apps (Appdome) and paid firmware protection exists (Emproof, Thales); our only defensible edge is firmware focus plus an open AI break-test, and it is thin"
tags: [market, pitch, security]
date: 2026-11-08
by: tea+claude
confidence: moderate
sources: [https://www.appdome.com/no-code-mobile-integration-knowledge-base/binary-code-obfuscation/, https://appsecsanta.com/appdome, re-emproof-already-claims-proof-backed-firmware-obfuscation, thales-envelope-plus-shows-a-paid-incumbent-response-to-ai-binary-analysis, re-free-open-source-ai-hardening-exists-for-app-formats-but-skips-firmware, re-protection-is-sold-per-app-per-year-not-per-build]
---

Question from Tea, 2026-11-08: does obfuscation as a service already exist, and what is our moat?

## Yes, it exists

| Who | What | Covers firmware for consumer devices? |
| --- | --- | --- |
| **Appdome** | No-code service: upload a mobile app, get a protected build back, including binary obfuscation. From about $50k a year | No, mobile apps only |
| Guardsquare, Promon, Digital.ai, Jscrambler, Verimatrix | App and web protection, sold per app per year ([[re-protection-is-sold-per-app-per-year-not-per-build]]) | No |
| **Emproof** (DE/NL) | Nyx: binary obfuscation for microcontroller firmware, claims formal proofs of correct output ([[re-emproof-already-claims-proof-backed-firmware-obfuscation]]) | **Yes. Closest competitor** |
| **Thales** Sentinel Envelope Plus | Paid add-on since Oct 2026 against AI-assisted binary analysis, with a vendor-run AI test ([[thales-envelope-plus-shows-a-paid-incumbent-response-to-ai-binary-analysis]]) | Desktop and server apps, not device firmware |
| `bla-agents` (free, open source) | Hardens apps against AI agents by inflating files | No, skips firmware ([[re-free-open-source-ai-hardening-exists-for-app-formats-but-skips-firmware]]) |

So "obfuscation as a service" alone is not new, and "obfuscation with a proof" is not new for firmware.

## What is our moat (honest version)

1. **Firmware for consumer devices.** App services do not touch it; free tools cannot fit into device flash.
   Only Emproof is there, and it sells mostly to automotive, aerospace and defence.
2. **An open, rerunnable AI break-test on every release.** We report how long AI agents need to rebuild
   the algorithm, before and after protection, on the customer's own firmware. Nobody publishes this as a
   repeatable product; Thales ran one vendor test on one app.
3. **Data that compounds.** Every break-test shows which protections hold against which AI agents. That
   tells us what to change before the next release; a static protector does not learn.
4. ~~**Runs on their premises.**~~ Not a moat: Emproof already offers both. Its FAQ (checked 2026-11-08,
   https://emproof.com/en/faqs) says Nyx "can also be run from the cloud via our in-house servers"
   (customers upload binaries) or "can be delivered within a Docker container" for in-house servers; it
   runs as "a post-compilation step" from CLI or CI (GitLab, Makefile), sold as "a subscription licence
   per supported Instruction Set Architecture". So firmware obfuscation as a service already exists.

Emproof's solution page (https://emproof.com/en/solution, checked 2026-11-08) lists exploit mitigation,
obfuscation, anti-tamper, platform security and anti-fuzzing for automotive, medical, aviation, industrial
IoT and semiconductors. It does not mention AI or LLM-based reverse engineering, and it does not mention
measuring how long an attacker needs.

The proof of identical behaviour is **not** a moat; Emproof already claims it. It is table stakes.

## Weak spots

- Emproof could add an AI break-test in a few months. Points 1 and 2 are a head start, not a wall.
- Point 3 only becomes real after many customers.
- Today the moat is speed and focus on consumer electronics. Say that plainly to judges.

Checked 2026-11-08. Two further web searches on embedded vendors were blocked by the search tool and
not completed; the embedded list comes from earlier kb notes.
