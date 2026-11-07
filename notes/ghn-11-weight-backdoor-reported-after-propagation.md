---
type: note
title: A commenter reports telling Hugging Face about a backdoor only after it reached model weights
tags: [security]
date: 2026-11-07
by: karla+grok
confidence: moderate
sources: [ghn-11-hn-48248289, https://news.ycombinator.com/item?id=48248289]
record_id: ghn-11
hypothesis: B2
stance: supports
signal: experience
---

GeorgeWoff25 says a backdoor was reported to Hugging Face on the day it was confirmed in model weights, and gives the reason as a lack of detection rather than the dataset itself. That supports B2 as a self-report that detection can miss a backdoor until it has propagated into weights. The comment does not name a scanner that was tested, and the event was not independently validated.

- record_id: ghn-11
- hypothesis: B2
- stance: supports
- stance_detail: supports as a self-report; not independently validated and does not identify a tested scanner
- signal: experience
- visible role: not found
- caveat: self-report. Do not cite it as a scanner benchmark.

Evidence: [[ghn-11-hn-48248289]].
Catalogue: [[github-hn-scan-2026-11-07-index]]. Methods: [[github-hn-scan-2026-11-07-methods]].
