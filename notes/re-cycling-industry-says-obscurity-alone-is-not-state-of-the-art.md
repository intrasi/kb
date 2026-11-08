---
type: note
title: "The European cycling industry's 2026 anti-tampering position asks motor makers for cryptographic firmware protection and calls reliance on obscurity alone not state of the art"
tags: [regulation, security, customer]
date: 2026-11-07
by: tea+claude
confidence: moderate
sources: [re-vehicle-firmware-anti-tampering-report-2026-11-07, https://cyclingindustries.com/wp-content/uploads/2026/09/Position-Paper-Anti-Tampering.pdf]
---

Cycling Industries Europe (ECI) position paper, September 2026: e-motor makers must take part because
they have the capacity to detect and react to tampering. Its state-of-the-art list includes
cryptographically verified updates without rollback, parameters protected by keys or certificates,
mutual authentication of motor, controller and battery, locked debug interfaces and tamper-resistant
logging. "Reliance on obscurity alone" and extractable keys do not meet the bar. It asks the next
EN 15194 revision to require cryptographic integrity.

Context: standard pedelecs (25 km/h, 250 W) are outside Regulation 168/2013 (Article 2(2)(h)); their
anti-tampering duty comes from EN 15194, whose cybersecurity revision is expected around Q4 2026
(secondary). Tuning is visible: Amsterdam police found about 54% of checked fatbikes tuned in early 2024.

Why it matters: never pitch obfuscation as the protection. Pitch it as a layer on top of cryptography,
plus measured evidence that the whole stack holds. Moderate confidence: read through a research agent,
not opened by us. Checked 2026-11-07.
