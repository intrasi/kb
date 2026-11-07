---
type: note
title: Three Reddit comments say current LLMs undo basic obfuscation, and one says AI will not replace deep reverse-engineering skill
tags: [market, customer, security]
date: 2026-11-07
by: karla+cursor
confidence: moderate
sources: [reddit-listener-code-protection-2026-11-07, https://www.reddit.com/r/ReverseEngineering/comments/1tiuuou/comment/omxcsfl/, https://www.reddit.com/r/gamedev/comments/1uqrhcg/comment/owa3cag/, https://www.reddit.com/r/programming/comments/1t2nimm/comment/ojoy1yr/, https://www.reddit.com/r/AskNetsec/comments/1p6b3pz/comment/nqpbm60/]
---

Hypothesis A1 from [[do-people-need-ai-resistant-code-protection]]: practitioners already see AI-assisted reverse engineering as a real, current threat.

This note is only the Reddit listener sweep checked 2026-11-07 (Europe/Belgrade). It is not a verdict. Confidence is moderate because every row is an opinion and no author role was visible. The words are copied from [[reddit-listener-code-protection-2026-11-07]].

| link | thread date | author role | verbatim quote | hyp | s/c | signal |
| --- | --- | --- | --- | --- | --- | --- |
| https://www.reddit.com/r/ReverseEngineering/comments/1tiuuou/comment/omxcsfl/ | 2026-05-20 | not visible | "obfuscated JavaScript is meant to be hard for humans to read, but still deterministic (i.e. mean the same thing) for machines to execute. LLMs are gigantic pattern recognition machines, and the patterns are still present" | A1 | supports | opinion |
| https://www.reddit.com/r/gamedev/comments/1uqrhcg/comment/owa3cag/ | 2026-07-08 | not visible | "with todays LLMs (AI), they are super good at reading/decrypting obfuscated code." | A1 | supports | opinion |
| https://www.reddit.com/r/programming/comments/1t2nimm/comment/ojoy1yr/ | 2026-05-03 | not visible | "Basic code obfuscation is almost certainly a 1 or 2 shot for any AI agent to undo, especially if it's JavaScript." | A1 | supports | opinion |
| https://www.reddit.com/r/AskNetsec/comments/1p6b3pz/comment/nqpbm60/ | 2025-11-25 | not visible | "AI will not replace any professional deep knowledge job. Just will make it easy for those who make the job. Or can your grandma RE an app just by using AI?" | A1 | contradicts (partly) | opinion |

Why it matters: Problem A in [[code-protection-project-description]] assumes AI already makes shipped code cheap to read. On this sweep, three comments support that for basic and JavaScript obfuscation, and one says AI helps people who already have the skill rather than replacing it. None of the four is a report of a crack, a cheat, or a clone.

The r/ReverseEngineering thread is also on the comment shortlist: [[reddit-five-threads-open-to-a-technical-comment]].
