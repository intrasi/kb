---
type: note
title: Connected-device customers deploy software hardening alongside hardware, key and update controls
tags: [customer, market, security]
date: 2026-11-07
by: luka+codex
confidence: moderate
sources: [https://www.quarkslab.com/partner-zap-surgical-robots-protection/, https://content.quarkslab.com/threatoptix, https://api-www.codesys.com/fileadmin/user_upload/CODESYS_Group/Ecosystem/Up-to-Date/Security/Security-Advisories/Advisory2022-15_CDS-82335.pdf]
---

## Actual demand versus product targeting

[Quarkslab's 1 April 2026 announcement](https://www.quarkslab.com/partner-zap-surgical-robots-protection/) names ZAP Surgical as deploying QShield for sensitive software and data in ZAP-X surgical robots, including targeting/dose calculation and guidance algorithms. This is a stronger signal than a generic medical-device marketing page: a named deployment with a stated IP concern. It remains a vendor/partner announcement, not independent proof of efficacy or a published contract value.

[ThreatOptix's named deployment](https://content.quarkslab.com/threatoptix) covers a vendor of protection for Linux servers, cloud workloads and IoT devices. Its testimonial reports initial QShield integration in under a week. This supports real demand while challenging an assumption that all incumbent tools take months to integrate.

[ST's QShield partner listing](https://www.st.com/en/partner-products-and-services/qshield.html) documents a microcontroller/firmware offering, not a customer count. These examples do not establish how often camera, router, automotive or medical OEMs use obfuscation specifically.

## Documented workflow and dependencies

[Quarkslab's compiler-tooling description](https://blog.quarkslab.com/internship-offers-for-the-2026-2027-season.html) says its LLVM-based protection compiler replaces the regular compiler. This suggests a build-time integration for supported native code, with protection settings and runtime defenses where configured. Actual per-customer choices are not disclosed. The surrounding device release must also address trusted loading, authenticated updates, device credentials and hardware access according to its threat model; code hardening cannot substitute for those controls.

An existing legacy migration example is [CODESYS advisory 2022-15 / CVE-2022-4048](https://api-www.codesys.com/fileadmin/user_upload/CODESYS_Group/Ecosystem/Up-to-Date/Security/Security-Advisories/Advisory2022-15_CDS-82335.pdf). A specific older boot-application encryption implementation used weak cryptography, permitting decryption and manipulation of compiled code. The advisory prescribes an updated development system plus changing existing project security settings to certificate encryption and downloading again. Its alternative X.509 route and other CodeMeter uses were not affected. This is a concrete maintenance/migration gap, not evidence that all dongles or present-day CODESYS protection are broken. The remedy is the vendor's fix, not AI-generated cryptography or obfuscation alone.

## Consequences and evidence limits

- Commercial: unauthorized product cloning, feature unlocking, and recovery of proprietary algorithms or credentials.
- Operational: tampered firmware or updates can compromise integrity and availability where authentication/trust boundaries permit it.
- Safety: vulnerable medical/control systems may permit harmful commands. [FDA's 2019 MiniMed recall record](https://www.accessdata.fda.gov/scripts/cdrh/cfdocs/cfRes/res.cfm?id=175808) identifies potential wireless alteration of pump settings; it does not establish a reverse-engineering-caused injury or that obfuscation would fix protocol authorization.

[The US DOJ's Cisco counterfeiting case](https://www.justice.gov/archives/opa/pr/leader-massive-scheme-traffic-fraudulent-and-counterfeit-cisco-networking-equipment) documents devices carrying pirated software and bypasses of license/hardware-authenticity controls. It illustrates monetized copying and tampering, not solely reconstruction of algorithms, and provides no counterfactual evidence that our proposal would stop it. Do not turn counterfeit sales or restitution into an estimate of obfuscation-preventable losses.

## Improvement hypothesis

Offer supported native-component protection plus compatibility/overhead evidence in a reproducible build pipeline. Strong targets are supported embedded Linux applications or libraries where the OEM retains source/build access. Locked firmware, unsupported proprietary compilers, assembly, tight memory/timing limits and qualification obligations make general firmware transformation a poor first product.

Demand: directly demonstrated for selected customers; broad OEM adoption and startup-specific demand remain unknown. Related: [[legacy-protection-workflows-offer-a-testable-integration-opportunity]].
