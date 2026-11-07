---
type: note
title: A defensible obfuscation market estimate must count eligible vendors rather than installed binaries
tags: [customer, market]
date: 2026-11-07
by: luka+codex
confidence: moderate
sources: [https://www.preemptive.com/customers/, https://www.guardsquare.com/customers]
---

## Claim

The 36 segments in [[shipped-software-customer-landscape]] describe possible exposure, not an addressable revenue estimate. A vendor can ship millions of copies under one protection contract; one software group can also have multiple separately budgeted product teams. SDKs embedded in apps overlap the app-vendor population.

Public customer cases prove neither that nearly all vendors pay nor that they will switch to us. [PreEmptive's page](https://www.preemptive.com/customers/) states both 5,000+ development teams and 5,000+ companies, without an audited denominator or clear historical/current-contract distinction. Use this as vendor-reported scale evidence only. Do not sum portfolio counts across vendors or mix them with APK samples in [[obfuscation-is-common-in-popular-android-apps]].

## Bottom-up sizing method

Build a deduplicated account list, then qualify:

- Ships a closed-source asset into a relevant third-party environment.
- Has an economically important algorithm, licensing/tamper control, or model asset.
- Uses a supported language/toolchain and fits current checker coverage.
- Has a reason to improve protection or reduce actual engineering effort.
- Has budget and a reachable buyer; can adopt without replacing an entire security stack.

**Annual opportunity scenario = eligible buying accounts × assumed annual contract value.** Keep price explicitly hypothetical until customer evidence exists. A separate reachable-market scenario must restrict geography, sales capacity, procurement and supported platforms. Count one account once unless separate budget ownership is verified. Do not present guessed filters as measured conversion rates.

## Unknowns that block a credible numerical TAM

No reliable cross-sector count of paid advanced-obfuscation buyers, no validated price for our proposal, no measured switching propensity, and no representative engineering-effort baseline were established here. Therefore this research intentionally does not invent a dollar TAM or adoption percentage.

Economic value differs by job: release piracy delay, reduced cloning, reduced abuse, protected OEM redistribution, and engineer-hours saved are not interchangeable. A pure code-recovery benchmark validates only part of that value.
