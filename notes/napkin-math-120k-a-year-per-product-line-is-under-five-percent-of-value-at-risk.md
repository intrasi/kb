---
type: note
title: "Napkin math: $120k a year per product line is about 1% of the $14M a cloned algorithm puts at risk, and under 5% even if only 1 in 5 makers ever gets copied"
tags: [market, pitch, customer]
date: 2026-11-08
by: tea+claude
confidence: low
sources: [re-device-cloning-build-cadence-pricing-report-2026-11-08, motorola-v-hytera-web-excerpts-2026-11-08]
---

Pricing proposal built by value at risk, not by cost. Every customer number below is an assumption
for a made-up mid-size robot-vacuum maker; only the comparables and the Hytera figures are sourced.
Not tested with any buyer. It raises the per-build price in
[[0003-use-case-device-makers-against-competitor-reverse-engineering]] (about $30k a year for the same
maker) roughly fourfold.

## What one algorithm is worth to the maker (assumptions)

| Line | Assumption | Value |
| --- | --- | --- |
| Product line | 1M units a year at $350, 25% gross margin | $87.5M gross profit a year |
| R&D a competitor skips | 20 engineers × $150k loaded × 3 years on navigation | $9.0M |
| Head start lost | clone ships 15 months earlier and takes 5% of the line's sales | $5.5M |
| **Value at risk** | per algorithm, per competitor | **about $14.5M** |

Both value lines have a court precedent: in Motorola v. Hytera the award included $73.6M of avoided
R&D, and the Australian court found Hytera reached market at least 15 months earlier
([[motorola-v-hytera-money-awarded-versus-collected]]). That case was insider theft, not extraction
from a shipped device; it only shows how courts price stolen know-how.

## The price against that value

| Measure | Result |
| --- | --- |
| $120k a year ÷ $14.5M at risk | 0.8% |
| Same, if only 20% of makers are ever copied ($2.9M expected loss) | 4.1% |
| Per release build (7 models × 5 releases = 35 builds) | about $3.4k |
| What they already pay to protect one phone app or game | Guardsquare about $44k, Appdome $50k-285k, Denuvo $300k a year ([[re-protection-is-sold-per-app-per-year-not-per-build]]) |

The pitch line this supports: "You pay less to protect the algorithm in the device than many companies
pay to protect a mobile app, and the device algorithm is where the R&D went."

## Proposed tiers

| Tier | Price | Includes |
| --- | --- | --- |
| Pilot | $25k, 90 days, credited to year one | one algorithm, one model, AI break-test report on their own firmware |
| Product line | $120k a year | up to 8 models, 40 release builds, break-test report every release; extra builds $2.5k, security-only builds $1.25k |
| Company | from $350k a year | all product lines, measurement agents run on their premises so firmware never leaves |
| Algorithm supplier (Bosch Sensortec-type) | $200k a year | protects a library shipped to many device makers |

Our cost per build is mostly agent tokens for the break test, guessed at $50-300, so gross margin
should be high (unmeasured).

## Revenue napkin

5 pilots ($125k) → 3 convert to product lines ($360k ARR) in year one; 15 lines plus 2 company
deals is about $2.5M ARR in year two. Pure assumptions.

## How to make the price feel cheap (honestly)

1. Fill the value table with the buyer's own numbers in the meeting; the price is set against their
   figure, not ours.
2. Run the pilot on their firmware: the "time bought" chart is the proof the money buys something.
3. Quote per product line per year; never lead with a per-build meter.
4. Anchor with what they already pay for app protection.

## What would break this

- The 20% chance of being copied is our guess. No public case shows a competitor extracting an algorithm
  from a shipped consumer device ([[re-no-public-case-of-clones-copying-algorithms-from-shipped-consumer-devices]]).
  If interviews say copying happens through people or patents, value at risk drops and so does the price.
- If the demo shows a small time-bought gap, the value story has nothing to stand on.
- Buyers may compare us to free hardening tools; those skip firmware today (see decision 0003).
