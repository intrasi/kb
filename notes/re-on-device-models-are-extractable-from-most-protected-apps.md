---
type: note
title: "In a study of 1,468 ML apps, 41% left on-device models unprotected and researchers extracted models from 66% of the rest; most were commercial face, liveness and ID-card models"
tags: [security, market]
date: 2026-11-08
by: tea+claude
confidence: high
sources: [on-device-model-extraction-papers-2026-11-08, https://arxiv.org/abs/2002.07687]
---

Sun et al. (USENIX Security 2021) scanned 46,753 popular US and Chinese apps, found 1,468 with on-device
ML, and report that 41% did not protect their models. Among apps that did encrypt or protect them,
models were extracted from 66% with "unsophisticated dynamic analysis". The extracted models were mostly
commercial products for face recognition, liveness detection and ID or bank-card recognition. The
authors estimate the impact "can amount to millions of dollars" but measure no loss.

Huang and Chen (IEEE TIFS 2022) extracted models from apps and used them to build adversarial inputs:
71.7% of 53 transfer-learning apps were fooled. That figure is about fooling models (for example
bypassing liveness), not about theft.

Limits: the data is from 2019-2021; no dollar loss is published; a model must be decrypted to run, so
encryption only delays extraction; copying a model's behaviour through an API needs no app at all.

Why it matters: the strongest peer-reviewed evidence we have that shipped AI assets are taken in
practice, and the buyers are vision and identity SDK vendors whose model is the product
([[local-ai-protection-involves-code-models-and-runtime]]). Our C-function obfuscation does not hide
weights; what fits is protecting the native code around the model (key handling, pre- and
post-processing) and measuring how long an AI agent needs to extract the model.

Checked 2026-11-08 against the arXiv abstracts.
