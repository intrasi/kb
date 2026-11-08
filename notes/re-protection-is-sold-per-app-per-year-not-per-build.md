---
type: note
title: "Code protection is sold per app per year (Guardsquare about $44k, Appdome from $50k, Denuvo $25k per game per month); no vendor bills per build, and metered dev-tool fees draw backlash"
tags: [market, pitch]
date: 2026-11-08
by: tea+claude
confidence: moderate
sources: [re-device-cloning-build-cadence-pricing-report-2026-11-08]
---

Prices found (mostly secondary): Guardsquare about $44k a year average, $83k maximum (Vendr, small
sample); Appdome from $50k a year (Capterra), an old sheet at $285k per app per year with "10 App updates
per year"; Denuvo on AWS Marketplace $25k per game per month plus $0.50 per activation; desktop packers
a few hundred euros per developer. Promon, Verimatrix, Digital.ai, Thales and Emproof quote privately.

Closest to per-build: Jscrambler counts protection runs; code signing charges per signature (cents);
Coverity Scan rationed builds per week by code size. GitHub postponed a per-minute fee on self-hosted
runners a day after announcing it, after backlash.

Our working model (assumptions, untested with buyers): count one protected release image per model or
control-unit variant inside an annual commitment; price per build by share of functions protected
($250 / $500 / $900); internal CI builds free; security-only releases at half; $12k minimum and a cap
per product line. Worked examples: e-bike drive-unit maker $12k, robot-vacuum maker with 7 models about
$30k, legacy carmaker about $75k, Tesla-cadence carmaker about $127k a year.

Why it matters: per-build as a pure meter taxes the security releases the CRA demands; an annual plan
with included builds is forecastable. Test with three pricing conversations before putting it on a
slide. Checked 2026-11-08.
