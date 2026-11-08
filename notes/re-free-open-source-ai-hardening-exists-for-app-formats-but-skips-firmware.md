---
type: note
title: "A free MIT-licensed tool (bla-agents) hardens app formats against AI reverse-engineering agents and claims verified runtime equivalence, but it explicitly skips firmware and inflates files by orders of magnitude"
tags: [market, security, agents, pitch]
date: 2026-11-08
by: tea+claude
confidence: moderate
sources: [https://github.com/qybaihe/bla]
---

Reported by Tea on 2026-11-08 and checked against the repo page the same day. `qybaihe/bla`
(npm `bla-agents`, site bla.tools) is an MIT-licensed project by a solo developer that hardens shipped
artifacts against AI reverse-engineering agents, specifically the REA tool, by injecting format-valid
decoys and canaries and by exceeding the analyser's resource budgets ("poison, exhaust, hallucinate").
2.8k stars, 361 forks, 433 commits.

What it covers: JavaScript and TypeScript, Electron `.asar`, WebAssembly, SQLite, Safetensors, GGUF,
Go buildinfo, Erlang BEAM, EVM metadata, PCAP, Flutter and NVIDIA PTX. Designed for but unverified:
Python `.pyc`, Android DEX, .NET, JVM, ZIP.

Three findings that matter to [[0003-use-case-device-makers-against-competitor-reverse-engineering]]:

1. **It skips firmware.** The README lists firmware, SPIR-V, CUDA fatbinaries and AMD GPU objects as
   skipped. Our segment, C code in microcontrollers, is untouched.
2. **Its method cannot work on a microcontroller.** Stated growth: an Electron archive from 607 B to
   16.9 MiB, EVM bytecode from 16 B to 4.00 MiB, Go buildinfo from 50 KiB to 1.16 MiB. Device flash is
   measured in KB to a few MB, so exhausting an analyser by inflating the artifact is not available to
   us, and selective protection with bounded overhead stays the embedded approach
   ([[re-tigress-virtualization-costs-42-to-247x-runtime]]).
3. **Behaviour preservation is now commoditised, the open measurement is not.** It reports runtime
   equivalence 14/14 as the measured part of its benchmark, while labelling its headline token and cost
   multipliers (about 639x tokens, 304x cost) as "internal estimates". Combined with
   [[re-emproof-already-claims-proof-backed-firmware-obfuscation]], the proof is table stakes; what is
   still missing is a measurement anyone can rerun with their own configuration
   ([[re-open-configurable-lift-benchmark-is-the-remaining-gap]]).

Limits to state honestly: it is tuned to one analyser's current documented budgets, which can be raised;
the README itself says the Ghidra, Frida, LLDB and JADX paths were not run; and free tooling collapses
pricing for app and web formats, which is one more reason not to sell there
([[re-protection-is-sold-per-app-per-year-not-per-build]]).

Moderate confidence: every figure above is the project's own documentation, not independently checked.
Checked 2026-11-08.
