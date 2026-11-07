---
type: note
title: "xollvm, kagura and O-MVLL load as LLVM plugins; ollvm17 and Polaris need their own LLVM build"
tags: [security, demo]
date: 2026-11-07
by: tea+claude
confidence: high
sources: [re-dossier-02-obfuscation-techniques-engines, https://github.com/und3ath/xollvm, https://github.com/qusamulab/kagura, https://github.com/open-obfuscator/o-mvll, https://github.com/DreamSoule/ollvm17, https://github.com/za233/Polaris-Obfuscator]
---

State of the repos on 2026-11-07:

| Tool | LLVM | Licence | Loads as plugin | Notes |
| --- | --- | --- | --- | --- |
| xollvm | 22, 23 | Apache-2.0 with LLVM exceptions | yes, `-fpass-plugin` | Passes: mba, substitution, bcf, flattening, strenc, vm, constenc, split, fmerge. Release v0.12.0 (31 Oct 2026) has plugins for Linux x64 and macOS arm64 only. |
| kagura | 17 to 22 | MIT | yes; Windows uses `kagura-opt` | No substitution/MBA pass. Prebuilt for LLVM 19/21/22 Linux x86_64 and 21/22 macOS arm64. |
| O-MVLL | – | Apache-2.0 | yes, `-fpass-plugin` | Active (pushed 29 Oct 2026). Not yet evaluated by us. |
| DreamSoule/ollvm17 | 17.0.6 | **none** | no: patch the LLVM tree and rebuild | A prebuilt zip exists. No licence file, so we have no right to redistribute it. Last commit 8 Oct 2024. |
| Polaris | 16.0.6 | Apache-2.0 | no: full llvm-project build | Prebuilt v1.0 toolchain for Ubuntu 22.04 x86_64. |

Tigress works on C source with no LLVM: [[re-tigress-virtualization-costs-42-to-247x-runtime]].
Before building, confirm our machines are Linux x64 or macOS arm64; xollvm has no plugin for
other platforms.

Verified 2026-11-07: each figure above was checked against the primary source listed in `sources:`.
