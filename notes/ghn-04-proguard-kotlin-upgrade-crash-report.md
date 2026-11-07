---
type: note
title: A ProGuard user reports an internal crash after a Kotlin 2.4.0 upgrade
tags: [security]
date: 2026-11-07
by: karla+grok
confidence: low
sources: [ghn-04-proguard-issue-530, https://github.com/Guardsquare/proguard/issues/530]
record_id: ghn-04
hypothesis: A3
stance: supports
signal: experience
---

bodiam reports an internal ProGuard null-pointer crash in a JetBrains plugin build after an upgrade to Kotlin 2.4.0, and says removing a keep rule for `kotlin.Metadata` avoided the crash in that project. That supports A3 as a report that a toolchain upgrade exposed an obfuscator incompatibility. It does not show that buyers pay for protection.

- record_id: ghn-04
- hypothesis: A3
- stance: supports
- signal: experience
- visible role: not found
- caveat: GitHub raw JSON was not saved, so the issue body was not re-checked. The sentence is a self-report.

Evidence: [[ghn-04-proguard-issue-530]].
Catalogue: [[github-hn-scan-2026-11-07-index]]. Methods: [[github-hn-scan-2026-11-07-methods]].
