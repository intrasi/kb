---
type: note
title: Strong code protection buys attacker cost and time, not impossibility
tags: [security, agents, pitch]
date: 2026-11-07
by: tea+claude
confidence: moderate
sources: [re-dossier-06-legal-verticals-harness, https://cpl.thalesgroup.com/about-us/newsroom/sentinel-envelope-plus-ai-reverse-engineering-protection, https://patents.google.com/patent/US6668325B1/en]
---

**Thales, Sentinel Envelope Plus press release (1 October 2026):**
- On an unprotected app, an AI agent found 8 of 10 vulnerabilities.
- On the protected app it found none, after "970 times the token consumption". The analysis "was
  halted after nearly seven hours".
- The release names neither the agent nor the model, and does not time the unprotected run.
- Vendor data, so the numbers carry low confidence. (Earlier drafts gave "3m10s" and "3h43m";
  neither appears in the source.)

**US patent 6,668,325 (Collberg, Thomborson and Low; granted 23 December 2003):** "code
obfuscation can never completely protect an application from malicious reverse engineering
efforts".

Why it matters: the honest product claim is a measured cost-to-break, not "AI-proof". The
direction is well supported; the Thales numbers are not independent. See
[[re-agents-route-around-obfuscation]].

Verified 2026-11-07: each figure above was checked against the primary source listed in `sources:`.
