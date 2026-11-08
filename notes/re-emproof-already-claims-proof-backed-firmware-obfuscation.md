---
type: note
title: "Emproof already sells embedded firmware obfuscation that it says is checked by formal translation-validation proofs under ISO 26262, so a behaviour-preservation proof is not unique to us"
tags: [market, security, formal-methods]
date: 2026-11-07
by: tea+claude
confidence: high
sources: [re-vehicle-firmware-anti-tampering-report-2026-11-07, https://emproof.com/en/solution, https://emproof.com/en/service-description, https://www.eejournal.com/article/from-code-chaos-to-cyber-confidence-inside-the-world-of-firmware-obfuscation/]
---

Emproof (Bochum and Eindhoven; founders include Tim Blazytko and Philipp Koppe) sells Nyx, binary-level
obfuscation, anti-debugging and integrity checks for microcontroller firmware. Its own solution page:
"We use formal proofs such as translation validation to ensure the correctness of our translations",
plus adherence to ISO 26262. Its service description says Nyx is engineered for ISO 26262 up to ASIL D
(Enterprise edition), with a process assessed by TÜV Nord. EEJournal (about late 2025) reported ASIL B,
SMT-based translation validation, and 10–20% overhead by protecting only selected functions.

The high confidence is that Emproof makes the claim; that the proofs or the TÜV assessment hold up is its
own statement, not verified. Funding: €2M seed (2022) and a 2026 round (secondary). No named customers.

What this corrects: [[0002-use-case-paid-professional-software]] and Karla's competitor table
([[competitor-claims-vendor-pages-2026-11-07]]) found no vendor claiming a proof; that table covered app
protection vendors, not embedded ones. For firmware, the proof is table stakes. What we found no vendor
publishing is an open, rerunnable AI-agent time-to-break measurement
([[re-open-configurable-lift-benchmark-is-the-remaining-gap]]).

Checked 2026-11-07 on emproof.com.
