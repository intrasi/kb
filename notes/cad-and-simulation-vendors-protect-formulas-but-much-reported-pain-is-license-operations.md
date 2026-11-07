---
type: note
title: CAD and simulation vendors protect valuable formulas but much documented workflow pain is license operations
tags: [customer, market, security, formal-methods]
date: 2026-11-07
by: luka+codex
confidence: moderate
sources: [cad-forensics-sdk-demand-web-excerpts-2026-11-07, https://cpl.thalesgroup.com/sites/default/files/content/case_studies/sdproget-leverages-thales-sentinel-to-implement-flexible-licensing-cs.pdf, https://en.industryarena.com/wibu-systems/blog/a-business-success-story-times-two--19056.html, https://www.glasercad.de/support/support-artikel/glaser-netzwerklizenzen-aktualisieren/, https://manuals.ggu-software.com/ger/ggu-consolidate-lizenzschutz, https://support.graphisoft.com/hc/en-us/articles/18783798430737-Re-Install-License-Key-Driver]
---

## Direct demand evidence

**SDProget is the clearest algorithm-value example in this investigation.** Its December 2024 Thales case describes electrical CAD based on AutoCAD, more than 12,000 customers and 20,000 installations. A named software engineer explicitly identifies proprietary engineering formulas as valuable IP. The company outgrew homegrown licensing/protection by 2015 and adopted Sentinel. The reported workflow includes hardware/software licenses, ERP/CRM integration, a self-service portal and thousands of annual updates. Automating key updates reportedly saved work. These figures describe this customer case; they are not current market counts, a protection contract value or measured AI-related losses. Most quantified workflow discussion concerns licensing, not correctness of obfuscation.

**GLASER/ISBCAD:** Wibu's February 2022 account describes a migration triggered in 2012 by .NET 4.0 incompatibility and inadequate previous protection. It also emphasizes sales-process integration. This is historical switching evidence. GLASER's own current support page confirms a concrete update process: stop all ISBCAD sessions, move the network dongle to an internet-connected workstation with ISBCAD, apply updates, return it to the server. Network licenses are unavailable during that operation. This establishes workflow friction, not duration, customer dissatisfaction or a task solved by an equivalence checker.

**GGU geotechnical software:** its first-party manual documents CodeMeter Runtime, product-code binding, USB, machine-bound software licenses and cloud containers, with license checks at startup and during execution. It establishes an additional deployed-software segment beyond mainstream CAD; it does not identify a particular obfuscation pass or willingness to change protection supplier.

**Graphisoft/Archicad:** its October 2023 support article documents reinstalling the CodeMeter driver when software/USB licenses cannot be found. This is first-party evidence of a real operational support issue; it supplies neither its frequency nor a link to code transformations. Do not pitch formal proofs as a remedy for a missing driver.

Existing simulation evidence: [[algorithm-protection-demand-intersection-remains-unproven-for-named-buyers]] covers DIgSILENT's CodeMeter deployment. SimVis' [LM-X case](https://www.x-formation.com/blog/lm-x-license-manager-customer-case-study-simvis/) adds a cross-platform simulation-data visualization buyer, but is licensing evidence rather than a verified obfuscation deployment.

## Current workflow and possible entry point

Evidence-grounded pattern: build engineering application/plugin → apply protection and integrate feature/license checks → generate entitlements → distribute executable plus license runtime → maintain customer upgrades and representative calculation outputs. The final regression-testing step is our recommended pilot practice, not a process disclosed by every named vendor.

**Our hypothesis:** isolate a customer-owned formula, geometry helper or optimization heuristic and protect it inside the existing licensing workflow. Compare output equivalence, representative performance and attacker reconstruction success. Standard published formulas or easily inferred behavior may have little protectable implementation value; ask which implementation detail actually provides advantage.

Floating point, numerical tolerances, solver convergence and third-party CAD dependencies complicate proof scope. A small supported function is a better first proof target than an entire simulation engine. No named AI reconstruction of these vendors' formulas was found in this bounded search. Existing paid protection does not establish willingness to buy our addition.

## Sources

Primary links above; raw excerpts: [[cad-forensics-sdk-demand-web-excerpts-2026-11-07]]. Related: [[cad-forensics-and-sdk-protection-have-different-buying-triggers-and-pilot-fit]]. Checked 2026-11-07.
