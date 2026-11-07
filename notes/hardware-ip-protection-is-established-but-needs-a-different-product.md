---
type: note
title: FPGA and simulation IP protection is established but its workflows differ from C software obfuscation
tags: [customer, market, security, formal-methods]
date: 2026-11-07
by: luka+codex
confidence: moderate
sources: [https://www.amd.com/en/products/adaptive-socs-and-fpgas/intellectual-property/ip-encryption.html, https://docs.amd.com/r/en-US/ug570-ultrascale-configuration/Bitstream-Encryption-and-Authentication, https://www.mathworks.com/help/rtw/model-protection.html]
---

## What the evidence does and does not establish

[AMD's IP-encryption documentation](https://www.amd.com/en/products/adaptive-socs-and-fpgas/intellectual-property/ip-encryption.html) supports IEEE 1735-compliant HDL encryption and rights handling for third-party IP. The encryption license is available at no cost to AMD customers; customers consuming encrypted IP need no special decryption license. Thus integration into a commercial ecosystem is evidence of a protection requirement, **not** evidence of an incremental paid obfuscation market. No representative adoption percentage, protection spend or named buyer of an additional AI layer was established here.

## Distinct workflows

- **Supplier HDL/IP:** author distributes encrypted Verilog/VHDL/SystemVerilog with permitted tool operations. Authorized design tools process it. Tool interoperability and access policy matter. Protecting source distribution does not automatically establish confidentiality at every later stage.
- **Finished FPGA configuration:** [AMD UltraScale documentation](https://docs.amd.com/r/en-US/ug570-ultrascale-configuration/Bitstream-Encryption-and-Authentication) describes hardware AES decryption/authentication. The [bitstream workflow](https://docs.amd.com/r/en-US/xapp1098-tamper-resist-designs/Bitstream-Confidentiality-and-Authentication-Symmetric) encrypts output through Vivado using supplied keys. Provisioning hardware keys and authenticated configuration are distinct from hiding RTL or native software.
- **Simulation/control models:** [MathWorks](https://www.mathworks.com/help/rtw/model-protection.html) packages derived compiled/obfuscated artifacts with optional functionality/password control and signatures. It recommends comparing protected and original models. [Recipients](https://www.mathworks.com/help/simulink/ug/use-a-protected-model-in-simulation.html) face platform/compiler compatibility requirements; a harness supports isolated testing. A Simulink protected model is not the same artifact as an FPGA bitstream or ML weights.

## Risks

Potential losses are design cloning, unauthorized IP reuse, recovery of proprietary signal-processing/control logic and malicious alteration where integrity is weak. [AMD security bulletin AMD-SB-8034](https://www.amd.com/en/resources/product-security/bulletin/amd-sb-8034.html) describes a specific optical side-channel exposure for 7-Series configurations using decryption in programmable logic and ICAP partial reconfiguration. It requires invasive physical access and specialized equipment; it is not evidence that ordinary AI agents can extract all FPGA designs. Its physical mitigations cannot be replaced by a C obfuscation pass.

## Opportunity and constraint

An agent might assist toolchain-policy checks, version compatibility, regression harnesses or searches over semantics-preserving RTL transforms. These are hypotheses, not observed unmet demand. RTL equivalence, synthesis, timing closure and power/area constraints require hardware tooling and expertise. Reusing a native-code verifier does not solve them. Compiled simulation libraries could fit our C/native scope when source/build access and semantic support exist; FPGA protection should be a separate product track.

Related: [[legacy-protection-workflows-offer-a-testable-integration-opportunity]].
