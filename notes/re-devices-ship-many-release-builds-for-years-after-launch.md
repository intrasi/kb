---
type: note
title: "Devices keep shipping release builds for years: Tesla 165 versions in 12 months, drones 4-5 per model a year, phones 7 years of support, and EU and UN rules make updates mandatory"
tags: [market, regulation, customer]
date: 2026-11-08
by: tea+claude
confidence: moderate
sources: [re-device-cloning-build-cadence-pricing-report-2026-11-08, https://stats.tessie.com]
---

| Segment | Release builds | Confidence |
| --- | --- | --- |
| Tesla | 165 software versions in the last 12 months (Tessie tracker, read in full) | high |
| Legacy carmakers | about 3-4 major OTA releases a year (XPeng 3 in 2025; BMW reportedly 3) | moderate |
| DJI drone | about 4-5 aircraft firmware releases per model a year | moderate |
| Robot vacuums | one Roborock update shipped as 7 per-model builds | moderate |
| Flagship phones | 7 years of support (Pixel 8+, Galaxy S24+); 12-16 builds a year is an estimate | low-moderate |
| Bosch eBike | several feature updates a year | moderate |

Release builds are a small share of internal builds: one 2022 consultant estimate puts Tesla at more than
20 builds a day against about 150 releases a year (low confidence).

Rules that force a stream of builds: the Cyber Resilience Act (support period of at least 5 years,
from December 2027), the EU phone ecodesign rule (OS updates for 5 years after the last unit is sold,
since June 2025), and UN R156 (a register of software versions per vehicle type).

Why it matters: billing per protected release build has a real, recurring volume, and builds grow with
the number of models. Count release images, never internal CI builds. Checked 2026-11-08.
