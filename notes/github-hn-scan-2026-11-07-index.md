---
type: note
title: Twelve GitHub and HN self-reports from the 2026-11-07 scan leave A2, A4, and A5 unresolved
tags: [security, agents]
date: 2026-11-07
by: karla+grok
confidence: high
sources: [github-hn-scan-2026-11-07-methods]
record_id: ghn-index
---

The 2026-11-07 GitHub and Hacker News scan filed twelve self-reports. A2 and A5 were not researched. A4 was searched and not found. This note is the catalogue. It does not answer [[do-people-need-ai-resistant-code-protection]]. The quotes are claims, not independently verified events. Raw wording is in the linked sources. Raw Hacker News JSON is under `sources/github-hn-scan-2026-11-07/hn/`. GitHub raw JSON was not saved.

How to find a record: `grep -l "record_id: ghn-01" notes sources`, or `grep -l "^hypothesis: A3" notes`. B1 and B2 share [[ghn-10-weights-do-not-show-training-provenance]], whose frontmatter is `hypothesis: [B1, B2]`. Stable IDs are `ghn-01` through `ghn-12`. The listening question is [[do-people-need-ai-resistant-code-protection]]. The field question is [[code-protection-field-open-questions]].

Hypotheses below were supplied for the scan. They are not conclusions.

| ID | Hypothesis | In this scan |
| --- | --- | --- |
| A1 | Practitioners see AI-assisted reverse engineering as a real current threat | [[ghn-06-ghidramcp-dat-quote-is-neutral]], [[ghn-07-opus-re-obfuscated-code-report]], [[ghn-08-ghidramcp-firmware-use-is-not-buyer-evidence]], [[ghn-09-ai-re-paused-for-heat-and-context]] |
| A2 | Someone pays to protect client-side code | Not researched |
| A3 | Obfuscation breakage and compatibility or deployment pain | [[ghn-01-production-build-crash-report]], [[ghn-02-dead-code-injection-breakage-report]], [[ghn-03-tigress-runtime-crash-report]], [[ghn-04-proguard-kotlin-upgrade-crash-report]], [[ghn-05-pluto-backend-pass-crash-report]] |
| A4 | Measured demand for AI cracking resistance | Searched, not found |
| A5 | Incumbents market protection against AI attackers | Not researched |
| B1 | Fine-tune provenance concerns | [[ghn-10-weights-do-not-show-training-provenance]] |
| B2 | Scanners are seen as insufficient for weight backdoors | [[ghn-10-weights-do-not-show-training-provenance]], [[ghn-11-weight-backdoor-reported-after-propagation]], [[ghn-12-javelin-claim-is-not-weight-backdoor-proof]] |

| ID | Date | Author | Role as visible | Hypothesis | Stance | Signal | Quote source |
| --- | --- | --- | --- | --- | --- | --- | --- |
| ghn-01 | 2026-10-07 | NotYoojun | not found | A3 | supports | experience | [[ghn-01-javascript-obfuscator-issue-1462]] |
| ghn-02 | 2026-07-07 | julianmesa-gitkraken | not found | A3 | supports | experience | [[ghn-02-javascript-obfuscator-issue-1423]] |
| ghn-03 | 2025-09-16 | ttyA0 | not found | A3 | supports | experience | [[ghn-03-tigress-issue-1]] |
| ghn-04 | 2026-06-11 | bodiam | not found | A3 | supports | experience | [[ghn-04-proguard-issue-530]] |
| ghn-05 | 2023-12-17 | mrh929 | GitHub association CONTRIBUTOR, not re-checked | A3 | supports | experience | [[ghn-05-pluto-issue-58]] |
| ghn-06 | 2025-04-04 | catmandx | not found | A1 | neutral/insufficient | experience | [[ghn-06-ghidramcp-issue-27]] |
| ghn-07 | 2026-02-22 | hereme888 | not found | A1 | supports | experience | [[ghn-07-hn-47113638]] |
| ghn-08 | 2026-04-16 | heeen2 | not found | A1 | supports practical use only | experience | [[ghn-08-hn-47790292]] |
| ghn-09 | 2026-10-12 | asimovDev | self-reported very little reverse-engineering experience | A1 | contradicts frictionless capability only | experience | [[ghn-09-hn-50052962]] |
| ghn-10 | 2026-07-28 | James333i | self-reports shipping open-weight models in iOS apps | B1, B2 | supports provenance concern; not a scanner benchmark | experience | [[ghn-10-hn-49076635]] |
| ghn-11 | 2026-05-23 | GeorgeWoff25 | not found | B2 | supports as a self-report | experience | [[ghn-11-hn-48248289]] |
| ghn-12 | 2025-08-14 | sharathr | self-described co-founder CEO of Javelin | B2 | contradicts blanket insufficiency; not weight-backdoor proof | experience, vendor claim | [[ghn-12-hn-44897077]] |

Dates are Europe/Belgrade creation dates. Notes: [[ghn-01-production-build-crash-report]], [[ghn-02-dead-code-injection-breakage-report]], [[ghn-03-tigress-runtime-crash-report]], [[ghn-04-proguard-kotlin-upgrade-crash-report]], [[ghn-05-pluto-backend-pass-crash-report]], [[ghn-06-ghidramcp-dat-quote-is-neutral]], [[ghn-07-opus-re-obfuscated-code-report]], [[ghn-08-ghidramcp-firmware-use-is-not-buyer-evidence]], [[ghn-09-ai-re-paused-for-heat-and-context]], [[ghn-10-weights-do-not-show-training-provenance]], [[ghn-11-weight-backdoor-reported-after-propagation]], [[ghn-12-javelin-claim-is-not-weight-backdoor-proof]].

## Gaps

- A2 and A5 were not researched. Absence of records is not a finding.
- A4, direct demand for a measured AI cracking-resistance score, was not found.
- Exact-phrase app shielding, anti-cheat experience that ties AI reversing to protection breakage, IDA LLM plugins, and directly observed R8 breakage were not filed. Details and the query list: [[github-hn-scan-2026-11-07-methods]].

## Caveats that are easy to miss

- [[ghn-06-ghidramcp-dat-quote-is-neutral]] is neutral/insufficient for A1.
- [[ghn-08-ghidramcp-firmware-use-is-not-buyer-evidence]] is practical use, not a buyer concern.
- [[ghn-09-ai-re-paused-for-heat-and-context]] contradicts frictionless capability, not the existence of a threat.
- [[ghn-12-javelin-claim-is-not-weight-backdoor-proof]] is a vendor claim and does not prove weight-backdoor detection.
