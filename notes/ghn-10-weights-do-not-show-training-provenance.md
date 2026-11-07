---
type: note
title: A commenter who ships open-weight iOS models says weights do not reveal training data or spiking
tags: [security]
date: 2026-11-07
by: karla+grok
confidence: moderate
sources: [ghn-10-hn-49076635, https://news.ycombinator.com/item?id=49076635]
record_id: ghn-10
hypothesis: [B1, B2]
stance: supports
signal: experience
---

James333i says behavior can be examined and guardrails stripped by fine-tuning, and that weights do not show what a model was trained on or whether the data was spiked. That supports B1, concern about fine-tune provenance, and it challenges the idea that a weight audit can assure training provenance. It is not a scanner benchmark, and it does not name a product scanner.

The same archived comment, not the excerpt above, says "I have shipped open weight models in iOS apps". That is the visible role. No seniority is stated.

- record_id: ghn-10
- hypothesis: B1, B2
- stance: supports
- stance_detail: supports provenance concern and challenges weight-audit assurance; not a scanner benchmark
- signal: experience
- visible role: self-reports shipping open-weight models in iOS apps
- caveat: self-report. Do not cite it as a test of a named scanner.

Evidence: [[ghn-10-hn-49076635]].
Catalogue: [[github-hn-scan-2026-11-07-index]]. Methods: [[github-hn-scan-2026-11-07-methods]].
