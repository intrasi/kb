---
type: note
title: "Incumbents spent years and tens of millions on one signature algorithm while a comparable device can be sourced as a finished ODM design in weeks, leaving the algorithm as the only asymmetry left"
tags: [market, customer, pitch, security]
date: 2026-11-08
by: tea+claude
confidence: moderate
sources: [re-xiaomi-case-study-2026-11-08]
---

What a signature algorithm or mechanism cost its owner:
- Dyson Supersonic hair dryer: $71M, 4 years, 103 engineers, about 600 prototypes (a CBS figure of
  $200M is an outlier).
- Dyson digital motor: started 1999, first motor after 4 years, about a decade and 50+ engineers,
  over $160M stated in 2013.
- Bose active noise cancelling: concept 1978, first product 1989.
- Firstbeat (Garmin's sleep and recovery analytics): founded 2002, 20+ years of HRV research.
- iRobot: bought Evolution Robotics for $74M in 2012; the vSLAM-navigating Roomba 980 shipped in 2015.
- Sonos: 3-4 years to its first product.

What a comparable device costs a fast follower, from supplier marketing (labelled as such): a full ODM
programme 4-8 months, a pre-certified modular launch under 90 days, a public-mould white label 25-45
days, with tooling and engineering around $30-40k. In phones, MediaTek's turnkey platform is documented
as cutting lead time from about 9 months to about 3, and the shanzhai ecosystem shipped in 4-6 weeks
against 12-18 months for an international brand. One robot-vacuum ODM platform (Shenzhen Picea, formerly
3irobotix) sits under several unrelated Western brands.

The inference, ours: roughly 16-20x on time and three orders of magnitude on engineering cost. Since
studying a lawfully bought product is legal in the EU and US
([[re-eu-law-lets-owners-study-and-decompile-software-for-interoperability]]), the incumbent's remaining
asymmetry is the algorithm inside the shipped device, and it survived only because reading it out of
firmware was slow and expensive. That cost is what AI agents change
([[re-agents-route-around-obfuscation]]), and what we propose to measure
([[0003-use-case-device-makers-against-competitor-reverse-engineering]]).

Limits: no case documents a competitor extracting an algorithm from a shipped consumer device; today's
leaders Dreame and Roborock now run real in-house R&D, so the turnkey argument is strongest for market
entry and the long tail of brands. Checked 2026-11-08.
