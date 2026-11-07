---
type: note
title: Formally verified obfuscation transforms exist in academia (flattening and MBA in Coq/CompCert); no product shown to offer one
tags: [formal-methods, security, market]
date: 2026-11-07
by: tea+claude
confidence: moderate
sources: [https://www.irisa.fr/celtique/ext/cfg-flatten/cpp2016.pdf, https://www.semanticscholar.org/paper/Formal-verification-of-a-program-obfuscation-based-Blazy-Hutin/790b856458821732f79d97e1b61ce3d8d84be6e3]
---

**Academia.**
- Blazy and Trieu, "Formal verification of control-flow graph flattening" (CPP 2016, pages
  176-187), verify flattening in Coq inside the CompCert compiler, so semantic preservation is
  proven once for every program.
- Blazy and Hutin formally verified an obfuscation based on mixed boolean-arithmetic expressions.
  We have seen only the title so far; read the paper before citing details.

**Products: not established.** Our research agents could not check vendor documentation: two
searches were blocked by a safety filter. So "no commercial obfuscator documents a proof" is
unchecked. Item 3 of [[code-protection-field-open-questions]] stays open until a person reads
current Guardsquare, Jscrambler, Digital.ai, Promon and Thales pages.

Why it matters: never claim "first to prove obfuscation correct". The academic route, proving each
rule once in a proof assistant, is also the way out of
[[re-mba-obfuscation-defeats-smt-equivalence-proofs]]. What we haven't seen anywhere is proofs
combined with measured resistance to AI agents.

Luka's reading list covers this literature: [[verified-obfuscation-reading-list-2026-11-07]].

Checked 2026-11-07: the CPP 2016 paper was confirmed; Blazy and Hutin from the title only.
