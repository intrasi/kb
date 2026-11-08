---
type: source
title: "On-device ML model extraction papers: Sun et al. USENIX Security 2021 and Huang and Chen IEEE TIFS 2022 (abstract excerpts)"
tags: [security, agents]
date: 2026-11-08
by: tea+claude
url: https://arxiv.org/abs/2002.07687
---

Excerpts collected 2026-11-08 from the arXiv abstract pages and search summaries.

## Sun, Sun, Lu, Mislove. "Mind Your Weight(s): A Large-scale Study on Insufficient Machine Learning Model Protection in Mobile Apps." USENIX Security 2021, pp. 1955-1972.

URLs: https://arxiv.org/abs/2002.07687 ; https://www.usenix.org/conference/usenixsecurity21/presentation/sun-zhichuang ; tool https://github.com/RiS3-Lab/ModelXRay

- Analysed 46,753 popular apps from US and Chinese markets; identified 1,468 ML apps.
- "41% of them are not protecting their models."
- Of apps that use protection or encryption, models were extracted from 66% "via unsophisticated dynamic analysis techniques".
- "The extracted models are mostly commercial products and used for face recognition, liveness detection, ID/bank card recognition, and malware detection."
- Impact "can amount to millions of dollars for different stakeholders" (qualitative estimate, no measured loss).

## Huang, Chen. "Smart App Attack: Hacking Deep Learning Models in Android Apps." IEEE TIFS 17 (2022) 1827-1840. doi:10.1109/TIFS.2022.3172213

URL: https://arxiv.org/abs/2204.11075

- Crawled Google Play: 394 apps with 1,345 TFLite models.
- Extracts the on-device model by reverse engineering the app, identifies the pre-trained model it was fine-tuned from, and builds a grey-box adversarial attack.
- "Among 53 apps adopting transfer learning, we find that 71.7% of them can be successfully attacked." Apps include medicine, automation and finance.
- Note: 71.7% is the success rate of adversarial inputs that fool the model, not of model theft.
