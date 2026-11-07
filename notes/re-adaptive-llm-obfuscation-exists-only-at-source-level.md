---
type: note
title: Feedback-loop LLM obfuscation exists in 2026 research, but only on source code, not compiled binaries
tags: [security, agents, idea]
date: 2026-11-07
by: tea+claude
confidence: high
sources: [re-dossier-05-competitors-market-funding, https://arxiv.org/html/2606.11755v1, https://arxiv.org/html/2512.21250]
---

**Acoda (arXiv 2606.11755).**
- Evolves obfuscated Python with a genetic algorithm scored against the target LLM's
  deobfuscation.
- Uses 100 CodeNet samples and 7 LLMs.
- Its equivalence check runs test cases.

**CoTDeceptor (arXiv 2512.21250).**
- Feeds a detector's failed reasoning chains back into generation.
- Works on Python, C++ and Java source.
- Is built to hide malicious code from LLM detectors, including real coding agents (Codex-based
  gpt-5.1-codex-max and gpt-5.2, and Qwen Code).
- Its equivalence check is judged by an LLM.

Neither works on compiled binaries, uses formal proofs, or is a product. So "adaptive obfuscation
is novel" must narrow to "novel on compiled binaries, for defence, with proofs". See
[[re-verified-obfuscation-exists-in-academia]].

Verified 2026-11-07 against the primary sources.
