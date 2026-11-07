---
type: note
title: Code obfuscation fits implementation secrecy but does not replace protection of credentials configuration or access
tags: [security, formal-methods, idea, customer]
date: 2026-11-07
by: luka+codex
confidence: moderate
sources: [https://github.com/OWASP/owasp-istg/blob/main/src/03_test_cases/firmware/README.md, https://docs.docker.com/build/building/secrets/, https://docs.nvidia.com/cuda/cuda-binary-utilities/, https://docs.tia.siemens.cloud/r/en-us/v21/protecting-blocks/setting-up-and-removing-block-copy-protection-s7-1200-s7-1500-s7-1200-g2, https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/SourceMap]
---

The target list in [[reverse-engineering-targets-and-intelligence-map]] spans several security problems. A transformation system only addresses some of them.

| Asset/problem | Appropriate role for verified obfuscation | Necessary boundary |
|---|---|---|
| Proprietary algorithm in supported native code | Raise the cost of reconstructing its implementation | Must measure attacker outcomes; no guarantee of secrecy |
| Local license or integrity decision | Potentially complicate locating and modifying the decision | Signing, key handling and server/hardware authority remain separate |
| Credentials accidentally embedded in an image | At most an added delay | Remove shared secrets; use appropriate storage and provisioning |
| Factory recipes, machine settings, logs and customer files | Code transformations generally do not protect these data | Access control, encryption and lifecycle handling are different tasks |
| Vulnerabilities in firmware | Could slow some investigation | It does not fix the bug; equivalent code can preserve a vulnerability |
| Model weights or FPGA bitstreams | Requires specialized techniques | A C/LLVM transformation proof does not extend automatically to these artifacts |
| Observable product behavior | May obscure its implementation | Cannot prevent all imitation from inputs and outputs |

OWASP's firmware guidance describes obfuscation as an impediment to analysis, while separately requiring secure handling of secrets. It explicitly rejects treating complete prevention of RE as achievable. [Firmware test cases](https://github.com/OWASP/owasp-istg/blob/main/src/03_test_cases/firmware/README.md).

**Not all leakage needs decompilation.** Docker warns against build arguments/environment variables for secrets because they can persist in the image. Browser source maps can expose original client source. Packaging hygiene can therefore matter before sophisticated protection. [Docker](https://docs.docker.com/build/building/secrets/), [MDN](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/SourceMap).

**Specialized artifacts have specialized tooling.** NVIDIA documents disassembly of CUDA binaries; this establishes inspectability, not automatic recovery of complete source or a ready GPU obfuscation market. [CUDA tools](https://docs.nvidia.com/cuda/cuda-binary-utilities/).

**Industrial know-how protection already exists.** Siemens STEP 7 V21 documents binding block execution to a CPU or memory card, used with know-how protection. A startup must establish incremental value over deployed controls rather than assume industrial software is unprotected. [Vendor documentation](https://docs.tia.siemens.cloud/r/en-us/v21/protecting-blocks/setting-up-and-removing-block-copy-protection-s7-1200-s7-1500-s7-1200-g2).

Product judgment: prove a supported transformation's semantics under stated assumptions, then separately test extraction resistance, performance, timing, integration and release effort. No single equivalence result proves the security or safety of an industrial installation. See [[verified-obfuscation-research-links]].
