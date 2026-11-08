---
type: note
title: "No open benchmark reports lift with confidence intervals and cost-to-break curves for user-chosen protection configs"
tags: [security, agents, idea]
date: 2026-11-07
by: tea+claude
confidence: moderate
sources: [re-dossier-01-benchmarks-and-grading, https://arxiv.org/html/2608.11469, https://arxiv.org/abs/2605.10597, https://github.com/agentrebench/AgentRE-Bench, https://arxiv.org/abs/2505.07360, https://arxiv.org/abs/2607.12507, https://generalanalysis.com/malwarebench]
---

What existing work covers:

| Benchmark | What it measures | Varies protection? |
| --- | --- | --- |
| CrackMeBench | 8 public calibration CrackMes plus 12 template-generated tasks | – |
| AgentRE-Bench v3.1 | 23 levels | stripping only |
| BinMetric | 1,000 binary-analysis questions | – |
| RARE-Bench | clean versus adversarial binaries | – |
| MalwareBench | malware analysis | – |
| SRE-Bench | hardening presets | yes, fixed presets on private binaries, no CIs ([[re-sre-bench-measures-hardening-lift-on-private-binaries]]) |

Vendor studies:
- Thales compares protected and unprotected, with one run and no CI
  ([[re-protection-buys-cost-not-impossibility]]).
- Promon compares obfuscation passes with zero-shot prompts
  ([[re-stacked-obfuscation-passes-cut-llm-success-in-vendor-study]]).
- No published AI-agent benchmark was found from Guardsquare or Digital.ai.
- Update 2026-11-07: vendors now sell closed AI-resistance scores. Digital.ai offers to "use AI to
  probe your app ... then score it"; EntropyJS scores every build; VeilCC sells "a measured number".
  None publishes its method or claims a proof ([[competitor-claims-vendor-pages-2026-11-07]]). The gap
  is the open, rerunnable method, not the existence of a score.

The gap that survives: an *open* benchmark where the user chooses the protection configuration,
reporting lift with confidence intervals and cost-to-break as a survival curve against budget.
Do not claim "first AI reverse-engineering benchmark" or "first to measure defensive lift".

Moderate confidence: this rests on a search that found nothing, which cannot prove nothing exists.
Re-check before pitching.

Searched 2026-11-07.
