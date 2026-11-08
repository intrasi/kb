---
type: note
title: "Hytera rewrote the stolen code to look different from Motorola's, but identical typos and coding errors still proved the copying"
tags: [security]
date: 2026-11-08
by: tea+claude
confidence: high
sources: [motorola-v-hytera-web-excerpts-2026-11-08, https://caselaw.findlaw.com/court/us-7th-circuit/116339567.html]
---

- June 2008 email from G.S. Kok: they "needed to re-write softwares to look different from Motorola"
  to "protect the company from impending lawsuits" (2020 N.D. Ill. post-trial opinion).
- The rewrite failed. The courts relied on identical misspellings and minor coding errors in both
  codebases. DOJ's complaint says the copying included code, comments and "even typos", across "hundreds
  of thousands of lines". Motorola mapped the copied code in every version of its DMR software.
- Hytera also deleted evidence; the Australian court applied the presumption against a party that
  destroys evidence. The former employees took the Fifth Amendment more than 100 times, and the jury
  could draw adverse inferences.

Why it matters: cosmetic transformation by the thief did not erase provenance. Small unique artefacts
(typos, quirks) were the fingerprints. That backs the idea that proving "this is our code" in someone
else's product is a real need, alongside or instead of hiding the code. Low-confidence extension, not
from the case: deliberate per-build fingerprints would make that proof easier.
