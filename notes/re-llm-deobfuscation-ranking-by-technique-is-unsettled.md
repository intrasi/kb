---
type: note
title: "Which single obfuscation pass resists LLMs best is unsettled: one paper's table and abstract disagree"
tags: [security, agents]
date: 2026-11-07
by: tea+claude
confidence: low
sources: [re-dossier-02-obfuscation-techniques-engines, https://arxiv.org/html/2505.19887v1]
---

*Deconstructing Obfuscation* (arXiv 2505.19887) scored 8 LLMs on OLLVM output from 0 (trivial)
to 5 (failed). The abstract says seven models; the method section lists eight. Its table and its
abstract rank the techniques in opposite orders:

- **Table:**
  - control-flow flattening scored 0 to 1-2 for every model;
  - instruction substitution scored 4, 4, 5 and 4 for four of the five models tested on it, and
    1-2 for Claude 3.7;
  - bogus control flow ranged from 0 to 5, depending on the model.
- **Abstract:** "bogus control flow (low resistance)", "control flow flattening (moderate
  resistance)", and instruction substitution highest.

What the paper does support:
- All models failed (score 5) against combined techniques.
- Single passes vary a lot by model.

Caveats:
- The authors work at Promon AS, so this is not independent of
  [[re-stacked-obfuscation-passes-cut-llm-success-in-vendor-study]].
- The paper calls its 0 to 5 scale "inherently" subjective.
- It tested OLLVM instruction substitution, not a dedicated MBA pass.
- It did not test renaming.

Why it matters: do not build on a per-technique ranking. Our benchmark should measure each single
pass itself, per model. The dossier's "Correction #1" overstated this.

Verified 2026-11-07: each figure above was checked against the primary source listed in `sources:`.
