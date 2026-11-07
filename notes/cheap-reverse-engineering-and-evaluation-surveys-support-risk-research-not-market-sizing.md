---
type: note
title: New cheap-reverse-engineering analysis and evaluation surveys support the research thesis but do not size buyer demand
tags: [security, agents, market]
date: 2026-11-07
by: luka+codex
confidence: moderate
sources: [https://arxiv.org/abs/2610.35633, https://arxiv.org/abs/2307.07300, https://www.elastic.co/security-labs/threat-command/llm-reversing-vs-llm-obfuscation]
---

- **Cheap Reverse Engineering and What It Will Do**, Ilan Mandel, Madiha Zahrah Choksi, Joey Castillo, Sebastian Benthall and James Grimmelmann. [Preprint](https://arxiv.org/abs/2610.35633), first submitted October 26, 2026; version 2 October 30. Legal/technical analysis of falling RE costs and consequences for competition and ownership, not a buyer survey. Its examples distinguish behavior-based reimplementation from binary analysis. This matters because binary obfuscation cannot prevent all copying of publicly observable behavior. Abstract and relevant full-text sections inspected; no universal cloning capability inferred.
- **Evaluation Methodologies in Software Protection Research**, Bjorn De Sutter, Sebastian Schrittwieser, Bart Coppens and Patrick Kochberger. [Preprint](https://arxiv.org/abs/2307.07300), July 14, 2023; revision April 30, 2024. Abstract reports review of 571 papers across 113 evaluation aspects and identifies methodological weaknesses. It supports careful attack-goal evaluation, not a claim of no existing useful benchmarks. Abstract inspected.
- Elastic Security Labs, [The Cost of Understanding](https://www.elastic.co/security-labs/threat-command/llm-reversing-vs-llm-obfuscation), April 21, 2026. Exploratory static-only reversing and iterative LLM-developed defenses against compiled targets. This qualifies any broad claim that adaptive LLM obfuscation exists only at source level. It is not a shipped verified-obfuscation product or customer-demand study.

Checked 2026-11-07. Related: [[verified-obfuscation-research-links]], [[algorithm-protection-demand-intersection-remains-unproven-for-named-buyers]].
