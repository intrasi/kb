---
type: note
title: "Pitch numbers for the agent-era device pitch: a $71M algorithm, AI agents reading protected code in about 45 minutes, an $8.5-10B embedded security market, and $15M ARR from 125 product lines"
tags: [market, pitch, customer]
date: 2026-11-08
by: tea+claude
confidence: low
sources: [re-market-sizing-tam-sam-som, re-incumbent-algorithms-take-years-while-odm-hardware-takes-weeks, re-agents-route-around-obfuscation, re-protection-buys-cost-not-impossibility, re-stacked-obfuscation-passes-cut-llm-success-in-vendor-study, napkin-math-120k-a-year-per-product-line-is-under-five-percent-of-value-at-risk, re-protection-is-sold-per-app-per-year-not-per-build, ai-security-acquisition-consideration, https://www.mordorintelligence.com/industry-reports/embedded-security-market, https://www.grandviewresearch.com/industry-analysis/embedded-security-market-report, https://www.fortunebusinessinsights.com/embedded-security-market-103738, https://www.marketsandmarkets.com/Market-Reports/smart-appliances-market-8228252.html]
---

Numbers bank for the pitch, built for [[target-audience-is-consumer-electronics-makers-like-philips]] and the
"older protection was built for human hackers, we protect against AI agents" line
([[obfuscation-as-a-service-exists-for-apps-our-moat-is-firmware-plus-an-open-ai-break-test]]).
Every number is sourced or labelled as our assumption. Checked 2026-11-08. Confidence is low as a whole
because the revenue lines are assumptions.

## Fixes to the first "The math" slide

The first draft sized us with mobile app numbers. Our customer is a device maker, so:

1. **$2.7B is the in-app (mobile app) protection market, not ours.** Keep it only as proof that companies
   pay for software protection. Our market line is **embedded security: about $8.5-10B in 2026, growing
   about 8-10% a year** (Grand View $8.5B, Fairfield $8.5B, Persistence $8.9B, Mordor $10.1B; outliers
   $4.8B and $12.5B). It is a hardware-heavy analyst model (Mordor: 49% hardware), so say "the market we
   sell into", never "our market".
2. **"Growing 20%, doubling in 4 years" was the app market.** Embedded security grows about 8-10%, which
   doubles in about 8 years. Do not reuse the doubling claim.
3. **250 customers × $60k uses app prices and Guardsquare's app customers.** At our device price it is
   **125 product lines × $120k = $15M ARR**, for example 40 companies with about 3 lines each. That is
   about 0.15-0.18% of embedded security. Assumption.

## The corrected slide

| | Number | Basis |
| --- | --- | --- |
| **1. The algorithm is the expensive part** | Dyson's Supersonic: **$71M, 4 years, 103 engineers**. A comparable device from an ODM: **weeks, about $30-40k** tooling | [[re-incumbent-algorithms-take-years-while-odm-hardware-takes-weeks]]; ODM figures are supplier marketing |
| **2. AI agents already read protected code** | An AI agent recovered hidden strings from protected binaries in **about 45 minutes** on average | Quarkslab, Aug 2026 ([[re-agents-route-around-obfuscation]]) |
| **3. Protection still buys time against agents** | Protected app: agent found nothing after **about 7 hours and 970× the tokens**. Stacked obfuscation cut AI rebuild success from **63.7% to 8.5%** | Thales and Promon, both vendor tests, low confidence ([[re-protection-buys-cost-not-impossibility]], [[re-stacked-obfuscation-passes-cut-llm-success-in-vendor-study]]) |
| **4. Companies already pay** | **$44k-$300k a year** to protect one app or game (Guardsquare about $44k, Appdome from $50k, Denuvo about $300k) | [[re-protection-is-sold-per-app-per-year-not-per-build]] |
| **5. Our price is small next to the risk** | **$120k a year** per product line against **$14.5M** at risk per cloned algorithm: **under 1%** | Assumption ([[napkin-math-120k-a-year-per-product-line-is-under-five-percent-of-value-at-risk]]) |
| **6. We need a tiny share** | **125 product lines × $120k = $15M ARR**, under 0.2% of an $8.5-10B embedded security market | Assumption + analyst range |
| **7. Exits are big** | AI-security companies sold for **$634.5M** (Protect AI) and **about $202M** (Lakera) | SEC filings ([[ai-security-acquisition-consideration]]) |

**The line to say out loud:**
> "Dyson spent $71 million and four years on one hair-dryer algorithm. A clone factory can build the
> device in weeks. The only thing left to copy is the algorithm, and an AI agent reads firmware in under
> an hour. We make that take days instead, and we measure it on every release. 125 product lines at
> $120k is $15M a year."

## Extra numbers, if a judge asks

| Topic | Number | Source |
| --- | --- | --- |
| Releases to protect | Devices ship builds for years: Tesla 165 versions in 12 months, drones 4-5 per model a year, phones 7 years of support | [[re-devices-ship-many-release-builds-for-years-after-launch]] |
| Shipped models are taken | Models extracted from **66%** of apps that tried to protect them (1,468 ML apps) | USENIX 2021 ([[re-on-device-models-are-extractable-from-most-protected-apps]]) |
| Copying is real in machines | German machine makers: **€4.1B** a year piracy damage, **82%** of cases from China | VDMA 2024 ([[re-machine-software-cloning-report-2026-11-08]]) |
| Patents fail | Dyson hair-dryer patents invalidated in China after Dreame and Laifen challenges | [[re-no-public-case-of-clones-copying-algorithms-from-shipped-consumer-devices]] |
| Customer market size | Smart home appliances alone **about $40-58B** in 2026 (Grand View $40.5B, MarketsandMarkets $46.2B) | Analyst estimates, context only |
| Rules that open budgets | EU Cyber Resilience Act: reporting since **11 Sep 2026**, full rules **11 Dec 2027** | [[first-customers-web-excerpts-2026-11-08]] |

## Do not use

- $12.6B application security or $244B security spending: judges will ask why that is our market.
- $16.2B in-app protection: no source ([[re-in-app-protection-16b-figure-has-no-source]]).
- "AI-proof" or "unbreakable": the honest claim is time and cost bought.
- Thales "3m10s vs 6h43m": does not appear in the source; use "about 7 hours, 970× tokens".
- Any claim that a competitor has copied an algorithm from a shipped consumer device: no public case.

## Weakest line to defend

Line 5 ($14.5M at risk) and line 6 ($15M ARR) are our assumptions. Present them as "illustrative" in
small text; the large-font numbers are $71M, 45 minutes, $8.5-10B and $634.5M, which all have sources.
