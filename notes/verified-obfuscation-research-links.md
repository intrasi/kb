---
type: note
title: Linked research supports verified transformations and AI-guided selection but not the combined startup hypothesis
tags: [security, formal-methods, agents, market, idea]
date: 2026-11-07
by: luka+codex
confidence: moderate
sources: [https://web.tecnico.ulisboa.pt/nuno.lopes/pubs.php?id=alive2-pldi21, https://www.site.uottawa.ca/~phil/papers/sad20.pdf, https://arxiv.org/abs/2609.19583, https://repository.hkust.edu.hk/ir/Record/1783.1-109134]
---

# Linked bibliography and evidence map

This adds links and evidence qualifications to the existing immutable team-supplied
reading list, [[verified-obfuscation-reading-list-2026-11-07]]. Sources were located
or inspected during the conversation ending 2026-11-07. This is a curated literature
map, not an exhaustive review, proof reproduction, licensing audit, or patent search.
Preprints and vendor reports have different evidentiary weight from peer-reviewed
papers. We have not run the cited tools or reproduced their measurements.

Main hypothesis: [[verified-obfuscation-could-reduce-protection-engineering-effort]].

## Adoption and production experience

| Paper | Relevance |
| --- | --- |
| [An Empirical Study on the Robustness of Android Third-Party Library Detection Tools Against Advanced Obfuscation, ICSE 2026](https://aoa0.github.io/pubs/icse26.pdf) | Table 2 quantifies renaming, package restructuring, and optimization adoption; does not measure company budgets. |
| [An Empirical Study of Code Obfuscation Practices in the Google Play Store, 2025 manuscript](https://arxiv.org/html/2502.04636v1) | Large historical Android sample; whole-APK classification and imperfect tool attribution limit conclusions. |
| [A Large Scale Investigation of Obfuscation Use in Google Play, 2018](https://arxiv.org/abs/1801.02742) | Distinguishes developer protection from included libraries and examines developer usability difficulties. |
| [Field experience with obfuscating million-user iOS apps in large enterprise mobile development, 2019](https://faculty.ist.psu.edu/wu/papers/obf-iii.pdf) | Production deployment, selective protection, and measured overhead; a historical case rather than market-wide prevalence. |

Detailed findings: [[obfuscation-is-common-in-popular-android-apps]] and
[[production-obfuscation-can-target-a-small-part-of-an-app]].

## Formal verification and machine-checked proofs

| Paper | What can be reused or investigated |
| --- | --- |
| [Alive2: Bounded Translation Validation for LLVM, PLDI 2021](https://web.tecnico.ulisboa.pt/nuno.lopes/pubs.php?id=alive2-pldi21) | Practical automatic refinement checking for concrete LLVM transformations. [Implementation](https://github.com/AliveToolkit/alive2). Loop checking is bounded; interprocedural transformations unsupported. |
| [Formal Verification of Control-flow Graph Flattening, CPP 2016](https://fileserver-az.core.ac.uk/download/49378179.pdf) | Coq simulation proof for a specific flattening implementation over CompCert Clight. A proof does not automatically transfer to our different implementation. |
| [Formal Verification of a Program Obfuscation Based on Mixed Boolean-Arithmetic Expressions, CPP 2019](https://doi.org/10.1145/3293880.3294103) | Verified arithmetic/bitwise obfuscation. Bibliographic record located; primary full text was not retrieved in this session, so implementation details need follow-up. |
| [Towards Formal Verification of Program Obfuscation, 2020](https://www.site.uottawa.ca/~phil/papers/sad20.pdf) | Coq proofs in restricted languages; discusses composition limitations. Coauthor Bahman Sistany is affiliated with Cloakware Research, Irdeto: commercial-adjacent prior art exists. [Referenced proof repository](https://github.com/weiyunlu/coq-certified-obfuscation). |
| [Enhancing Translation Validation of Compiler Transformations with Large Language Models, 2024 preprint](https://arxiv.org/abs/2401.16797) | Related LLM-assisted validation work; investigate actual guarantee boundaries before reuse. |
| [LLM-Vectorizer: LLM-based Verified Loop Vectorizer, 2024 preprint](https://arxiv.org/abs/2406.04693) | Adjacent generation-and-checking architecture for optimization rather than obfuscation. |
| [LLVM Translation Validation Automated with Large Language Models and Lean, 2026 preprint](https://arxiv.org/abs/2609.19583) | Trivet uses structured LLM-assisted proof generation checked by Lean. Reported results concern selected transformations, not arbitrary production software or obfuscation. |

Two approaches should remain distinct: prove a transformation algorithm correct
once, or validate each concrete generated result. The latter is the initial
prototype direction. Correctness proofs are separate from protection-strength claims.

## AI-selected and AI-generated obfuscation

| Paper | Relevance |
| --- | --- |
| [Generating Effective Software Obfuscation Sequences With Reinforcement Learning, 2022](https://repository.hkust.edu.hk/ir/Record/1783.1-109134) | Direct prior art for learned sequencing with an overhead objective; source repository abstract inspected, full text not reproduced. DOI: [10.1109/TDSC.2020.3041655](https://doi.org/10.1109/TDSC.2020.3041655). |
| [Generating Adversarial Computer Programs Using Optimized Obfuscations, ICLR 2021](https://research.ibm.com/publications/generating-adversarial-computer-programs-using-optimized-obfuscations) | Optimizes transformation selection and locations against ML models; different task from general commercial IP protection. |
| [Can LLMs Obfuscate Code? A Systematic Analysis of Large Language Models into Assembly Code Obfuscation, AAAI 2025](https://ojs.aaai.org/index.php/AAAI/article/view/34672) | MetamorphASM benchmark; does not establish production reliability or blanket equivalence guarantees. |
| [Simplicity by Obfuscation: Evaluating LLM-Driven Code Transformation with Semantic Elasticity, EASE 2025](https://arxiv.org/abs/2504.14024) | Small Python-function study: LLM transformations can simplify structure and correctness is not automatic. |

## AI reverse engineering and evaluation

| Paper | Relevance |
| --- | --- |
| [Evaluation of Large Language Models on Code Obfuscation, AAAI 2024 student abstract](https://ojs.aaai.org/index.php/AAAI/article/view/30517) | Early evidence on LLM understanding of transformed code; historical models and limited tasks. |
| [Towards LLM-Resistant Software Protection: Agent Failure Patterns in CTF Reverse Engineering, BAR 2026](https://www.ndss-symposium.org/wp-content/uploads/bar2026-58.pdf) | Three agents on 24 CTF tasks; identifies failure patterns. CTF outcomes are not a production security guarantee. |
| [Can LLMs Deobfuscate Binary Code? A Systematic Analysis of Large Language Models into Pseudocode Deobfuscation, 2026 preprint](https://arxiv.org/abs/2604.08083) | BinDeObfBench; relevant attacker capability and benchmark design research. |

## Research overviews and competitor disclosures

These are useful primary descriptions, not independently validated product results.

- [Verifying Code Correctness of Protected Software through Translation Validation, ERCIM News, October 2024](https://ercim-news.ercim.eu/en139/special/verifying-code-correctness-of-protected-software-through-translation-validation): breaks complex protection into smaller LLVM passes for validation. Research overview, not a full conference paper.
- [Quarkslab: Defeating AI-Assisted Reverse Engineering, August 2026](https://blog.quarkslab.com/defeating-ai-assisted-reverse-engineering-or-at-least-trying-to.html): exploratory agent attacks and benchmark leakage. Supports independent scoring and isolation; not a broad protection guarantee.
- [Digital.ai: LLM-enhanced Quick Protect Agent v2, March 2026](https://digital.ai/press-releases/digital-ai-brings-enterprise-grade-post-build-mobile-app-protection-into-the-ci-cd-pipeline-with-llm-enhanced-quick-protect-agent-v2/): claims code-aware targeting and integrated testing. Does not establish arbitrary AI-generated transformations or formal proofs.
- [Guardsquare: profiling and AI-driven testing, July 2026](https://www.guardsquare.com/blog/mobile-app-profiling-security-ux): describes protection placement, compatibility, performance, and profiling effort.
- [QShield product description](https://www.quarkslab.com/qshield-software-protection-cybersecurity/): describes 30+ obfuscation schemes, diversification, and runtime protection; not evidence of formal proof coverage.
- [Guardsquare 2026 survey announcement](https://www.guardsquare.com/press-release/mobile-apps-are-the-new-attack-surface): customer-count claim and commissioned survey methodology.
- [ThreatOptix deployment announcement](https://content.quarkslab.com/threatoptix): named Linux/IoT protection customer; vendor reports initial integration in less than a week. Not representative deployment-time data.

## Remaining research questions

1. Which transformations and valuable real customer functions can we validate within
   a useful time budget? No production-scale coverage number has been established.
2. Does whole-application context outperform tuned configurations and ordinary search
   under equal candidate and compute budgets?
3. Does verification reduce human debugging effort more than it adds build and
   integration cost?
4. Do customers have enough unmet pain to pay for an additional tool or migration?
5. Which research artifacts can be reused commercially under their actual licenses?
6. How much measured protection survives unseen attackers, dynamic analysis, and
   compiler optimization of the final binary?

All citations are linked inline. These open questions remain hypotheses and gaps,
not established product capabilities.
