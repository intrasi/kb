---
type: note
title: Proprietary native SDK and vision-library vendors are plausible first markets for verified obfuscation
tags: [customer, market, idea, formal-methods]
date: 2026-11-07
by: luka+codex
confidence: low
sources: [https://www.preemptive.com/wp-content/uploads/2023/11/N-Software-Case-Study.pdf, https://www.wibu.com/case-studies/success-stories/story/detail/euresys-protecting-cross-platform-machine-vision.html, https://www.preemptive.com/wp-content/uploads/2023/11/Surgical-Theater-Case-Study-1.pdf]
---

## Hypothesis, not validated demand

Start discovery with smaller proprietary native SDK and industrial vision-library vendors, because their commercial product contains valuable callable algorithms that customers can inspect. Public component and vision cases establish adjacent category demand. They do **not** establish that a new C/LLVM formal-verification product is wanted or that native variants have the same purchasing process.

## Comparative assessment

These rankings are our qualitative inference, not measured customer scores or market-share data. Technical fit is relative to the proposed narrow C/C++/LLVM approach, not to a mature general obfuscation platform.

| Segment | Protection demand evidence | Fit to initial technique | Main adoption obstacle | Discovery priority |
| --- | --- | --- | --- | --- |
| Proprietary native SDKs/algorithm libraries | Component cases and direct SDK offerings; native scope must be qualified | Relatively good for selected supported functions | OEM compatibility, exported ABI, performance, incumbent licensing | First |
| Industrial vision software | Named protection/licensing customers | Relatively good for selected CPU logic | Floating point, vectorization, device support, latency | First |
| Specialized desktop/forensic tools | Named direct obfuscation customers | Depends heavily on .NET vs native implementation | Supporting correct runtime and established workflow | First interviews; implementation-specific |
| Audio DSP plugins | Historical customers and direct vendor account | Native code, but hard real-time/numerical constraints | Tight latency budget, platform/plugin compatibility, existing ecosystems | Second |
| Local AI component vendors | Explicit technical exposure and competing products | Good for some wrappers/operators; weak for full model protection | Asset confusion, GPU semantics, weight extraction | Second; attractive learning segment |
| Mobile banking and payment | Strong protection category evidence | Limited for Java/Kotlin/Swift/.NET under a C-only prototype | Mature platforms, broad RASP needs, procurement and assessments | Later product or partner route |
| Enterprise customer-hosted ISVs | Deployment/licensing evidence | Variable languages; substantial native opportunities | Whole-system integration and whether important IP is actually shipped | Qualify selectively |
| Games | Named commercial customers | Some C++ fit | Incumbents, full anti-tamper integration, compatibility, launch support | Later |
| General embedded/industrial firmware | Protection offerings and adjacent customer cases | Some C fit | Hardware access, RTOS/toolchains, memory and timing constraints | Later |
| Medical/automotive safety-critical control | Adjacent customer and industry evidence | Function proofs useful but insufficient | Validation processes, deadlines, qualification, long procurement | Later; avoid as first release target |
| FPGA/RTL IP | Explicit design-IP standard | Different semantics and toolchain | Hardware verification/encryption ecosystem | Separate product |

## Initial offer to test

"For a selected proprietary native component, produce measured harder-to-reconstruct builds while checking supported transformations preserve behavior and stay within an agreed performance budget."

Alternatively test reduced **engineer-hours** at comparable protection. Either outcome can justify a product; do not require both or silently trade one away. Formal verification might add build time while reducing debugging effort. See [[verified-obfuscation-could-reduce-protection-engineering-effort]].

## Qualification checklist for a real prospect

1. Which precise proprietary asset leaves your control, in which file and language?
2. Who can access the code or runtime, and what attack would create economic loss?
3. What do you use today, including free tools, in-house scripts and paid support?
4. What failed or consumed time in the last protected release? Ask for a concrete example.
5. What performance, size, build-time, ABI and platform limits apply?
6. Can we benchmark one isolated component against your current configuration?
7. Who owns budget, and what measured improvement would justify switching or adding a tool?

No outreach was sent and no customer interviews were completed by this research. Named cases are evidence and prospect analogues, not warm leads or promises of availability.

## A bounded discovery exercise

Create a deduplicated list of 15 candidate vendors: five native SDK vendors, five industrial vision vendors, five local-AI vendors with proprietary native components. Humans can seek five interviews and request one representative component under suitable terms. Record current workflow, painful release evidence, available budget and willingness to run a comparison. These are proposed research targets, not achieved results or statistically representative thresholds.

For the hackathon, use synthetic/self-authored code and report empirical protection lift plus verification scope. Do not claim customer validation from the existence of these industries.

## Sources

Purchase and adoption evidence with limitations: [[shipped-software-protection-customer-evidence]]. Full segment map: [[shipped-software-customer-landscape]]. AI-specific scope: [[local-ai-protection-involves-code-models-and-runtime]].
