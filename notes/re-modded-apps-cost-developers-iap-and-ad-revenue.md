---
type: note
title: Modded mobile apps unlock paid features for free and cost most affected developers purchase and ad revenue, per two Cambridge studies
tags: [security, market, customer]
date: 2026-11-07
by: tea+claude
confidence: moderate
sources: [https://www.repository.cam.ac.uk/items/c95debfe-f5f1-4682-a8cd-5f43fe882780, https://arxiv.org/html/2402.19180v2]
---

**"App-solutely Modded"** (Saavedra, Dutta, Beresford, Hutchings; ASIA CCS 2025). The abstract, which we
opened, says:
- the study surveyed 717 developers, after contacting 27,000 affected developers, plus 19 operators of
  modded-app markets;
- "affected developers incur revenue losses from purchases, advertising, increased server calls";
- "DMCA copyright claims are unusable at scale".

Per search snippets of the ACM version, not opened: affected developers reported losses from in-app
purchases (54.5%), ads (45.2%) and app sales (38.7%).

**ModZoo** (Cambridge, eCrime 2024) studied 146,000 apps from 13 modded-app markets:
- "Premium features usually charged via IAPs in popular apps are available for free in modded
  versions";
- 21% of modded apps that carried ad IDs had the advertiser ID swapped, so the modder takes the ad
  revenue;
- it estimates about $2.28B in lifetime Play revenue for 6,984 apps that were pirated though paid.

No credible current dollar figure exists for total losses to cracked apps. The only one is a 2017
vendor estimate (Tapcore, $3–4B a year), which is too old and too weak for a slide.

Why it matters: the premium-unlock problem is real and measured by peer-reviewed work. It is long
standing, not new. No source measures AI being used for modding specifically; that link rests on
vendor claims and benchmarks ([[re-stacked-obfuscation-passes-cut-llm-success-in-vendor-study]]).
The usual fix is a server-side check: [[re-server-side-entitlement-checks-are-the-standard-fix]].

Checked 2026-11-07.
