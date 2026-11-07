---
type: note
title: Payment-app standards set the bar as attack effort, not technique; PCI MPoC uses an attack rating of 25 points
tags: [regulation, market, customer]
date: 2026-11-07
by: tea+claude
confidence: moderate
sources: [re-dossier-05-competitors-market-funding, https://raw.githubusercontent.com/OWASP/masvs/master/Document/11-MASVS-RESILIENCE.md, https://licelus.com/resources/knowledge_hub/emvco-sbmp-security-requirements, https://promon.io/resources/knowledge-center/pci-mpoc-compliance-mobile-payments-cots]
---

The compliance locators are Karla's: [[client-side-protection-compliance-locators]] (MASVS, PSD2,
DORA, EMVCo, PCI MPoC; no universal obfuscation mandate). This note adds what makes a measured
score relevant.

- **PCI MPoC.** Read only through a vendor summary (Promon); we did not open the PCI SSC PDF.
  - Requirements 1B-1.14, 1C-4 (including 1C-4.4) and 2B-1.2 call for anti-tampering, rated
    against an attack rating of 25 points.
  - "The MPoC standard doesn't mandate any methods, as long as they are robust."
- **EMVCo SBMP v1.5.** Read only through a vendor quotation (Licel).
  - Section 2.4.1 says protection "should" be applied, with alternatives: software protection
    tools and/or a virtual TEE.
  - Section 4.1 says "must be applied", listing white-box crypto, obfuscation and binary
    protection "for example".
- **OWASP MASVS.** Anti-tampering or obfuscation "must not be used as a substitute for proper
  security architecture".

Why it matters: the bar is defined by attack effort, not by technique, and a measured resistance
score fits that frame. It feeds hypothesis A4 in [[do-people-need-ai-resistant-code-protection]].
The PCI and EMVCo wording is secondhand until someone reads the primary PDFs
([[re-research-gaps-to-verify]]).

Checked 2026-11-07.
