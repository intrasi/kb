---
type: note
title: "The largest documented thefts of machine control software (Sinovel, Hytera, Waymo) started with insiders taking source code, which protecting the shipped binary would not have stopped"
tags: [security, market]
date: 2026-11-08
by: tea+claude
confidence: moderate
sources: [re-machine-software-cloning-report-2026-11-08]
---

- Sinovel v. AMSC: stolen wind-turbine converter control code was compiled into Sinovel turbines; the
  court found AMSC losses above $550M; Sinovel was convicted in January 2018 and paid about $57.5M
  restitution plus a $1.5M fine (DOJ, AMSC releases).
- Motorola v. Hytera: $764.6M jury verdict (February 2020) over copied radio firmware; the 7th Circuit
  upheld $407.4M in trade-secret damages (2024); the Supreme Court declined review (February 2025).
- Waymo v. Uber, GM/Du, Tesla v. Cao: employees took code to a rival.

No public case was found of Deere, CNH, AGCO, Caterpillar, Komatsu, Liebherr or Bosch control software
being copied onto a competitor's machine (English sources only; Chinese court records not searched).
Documented clone devices (Hondata ECU boards) copied whole programs onto identical hardware, which needs
no understanding and is handled by hardware-bound licensing.

Why it matters: "a competitor reverse-engineers Deere's software and puts it on another brand" is the
case our product fits (porting needs understanding) but the one with the least evidence. Keep it in
the vision, not as the lead use case ([[0003-use-case-vehicle-and-machine-control-firmware]]).
Moderate confidence: figures come from search summaries and court/DOJ releases read by research agents.
Checked 2026-11-08.
