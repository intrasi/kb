---
type: note
title: "Motorola sued seven years after Hytera's copied radios shipped, and proved the code copying only by reading Hytera's source in discovery"
tags: [security, market]
date: 2026-11-08
by: tea+claude
confidence: high
sources: [motorola-v-hytera-web-excerpts-2026-11-08, https://caselaw.findlaw.com/court/us-7th-circuit/116339567.html]
---

- Hytera's DMR radios reached the market in March 2010. Motorola sued for trade-secret theft in March
  2017 (US) and July 2017 (Australia, patents).
- Motorola added copyright claims (July 2018 US, December 2018 Australia) only after Hytera's source code
  was produced in those suits. Motorola then spent months comparing the code.
- Earlier, an internal Motorola investigation had concluded there was no issue. Hytera argued Motorola
  could have caught it by 2012-2014 from its own download logs. The jury found Hytera concealed the theft.
- None of the opinions read describe Motorola tearing down or disassembling Hytera radios to find the
  copying (not confirmed absent; only the opinions above were read).

Why it matters: the gap was detection. A rival's look-alike product sat on the market for years before
the owner could prove anything, and the proof needed court-ordered access to source. A way to show from
a shipped device that it runs your code, without discovery, would have shortened that gap. That points at
provenance or forensics rather than at obfuscation (see
[[hytera-rewrote-stolen-code-to-look-different-but-copied-typos-proved-it]]).
