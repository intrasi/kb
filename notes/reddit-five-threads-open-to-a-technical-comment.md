---
type: note
title: Five Reddit threads from the 2026-11-07 sweep allow a technical comment, and five subreddits stayed read-only
tags: [market, customer, security, hackathon]
date: 2026-11-07
by: karla+cursor
confidence: high
sources: [reddit-listener-code-protection-2026-11-07]
---

Copied from the sweep in [[reddit-listener-code-protection-2026-11-07]]. The sweep wrote "Comment shortlist (no drafts)". No reply text is included here. A human sends anything that gets posted. Agents draft; they do not publish. See the posting rules in [[do-people-need-ai-resistant-code-protection]].

## Comment shortlist (no drafts)

1. https://www.reddit.com/r/ReverseEngineering/comments/1tiuuou/ : AI deobfuscation of JS is the core of Problem A; Rule 2 welcomes technical content.
2. https://www.reddit.com/r/androiddev/comments/1txmltu/ : DexGuard RASP crash pain (A3); technical answer fits; no app promotion allowed (Rule 2).
3. https://www.reddit.com/r/gamedev/comments/1uqrhcg/ : asks how to protect browser games, LLM deobfuscation raised; Rule 4 allows discussion links with context.
4. https://www.reddit.com/r/programming/comments/1t2nimm/ : obscurity vs AI-undo debate; comments fine, no product promo (Rule 5) or surveys (Rule 7).
5. https://www.reddit.com/r/LocalLLaMA/comments/1uiqbje/ : weight backdoor feasibility (B); Rule 4 requires disclosed affiliation, 1/10 self-promo.

Excluded: r/gamedev 1shhyx6 is archived.

## Read-only subreddits

- r/netsec: Rule 4 bars commercial content without 6+ months of community history.
- r/MachineLearning: Rule 3 bans marketing campaigns with permanent bans; line for a founder's comment unclear.
- r/AskNetsec: Rule 2 says industry surveys not relevant; rep disclosure allowed (Rule 7) but research intent unclear.
- r/cybersecurity: Rules 5/6 strict on promotion; no in-window thread read.
- r/iOSProgramming: rules allow some self-promo; no relevant thread found.

## Coverage

reddit.com JSON endpoints all 403; old.reddit.com redirected to login. Quotes read on public www.reddit.com pages without logging in. Reddit pages had hidden instructions aimed at AI agents; ignored. No votes, posts, comments or DMs.

Quotes from the five threads are in the hypothesis notes linked from [[do-people-need-ai-resistant-code-protection]]. The archived Denuvo thread is quoted in [[reddit-client-side-protection-spend-is-mixed]].
