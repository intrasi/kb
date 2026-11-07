---
type: note
title: Reverse engineering needs an accessible artifact rather than an internet-connected target
tags: [security, agents, customer]
date: 2026-11-07
by: luka+codex
confidence: high
sources: [https://github.com/scriptingxss/owasp-fstm, https://redballoonsecurity.com/siemens-discovery/, https://cert-portal.siemens.com/productcert/html/ssa-482757.html, https://documents.trendmicro.com/assets/wp/wp-industrial-robot-security.pdf]
---

**A machine can be completely offline and its software can still be reverse engineered.** Access to a copy of the program, firmware, relevant hardware or observable behavior is the prerequisite. Obtaining that copy, understanding it and reaching someone else's deployed installation are separate problems.

## The access ladder

| Access available | What can be studied | Main boundary |
|---|---|---|
| Downloadable installer, SDK or update | Files shipped with that release | Download may require a customer account; encryption may prevent inspection |
| Purchased or secondhand device | Its firmware, components and any retained configuration | Readout protection, secure hardware and physical extraction costs vary |
| Engineering software or simulator | Controller logic, file formats and simulated behavior | Simulator coverage may differ from real hardware |
| Authorized local execution | Runtime behavior and, subject to platform permissions, process state | Trusted execution and privilege separation can constrain observation |
| Access to a specific installation or its backup | Its actual configuration and process data | A generic firmware sample does not contain every customer's data |
| Only a remote service interface | Inputs, outputs and protocol behavior | Does not automatically reveal the server binary or implementation |

OWASP FSTM explicitly includes vendor downloads and hardware acquisition routes, and treats static inspection separately from runtime and emulation. Encryption and unfamiliar architectures are obstacles, rather than evidence that a sample cannot exist. [Methodology](https://github.com/scriptingxss/owasp-fstm).

**Historical concrete example:** the 2017 robot study explains that ABB controller firmware accompanied RobotStudio/RobotWare and that simulators could support investigation without a complete robot. It distinguishes that from access needed to test on physical equipment. Its availability statements and equipment prices are historical, not a check of today's download terms. [Original report, pp. 17–18](https://documents.trendmicro.com/assets/wp/wp-industrial-robot-security.pdf).

**Physical research example:** Red Balloon's 2023 S7-1500 work demonstrated offline analysis and firmware decryption on affected hardware. Siemens confirms physical tampering is required for CVE-2022-38773 and lists replacement hardware revisions. This does not imply a universal remote compromise of Siemens controllers or that current revisions share the flaw. [Research](https://redballoonsecurity.com/siemens-discovery/), [vendor advisory, updated 2025-01-14](https://cert-portal.siemens.com/productcert/html/ssa-482757.html).

## Two distinctions for explaining this to customers

1. Buying one product can reveal reusable implementation knowledge. Reaching a different owner's installation still requires an access path and applicable weakness.
2. A cloud RE agent needs access to its model service. That does **not** require the analyzed target to be online. Conversely, a local agent may analyze locally; output quality depends on model and tools.

Static analysis means reading artifacts without running them. Dynamic analysis means observing execution; it may require a device or compatible environment. Neither inherently requires an Internet-connected target.

See [[reverse-engineering-targets-and-intelligence-map]] and [[ai-plc-targeting-is-documented-but-does-not-show-an-obfuscation-failure]].
