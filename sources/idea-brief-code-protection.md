---
type: source
title: "Team idea brief: code protection with formal verification"
date: 2026-11-07
url:
tags: [idea, security, formal-methods]
---

Verbatim team summary by Luka, shared on 2026-11-07. Status when filed: the problem
field the team intends to work in. The proposed solution is a hypothesis, and no claim
in the brief is verified. Open questions: [[code-protection-field-open-questions]].

# Startup Summary: AI + Formal Verification for Code Protection

## One-line pitch
A code-protection tool that uses AI to obfuscate your code against AI-driven reverse engineering, and formal verification to prove the protected code behaves identically to the original before you ship it.

## The problem
AI agents (Claude, GPT, open models with decompilers) can now reverse-engineer shipped software fast and cheaply, lowering the skill bar for attackers. Traditional obfuscation was built to slow down humans and is increasingly weak against machines. Companies with valuable client-side logic (fintech, mobile, games, media, edge AI) need protection that holds up against automated analysis.

## How it works
- AI proposes obfuscation transformations, chosen to exploit where LLM reasoning breaks down (context limits, hallucination, forcing expensive dynamic analysis).
- Formal verification proves each transformation didn't change behavior, for all inputs, not just tested ones. Nothing ships unless the proof passes.
- Attacker simulation scores the result: run AI agents and solver-based tools against it, measure how much the attacker's time, tokens, and success rate drop.
- Deploy the protected build, with a report: "proven functionally identical, attacker cost raised Nx."

## The differentiator
Incumbents (Jscrambler, Guardsquare, Zimperium, Obfuscator.io) are adding "anti-LLM" obfuscation, but none cleanly offers a correctness guarantee via formal proof. "Provably identical behavior, measurably harder to reverse" is a claim competitors don't make. The formal-methods layer is both the differentiator and the moat, because it's hard to build and needs rare expertise.

## Who buys it
Fintech and payments, mobile apps, game studios (anti-cheat/piracy), media (DRM), and teams shipping AI models to devices. Existing budget line (application shielding, ~$2.7B market in 2026, growing fast), new urgent reason to buy.

## Business model
Per-app or per-build licensing, like existing shielding vendors. Recurring, because it's a permanent arms race: as models improve, protection must be continuously updated.

## Biggest risks
- Entrenched incumbents with enterprise relationships and the same "anti-LLM" idea already in motion.
- Formal verification doesn't fully scale to large programs; you'd prove equivalence for critical functions and use lighter checks elsewhere.
- Arms race means ongoing R&D cost (also why revenue recurs).
- Conservative, trust-based security sale; a newcomer needs proof and references.
