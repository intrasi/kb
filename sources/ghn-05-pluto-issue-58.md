---
type: source
title: Pluto issue 58 backend-pass crash report
date: 2026-11-07
url: https://github.com/bluesadi/Pluto/issues/58
tags: [security]
record_id: ghn-05
platform: GitHub
quoted_on: 2023-12-17
---

Verbatim excerpt from the 2026-11-07 bounded scan. This statement is a claim or self-report. It is not an independently verified fact.

GitHub raw JSON was not saved. The quote, creation date, and visible role are copied from that scan handoff and were not re-fetched for this filing. `quoted_on` is the item creation date as the scan converted it to Europe/Belgrade, not a last-updated date.

- record_id: ghn-05
- platform: GitHub
- url: https://github.com/bluesadi/Pluto/issues/58
- quoted_on: 2023-12-17 (Europe/Belgrade)
- author: mrh929
- visible role: GitHub association CONTRIBUTOR, as reported by the scan. Professional role not found. Seniority not found. The association was not re-checked, because GitHub raw JSON was not saved.
- signal: experience
- words: 11

```text
压缩包里面附上了 debug.ll，说明中间层的 pass 本身没有 crash，而是后端 pass crash 了，原因就是它无法处理 double 类型的 IR：
```

Interpretation: [[ghn-05-pluto-backend-pass-crash-report]]. Catalogue: [[github-hn-scan-2026-11-07-index]]. Methods: [[github-hn-scan-2026-11-07-methods]].
