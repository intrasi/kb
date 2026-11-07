---
type: note
title: Code-protection evidence records use one schema, stable IDs, and unmerged vintages
tags: [market, security, regulation]
date: 2026-11-07
by: karla+grok
confidence: high
sources: []
---

Agents cite a record by file and ID. Example: [[in-app-protection-and-shielding-estimates]] `EV-CMI-IAP-2026`.

Catalogue of the 51 records: [[code-protection-evidence-index]]. These notes restate the cutoff package of 7 November 2026. They are analyst estimates, filings, surveys, or locators. They are not audited facts. USD is not implied: read `unit` when it is present. Ranges stay ranges. A later vintage does not replace an earlier record.

## Record fields

Required on every record:

- `id`: stable ID. New vintages get new IDs.
- `evidence_status`: controlled token, defined below.
- `measure`: the package’s exact measure, primary-evidence quote, or gap item.
- `publication_date`: exact package date, including partial dates and “not found” wording. Not normalized to a full day.
- `source`: Markdown link whose URL is the package URL, or `Not found` when the package has no URL.
- `limitations`: caveat that has to travel with a citation.

Populated only when the package supports them:

- `value`: exact value cell, qualifiers included (`Approximately`, `>`, ranges, `>700 respondents`).
- `unit`, `period`: parsed beside `value`. `period` is the year or interval the figure describes. It is not the forecast vintage.
- `vintage`: forecast or model vintage. Separate from `period`. When the package gave one combined publication/vintage statement, both fields repeat that statement.
- `confidence`: `high`, `moderate`, or `low`.
- `confidence_basis`: the package’s confidence cell when it said more than the bare level.
- `locator`: table, article, or certificate locator.
- `instrument_class`: `standard`, `regulation`, or `certification`. Same token as `evidence_status` on compliance records.
- `mandate_limitation`: exact applicability limit. On compliance records it matches `limitations`.
- `sample`, `geography`, `fieldwork`, `sponsorship`: on survey-response and survey-method records. Method records are canonical; response records repeat the frame and link the method IDs.
- `related`: other record IDs. Linked records are not substitutes.

`confidence` is omitted on compliance locators and explicit gaps because the package did not assign one. File-level confidence in frontmatter is the lowest assigned record confidence in that file, or `low` when no record confidence was assigned. Do not treat that file label as a grade of a quoted statute.

## evidence_status

`forecast`, `base-year-estimate`, `growth-forecast`, `not-found`, `cutoff-unverified`, `modeled-loss`, `activity-share`, `campaign-estimate`, `vendor-telemetry`, `disclosed-investment`, `disclosed-financing`, `disclosed-controlling-interest`, `disclosed-consideration`, `media-estimate`, `survey-response`, `survey-method`, `standard`, `regulation`, `certification`, `gap`.

## Do not collapse these distinctions

- Gartner and IDC totals stay apart. Category definitions and vintages differ.
- `EV-CMI-IAP-2026` is CMI’s January 2026 forecast for 2026 global in-app protection. It is not a shielding-only market size and not actual spending. The shielding-only 2026 value is `EV-INSIGHT-SHIELD-2026-NOT-FOUND`.
- `EV-CHAMBER-VIDEO-PIRACY-LOSS-2019` is not app-tampering loss, not streaming-only loss, and not a broad-fraud total. The `>80%` record is traffic or consumption share, not losses.
- `EV-LAKERA-CONSIDERATION-2026` is official preliminary accounting. `EV-LAKERA-MEDIA-ESTIMATE-2025` is a media estimate whose article says the price was not disclosed.
- PSD2 and DORA records do not mandate obfuscation. `EV-EMVCO-SECN0130` is certification evidence, not a universal banking-app requirement.
- `cutoff-unverified` records are not cutoff-safe headlines. `not-found` is not zero, and no inferred total is allowed.
