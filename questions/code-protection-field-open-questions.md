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

- Luka's supplied reading list (2026-11-07): [[verified-obfuscation-reading-list-2026-11-07]]. Fourteen paper references and two additional sources covering verified transformations, AI-selected obfuscation, and AI reverse engineering. Start with entries 1, 2, 8, and 13. Bibliographic details and paper claims remain unverified; this is context for items 3, 4, and 6, not an answer to them.
- Project description: [[code-protection-project-description]].
- Public listening and budget numbers, owned by Karla: [[do-people-need-ai-resistant-code-protection]].
- Reddit listener only, checked 2026-11-07, not a verdict on items 1, 2, or 5. Raw sweep: [[reddit-listener-code-protection-2026-11-07]]. A2 (who already pays) is mixed and has no price: [[reddit-client-side-protection-spend-is-mixed]]. A4 and A5 were recorded as `not found` on Reddit: [[reddit-sweep-found-no-ask-for-an-ai-crack-score]], [[reddit-sweep-found-no-incumbent-ai-attacker-marketing]]. Incumbent pages are still open.
- Sourced market, loss, deal, survey, compliance, and gap records through cutoff 2026-11-07: [[code-protection-evidence-index]]. Schema: [[code-protection-evidence-schema]]. These are not a verdict on item 1.
- GitHub and Hacker News breakage and reversing reports from the 2026-11-07 scan: [[github-hn-scan-2026-11-07-index]]. Incumbent claims and equivalence limits remain open.

## Answer
