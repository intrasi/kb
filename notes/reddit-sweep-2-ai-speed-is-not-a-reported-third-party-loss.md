---
type: note
title: AI reverse-engineering speed is claimed in first person, and no row reports a third-party AI crack that cost money
tags: [market, customer, security, agents]
date: 2026-11-07
by: karla+cursor
confidence: moderate
sources: [reddit-listener-ai-re-money-2026-11-07, reddit-comments-say-llms-undo-basic-obfuscation, https://www.reddit.com/r/electronjs/comments/1totsv0/, https://www.reddit.com/r/androiddev/comments/1r0hiuh/, https://www.reddit.com/r/ClaudeCode/comments/1qm7mwq/, https://www.reddit.com/r/LocalLLaMA/comments/1u3i3tu/, https://www.reddit.com/r/ReverseEngineering/comments/1vxig19/, https://www.reddit.com/r/Unity3D/comments/1vucg8e/, https://www.reddit.com/r/LocalLLaMA/comments/1vzg84e/]
---

Checked 2026-11-07 (Europe/Belgrade). Quotes are copied from [[reddit-listener-ai-re-money-2026-11-07]]. In the E1 cell, `\|` is only the table escaping a pipe. The words are `strings | sort -u`.

Sweep 1 recorded opinions that LLMs undo basic obfuscation, with no incident: [[reddit-comments-say-llms-undo-basic-obfuscation]]. This sweep adds first-person times. It still has no row in which someone reports that a third party used AI to crack their product and that the crack caused a measured loss.

E1 is verified. The person ships an Electron desktop app (self-stated) and ran the test on their own build. The time in the quote is ten minutes. A5 is verified and is a general clone-speed claim, not a named victim's loss. R10 still needs a thread check. The findings file describes the person as someone who reverse-engineers automotive ECUs. The quote says 1.5-2 years of understanding shrank to days, and it names ida-pro-mcp. The role cell says "implied", not a role the person stated. There is no link to that tool here. R8 is verified: $85k of tokens, 200 euros paid. The browser check did not include a 34% figure or a one-month figure. Those stay on R8b as needs-check. The thread is a decompilation project, not a studio reporting lost sales. R5 still needs a check. Its quote is a token bill of roughly $200 for decompiling an old chess app, which is the speaker's cost, not a victim's loss. G34 is verified and is second-hand: someone else passed obfuscated code through an AI. R7 is verified and says PS5 emulator work uses Claude or ChatGPT with Ghidra or IDA. That is not a loss report.

| ID | Link | Date | Username | Role (stated) | Verbatim quote | Quote status |
| --- | --- | --- | --- | --- | --- | --- |
| E1 | https://www.reddit.com/r/electronjs/comments/1totsv0/ | ~2026-05-26 | not found (OP) | ships an Electron desktop app (self) | "Today I unzipped my own DMG, ran `strings \| sort -u` on the renderer bundle, pasted the output into Claude … Ten minutes later I had an accurate diagram. Stores, actions, data flow, cache invalidation — all of it." | verified-in-thread |
| A5 | https://www.reddit.com/r/androiddev/comments/1r0hiuh/ | 2026-02-10 | alifesoftware | not found | "Without AI: can be done in days. With AI: Matter of hours. If it's an exact clone, the only thing that needs to change is app ID, and even changing all the package names isn't too hard." | verified-in-thread (browser 2026-11-07) |
| R10 | https://www.reddit.com/r/ClaudeCode/comments/1qm7mwq/ | 2026-01-25 | FirmConsideration717 | reverse-engineers automotive ECUs (implied) | "It did in a few days, sometimes a month, what took me 1.5-2 years to understand. I use ida-pro-mcp, I give it an automotive binary" | snippet-verbatim, needs thread check |
| R5 | https://www.reddit.com/r/LocalLLaMA/comments/1u3i3tu/ | 2026-06-12 | Wishitweretru | not found | "I had cline decompile a very old windows chess app. Deconstruct the data storage, and generate a web app out of it … That was last year, and the tokens ran to roughly $200." | mirror-verbatim, needs-check |
| R8 | https://www.reddit.com/r/ReverseEngineering/comments/1vxig19/ | 2026-08-24 | NXGZ | not found | "Burned $85k worth of tokens, though only cost 200 euros for using a subscription." | verified-in-thread (browser 2026-11-07) |
| R8b | https://www.reddit.com/r/ReverseEngineering/comments/1vxig19/ | 2026-08-24 | NXGZ | not found | "34% of the game has been decompiled to C++" | snippet-verbatim, needs thread check |
| G34 | https://www.reddit.com/r/Unity3D/comments/1vucg8e/ | not found (reply; thread ~2026-08-20) | Banholio | not found | "I remember when one guy did this in another engine. He put the obfuscated code to show the results. Another guy passed it through an AI and got everything back to normal xD." | verified-in-thread (browser 2026-11-07) |
| R7 | https://www.reddit.com/r/LocalLLaMA/comments/1vzg84e/ | ~2026-08-27 | Rasekov | not found | "Also, not local but the PS5 emulators are being developed with heavy use of claude/chatgpt + ghidra/IDA Pro. IIRC some of the N64 and PS1 decompilations did use LLMs too." | verified-in-thread (browser 2026-11-07) |

Why it matters: AI's role in this sweep is speed of analysis. The 2026 game-window rows do not name AI at all: [[reddit-sweep-2-game-drm-timing-rows-do-not-name-ai]]. A buyer who wants a measured attacker cost is asking a question this sweep did hear: [[reddit-sweep-2-people-ask-how-long-protection-holds]].

Source: [[reddit-listener-ai-re-money-2026-11-07]].
