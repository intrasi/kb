---
type: note
title: A Tigress user reports an executable that compiled and then crashed when calling fib
tags: [security]
date: 2026-11-07
by: karla+grok
confidence: low
sources: [ghn-03-tigress-issue-1, https://github.com/collberg/tigress_issue_reports/issues/1]
record_id: ghn-03
hypothesis: A3
stance: supports
signal: experience
---

ttyA0 reports that a Tigress build finished, with warnings, and the executable then crashed when calling `fib()`. The spelling "complie" is the author's. The report supports A3: obfuscated output can compile and still fail at runtime. The failure was not reproduced for this filing.

- record_id: ghn-03
- hypothesis: A3
- stance: supports
- signal: experience
- visible role: not found
- caveat: GitHub raw JSON was not saved, so the issue body was not re-checked. The sentence is a self-report.

Evidence: [[ghn-03-tigress-issue-1]].
Catalogue: [[github-hn-scan-2026-11-07-index]]. Methods: [[github-hn-scan-2026-11-07-methods]].
