---
type: note
title: A javascript-obfuscator user reports that disabling dead-code injection removed a build-dependent failure
tags: [security]
date: 2026-11-07
by: karla+grok
confidence: low
sources: [ghn-02-javascript-obfuscator-issue-1423, https://github.com/javascript-obfuscator/javascript-obfuscator/issues/1423]
record_id: ghn-02
hypothesis: A3
stance: supports
signal: experience
---

julianmesa-gitkraken reports that turning off `deadCodeInjection`, with every other setting unchanged, made a javascript-obfuscator problem disappear, and that a non-zero seed made the outcome reproducible. That supports A3 as a report of build-dependent breakage. It is not a measurement of how often builds break.

- record_id: ghn-02
- hypothesis: A3
- stance: supports
- signal: experience
- visible role: not found
- caveat: GitHub raw JSON was not saved, so the issue body was not re-checked. The sentence is a self-report.

Evidence: [[ghn-02-javascript-obfuscator-issue-1423]].
Catalogue: [[github-hn-scan-2026-11-07-index]]. Methods: [[github-hn-scan-2026-11-07-methods]].
