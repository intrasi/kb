---
type: note
title: Reddit reports obfuscation pain as DexGuard RASP crashes at tens of thousands, plus harder maintenance, performance, and debugging
tags: [market, customer, security]
date: 2026-11-07
by: karla+cursor
confidence: moderate
sources: [reddit-listener-code-protection-2026-11-07, https://www.reddit.com/r/androiddev/comments/1txmltu/, https://www.reddit.com/r/gamedev/comments/1ur0ed0/comment/owc2thp/, https://www.reddit.com/r/programming/comments/1t2nimm/comment/ojwgcoe/]
---

Hypothesis A3 from [[do-people-need-ai-resistant-code-protection]]: breakage is a real pain with obfuscation today (this is what a proof would fix).

This note is only the Reddit listener sweep checked 2026-11-07 (Europe/Belgrade). It is not a verdict. The DexGuard row is also A2 and is repeated in [[reddit-client-side-protection-spend-is-mixed]]. The AAA row is labelled `A3 supports; A2 contradicts` in the sweep; the A2 half is in that same note. Words are copied from [[reddit-listener-code-protection-2026-11-07]].

| link | thread date | author role | verbatim quote | hyp | s/c | signal |
| --- | --- | --- | --- | --- | --- | --- |
| https://www.reddit.com/r/androiddev/comments/1txmltu/ | 2026-06-05 | not visible (post author, team uses DexGuard) | "Currently, we're using the default behavior, which results in the app crashing when a RASP check is triggered. Because of this, we're seeing tens of thousands of crashes reported in Crashlytics, making it harder to monitor real production issues." | A3 + A2 | supports | experience, scale |
| https://www.reddit.com/r/gamedev/comments/1ur0ed0/comment/owc2thp/ | 2026-07-08 | programmer, AAA, three titles (self-stated) | "Imo obfuscating your code base is only going to make it harder for you and your team to actually work within it. Even in my experience in AAA working across three titles as a programmer, obfuscating was not a thing in any capacity on any of them." | A3 supports; A2 contradicts | mixed | experience |
| https://www.reddit.com/r/programming/comments/1t2nimm/comment/ojwgcoe/ | 2026-05-03 | not visible | "(usually) the downsides (harder maintenance, performance hits, debugging problems) aren't worth the amount of security it gives you." | A3 | supports | opinion |

`hyp`, `s/c`, and `signal` are the sweep's own cells. No row here is a measured before-and-after of a proof. The crash report is the RASP check firing, which [[code-protection-project-description]] already separates from a rewrite that is supposed to leave behaviour unchanged.

Why it matters: a proof of equivalence would not, on these quotes alone, address a RASP crash that is the check firing. It would address the maintenance, performance, and debugging costs in the r/programming comment, and the AAA comment that obfuscation makes the team's own code harder to work in.
