---
type: note
title: Named vendors demonstrate algorithm protection demand but none in this search publicly establishes all three buying triggers
tags: [customer, market, security, agents]
date: 2026-11-07
by: luka+codex
confidence: moderate
sources: [algorithm-protection-demand-intersection-web-excerpts-2026-11-07, https://www.maat.digital/copy-protection/, https://www.wibu.com/case-studies/success-stories/story/detail/euresys-protecting-cross-platform-machine-vision.html, https://www.quarkslab.com/partner-zap-surgical-robots-protection/, https://www.preemptive.com/wp-content/uploads/2023/11/DME-Forensics-Case-Study.pdf, https://cdn.wibu.com/fileadmin/wibu_downloads/Case_Studies/D/DIgSILENT/DIgSILENT-EN.pdf]
---

## Finding

There is credible demand for protecting valuable shipped software. This investigation did **not identify a named company publicly documenting all three conditions together**: valuable shipped algorithm, unresolved protection-maintenance pain, and observed AI reconstruction of that algorithm. This is a bounded search result, not proof that such buyers do not exist.

AI reversing has concrete evidence: an anonymous protection customer, technical experiments and reported malicious firmware analysis. Those signals justify customer discovery; they do not establish our obtainable revenue, market-wide incident rate or willingness to switch.

## Named leads and missing evidence

Case studies are selected vendor accounts unless marked first-party. A commercial deployment is a budget-category signal, not a disclosed contract value. Historical migrations do not prove an unresolved present problem.

| Candidate | Valuable software shipped | Maintenance/migration evidence | Public AI reconstruction of its algorithm | Qualification priority (our judgment) |
| --- | --- | --- | --- | --- |
| [Euresys](https://www.wibu.com/case-studies/success-stories/story/detail/euresys-protecting-cross-platform-machine-vision.html) | Machine-vision libraries | Historical fragmented tools/platform coverage; CodeMeter migration reportedly solved this | Not found | High: native libraries, measurable latency, clear algorithm value |
| [MAAT](https://www.maat.digital/copy-protection/) | Commercial DSP/audio tools | First-party account calls protection burdensome and describes replacing Wibu with an in-house cloud system | Not found | High: ask whether the remaining problem is algorithm extraction or licensing experience |
| [DME Forensics](https://www.preemptive.com/wp-content/uploads/2023/11/DME-Forensics-Case-Study.pdf) | Proprietary DVR evidence-recovery logic | Reports renewal and good support; counterevidence to assuming dissatisfaction | Not found | Medium: strong IP motivation; .NET requires a different implementation from LLVM |
| [DIgSILENT](https://cdn.wibu.com/fileadmin/wibu_downloads/Case_Studies/D/DIgSILENT/DIgSILENT-EN.pdf) | PowerFactory grid-analysis software | Historical CodeMeter case praises maintainability and flexibility | Not found | Medium: budget-category signal, weak switching trigger |
| [CONNECTEVE](https://cpl.thalesgroup.com/sites/default/files/content/case_studies/connecteve-ai-medical-software-cs.pdf) | Local medical-AI Python software/models | Existing research documents offline deployment and protection adoption | Not found | Separate model-protection track; native code proof does not protect weights |
| [ZAP Surgical](https://www.quarkslab.com/partner-zap-surgical-robots-protection/) | Beam targeting, dose calculation, planning and image guidance | QShield deployment announced April 2026; no unresolved maintenance pain disclosed | Not found | Lower for first pilot: clinically sensitive integration, established supplier |
| [Anonymous Quarkslab customer](https://blog.quarkslab.com/defeating-ai-assisted-reverse-engineering-or-at-least-trying-to.html) | Obfuscated library; underlying business unspecified | Raised concerns about existing protection | AI recovered hidden strings, according to Quarkslab; **not a demonstrated algorithm clone** | Strongest direct concern signal; cannot identify or approach from this account |

DIgSILENT's case reports adoption in 2016, more than 2,500 customers and over 40 modules in its historical case. These are DIgSILENT deployment figures, not numbers of obfuscation buyers or a current 2026 customer census.

## Recommended initial customer profile

**Hypothesis:** a small or midsize vendor of non-safety-critical native vision/image-processing libraries, with source/build access, offline customer execution and identifiable valuable functions. Audio/DSP is a useful adjacent interview group, but strict timing and floating-point behavior complicate a verification MVP. Prioritize an actual dissatisfied team over a famous logo.

The initial product opportunity is a repeatable workflow: select customer-designated valuable functions → propose supported transformations → check semantics → profile representative workloads → run equal-budget AI reconstruction attempts → produce a release report. Preserve existing license provisioning.

Formal verification only helps with modeled transformation correctness. It does not establish secrecy, prevent extracting model files, fix licensing administration, or prove worst-case execution time.

## What would validate or reject this

For five discovery conversations, request concrete artifacts rather than hypothetical interest:

1. Which proprietary function ships, and what would a competitor gain by reconstructing it?
2. Last release affected by protection: engineer-hours, build failure, regression or support incident; distinguish intentional RASP responses from transformation bugs.
3. Actual AI reversing attempt: binary, tools, task, budget, independently checked recovered behavior. Strings and license bypass are different outcomes from reproducing the valuable algorithm.
4. Existing protection supplier and renewal owner; what measurable improvement would justify an evaluation?
5. Will they provide a bounded function/workload for an authorized pilot and commit engineering time? A paid pilot is stronger evidence than agreement with the risk narrative.

These are proposed questions, not completed interviews. A useful pilot must improve attack cost at an accepted latency/size budget **or** reduce release-engineering effort at comparable resistance. Compare against the customer's current tuned tool, not only an unprotected binary.

## Research scope

Checked 2026-11-07. Searched combinations of AI reverse engineering, proprietary algorithms, customer cases, obfuscation integration, maintenance, industrial practitioners and audio/DSP protection; followed original vendor, researcher, documentation and paper links. Social comments and general piracy/IP-loss estimates were not treated as customer validation. No representative survey, buyer count, incremental AI-loss estimate or price acceptance was established. No outreach was sent.

## Related findings

- [[quarkslab-reports-a-customer-ai-recovery-of-hidden-library-strings]]
- [[ai-firmware-reversing-is-observed-in-malicious-operations-but-is-not-algorithm-theft-demand]]
- [[thales-envelope-plus-shows-a-paid-incumbent-response-to-ai-binary-analysis]]
- [[existing-protectors-already-automate-profiling-and-release-integration]]
- [[cheap-reverse-engineering-and-evaluation-surveys-support-risk-research-not-market-sizing]]
- [[legacy-protection-workflows-offer-a-testable-integration-opportunity]]

## Sources

Primary URLs are linked in the table. Short raw excerpts and search limitations: [[algorithm-protection-demand-intersection-web-excerpts-2026-11-07]].
