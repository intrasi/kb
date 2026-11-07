---
type: note
title: A javascript-obfuscator user reports a production crash on a static class-field callback
tags: [security]
date: 2026-11-07
by: karla+grok
confidence: low
sources: [ghn-01-javascript-obfuscator-issue-1462, https://github.com/javascript-obfuscator/javascript-obfuscator/issues/1462]
record_id: ghn-01
hypothesis: A3
stance: supports
signal: experience
---

NotYoojun reports that a javascript-obfuscator production build crashed on a static class-field callback. That report supports hypothesis A3, obfuscation breakage and compatibility or deployment pain. It is one experience report. It does not show how often this happens, and this filing did not reproduce the crash.

- record_id: ghn-01
- hypothesis: A3
- stance: supports
- signal: experience
- visible role: not found
- caveat: GitHub raw JSON was not saved, so the issue body was not re-checked. The sentence is a self-report, not an independently verified failure.

Evidence: [[ghn-01-javascript-obfuscator-issue-1462]].
Catalogue: [[github-hn-scan-2026-11-07-index]]. Methods: [[github-hn-scan-2026-11-07-methods]].
