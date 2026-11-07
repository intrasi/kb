---
type: note
title: Quarkslab reports a customer whose AI tooling recovered hidden strings from an obfuscated library
tags: [customer, security, agents]
date: 2026-11-07
by: luka+codex
confidence: moderate
sources: [https://blog.quarkslab.com/defeating-ai-assisted-reverse-engineering-or-at-least-trying-to.html]
---

Quarkslab's Rémy Salim reports on 20 August 2026 that an unnamed customer brought a walkthrough from its own tooling: an AI model analyzed its obfuscated library and recovered hidden strings. The account is unusually direct evidence of a protection customer raising an AI-specific concern. It does not identify the customer, quantify losses, describe an algorithm clone or establish willingness to buy our product.

Quarkslab's exploratory follow-up used small AArch64 targets. Agents frequently executed/emulated decoder logic instead of understanding every protection. The experiments also exposed harness and grading problems. Hidden-string recovery is an asset-extraction task; it is not interchangeable with independently reproducing proprietary numerical behavior.

Implication: evaluate the customer's actual asset and allow realistic dynamic analysis. A function can remain difficult to understand while an attacker obtains its output or extracts a usable implementation. Correctness proofs do not establish resistance to this route.

Source: [Quarkslab research account](https://blog.quarkslab.com/defeating-ai-assisted-reverse-engineering-or-at-least-trying-to.html), checked 2026-11-07. Related: [[algorithm-protection-demand-intersection-remains-unproven-for-named-buyers]].
