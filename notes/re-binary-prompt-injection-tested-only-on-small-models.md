---
type: note
title: Prompt injection hidden in a binary hijacked a GhidraMCP agent on Qwen3-8B every time; frontier models are untested
tags: [security, agents]
date: 2026-11-07
by: tea+claude
confidence: high
sources: [re-dossier-03-ai-re-tooling-and-attack-behavior, https://arxiv.org/html/2605.30677v1]
---

Crawford and McClure (Naval Postgraduate School, arXiv 2605.30677, 29 May 2026) used the Cline
agent connected to Ghidra through GhidraMCP. The only models tested were Qwen3-8B and OSS-120B.

- **Qwen3-8B:** angle-bracket pseudo-system tokens succeeded 100% of the time. Replacing them with
  square brackets "dropped from 100% to 40%".
- **OSS-120B:** success "only dropped from 65% to 50%".
- **Non-printing byte:** placing one before the injected text keeps it out of the string listing
  while it still shows in decompiled code. Its main effect was to evade the detection classifier:
  all 20 cases were classified benign. The attack still worked on 18 of 20 programs.

Why it matters: in-binary injection is a cheap ablation against weak attackers, not a proven
defence against frontier agents. It is also a threat to our own harness
([[re-benchmark-harness-must-be-hardened-against-agent-cheating]]).

Verified 2026-11-07: each figure above was checked against the primary source listed in `sources:`, except where marked unverified.
