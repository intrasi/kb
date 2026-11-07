---
type: note
title: A March 2026 consumer robot preprint connects AI-assisted reverse engineering to physical and privacy risks
tags: [security, agents, customer]
date: 2026-11-07
by: luka+codex
confidence: moderate
sources: [https://arxiv.org/abs/2603.08665, https://arxiv.org/html/2603.08665v2]
---

**Cybersecurity AI: Hacking Consumer Robots in the AI Era**, Mayoral-Vilches et al., submitted 9 March 2026, revised 10 March. Authors include Alias Robotics and IOActive researchers. [Metadata](https://arxiv.org/abs/2603.08665), [full text](https://arxiv.org/html/2603.08665v2).

| Product | Author-reported result | Boundary |
|---|---|---|
| Hookii Neomow mower | Local foothold exposed shared cloud credentials; telemetry and command access extended to 267+ connected robots | No reported physical attack across that fleet |
| Hypershell X exoskeleton | App decompilation exposed protocols; unauthenticated motor controls and data exposure | Parameter-inversion vulnerability was static-only, without working exploit |
| HOBOT S7 Pro window cleaner | App RE recovered BLE protocol; unauthorized controls and non-destructive OTA writes tested | Suction interruption presents a possible fall risk; no demonstrated injury |

The preprint reports **38 findings** and approximately **1.5–3 hours** of active analysis/validation per platform. These are not controlled timing measurements. Human operators guided testing. Two Hypershell findings lacked working exploits; one cloud observation was not reproducible. The paper does not establish a general months-to-hours speedup, market-wide incidence or obfuscation efficacy.

These are author-reported research outcomes, not documented criminal campaigns. No current patch deployment was independently verified. Relevant follow-up: [[everyday-device-reverse-engineering-harm-casebook]] and [[device-harm-evidence-does-not-establish-obfuscation-as-the-main-remedy]].
