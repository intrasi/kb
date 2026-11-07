---
type: note
title: Automatic equivalence proofs scale to thousands of lines only when the two versions are structurally similar
tags: [formal-methods]
date: 2026-11-07
by: tea+claude
confidence: moderate
sources: [re-dossier-04-formal-verification-equivalence, https://ofers.dds.technion.ac.il/publications/stvr12.pdf, https://users.cs.utah.edu/~regehr/alive2-pldi21.pdf, https://arxiv.org/pdf/2302.02384]
---

**Regression verification (Strichman et al., STVR 2012).**
- It proved random C programs with "up to 20 functions and thousands of lines of code", in seconds
  to 30 minutes.
- When functions could not be matched, they were inlined and the decision procedure "runs for
  hours or even fails to reach a decision".
- Multiplication, division and modulo burden the SAT solver.
- SymDiff, as cited there, handled "about 10 programs of several hundreds of lines each".

**Alive2 (PLDI 2021).** Validates per function pair and unrolls loops to a bound ("Bounded
Translation Validation").

**CBMC (arXiv 2302.02384).** A pass with `--unwind` is unsound unless the bounds amount to complete
unwinding. A bounded-model-checking pass counts as a proof only when `--unwinding-assertions` also
pass.

Our inference: flattening and MBA destroy the structural similarity these tools rely on, so
original-versus-obfuscated proofs fall into the slow, unmatched regime. Combined with
[[re-mba-obfuscation-defeats-smt-equivalence-proofs]], per-build proofs will cover only small
critical functions.

Labels to use:
- "proven for all inputs" only for an UNSAT result on loop-free code;
- "bounded to k" for bounded model checking without passing unwinding assertions;
- "differential testing, N inputs, 0 divergences" otherwise.

Answers item 4 of [[code-protection-field-open-questions]]. We found no measured
"function size versus solve time" for obfuscated code; our benchmark could produce it.

Verified 2026-11-07 against the primary sources listed. We did not check a SAW source.
