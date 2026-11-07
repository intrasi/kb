---
type: note
title: Improving existing protection configurations is a testable opportunity but demand for our AI and proof layer remains unvalidated
tags: [customer, market, idea, security, formal-methods]
date: 2026-11-07
by: luka+codex
confidence: low
sources: [https://docs.sentinel.thalesgroup.com/ldk/LDKdocs/Env-Win/Java/Optimizing_Protection_Settings.htm, https://cpl.thalesgroup.com/resources/software-monetization/all4tec-secure-offline-software-licensing-case-study, https://www.wibu.com/case-studies/success-stories/story/detail/euresys-protecting-cross-platform-machine-vision.html]
---

## Conclusion from the five-segment follow-up

There is concrete reported commercial protection demand in industrial software, connected devices, on-prem enterprise products and local AI. We do not have representative numbers for how much of each sector buys obfuscation, how much it spends, or how much incremental demand exists for AI-guided verified transformations. Hardware IP has established protection workflows, including vendor-provided encryption, but less direct purchase evidence for an additional product in this research. Checked 2026-11-07.

Qualitative ranking below is our inference from product fit and evidence, **not market size or measured demand intensity**:

| Initial discovery order | Evidence of existing workflow/budget | Where we could enter | Principal risk |
| --- | --- | --- | --- |
| 1. Industrial vision/native algorithm vendors | Euresys and adjacent named industrial customers | Supported native library protection, selection, latency regression and attack-cost comparison | Existing protection may already be adequate; cross-platform/long-life compatibility |
| 2. On-prem native ISVs and appliances | ALL4TEC maintenance pain; Hexagon hardening; ThreatOptix deployment | Add automation/measurement around builds while retaining licensing | Most pain may be licensing administration, which our verifier does not solve |
| 3. Local AI with proprietary native components | CONNECTEVE named offline case plus commercial protection runtimes | Native operators/wrappers, model export checks and compatibility testing | Model secrecy, GPU semantics and confidential compute are different capabilities |
| 4. General connected-device firmware | ZAP Surgical named deployment and microcontroller offerings | Supported non-safety-critical native components | Hardware/toolchain fragmentation, timing, safety validation and key provisioning |
| 5. FPGA/RTL | Vendor tool and standard support; free encryption capability | Potential separate hardware workflow product | Different semantics, synthesis/timing and free incumbent capabilities |

## What a legacy target actually means

Good candidates: brittle in-house protection scripts; outdated protection configurations; repeated manual choices about sensitive/hot functions; several supported platform builds whose protection settings drift; changing app releases without systematic resistance measurements. These are prospect-qualification hypotheses; not every customer has these problems.

Evidence supporting the search:

- Euresys reported fragmented legacy tools/platform gaps and already migrated to a unified solution. This is a **past migration**, not a currently unresolved lead.
- ALL4TEC reported ongoing engineering burden before its migration. Existing commercial tools have already solved at least part of that pain.
- Thales' Java guide explicitly describes suboptimal default method choices and manual customization. That is a concrete configuration surface, with a language-specific scope.
- Current competitors already offer automation, profilers, granular protection and AI-threat positioning. AI alone, selecting methods alone, and on-prem operation alone are not established differentiation.

## Concrete product hypothesis

Build a local toolchain integration that takes customer-designated critical functions and representative workloads, proposes supported protection configurations, rejects invalid/unsupported changes, measures runtime/size, and evaluates remaining builds against independently scored attacks. Emit a reproducible build recipe and evidence showing exactly what was verified, tested and attacked. Human asset designation and threat modeling remain necessary; code context alone does not reveal business value.

It can generate value through **either** stronger empirical resistance at an acceptable engineering/performance cost **or** fewer engineer-hours at comparable protection. Do not require both in the first pilot. Preserve existing licensing, device identity and update mechanisms unless the customer specifically needs migration. A compiler integration is one option; a post-build-only customer may be unable to supply the IR needed for our current verification approach.

Formal evidence must follow the artifact boundary: source/IR proof → compiler/backend → optional third-party wrapper → packaging/signing → target device. A proof at one arrow does not certify all later stages or intended anti-tamper reactions. Unsupported transformations, timeouts and failed checks need explicit rejection; do not call passing samples a formal proof.

## Minimal customer validation

Recruit actual users of existing protectors, ask for the last painful protected release and request a representative supported component. Compare against their tuned existing configuration and automation, not just unprotected code. Record engineer-hours, number of failed builds/regressions, build time, supported scope, runtime/size and independently scored attacker cost/success. Fix search and attack budgets; use held-out inputs/tasks and reject model refusals as evidence of security. An improvement on synthetic programs proves a technical result only.

No interviews, outreach, customer budget confirmation or pilots were performed in this research. No measured engineering savings or efficacy advantage has been established. Top-down app-security market estimates in [[re-market-sizing-tam-sam-som]] do not fill these segment-specific gaps.

## Underlying evidence

- [[industrial-protection-demand-includes-maintaining-platform-and-license-compatibility]]
- [[connected-device-protection-demand-is-real-but-obfuscation-is-only-one-layer]]
- [[offline-enterprise-vendors-report-protection-and-licensing-maintenance-pain]]
- [[local-ai-protection-has-a-named-offline-customer-and-established-deployment-workflows]]
- [[hardware-ip-protection-is-established-but-needs-a-different-product]]
