---
type: decision
title: "Start with paid professional software (engineering/CAD, creative and audio tools): protect licence checks and proprietary formulas against AI-assisted cracking, prove behaviour is unchanged, and measure the time bought"
tags: [idea, pitch, security, market, demo]
date: 2026-11-07
by: tea+claude
status: superseded
superseded_by: [[0003-use-case-vehicle-and-machine-control-firmware]]
---

Proposed by Tea, who owns the use case; Luka builds the tech. Needs Karla's and Luka's agreement.
When they agree, mark [[0001-direction-verified-pqc-migration]] as superseded (the team already
moved from post-quantum migration to code protection).

## Context

The problem field is settled: AI makes shipped code cheap to reverse-engineer
([[code-protection-project-description]]). The open question was which customer to start with.
Evidence used:

- Where reverse engineering costs money, per Karla's Reddit sweep: PC game launch windows first, paid
  desktop apps and plugins second, mobile premium and banking third
  ([[where-does-ai-reverse-engineering-cost-money-reddit]]).
- Luka's buyer research: CAD and engineering vendors protect proprietary formulas and already pay for
  protection and licensing; commercial SDKs and forensic tools too
  ([[cad-forensics-and-sdk-protection-have-different-buying-triggers-and-pilot-fit]],
  [[shipped-software-protection-customer-evidence]]).
- Competitors already claim AI resistance, and Digital.ai, EntropyJS and VeilCC sell an AI-resistance
  score. None claims a proof that protection preserves behaviour
  ([[competitor-claims-vendor-pages-2026-11-07]]).
- The strict reverse-engineering incidents, and AI agents reading native code
  ([[re-incident-records]], [[re-agents-route-around-obfuscation]]).

## Options considered

| Option | Why not first |
| --- | --- |
| Algorithms in native SDKs only | Good technical fit, but almost no public harm evidence and a simple algorithm can be rewritten from scratch |
| Consumer subscription apps (fitness and similar) | Server-side purchase checks already fix it; practitioners call simple apps not worth protecting ([[re-server-side-entitlement-checks-are-the-standard-fix]]) |
| On-device AI models | Weights are copied, not understood; incumbents exist; on-device AI is mostly free ([[local-ai-protection-involves-code-models-and-runtime]], [[re-on-device-ai-is-mostly-the-free-tier]]) |
| Mobile banking and payments | Mostly Kotlin/Swift, crowded, slow certification |
| PC games | Strongest money story, but a performance-sensitive engine, Denuvo/Irdeto and VeilCC, and no named leads. Kept as the opening story and an expansion market |
| Cars, medical, industrial devices, fridges | Reverse engineering there is mostly how defenders find bugs; fixes are patches, authentication and unique keys; slowest buyers; right to repair ([[re-incident-records]] `RE-INC-012`, `RE-INC-013`, `RE-INC-030`, `RE-INC-039`) |

## The choice

**Customer:** a vendor of paid professional desktop software whose value runs on the customer's
machine: engineering, CAD and simulation tools first, then creative and audio software and plugins.
Seats are expensive, the software must work offline, and these vendors already buy protection and
licensing (Thales Sentinel, Wibu CodeMeter, PreEmptive).

**Two assets, one product:**
1. The **licence or Pro check**: cracked, so people use the full product without paying. A security
   researcher found a local bypass in every one of 32 audited Mac apps
   ([[reddit-sweep-2-paid-desktop-apps-and-plugins-lose-local-checks]]).
2. The **proprietary formula or calculation**: read and reused by a competitor. CAD vendors name this
   asset ([[cad-and-simulation-vendors-protect-formulas-but-much-reported-pain-is-license-operations]]).

**Threat:** an AI agent with a decompiler finds the check and reads the formula in hours instead of
weeks ([[re-agents-route-around-obfuscation]], `RE-INC-026`, `RE-INC-028`).

**Promise:** protect the selected functions, prove the protected build behaves identically on them,
and report how much longer an AI agent needs ("time bought"). Not unbreakable; protection buys cost
and time ([[re-protection-buys-cost-not-impossibility]]).

**Out of scope:** copying the whole binary, model weights, server-side features, and anti-tamper
responses that change behaviour on purpose (the proof does not cover those).

**Differentiator:** the only protection that proves it cannot break the protected functions, scored by
an open test anyone can rerun. Competitors' scores are closed and none claims a proof. Breakage is a
reported pain, not a proof request ([[reddit-sweep-2-formal-proof-was-not-asked-for-breakage-was]],
[[reddit-obfuscation-breakage-shows-up-as-crashes-and-maintenance]]).

**Market:** $12.6B application-security TAM, $2.7B in-app protection SAM, about $15M ARR assumed SOM
([[re-market-sizing-tam-sam-som]]). Context: $167B consumer app and game spending in 2025
([[re-consumer-app-spending-167b-in-2025]]).

## What the demo must show (brief for Luka)

A small self-written paid desktop tool in C with (a) a licence check and (b) one proprietary
calculation in **integer or fixed-point** arithmetic (floating point makes the proof harder, per
Luka's CAD note). Silent, 60 seconds:

1. An AI agent cracks the licence and rebuilds the formula from the plain build: minutes, cents.
2. Protect both functions. Z3 shows the formula function is proven identical.
3. The same agent on the protected build: fails, or needs many times the time and tokens.
4. A chart of "time bought" per function.

Grade the formula by comparing the agent's version with the original on thousands of inputs
([[re-shipped-tests-miss-decompiler-divergence]]); grade the crack by whether the tool unlocks.

## Pitch order

1. Hook: games cracked on launch day and a Switch 2 jailbroken with AI in two weeks.
2. Problem: paid professional software ships its licence check and its formulas to every customer.
3. Solution and demo.
4. Why us: proof plus an open score; competitors' scores are closed.
5. Market and the expansion path: professional software → SDKs and games → device and machine software.
6. Risk as "if we prove X": if five vendors confirm cracking or formula theft costs them money, the
   product sells.

## Revisit when

- Interviews with Luka's leads (SDProget, GLASER, GGU, /n software, Blue Marble, Tech Soft 3D,
  Dynamsoft) say cracking and reconstruction are not a current cost, or that licensing operations are
  the only pain.
- Luka's spike shows no measurable gap between plain and protected builds.
- A competitor publishes a proof of behaviour preservation.
- The pitch must lead with games after all: same product, different first customer.
