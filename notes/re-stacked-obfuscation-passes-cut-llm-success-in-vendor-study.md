---
type: note
title: "Three stacked OLLVM passes cut LLM recovery success on ARM from 63.7% to 8.5%, in one vendor study"
tags: [security, agents]
date: 2026-11-07
by: tea+claude
confidence: low
sources: [re-dossier-02-obfuscation-techniques-engines, https://promon.io/security-news/app-threat-report-2026-q1-the-state-of-code-obfuscation-against-ai]
---

Promon App Threat Report Q1 2026 (published 26 March 2026):

- **Corpus:** 200 C programs compiled to 2,000 x86-64 and ARM64 binaries.
- **Models (10):** Claude 4.5 Opus, Sonnet and Haiku; GPT-5 and GPT-4o; Gemini 3 Pro, 3 Flash
  and 2.5 Pro; DeepSeek Chat and Reasoner.
- **Task:** zero-shot prompts. A success had to compile and match the original's outputs.
- **Result:** on clean ARM the average success was 63.7%. With three stacked passes
  (substitution + flattening + bogus control flow) it fell to 8.5%.
- **Complexity:** flattening plus bogus control flow made the code 4.18x (x86) and 5.50x (ARM)
  more complex than bogus control flow alone. That is a code metric, not attacker cost or success.

Low confidence: the source is a vendor with a product to sell. The per-technique results are
published only as an image, which we have not checked. Zero-shot prompting is weaker than a
tool-using agent ([[re-agents-route-around-obfuscation]]). No independent "lift versus number of
passes" curve exists; our benchmark could publish one.

Verified 2026-11-07: each figure above was checked against the primary source listed in `sources:`.
