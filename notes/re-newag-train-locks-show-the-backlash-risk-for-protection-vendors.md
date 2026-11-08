---
type: note
title: "Newag's hidden train-firmware locks against independent repair led to parliamentary hearings and a criminal case, the worst-case reputation risk for any firmware protection vendor"
tags: [regulation, security, pitch]
date: 2026-11-08
by: tea+claude
confidence: moderate
sources: [re-machine-software-cloning-report-2026-11-08]
---

In Poland (2023), researchers found code in Newag trains that disabled them after long stops, stays
at independent repair yards, or non-original parts; it was reported in 24 of 30 trains examined.
CERT Polska backed the findings; there were three parliamentary hearings, a competition-authority
investigation and a criminal case in Kraków. Newag sued the researchers and the repair shop for about
PLN 11.5M. No verdict as of May 2026 (secondary sources).

Lesson: backlash in Newag, BMW heated seats and Tesla came from how software was used against owners,
not from code protection itself. A protection vendor needs a contract clause banning anti-repair and
defeat logic and a way for certifiers to audit the protected build; the behaviour-preservation proof
helps show protection added no hidden behaviour. Checked 2026-11-08.
