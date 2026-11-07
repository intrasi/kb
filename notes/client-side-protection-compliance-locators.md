---
type: note
title: MASVS, PSD2, DORA, EMVCo, and PCI MPoC locators do not impose a universal obfuscation mandate
tags: [regulation, security]
date: 2026-11-07
by: karla+grok
confidence: low
sources: [https://mas.owasp.org/MASVS/11-MASVS-RESILIENCE/, https://eur-lex.europa.eu/eli/reg_del/2018/389/2023-09-12/eng, https://eur-lex.europa.eu/eli/reg/2022/2554/oj/eng, https://www.emvco.com/wp-content/uploads/loa/EMVCo_SECN0130_N_05_2025.pdf, https://www.pcisecuritystandards.org/standards/mobile-payments-on-cots-mpoc/]
---

Schema: [[code-protection-evidence-schema]]. Index: [[code-protection-evidence-index]].

Nine locators. `instrument_class` is `standard` (OWASP MASVS and PCI MPoC), `regulation` (PSD2 RTS and DORA), or `certification` (EMVCo SECN0130). The package assigned no per-record confidence; the frontmatter label is not a grade of the quoted text. PSD2 does not name or mandate obfuscation. DORA does not mandate code obfuscation. MASVS resilience is a security standard, not a statute. SECN0130 lists protection techniques on one certificate and is not a universal requirement that all banking apps use obfuscation. The PCI page’s primary-text obfuscation or tamper-resistance clause was not found, and vendor references were not promoted to primary evidence.

<a id="ev-masvs-resilience-2"></a>

### EV-MASVS-RESILIENCE-2

- id: EV-MASVS-RESILIENCE-2
- evidence_status: standard
- instrument_class: standard
- locator: OWASP MASVS-RESILIENCE-2
- measure: “The app implements anti-tampering mechanisms.”
- publication_date: date not found
- source: [OWASP MASVS resilience](https://mas.owasp.org/MASVS/11-MASVS-RESILIENCE/)
- mandate_limitation: Security standard, not regulation. Chapter explicitly says absence of resilience measures does not itself constitute a vulnerability
- limitations: Security standard, not regulation. Chapter explicitly says absence of resilience measures does not itself constitute a vulnerability
- related: [EV-MASVS-RESILIENCE-3](#ev-masvs-resilience-3); [EV-MASVS-RESILIENCE-4](#ev-masvs-resilience-4)

<a id="ev-masvs-resilience-3"></a>

### EV-MASVS-RESILIENCE-3

- id: EV-MASVS-RESILIENCE-3
- evidence_status: standard
- instrument_class: standard
- locator: OWASP MASVS-RESILIENCE-3
- measure: “The app implements anti-static analysis mechanisms.” Chapter names “code obfuscation, anti-debugging, anti-tampering, and runtime application self-protection.”
- publication_date: date not found
- source: [OWASP MASVS resilience](https://mas.owasp.org/MASVS/11-MASVS-RESILIENCE/)
- mandate_limitation: Does not establish a universal legal obfuscation mandate
- limitations: Does not establish a universal legal obfuscation mandate
- related: [EV-MASVS-RESILIENCE-2](#ev-masvs-resilience-2); [EV-MASVS-RESILIENCE-4](#ev-masvs-resilience-4)

<a id="ev-masvs-resilience-4"></a>

### EV-MASVS-RESILIENCE-4

- id: EV-MASVS-RESILIENCE-4
- evidence_status: standard
- instrument_class: standard
- locator: OWASP MASVS-RESILIENCE-4
- measure: “The app implements anti-dynamic analysis techniques.”
- publication_date: date not found
- source: [OWASP MASVS resilience](https://mas.owasp.org/MASVS/11-MASVS-RESILIENCE/)
- mandate_limitation: Threat-specific defense-in-depth; not a replacement for secure architecture
- limitations: Threat-specific defense-in-depth; not a replacement for secure architecture
- related: [EV-MASVS-RESILIENCE-2](#ev-masvs-resilience-2); [EV-MASVS-RESILIENCE-3](#ev-masvs-resilience-3)

<a id="ev-psd2-rts-9-3-a"></a>

### EV-PSD2-RTS-9-3-A

- id: EV-PSD2-RTS-9-3-A
- evidence_status: regulation
- instrument_class: regulation
- locator: PSD2 RTS, Article 9(3)(a)
- measure: Requires “separated secure execution environments through the software installed inside the multi-purpose device.”
- publication_date: original publication 13 Mar 2018; consolidated version 12 Sep 2023
- source: [PSD2 RTS](https://eur-lex.europa.eu/eli/reg_del/2018/389/2023-09-12/eng)
- mandate_limitation: Applies in the stated multipurpose-device authentication context; does not name or mandate obfuscation
- limitations: Applies in the stated multipurpose-device authentication context; does not name or mandate obfuscation
- related: [EV-PSD2-RTS-9-3-BC](#ev-psd2-rts-9-3-bc)

<a id="ev-psd2-rts-9-3-bc"></a>

### EV-PSD2-RTS-9-3-BC

- id: EV-PSD2-RTS-9-3-BC
- evidence_status: regulation
- instrument_class: regulation
- locator: PSD2 RTS, Article 9(3)(b)–(c)
- measure: Requires mechanisms ensuring software/device “has not been altered by the payer or by a third party”; mechanisms mitigating consequences where alterations occur
- publication_date: original publication 13 Mar 2018
- source: [PSD2 RTS](https://eur-lex.europa.eu/eli/reg_del/2018/389/2023-09-12/eng)
- mandate_limitation: Explicit alteration/integrity requirement; no prescribed obfuscation technique
- limitations: Explicit alteration/integrity requirement; no prescribed obfuscation technique
- related: [EV-PSD2-RTS-9-3-A](#ev-psd2-rts-9-3-a)

<a id="ev-dora-9-2"></a>

### EV-DORA-9-2

- id: EV-DORA-9-2
- evidence_status: regulation
- instrument_class: regulation
- locator: DORA, Article 9(2)
- measure: Requires appropriate ICT security tools/policies/procedures, including ensuring software/data/network security
- publication_date: 27 Dec 2022
- source: [DORA](https://eur-lex.europa.eu/eli/reg/2022/2554/oj/eng)
- mandate_limitation: General security outcome requirement; does not mandate code obfuscation
- limitations: General security outcome requirement; does not mandate code obfuscation
- related: [EV-DORA-9-4-F](#ev-dora-9-4-f)

<a id="ev-dora-9-4-f"></a>

### EV-DORA-9-4-F

- id: EV-DORA-9-4-F
- evidence_status: regulation
- instrument_class: regulation
- locator: DORA, Article 9(4)(f)
- measure: Requires appropriate, comprehensive documented policies for patches and updates
- publication_date: 27 Dec 2022
- source: [DORA](https://eur-lex.europa.eu/eli/reg/2022/2554/oj/eng)
- mandate_limitation: Patch/update requirement—not application shielding or obfuscation mandate
- limitations: Patch/update requirement—not application shielding or obfuscation mandate
- related: [EV-DORA-9-2](#ev-dora-9-2)

<a id="ev-emvco-secn0130"></a>

### EV-EMVCO-SECN0130

- id: EV-EMVCO-SECN0130
- evidence_status: certification
- instrument_class: certification
- locator: EMVCo SBMP, certificate SECN0130, “Type” field
- measure: Official software-protection-tool certificate lists “Obfuscation, Tamper detection, Anti-instrumentation, Anti-debugging, Root detection.”
- publication_date: 16 May 2025
- source: [EMVCo certificate SECN0130](https://www.emvco.com/wp-content/uploads/loa/EMVCo_SECN0130_N_05_2025.pdf)
- mandate_limitation: Certification evidence, not a universal requirement that all banking apps use obfuscation. Exact normative SBMP clause not found
- limitations: Certification evidence, not a universal requirement that all banking apps use obfuscation. Exact normative SBMP clause not found

<a id="ev-pci-mpoc"></a>

### EV-PCI-MPOC

- id: EV-PCI-MPOC
- evidence_status: standard
- instrument_class: standard
- locator: PCI MPoC
- measure: Official page identifies the standard’s COTS payment-acceptance scope and laboratory evaluation framework
- publication_date: publication date not found
- source: [PCI SSC, Mobile Payments on COTS (MPoC)](https://www.pcisecuritystandards.org/standards/mobile-payments-on-cots-mpoc/)
- mandate_limitation: Exact primary-text obfuscation/tamper-resistance clause not found in this pass. Vendor references to requirements were not promoted to verified primary evidence. Payment brands manage compliance applicability
- limitations: Exact primary-text obfuscation/tamper-resistance clause not found in this pass. Vendor references to requirements were not promoted to verified primary evidence. Payment brands manage compliance applicability
