---
type: note
title: Reddit comments say weight-level attacks are hard to spot in time, and one calls the problem really hard
tags: [market, customer, security]
date: 2026-11-07
by: karla+cursor
confidence: moderate
sources: [reddit-listener-code-protection-2026-11-07, https://www.reddit.com/r/LocalLLaMA/comments/1uiqbje/comment/oujuma0/, https://www.reddit.com/r/LocalLLaMA/comments/1tmpqrv/comment/onokk3l/, https://www.reddit.com/r/MachineLearning/comments/1sarnt0/comment/odytozn/]
---

Hypothesis B2 from [[do-people-need-ai-resistant-code-protection]]: existing scanners are seen as insufficient for weight-level backdoors.

This note is only the Reddit listener sweep checked 2026-11-07 (Europe/Belgrade). It is not a verdict. The middle row is labelled `B1 + B2` and is repeated in [[reddit-weight-backdoor-comments-name-papers-and-supply-chain]]. Words are copied from [[reddit-listener-code-protection-2026-11-07]]. No author role was visible. No row names a scanner product.

| link | thread date | author role | verbatim quote | hyp | s/c | signal |
| --- | --- | --- | --- | --- | --- | --- |
| https://www.reddit.com/r/LocalLLaMA/comments/1uiqbje/comment/oujuma0/ | 2026-06-29 | not visible | "These types of attack will use either very subtle effects that are damn near impossible to spot, or be built for single target attacks where spotting the problem as it happens is already too late" | B2 | supports | opinion |
| https://www.reddit.com/r/LocalLLaMA/comments/1tmpqrv/comment/onokk3l/ | 2026-05-25 | not visible | "It's absolutely doable and it has been done in a few papers, and there isn't really a way to guard against it other than manually verifying every tool call or having a known trusted model verify the calls" | B1 + B2 | supports | opinion, cites papers |
| https://www.reddit.com/r/MachineLearning/comments/1sarnt0/comment/odytozn/ | 2026-04-02 | not visible | "Looks like an interesting approach towards solving a really hard problem." | B2 | supports (weak) | opinion |

The third row is the sweep's only `supports (weak)` label. The parent post that "interesting approach" refers to is not quoted in the sweep, so this note does not describe that approach.

Why it matters: [[glassbox-project-description]] claims file scanners miss behaviour trained into the weights. These comments support "hard to spot" and "no guard except manual verification or a trusted model." They do not say that today's scanners are good enough, and they do not name a scanner that failed. r/MachineLearning was left read-only for a founder's comment: [[reddit-five-threads-open-to-a-technical-comment]].
