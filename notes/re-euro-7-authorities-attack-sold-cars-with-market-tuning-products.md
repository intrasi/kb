---
type: note
title: "Under Euro 7 implementing rules, market-surveillance authorities must attack sold cars with tuning products bought on the market and grade them pass, follow-up or fail"
tags: [regulation, security, pitch]
date: 2026-11-07
by: tea+claude
confidence: moderate
sources: [re-vehicle-firmware-anti-tampering-report-2026-11-07, https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=CELEX:32025R1706]
---

Implementing Regulation (EU) 2025/1706, Annex XIV, per the research notes that read the EUR-Lex text:
- The maker meets the anti-tampering duty by passing UN R155 and covering the annex's threat tables in
  its threat analysis (TARA); it hands over the R155 documentation and a signed declaration of compliance,
  kept 10 years after production ends.
- Market-surveillance authorities run regular real attack tests, including with tuning products sold on
  the market. Results are graded pass, follow-up or fail using emission retests and the vehicle's
  tampering detection. A fail leads to corrective measures, preferably an over-the-air update.
- Example mitigations named: update authentication, integrity checks, secure boot, tamper-resistant or
  tamper-evident hardware. Obfuscation is not named; UN R155 allows "another appropriate mitigation",
  and mitigation M7 is "protect system data/code". R155 threat 19.1 is extraction of proprietary software.

Why it matters: our Measure step is the same act the authority will perform, done earlier and with AI
agents. The pitch line is "we run the authority's attack test before the authority does". This mapping
is our inference.

Moderate confidence: quotes come from a research agent's reading of EUR-Lex; re-read Annex XIV yourself
before putting article numbers on a slide. Checked 2026-11-07.
