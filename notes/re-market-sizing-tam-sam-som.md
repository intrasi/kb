---
type: note
title: "Pitch market sizing: $12.6B application-security TAM, $2.7B in-app protection SAM, about $15M ARR five-year SOM (assumed)"
tags: [market, pitch]
date: 2026-11-07
by: tea+claude
confidence: moderate
sources: [application-security-market-estimates, in-app-protection-and-shielding-estimates, worldwide-security-spending-forecasts, ai-security-acquisition-consideration, https://www.verimatrix.com/newsroom/sale-of-extended-threat-defense-assets-mobile-application-protection-to-guardsquare/, https://www.businesswire.com/news/home/20260204124653/en/Guardsquare-Acquires-Verimatrix-XTD-Setting-a-New-Standard-for-End-to-End-Mobile-App-Security]
---

Framing: the product is AI-resistance protection and testing for software that ships outside the
company. Its two halves sit in two existing budgets: **protect** (obfuscation with a proof) in
in-app protection, and **measure** (the AI-attack score) in application-security testing. Native
SDK vendors are the first customers, not the market boundary
([[native-sdk-vendors-are-a-plausible-first-obfuscation-market]]).

## The numbers

| Layer | Value | Scope | Record |
| --- | --- | --- | --- |
| Context, not TAM | $244B for 2026 | Worldwide information-security spending | Gartner, 5 Feb 2026 vintage, `EV-GARTNER-IS-2026-V20260205` in [[worldwide-security-spending-forecasts]] |
| TAM | $12.64B for 2026 ($10.6B for 2025) | Application security: solutions and services, web/mobile security and testing | Grand View Research, June 2026, `EV-GVR-APPSEC-2026` in [[application-security-market-estimates]] |
| SAM | $2.7B for 2026 ($2.1B for 2025) | In-app protection: shielding, RASP, obfuscation, anti-tamper, services | Custom Market Insights, Jan 2026, `EV-CMI-IAP-2026` in [[in-app-protection-and-shielding-estimates]] |
| SOM, 5 years | About $15M ARR | 250 customers × about $60k a year | **Our assumption**, calibrated below |

All three market figures are analyst models, not audited spending (moderate confidence each).
Growth implied by the same publishers' consecutive years: about 19% for application security and
about 28% for in-app protection. CMI's own long-run rate is 17.7%, so say "high teens to high
twenties", never a single precise rate.

## How the SOM is calibrated

- **Price per customer.** Verimatrix's mobile app-protection unit (XTD) earned about $3.8M in the nine
  months to September 2025 (secondary report), and media coverage credits it with about 60
  customers. That is roughly $60–80k per customer per year. Guardsquare bought the unit for an
  initial $8.5M; the sale closed on 5 February 2026.
- **Customer count.** Guardsquare reports 975+ customers in more than 95 countries, so 250 customers in
  five years is within what one vendor has reached.
- **Result.** 250 × $60k ≈ $15M ARR, about 0.5% of the SAM. This is an assumption, not a count of
  eligible vendors. A real bottom-up count is still missing; the method is in
  [[obfuscation-market-size-needs-vendor-counts-not-installed-binaries]].

## Why the category can be bigger than past code-protection exits

| Company | Buyer | Price | Confidence |
| --- | --- | --- | --- |
| Protect AI (AI security) | Palo Alto Networks | $634.5M consideration | high, SEC filing ([[ai-security-acquisition-consideration]]) |
| Lakera (AI security) | Check Point | about $201.8M consideration | high, SEC filing ([[ai-security-acquisition-consideration]]) |
| Arxan (code protection) | TA Associates, 2013 | $132M | press reports |
| Cloakware (code protection) | Irdeto, 2007 | $72.5M | press reports |
| Verimatrix XTD (app protection) | Guardsquare, 2026 | $8.5M initial offer | Verimatrix release |

Code-protection exits were small and mostly private-equity
([[re-code-protection-vendors-mostly-pe-owned]]). The AI-security exits are larger, which supports
positioning the product as AI security rather than another obfuscator. That is an inference from
five deals, not a forecast.

## Do not use

- $16.2B in-app protection: no source ([[re-in-app-protection-16b-figure-has-no-source]]).
- MarketsandMarkets application-security figures: undated or unsettled; Karla's records exclude them
  from cutoff-safe headlines.
- The $8.5B cheat economy: a vendor model listed as an open gap ([[code-protection-evidence-gaps]]).
- Any "AI security market" total from report mills: none has been checked.

Why it matters: judges score ambition (criterion 5, [[garaza-judging-six-criteria]]). A sourced
funnel with a small, explained SOM survives Q&A; an inflated TAM does not.

Checked 2026-11-07. The Arxan and Cloakware prices come from press reports found by web search
and are not separate kb records yet.
