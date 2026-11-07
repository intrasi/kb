---
type: source
title: Primary-source excerpts on offline reverse engineering targets and exposed intelligence
tags: [security, agents, market, customer]
date: 2026-11-07
by: luka+codex
url: https://www.ic3.gov/CSA/2026/260819.pdf
---

Collected 2026-11-07. Short verbatim excerpts, not complete snapshots. Each entry identifies the original source. Historical laboratory studies, vendor documentation and threat observations are different kinds of evidence. This source collection is immutable after filing.

1. NSA/CISA/FBI/DOE/EPA, joint advisory indexed by IC3 on 19 August 2026, PDF p. 4. Excerpt: "Compromise of sensitive operational data, including proprietary process recipes, control strategies, and facility configurations"
   URL: https://www.ic3.gov/CSA/2026/260819.pdf
2. OWASP FSTM, firmware acquisition. Excerpt: "From the vendor's support site"
   URL: https://github.com/scriptingxss/owasp-fstm
3. OWASP ISTG, disclosure of source and binaries. Excerpt: "the reverse-engineering process can be impeded, e.g., by obfuscating the code."
   URL: https://github.com/OWASP/owasp-istg/blob/main/src/03_test_cases/firmware/README.md
4. Siemens SSA-482757, originally 10 January 2023, updated 14 January 2025. Excerpt: "As exploiting this vulnerability requires physical tampering with the product"
   URL: https://cert-portal.siemens.com/productcert/html/ssa-482757.html
5. Red Balloon Security, 10 January 2023. Excerpt: "With physical access to a single device"
   URL: https://redballoonsecurity.com/siemens-discovery/
6. Nozomi Networks Labs, 14 December 2023. Excerpt: "These details were acquired through extensive reverse engineering efforts on an iQ-R R08SFCPU."
   URL: https://www.nozominetworks.com/blog/nozomi-networks-labs-presents-zero-day-vulnerabilities-affecting-mitsubishi-electric-safety-plcs-at-black-hat-mea-23
7. ESET, April 2023, PDF p. 7. Excerpt: "Percentages are based on the 16 functioning devices with unique network configurations."
   URL: https://web-assets.esetstatic.com/wls/en/papers/white-papers/used_routers_corporate_secrets.pdf
8. Trend Micro/Politecnico di Milano, 2017, PDF p. 18. Excerpt: "the controller firmware for ABB robots is included in RobotWare, part of the RobotStudio software suite"
   URL: https://documents.trendmicro.com/assets/wp/wp-industrial-robot-security.pdf
9. Check Point Research, 12 August 2018. Excerpt: "HP Inc published the patched firmware on their site"
   URL: https://research.checkpoint.com/2018/sending-fax-back-to-the-dark-ages/
10. Microsoft firmware analysis overview, updated 23 September 2026. Excerpt: "See which firmware components have publicly known security vulnerabilities and exposures."
    URL: https://learn.microsoft.com/en-us/azure/firmware-analysis/overview-firmware-analysis
11. NVIDIA TensorRT-RTX disclosures, updated 15 October 2026. Excerpt: "it may be possible to reverse-engineer the original model from the engine file."
    URL: https://docs.nvidia.com/deeplearning/tensorrt-rtx/latest/reference/cybersecurity-disclosures.html
12. NVIDIA CUDA binary utilities documentation, overview. Excerpt: "CUDA provides two binary utilities for examining and disassembling cubin files and host executables"
    URL: https://docs.nvidia.com/cuda/cuda-binary-utilities/
13. Ender, Moradi and Paar, USENIX Security 2020, abstract. Excerpt: "only access to a configuration interface is needed."
    URL: https://www.usenix.org/conference/usenixsecurity20/presentation/ender
14. Docker build secrets documentation. Excerpt: "Build arguments and environment variables are inappropriate for passing secrets to your build, because they persist in the final image."
    URL: https://docs.docker.com/build/building/secrets/
15. MDN SourceMap header documentation, modified 21 November 2025. Excerpt: "Developer tools use the source map to reconstruct the original source"
    URL: https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/SourceMap
16. Siemens STEP 7 V21, publication date November 2025. Excerpt: "binds execution of the block to a specific CPU or a specific memory card."
    URL: https://docs.tia.siemens.cloud/r/en-us/v21/protecting-blocks/setting-up-and-removing-block-copy-protection-s7-1200-s7-1500-s7-1200-g2
17. Anthropic September 2026 report, GTG-10007. Excerpt: "more than a dozen possible zero day findings in a single month."
    URL: https://www.anthropic.com/threat-intelligence-report-september-2026

Additional sources re-opened: SDProget/Thales and DME/PreEmptive case studies, whose excerpts are already filed in [[cad-forensics-sdk-demand-web-excerpts-2026-11-07]]; SRE-Bench arXiv:2608.11469 and Cheap Reverse Engineering arXiv:2610.35633, already linked in the research notes.

Access limitation: CISA's HTML copy of AA26-231A returned HTTP 403. The complete joint advisory was successfully opened at the original FBI IC3 PDF URL above, linked from https://www.ic3.gov/CSA. No third-party proxy was used as evidence.
