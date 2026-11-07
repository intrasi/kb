---
type: note
title: Studies detect obfuscation in roughly nine in ten popular Android apps but do not measure company-wide paid adoption
tags: [market, customer, security]
date: 2026-11-07
by: luka+codex
confidence: moderate
sources: [https://aoa0.github.io/pubs/icse26.pdf, https://arxiv.org/html/2502.04636v1, https://cispa.de/en/research/publications/69069-a-large-scale-investigation-of-obfuscation-use-in-google-play]
---

## Claim

Obfuscation is common in popular Android apps, but available measurements do not
support the claim that almost every company shipping a client binary purchases
advanced protection or obfuscates its entire application. Sources checked 2026-11-07.

## Evidence

| Study | Population and measure | Reported result |
| --- | --- | --- |
| Pan et al., ICSE 2026 | 77,504 closed-source Google Play APKs, including updates, from a post-2022 dataset | Identifier renaming: 45,270/77,504, or 58.41%; package hierarchy obfuscation: 29.08% |
| Same study, Table 2 | 611 analyzable popular apps from a 619-app collection | Identifier renaming: 539/611, or 88.22%; package hierarchy obfuscation: 43.71% |
| Niroshan et al., 2025 manuscript | 548,967 APKs covering 2016-2023 | 56.25% overall; approximately 66% in the 2023 cohort |
| Same manuscript, Table XI | Top 1,000 apps in its 2023 snapshot | 92.50% detected as obfuscated |
| Wermke et al., 2018 | 1.7 million free Google Play apps; developer-applied protection distinguished from libraries | 24.92% obfuscated by the developer |

## Limits

- These are sampled APKs or app versions, not unique companies, current installed
  user shares, or independently measured paid-tool adoption.
- Publication year is not collection year. Do not call historical cohorts a 2026
  market census or combine unlike studies into a single growth estimate.
- Renaming is basic protection; package restructuring or compiler optimization does
  not establish virtualization, sophisticated runtime defenses, or proven resistance.
- The 2025 manuscript classifies whole APKs. Its authors explicitly warn that detected
  obfuscation can originate in first-party or third-party libraries and that tool
  attribution can confuse DexGuard and ProGuard. Tool-market-share estimates are
  therefore particularly uncertain.
- A separate nearly 2.5-million-APK protection study reports about 4% detected known
  packers/obfuscators/protectors via APKiD signatures. That is a different detection
  scope and mixed population, not evidence that only 4% use any obfuscation.
- We did not establish a comparable current adoption rate across iOS, desktop,
  embedded, or .NET software.

## Commercial scale

Guardsquare reports more than 975 customers across its security portfolio. This is
vendor-reported evidence of an established enterprise category, not an audited count
of obfuscation-only contracts, a market-share estimate, or evidence of willingness
to buy our proposed product. Its 2026 research announcement identifies a commissioned
survey of 1,360 developers and security leaders; survey responses should not be
treated as binary measurements or causal proof of protection effectiveness.

## Why this matters

Popular-app vendors are an evidence-backed discovery segment, but free baseline
obfuscation competes with the proposal. Interview existing protection users about
engineering effort and stronger protection rather than assuming every detected app
represents an available paying customer. See
[[verified-obfuscation-could-reduce-protection-engineering-effort]].

## Sources

- [Pan et al., ICSE 2026, Table 2 and section 3.3](https://aoa0.github.io/pubs/icse26.pdf).
- [Niroshan et al., 2025, results and limitations](https://arxiv.org/html/2502.04636v1).
- [Wermke et al., 2018, institutional summary](https://cispa.de/en/research/publications/69069-a-large-scale-investigation-of-obfuscation-use-in-google-play).
- [Quarkslab summary of the APKiD-based study, 2026](https://blog.quarkslab.com/practical-android-software-protection-in-the-wild-an-appetizer.html).
- [Guardsquare customer count and commissioned survey methodology, 2026](https://www.guardsquare.com/press-release/mobile-apps-are-the-new-attack-surface).
