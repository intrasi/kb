---
type: note
title: Some comments say an AI key rebuilds an app in minutes, and others say binaries and C++ still resist
tags: [market, customer, security, agents]
date: 2026-11-07
by: karla+cursor
confidence: moderate
sources: [reddit-listener-ai-re-money-2026-11-07, https://www.reddit.com/r/electronjs/comments/1totsv0/, https://www.reddit.com/r/androiddev/comments/1r0hiuh/, https://www.reddit.com/r/ClaudeCode/comments/1qm7mwq/, https://www.reddit.com/r/Unity3D/comments/1vucg8e/, https://www.reddit.com/r/ReverseEngineering/comments/1vxig19/, https://www.reddit.com/r/LocalLLaMA/comments/1u3i3tu/, https://www.reddit.com/r/LocalLLaMA/comments/1wlql0p/, https://www.reddit.com/r/LocalLLaMA/comments/1vzg84e/]
---

Checked 2026-11-07 (Europe/Belgrade). Both sides, copied from [[reddit-listener-ai-re-money-2026-11-07]]. The E1 pipe is table escaping, as in [[reddit-sweep-2-ai-speed-is-not-a-reported-third-party-loss]].

Side that says the window has collapsed to minutes: E1 and E4 are verified, and they are the same developer testing their own Electron app. A5 is verified and states days without AI, hours with AI. A7 and R10 still need a check. G34 is verified and is a second-hand anecdote, not a timed test.

Side that disagrees: R9 is verified and is quoted in [[reddit-sweep-2-objection-cpp-decompilation-is-still-hard-for-llms]]. R6 is verified: hallucinations in reverse engineering are a huge problem. The sentence before it, about automating a validity check, is R6b and still needs a check. R4, R2, and R11 still need a check. R2's stated role is using a local model at work for reverse engineering. R11 says the automotive result was not tried on 2015-and-later vehicles that might have obfuscation.

A lab refusing the work is a separate row and still needs a check: [[reddit-sweep-2-legality-threads-not-found-except-a-lab-refusal]].

| ID | Link | Date | Username | Role (stated) | Verbatim quote | Quote status |
| --- | --- | --- | --- | --- | --- | --- |
| E1 | https://www.reddit.com/r/electronjs/comments/1totsv0/ | ~2026-05-26 | not found (OP) | ships an Electron desktop app (self) | "Today I unzipped my own DMG, ran `strings \| sort -u` on the renderer bundle, pasted the output into Claude … Ten minutes later I had an accurate diagram. Stores, actions, data flow, cache invalidation — all of it." | verified-in-thread |
| E4 | https://www.reddit.com/r/electronjs/comments/1totsv0/ | ~2026-05-26 | not found (OP) | Electron dev | "In the world where anyone with an Anthropic/OpenAI key can reconstruct your architecture in 10 minutes — what's working?" | verified-in-thread |
| A5 | https://www.reddit.com/r/androiddev/comments/1r0hiuh/ | 2026-02-10 | alifesoftware | not found | "Without AI: can be done in days. With AI: Matter of hours. If it's an exact clone, the only thing that needs to change is app ID, and even changing all the package names isn't too hard." | verified-in-thread (browser 2026-11-07) |
| A7 | https://www.reddit.com/r/androiddev/comments/1r0hiuh/ | 2026-02-10 | Tombstones19 | not found | "I can imagine with a couple of AI agent prompts it would be childishly easy to convert it back into a working project." | mirror-verbatim, needs-check |
| R10 | https://www.reddit.com/r/ClaudeCode/comments/1qm7mwq/ | 2026-01-25 | FirmConsideration717 | reverse-engineers automotive ECUs (implied) | "It did in a few days, sometimes a month, what took me 1.5-2 years to understand. I use ida-pro-mcp, I give it an automotive binary" | snippet-verbatim, needs thread check |
| G34 | https://www.reddit.com/r/Unity3D/comments/1vucg8e/ | not found (reply; thread ~2026-08-20) | Banholio | not found | "I remember when one guy did this in another engine. He put the obfuscated code to show the results. Another guy passed it through an AI and got everything back to normal xD." | verified-in-thread (browser 2026-11-07) |
| R9 | https://www.reddit.com/r/ReverseEngineering/comments/1vxig19/ | 2026-08-25 | Lahvuun | not found | "Had some success, but C++ decompilation is clearly still really difficult for LLMs." | verified-in-thread (browser 2026-11-07; corrected text) |
| R4 | https://www.reddit.com/r/LocalLLaMA/comments/1u3i3tu/ | 2026-06-12 | Due-Function-4877 | not found | "Absent a convenient short cut (like a virtual machine), "binaries" are going to be very difficult to reverse engineer." | mirror-verbatim, needs-check |
| R2 | https://www.reddit.com/r/LocalLLaMA/comments/1wlql0p/ | 2026-09-20 | Big_Importance_4265 | uses it "at work for RE" (self) | "I've used Qwen3.8-27b at Q8 232k context at work for RE. … It does draw incorrect conclusions sometimes but should be easy to nudge along the right path" | snippet-verbatim, needs thread check |
| R6 | https://www.reddit.com/r/LocalLLaMA/comments/1vzg84e/ | ~2026-08-27 | DanielSReichenbach | uses Qwen with a Ghidra MCP (self) | "Hallucinations in RE are a huge problem." | verified-in-thread (browser 2026-11-07) |
| R11 | https://www.reddit.com/r/ClaudeCode/comments/1qm7mwq/ | 2026-01-25 | FirmConsideration717 | automotive ECU reverser | "I have not tried it on modern vehicles like 2015+ which might have obfuscation, but on those where there isn't it is a beast." | snippet-verbatim, needs thread check |

Why it matters: "AI makes client-side protection obsolete" is true of one developer's own JavaScript bundle on the verified evidence, and it is disputed for C++ and for binaries. Both sentences belong on the slide.

Source: [[reddit-listener-ai-re-money-2026-11-07]].
