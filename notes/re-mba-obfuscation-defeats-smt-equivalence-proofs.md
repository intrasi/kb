---
type: note
title: MBA obfuscation defeats the SMT solvers you would use to prove the obfuscated code equivalent
tags: [formal-methods, security]
date: 2026-11-07
by: tea+claude
confidence: high
sources: [re-dossier-04-formal-verification-equivalence, https://www.usenix.org/system/files/sec21-liu-binbin.pdf, https://hex-rays.com/blog/deobfuscation-with-goomba, https://patents.google.com/patent/US12585460B2/en]
---

**MBA-Blast (Liu et al., USENIX Security 2021).**
- Using Z3 "to check the equivalence of the original expression and its MBA obfuscated form …
  Z3 fails to return a result in five hours". Five hours was the timeout they set, not a measured
  upper bound.
- After MBA-Blast simplified 70 MBA opaque predicates, Z3 solved all of them.

**Hex-Rays gooMBA (blog, 25 January 2023).** Calling the solver "often times out or takes an
unreasonable amount of time", so gooMBA first runs several hundred random tests on each candidate.

**US patent 12,585,460 B2 (Thales DIS CPL USA, granted 24 March 2026).** It builds MBA opaque
predicates on purpose so that solving time "increases exponentially with the bitwidth" under
bit-blasting.

Why it matters: the obfuscator and the verifier use the same technology in opposite directions.
- Obfuscate weakly enough to prove automatically, and an attacker's simplifier cracks it too.
- Obfuscate strongly, and our own proof times out.

The way out is to prove each rewrite rule once, as academic work already does
([[re-verified-obfuscation-exists-in-academia]]), rather than per build. State this tension openly
in the pitch.

Verified 2026-11-07 against the primary sources listed.
