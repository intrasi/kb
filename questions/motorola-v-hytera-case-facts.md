---
type: question
title: What exactly happened in Motorola v. Hytera, and what does it teach a code-protection product?
tags: [security, market]
date: 2026-11-08
by: tea+claude
status: answered
owner: tea+claude
---

Motorola v. Hytera is the largest "competitor put our device software in its products" case. We cite it in
[[re-big-machine-software-theft-cases-started-with-insiders]] and decision 0003. We need the full facts:
how the code was taken, how it was detected, what the courts awarded and why, the criminal case, the
remedies (royalty, injunction), collection, and whether anything in it involved reverse engineering of
shipped firmware or obfuscation.

## Leads

- 7th Circuit opinion, July 2024 (Nos. 20-3213 etc.).
- DOJ indictment of Hytera, February 2022 (N.D. Ill.).

## Answer

Seven Motorola Malaysia engineers, paid by Hytera, downloaded the DMR source code and more than 10,000
documents in 2008. Hytera compiled that code into its radios. Nothing in the record involves reverse
engineering shipped firmware, so the case argues for insider controls and provenance proof, not for
obfuscating binaries.

- How the code was taken: [[hytera-got-motorola-firmware-from-paid-insiders-not-from-shipped-radios]]
- Concealment and how copying was proven: [[hytera-rewrote-stolen-code-to-look-different-but-copied-typos-proved-it]]
- Detection gap (2010 ship, 2017 suit, proof only in discovery): [[motorola-found-the-copied-code-only-in-discovery-years-after-hytera-shipped]]
- Money awarded vs collected, criminal sentence: [[motorola-v-hytera-money-awarded-versus-collected]]
- Enforcement across countries: [[collecting-from-hytera-took-contempt-orders-in-several-countries]]

Raw material: [[motorola-v-hytera-web-excerpts-2026-11-08]].
