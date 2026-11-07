---
type: note
title: Tigress virtualization costs 42x to 247x runtime on crypto kernels, and Tigress needs a licence for commercial use
tags: [security, demo]
date: 2026-11-07
by: tea+claude
confidence: high
sources: [re-dossier-02-obfuscation-techniques-engines, https://arxiv.org/html/2601.10261v1, https://tigress.wtf/download.html]
---

**Runtime cost.** XuanJia (arXiv 2601.10261, Zou et al., January 2026) measured Tigress v4.0.10
virtualization on five crypto kernels:

| Kernel | Slowdown |
| --- | --- |
| AES | 246.88x |
| DES | 59.83x |
| MD5 | 71.39x |
| RC4 | 42.02x |
| SHA1 | 85.08x |

XuanJia's own VM costs 120x to 337x.

**Licence.**
- Tigress is closed-source C-to-C, "free to use for non-profit organizations". Commercial use needs a
  licence from the University of Arizona.
- Binaries exist for Linux x86-64, Darwin x86-64 and Linux ARMv7.
- A startup cannot ship it without that licence; a research benchmark can use it.

Our inference, not from the paper: virtualization only fits small, rarely run, secret functions.
Report overhead next to every lift number.

Verified 2026-11-07: each figure above was checked against the primary source listed in `sources:`.
