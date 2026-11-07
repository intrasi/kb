---
type: question
title: Which reverse-engineering research claims are still unverified, and who can close them?
tags: [security, market, regulation, formal-methods, human]
date: 2026-11-07
by: tea+claude
status: open
owner:
---

On 2026-11-07 every `re-` note was checked against its primary source. These items could not be
closed: pages were blocked, paywalled or image-only, or our research agents' searches were stopped
by a safety filter. Until an item is closed, the note that depends on it keeps its stated
confidence and must not be cited as fact.

## Needs a human to read the primary source

1. **Vendor correctness claims.** Do Guardsquare, Jscrambler, Digital.ai, Promon, Thales,
   Verimatrix or Appdome document any proof or guarantee that protected code behaves like the
   original? Affects [[re-verified-obfuscation-exists-in-academia]].
2. **Blazy and Hutin, MBA obfuscation verified in Coq.** Read the paper: venue, year, scope.
   Affects [[re-verified-obfuscation-exists-in-academia]].
3. **EMVCo SBMP v1.5 and PCI MPoC PDFs.** Our wording comes from vendor summaries (Licel, Promon).
   Confirm the "should"/"must" wording and the requirement IDs. Affects
   [[re-compliance-requires-resilience-not-method]].
4. **OpenAI's ExploitGym incident post** returned HTTP 403. Confirm the date (21 July 2026) and the
   models named. Affects [[re-benchmark-harness-must-be-hardened-against-agent-cheating]].
5. **MarketsandMarkets application-security revision**, from $41.16B to $13.63B for 2026.
   Affects [[re-in-app-protection-16b-figure-has-no-source]].
6. **Promon Q1 2026 per-technique results** are only in an image. Affects
   [[re-stacked-obfuscation-passes-cut-llm-success-in-vendor-study]].
7. **Thales blog** naming Claude Opus 4.7 as the agent. Seen only in a search snippet; the press
   release names no model. Affects [[re-protection-buys-cost-not-impossibility]].

## Absence claims to re-check before any pitch

- No open, configurable lift benchmark with confidence intervals:
  [[re-open-configurable-lift-benchmark-is-the-remaining-gap]].
- No measured function-size versus solve-time data for obfuscated code:
  [[re-equivalence-proofs-scale-with-structural-similarity]].

## Leads

- Luka's reading list [[verified-obfuscation-reading-list-2026-11-07]] cites the Blazy and Hutin MBA
  paper (2019) and "Towards Formal Verification of Program Obfuscation" (2020), which it says
  includes a researcher from Irdeto/Cloakware. Start item 2 there; the Irdeto link bears on item 1.
- Karla's open evidence gaps are separate: [[code-protection-evidence-gaps]].

## Answer
