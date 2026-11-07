---
type: question
title: Is protecting shipped code against automated analysis a field we should work in, and does the formal-proof angle hold?
tags: [idea, security, formal-methods, market, customer]
date: 2026-11-07
by: karla+claude
status: open
owner:
---

Context: [[idea-brief-code-protection]]. The field is the commitment; the solution is not.

Nothing in the brief is verified yet. Before building, answer:

1. Market size and growth for application shielding, from a named report with its date.
2. What each incumbent (Jscrambler, Guardsquare, Zimperium) now claims about machine
   analysis, read from their own current pages, with dates.
3. Whether any vendor or research group already claims proof of equivalence for
   protecting transformations. Search academic work on verified compilation and
   equivalence checking, which is older than the product framing.
4. How large a function current equivalence tools handle in practice, with a measured
   number, since this sets whether the proof covers anything that matters.
5. Who signs: ask three buyers what they use today, what it costs them, and what would
   make them replace it. Drafts only; a human sends them.
6. Whether the measurement of attacker effort can be made honest and repeatable, or
   whether it reduces to a number we choose.

Question 4 is the one that decides the shape, so do it first; it is also the cheapest.

## Leads

- Saved conversation research, 2026-11-07: [[verified-obfuscation-could-reduce-protection-engineering-effort]] states the unvalidated engineering-effort hypothesis and a bounded experiment. [[obfuscation-is-common-in-popular-android-apps]] records adoption measurements with denominator limits; [[production-obfuscation-can-target-a-small-part-of-an-app]] records production scope and overhead. [[verified-obfuscation-research-links]] adds paper URLs, competitor disclosures, and evidence qualifications. This adds evidence for items 2, 3, and 6; production verification scale, customer interviews, and the overall decision remain open.
- Luka's supplied reading list (2026-11-07): [[verified-obfuscation-reading-list-2026-11-07]]. Fourteen paper references and two additional sources covering verified transformations, AI-selected obfuscation, and AI reverse engineering. Start with entries 1, 2, 8, and 13. Bibliographic details and paper claims remain unverified; this is context for items 3, 4, and 6, not an answer to them.
- Project description: [[code-protection-project-description]].
- Public listening and budget numbers, owned by Karla: [[do-people-need-ai-resistant-code-protection]].
- Reddit sweep 2 (2026-11-07) heard people ask how long client-side protection holds and whether it survives an LLM. That contradicts the sweep 1 "not found" on a measured score. It is evidence toward item 6, not an answer to it: [[where-does-ai-reverse-engineering-cost-money-reddit]], [[reddit-sweep-2-people-ask-how-long-protection-holds]].
- Reddit listener only, checked 2026-11-07, not a verdict on items 1, 2, or 5. Raw sweep: [[reddit-listener-code-protection-2026-11-07]]. A2 (who already pays) is mixed and has no price: [[reddit-client-side-protection-spend-is-mixed]]. A4 and A5 were recorded as `not found` on Reddit: [[reddit-sweep-found-no-ask-for-an-ai-crack-score]], [[reddit-sweep-found-no-incumbent-ai-attacker-marketing]]. Incumbent pages are still open.
- Sourced market, loss, deal, survey, compliance, and gap records through cutoff 2026-11-07: [[code-protection-evidence-index]]. Schema: [[code-protection-evidence-schema]]. These are not a verdict on item 1.
- GitHub and Hacker News breakage and reversing reports from the 2026-11-07 scan: [[github-hn-scan-2026-11-07-index]]. Incumbent claims and equivalence limits remain open.
- Tea's reverse-engineering desk research (tea+claude, checked 2026-11-07). Raw reports and the
  six-module dossier: [[re-defense-dossier]], [[re-agentic-resilience-benchmark-source-pack]],
  [[re-2026-cases-patterns-defenses]], [[re-deep-research-2026]], [[re-global-quantitative-taxonomy]].
  Twenty notes checked against primary sources are linked under `## Answer`; open items are in
  [[re-research-gaps-to-verify]].

## Answer

Partial, 2026-11-07, by tea+claude. Every linked note was checked against its primary source;
open gaps are tracked in [[re-research-gaps-to-verify]]. Status stays open until items 2, 3 and 5
are done.

1. Market size: use Karla's sourced records in [[code-protection-evidence-index]]; drop $16.2B.
   [[re-in-app-protection-16b-figure-has-no-source]], [[re-code-protection-vendors-mostly-pe-owned]],
   [[re-compliance-requires-resilience-not-method]].
2. Incumbent claims about machine analysis: Thales and Promon publish agent and LLM studies
   ([[re-protection-buys-cost-not-impossibility]],
   [[re-stacked-obfuscation-passes-cut-llm-success-in-vendor-study]]). Not yet read: Guardsquare,
   Jscrambler, Digital.ai.
3. Proof of equivalence: academia has Coq-verified flattening and MBA; no product has been checked
   yet. [[re-verified-obfuscation-exists-in-academia]],
   [[re-adaptive-llm-obfuscation-exists-only-at-source-level]].
4. Function size: proofs scale to thousands of lines only when the versions are structurally
   similar, and obfuscation removes that similarity. MBA breaks the solver.
   [[re-equivalence-proofs-scale-with-structural-similarity]],
   [[re-mba-obfuscation-defeats-smt-equivalence-proofs]].
5. Who signs: still open; needs buyer conversations, which a human sends.
6. Honest measurement: possible with an external oracle plus differential fuzzing, lift with
   confidence intervals, and refusals reported separately. SRE-Bench is the closest prior work.
   [[re-sre-bench-measures-hardening-lift-on-private-binaries]],
   [[re-open-configurable-lift-benchmark-is-the-remaining-gap]],
   [[re-shipped-tests-miss-decompiler-divergence]],
   [[re-benchmark-harness-must-be-hardened-against-agent-cheating]],
   [[re-frontier-agents-score-under-8-percent-on-malwarebench]].

Build-relevant notes: [[re-agents-route-around-obfuscation]],
[[re-llm-deobfuscation-ranking-by-technique-is-unsettled]],
[[re-free-llvm-obfuscators-plugin-or-source-build]],
[[re-tigress-virtualization-costs-42-to-247x-runtime]],
[[re-binary-prompt-injection-tested-only-on-small-models]],
[[re-benchmark-self-authored-binaries-for-legal-safety]].
