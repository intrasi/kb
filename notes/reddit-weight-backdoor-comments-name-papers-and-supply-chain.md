---
type: note
title: One Reddit comment calls supply-chain compromise the more realistic attack, and another says weight attacks are doable and shown in papers
tags: [market, customer, security]
date: 2026-11-07
by: karla+cursor
confidence: moderate
sources: [reddit-listener-code-protection-2026-11-07, https://www.reddit.com/r/LocalLLaMA/comments/1uiqbje/comment/ouhpvve/, https://www.reddit.com/r/LocalLLaMA/comments/1tmpqrv/comment/onokk3l/]
---

Hypothesis B1 from [[do-people-need-ai-resistant-code-protection]]: teams worry about the provenance and safety of fine-tunes they did not train.

This note is only the Reddit listener sweep checked 2026-11-07 (Europe/Belgrade). It is not a verdict. The second row is labelled `B1 + B2` in the sweep and is repeated in [[reddit-comments-say-weight-backdoors-are-hard-to-spot]]. Words are copied from [[reddit-listener-code-protection-2026-11-07]]. No author role was visible. The "few papers" are not named in the quote, so this note does not name them.

| link | thread date | author role | verbatim quote | hyp | s/c | signal |
| --- | --- | --- | --- | --- | --- | --- |
| https://www.reddit.com/r/LocalLLaMA/comments/1uiqbje/comment/ouhpvve/ | 2026-06-29 | not visible | "The more realistic attack imo is supply-chain: one of the big open agent/harness projects, templates, MCP servers, or tool runtimes gets compromised, and the model is just the thing that executes the poisoned workflow." | B1 | contradicts | opinion |
| https://www.reddit.com/r/LocalLLaMA/comments/1tmpqrv/comment/onokk3l/ | 2026-05-25 | not visible | "It's absolutely doable and it has been done in a few papers, and there isn't really a way to guard against it other than manually verifying every tool call or having a known trusted model verify the calls" | B1 + B2 | supports | opinion, cites papers |

Why it matters: [[glassbox-project-description]] is about hidden behaviour in a fine-tune's weights, and about getting that model through review. This sweep did not record a team blocking a fine-tune, a Hugging Face review, or a preference for API models. One comment points the realistic attack at the tool supply chain. The other says the attack is doable, cites unnamed papers, and names manual checks or a trusted model as the guard. The r/LocalLLaMA thread `1uiqbje` is on the comment shortlist: [[reddit-five-threads-open-to-a-technical-comment]].
