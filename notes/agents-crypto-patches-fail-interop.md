---
type: note
title: In one benchmark, 12 of 160 agent-written crypto patches passed local tests but failed against OpenSSL
tags: [agents, pqc]
date: 2026-11-07
by: karla+claude
confidence: moderate
sources: [https://arxiv.org/abs/2512.12989]
---

arXiv 2512.12989: coding agents can write multi-file cryptographic patches, but 12 of
160 passed their local tests and then failed an interoperability check against OpenSSL.
Open-weight models failed in every attempt (as we read it; re-check the table).

Why it matters: this is the frontier argument. Agents can now write the migration;
nobody proves it works. The 60-second demo is the checker catching one of these.

Related: [[pqc-signature-size]], [[pqc-market-discovery-crowded-remediation-open]].
