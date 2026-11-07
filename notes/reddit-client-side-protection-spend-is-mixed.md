---
type: note
title: Reddit evidence on paying for client-side protection is mixed, with DexGuard in use, Denuvo spend, and two comments against obfuscation
tags: [market, customer, security]
date: 2026-11-07
by: karla+cursor
confidence: moderate
sources: [reddit-listener-code-protection-2026-11-07, https://www.reddit.com/r/androiddev/comments/1txmltu/, https://www.reddit.com/r/androiddev/comments/1txmltu/comment/oq6edbx/, https://www.reddit.com/r/gamedev/comments/1ur0ed0/comment/owc2thp/, https://www.reddit.com/r/gamedev/comments/1shhyx6/]
---

Hypothesis A2 from [[do-people-need-ai-resistant-code-protection]]: someone already pays to protect client-side code.

This note is only the Reddit listener sweep checked 2026-11-07 (Europe/Belgrade). It is not a verdict. The DexGuard row is also evidence for A3 and is repeated in [[reddit-obfuscation-breakage-shows-up-as-crashes-and-maintenance]]. The AAA row is labelled mixed in the sweep (A3 supports; A2 contradicts) and is repeated there too. Words are copied from [[reddit-listener-code-protection-2026-11-07]].

| link | thread date | author role | verbatim quote | hyp | s/c | signal |
| --- | --- | --- | --- | --- | --- | --- |
| https://www.reddit.com/r/androiddev/comments/1txmltu/ | 2026-06-05 | not visible (post author, team uses DexGuard) | "Currently, we're using the default behavior, which results in the app crashing when a RASP check is triggered. Because of this, we're seeing tens of thousands of crashes reported in Crashlytics, making it harder to monitor real production issues." | A3 + A2 | supports | experience, scale |
| https://www.reddit.com/r/androiddev/comments/1txmltu/comment/oq6edbx/ | 2026-06-05 | not visible | "It's not worth the hassle or the headache. It's all security through obscurity and any dedicated adversary will make mincemeat out of it." | A2 | contradicts | opinion |
| https://www.reddit.com/r/gamedev/comments/1ur0ed0/comment/owc2thp/ | 2026-07-08 | programmer, AAA, three titles (self-stated) | "Imo obfuscating your code base is only going to make it harder for you and your team to actually work within it. Even in my experience in AAA working across three titles as a programmer, obfuscating was not a thing in any capacity on any of them." | A3 supports; A2 contradicts | mixed | experience |
| https://www.reddit.com/r/gamedev/comments/1shhyx6/ | 2026-04-10 | not visible | "I still don't get why big studios still blow SO much money on Denuvo when public distain towards it is so clear." | A2 | supports | money mentioned |

`hyp`, `s/c`, and `signal` are the sweep's own cells. No price, contract, or vendor invoice is in any quote. "SO much money" is not a number. The DexGuard thread is on the comment shortlist; the Denuvo thread is excluded because it is archived. See [[reddit-five-threads-open-to-a-technical-comment]].

Why it matters: [[idea-brief-code-protection]] treats application shielding as an existing budget. On this sweep, one team is already on DexGuard, and one comment says studios "blow SO much money on Denuvo". The sweep marks two rows against A2: one says the hassle is not worth it, and a self-stated AAA programmer says obfuscation was not used on three titles and makes the team's own work harder.
