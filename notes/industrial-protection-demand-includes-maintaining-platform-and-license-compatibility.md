---
type: note
title: Industrial protection customers buy IP defense together with platform coverage and long-lived licensing
tags: [customer, market, security]
date: 2026-11-07
by: luka+codex
confidence: moderate
sources: [https://www.wibu.com/case-studies/success-stories/story/detail/euresys-protecting-cross-platform-machine-vision.html, https://content.helpme-codesys.com/en/CODESYS%20Development%20System/_cds_encrypting_application.html, https://content.helpme-codesys.com/en/CODESYS%20Security%20Agent/_csa_encrypting_bootapplication.html]
---

## Evidence of actual demand

[Euresys' CodeMeter case](https://www.wibu.com/case-studies/success-stories/story/detail/euresys-protecting-cross-platform-machine-vision.html) describes replacing fragmented tools and limited platform coverage as demand shifted toward Linux. AxProtector protects Windows/Linux code; License Central provisions modular, perpetual and offline licenses; dongles or CmActLicenses authorize execution. The vendor reports 80–90% of Euresys licenses use hardware dongles and support cycles exceed 15 years. These are deployment-specific vendor claims, not industrial market penetration or audited security results.

This establishes a real commercial workflow and a migration trigger. It does not establish that customers want to remove dongles or replace their licensing platform with an AI obfuscator. Industrial customers may value stable offline operation more than novelty.

## Current workflows

Machine-vision/native-library workflow, exemplified by Euresys:

1. Build native application/library for each supported platform.
2. Apply vendor protection and configure runtime/license integration.
3. Issue feature-based or machine/customer-specific entitlements.
4. Deploy the protected binary and compatible licensing components.
5. Maintain customer compatibility and supported upgrades. Application regression/latency testing is our recommended release practice, not a measured Euresys process disclosed in the case.

PLC application workflow is different. [CODESYS application protection](https://content.helpme-codesys.com/en/CODESYS%20Development%20System/_cds_encrypting_application.html) supports encryption/signing of downloads and boot applications. Its [certificate workflow](https://content.helpme-codesys.com/en/CODESYS%20Security%20Agent/_csa_encrypting_bootapplication.html) obtains a controller encryption certificate, configures application security in the engineering environment, then encrypts downloads/online changes. It is not simply an LLVM pass on arbitrary C source.

[MVTec's HALCON commercial licensing page](https://www.mvtec.com/products/halcon/editions-licensing/get-a-license) distinguishes development/runtime licenses and provides custom quotes. This confirms runtime monetization, not that every HALCON integrator buys a separate obfuscator. [HALCON embedded installation guidance](https://go.mvtec.com/acton/media/43208/installation-guide-evaluation-halcon-embedded) includes CodeMeter Runtime Lite support.

## Reverse-engineering risks

Potential losses: copying inspection/calibration logic, imitating premium features, license-check patching, or recovering process know-how. These are asset-specific threat hypotheses consistent with the customer case, not measured losses. Runtime manipulation of control software could affect production or safety **if** an exploitable integrity weakness exists; code recovery alone does not imply control of a machine.

## Where we could improve legacy workflows

Promising initial target: a customer-owned C/C++ vision library built with a supported compiler, where valuable functions and tight latency constraints can be identified. Add protection configuration search, supported equivalence checks, representative workload profiling and fixed-budget attack evaluation around the existing release process.

Preserve licensing and provisioning unless the customer specifically wants migration. Prefer non-safety-critical algorithms for the first pilot. Bare PLC projects, inaccessible legacy toolchains, inline assembly, device I/O and safety-certified motion control need different integration and guarantees. A function-level semantics result does not establish worst-case timing or hardware behavior.

Demand strength: direct evidence for particular industrial software customers; no representative adoption, expenditure, or willingness-to-switch rate established. Related comparison: [[legacy-protection-workflows-offer-a-testable-integration-opportunity]].
