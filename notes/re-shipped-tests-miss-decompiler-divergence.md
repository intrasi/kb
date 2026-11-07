---
type: note
title: Passing shipped tests is not evidence a recovered program is correct; differential fuzzing is needed
tags: [security, formal-methods]
date: 2026-11-07
by: tea+claude
confidence: high
sources: [re-dossier-01-benchmarks-and-grading, https://arxiv.org/html/2609.05370v1]
---

Decompile-Diverge (Liu, Raff and Micinski, arXiv 2609.05370, 4 September 2026):
- Across 15,379 candidates scored by both oracles, "3.9% pass every shipped test yet diverge on the
  generated corpus". The abstract's figure, 4.9%, uses a different denominator: the 12,133
  test-passers. Don't mix the two.
- Shipped suites "fail to capture 3% to 45% of the divergence in function behavior".
- The strongest LLM refinement raised Ghidra's build rate from 75% to 90%, while its matched rate
  fell from 74% to 62%. Recompiling is not being correct.

Method:
- fuzz the original with AFL++;
- splice the candidate in;
- compare a bounded post-state: return values, bytes written, writable globals;
- count a divergence only if it reproduces across four reruns.

Why it matters: our grader should be an external oracle plus differential fuzzing, not test-pass
or an LLM judge. The paper does not cover obfuscated binaries. Whether such an oracle keeps up with
binaries slowed up to 247x is an open question
([[re-tigress-virtualization-costs-42-to-247x-runtime]]).

Verified 2026-11-07 against the primary source.
