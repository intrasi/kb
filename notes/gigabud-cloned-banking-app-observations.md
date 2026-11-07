---
type: note
title: Group-IB estimates approximately $960,939 of losses in one Indonesian cloned-banking-app campaign
tags: [security, market]
date: 2026-11-07
by: karla+grok
confidence: low
sources: [https://www.group-ib.com/blog/vwork-app-cloning-gigabud-goldfactory/]
---

Schema: [[code-protection-evidence-schema]]. Index: [[code-protection-evidence-index]].

Three observations from the same Group-IB report. The loss figure is a campaign estimate for observed Indonesian Gigabud/Vwork activity in Feb–Jul 2026. The report documents cloned or modified banking apps. The dollars are not losses separately attributed to cloning alone. Device and login counts are vendor telemetry, not losses, and the login count is not a confirmed victim count.

<a id="ev-groupib-gigabud-losses-2026"></a>

### EV-GROUPIB-GIGABUD-LOSSES-2026

- id: EV-GROUPIB-GIGABUD-LOSSES-2026
- evidence_status: campaign-estimate
- measure: Group-IB estimated losses in observed Indonesian Gigabud/Vwork activity, Feb–Jul 2026. Report explicitly documents cloned/modified banking apps; campaign estimate, not losses separately attributed to cloning alone
- value: Approximately $960,939
- unit: USD
- period: Feb–Jul 2026
- publication_date: 9 Sep 2026; updated 27 Oct 2026
- source: [Group-IB, Vwork app cloning / Gigabud](https://www.group-ib.com/blog/vwork-app-cloning-gigabud-goldfactory/)
- confidence: low
- confidence_basis: Low—vendor estimate
- limitations: Campaign estimate, not losses separately attributed to cloning alone. The report documents cloned/modified banking apps. Vendor estimate. The qualifier Approximately is part of the value. Not a general mobile-banking fraud total.
- related: [EV-GROUPIB-GIGABUD-DEVICES-2026](#ev-groupib-gigabud-devices-2026); [EV-GROUPIB-GIGABUD-LOGINS-2026](#ev-groupib-gigabud-logins-2026)

<a id="ev-groupib-gigabud-devices-2026"></a>

### EV-GROUPIB-GIGABUD-DEVICES-2026

- id: EV-GROUPIB-GIGABUD-DEVICES-2026
- evidence_status: vendor-telemetry
- measure: Compromised devices observed in that Indonesian campaign; not losses
- value: Approximately 1,469 devices
- unit: devices
- publication_date: 9 Sep 2026
- source: [Group-IB, Vwork app cloning / Gigabud](https://www.group-ib.com/blog/vwork-app-cloning-gigabud-goldfactory/)
- confidence: low
- confidence_basis: Low—vendor telemetry
- limitations: Not losses. Vendor telemetry for that Indonesian campaign. The qualifier Approximately is part of the value.
- related: [EV-GROUPIB-GIGABUD-LOSSES-2026](#ev-groupib-gigabud-losses-2026); [EV-GROUPIB-GIGABUD-LOGINS-2026](#ev-groupib-gigabud-logins-2026)

<a id="ev-groupib-gigabud-logins-2026"></a>

### EV-GROUPIB-GIGABUD-LOGINS-2026

- id: EV-GROUPIB-GIGABUD-LOGINS-2026
- evidence_status: vendor-telemetry
- measure: Potentially compromised logins observed in that campaign; not confirmed victim count or losses
- value: 1,281 logins
- unit: logins
- publication_date: 9 Sep 2026
- source: [Group-IB, Vwork app cloning / Gigabud](https://www.group-ib.com/blog/vwork-app-cloning-gigabud-goldfactory/)
- confidence: low
- confidence_basis: Low—vendor telemetry
- limitations: Not a confirmed victim count and not losses. Vendor telemetry.
- related: [EV-GROUPIB-GIGABUD-LOSSES-2026](#ev-groupib-gigabud-losses-2026); [EV-GROUPIB-GIGABUD-DEVICES-2026](#ev-groupib-gigabud-devices-2026)
