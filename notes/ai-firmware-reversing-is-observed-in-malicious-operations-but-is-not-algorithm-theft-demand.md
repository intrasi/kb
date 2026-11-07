---
type: note
title: Reported malicious AI firmware reversing validates a threat mechanism but not algorithm-theft purchasing demand
tags: [security, agents, customer]
date: 2026-11-07
by: luka+codex
confidence: moderate
sources: [https://www.anthropic.com/threat-intelligence-report-september-2026, https://faradaysec.com/ai-reverse-engineering-firmware-isa-recovery/]
---

Anthropic's September 2026 threat report describes GTG-10007 using agent workflows to decompile appliance firmware, develop vulnerability hypotheses, write exploit code and test against lab copies. The report says one continuously running network-appliance workflow produced more than a dozen **possible** zero-day findings in a month. This is provider-observed malicious activity, not just a crackme demonstration. It is not an independently audited count of confirmed exploitable zero-days, a measurement of stolen algorithms, or evidence those vendors want our product.

Faraday separately describes a research pipeline reconstructing a proprietary JieLi processor ISA into Ghidra SLEIGH support. It combined LLM semantic inference with deterministic handling of numeric encoding and relied on vendor disassembly. Its authors label it a proof of concept. This supports investigating the erosion of obscure-platform barriers, not claiming arbitrary firmware can now be cloned automatically.

For appliance vendors, IP extraction and vulnerability discovery are distinct buying motives. Secure development, vulnerability remediation and key management remain necessary; obfuscation does not remove exploitable defects.

Sources: [Anthropic report](https://www.anthropic.com/threat-intelligence-report-september-2026), [Faraday research](https://faradaysec.com/ai-reverse-engineering-firmware-isa-recovery/), checked 2026-11-07. Related: [[algorithm-protection-demand-intersection-remains-unproven-for-named-buyers]].
