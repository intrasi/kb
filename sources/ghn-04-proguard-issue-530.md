---
type: source
title: ProGuard issue 530 Kotlin-upgrade crash report
date: 2026-11-07
url: https://github.com/Guardsquare/proguard/issues/530
tags: [security]
record_id: ghn-04
platform: GitHub
quoted_on: 2026-06-11
---

Verbatim excerpt from the 2026-11-07 bounded scan. This statement is a claim or self-report. It is not an independently verified fact.

GitHub raw JSON was not saved. The quote, creation date, and visible role are copied from that scan handoff and were not re-fetched for this filing. `quoted_on` is the item creation date as the scan converted it to Europe/Belgrade, not a last-updated date.

- record_id: ghn-04
- platform: GitHub
- url: https://github.com/Guardsquare/proguard/issues/530
- quoted_on: 2026-06-11 (Europe/Belgrade)
- author: bodiam
- visible role: not found. Seniority not found.
- signal: experience
- words: 37

```text
This was originally observed in a JetBrains plugin build after upgrading to Kotlin 2.4.0. Removing the explicit ProGuard rule that keeps `kotlin.Metadata` avoids the crash in that project, but ProGuard should not terminate with an internal NPE.
```

Interpretation: [[ghn-04-proguard-kotlin-upgrade-crash-report]]. Catalogue: [[github-hn-scan-2026-11-07-index]]. Methods: [[github-hn-scan-2026-11-07-methods]].
