---
type: note
title: "SRE-Bench already measures how much hardening lowers agent scores, on private binaries with fixed presets"
tags: [security, agents, idea]
date: 2026-11-07
by: tea+claude
confidence: high
sources: [re-dossier-01-benchmarks-and-grading, https://arxiv.org/html/2608.11469]
---

**Setup.** SRE-Bench (arXiv 2608.11469; authors include people from OpenAI, Anthropic and Google
DeepMind) has:
- 19 private, real-world-scale programs averaging 16.9K lines;
- 262 instances and 1,572 tasks;
- runs budgeted at 500 steps and 6 hours;
- the build held fixed while only the protection varies, across eight presets (P1 to P8).

**Results.**
- "Hardening cuts GPT-5.6-sol's score from 4.69 to 2.50 and reduces every other model besides
  GPT-6-Astra to at most 0.33."
- GPT-6-Astra loses only 0.10 points.
- Cost per point rises 1.5x for Astra, 3.4x for GPT-5.6-sol, and 9 to 35x for weaker models.
- Strict and server-side-key presets (P4, P8) were hardest.
- Anti-agent deterrents were a negative result.

**Refusals.** Only 181 of 262 instances could be graded for GPT-6-Astra, which the paper blames
on "frequent refusals on cyber safety grounds". There is no per-model refusal breakdown; other
models had up to 262 of 262 graded.

**What it lacks:**
- confidence intervals (its "±" values are undefined);
- open binaries (it runs only through an evaluation service);
- survival curves over budget;
- protection configurations chosen by the user.

Why it matters: SRE-Bench is the closest prior work and must be cited in the pitch. Our gap is
narrower: [[re-open-configurable-lift-benchmark-is-the-remaining-gap]].

Verified 2026-11-07: each figure above was checked against the primary source listed in `sources:`, except where marked unverified.
