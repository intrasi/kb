---
type: note
title: "Hytera got Motorola's radio firmware from paid insiders who downloaded the source code, not by reverse engineering shipped radios"
tags: [security, market]
date: 2026-11-08
by: tea+claude
confidence: high
sources: [motorola-v-hytera-web-excerpts-2026-11-08, https://caselaw.findlaw.com/court/us-7th-circuit/116339567.html]
---

Checked 2026-11-08 against the 7th Circuit opinion (July 2024), the 2020 post-trial opinion, the
Australian Full Court ruling and DOJ coverage.

- 2007: Hytera's CEO recruited Motorola Malaysia engineer G.S. Kok (600,000 Hytera shares, about $2.5M).
  Kok brought in Y.T. Kok and Sam Chia; Y.T. Kok stayed at Motorola while on Hytera's payroll.
- 2008: before leaving, they downloaded more than 10,000 technical documents and the DMR source code
  from Motorola's internal ClearCase and COMPASS repositories, at Hytera's request.
- Hytera compiled that code into its own DMR radios, sold 2010-2014 as "functionally
  indistinguishable" from Motorola's. Hytera had failed to build its own DMR stack before the theft.
- DOJ charged seven people; the Australian court found G.S. Kok and 12 others took code.

Why it matters: this is the case people cite as "a competitor put our device software in its radios",
but the code left through employees with repository access. Obfuscating or encrypting the firmware on
the radios would have changed nothing. It belongs with [[re-big-machine-software-theft-cases-started-with-insiders]]
and supports the caution in decision 0003. It is not evidence for protecting shipped binaries.
