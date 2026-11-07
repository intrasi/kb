---
type: note
title: Reddit threads ask how long obfuscation holds and whether it survives an LLM, which contradicts the first sweep
tags: [market, customer, security, idea]
date: 2026-11-07
by: karla+cursor
confidence: moderate
sources: [reddit-listener-ai-re-money-2026-11-07, reddit-sweep-found-no-ask-for-an-ai-crack-score, reddit-listener-code-protection-2026-11-07, https://www.reddit.com/r/AskNetsec/comments/1ue7334/, https://www.reddit.com/r/AskNetsec/comments/1vksrwn/, https://www.reddit.com/r/electronjs/comments/1totsv0/, https://www.reddit.com/r/javascript/comments/1s0d0ns/, https://www.reddit.com/r/brdev/comments/1utun12/, https://www.reddit.com/r/macapps/comments/1ryvdei/, https://www.reddit.com/r/LocalLLaMA/comments/1vzg84e/, https://www.reddit.com/r/AskNetsec/comments/1s1u4l8/, https://www.reddit.com/r/PiratedGames/comments/1tpeppa/]
---

Checked 2026-11-07 (Europe/Belgrade). Quotes are copied from [[reddit-listener-ai-re-money-2026-11-07]]. This note supersedes [[reddit-sweep-found-no-ask-for-an-ai-crack-score]]. That note stays. It is the sweep 1 record, and its only A4 row was `not found`.

Sweep 1's conclusion was that nobody asked for a measured "how hard is my app for AI to crack" score. These rows are asks, or the nearest rejection. They are not purchase orders for a score.

Verified asks:

- F1 asks how teams validate shielding across releases, because a control can be weakened on the next build.
- E2 asks whether VM-tier commercial obfuscators survive LLM analysis.
- E4 asks what is working, given a ten-minute reconstruction with an API key.
- W1 is a verified title only: a JavaScript obfuscator that AI cannot crack.
- BR1, an Android developer thread in Brazil, asks whether teams do more than R8 or ProGuard and whether they are satisfied.

Still needs a check, and this is the sharpest time question: F5, someone who ships a native binary in a hardware product (self-stated), asks whether obfuscation adds hours, a day, or a week. R6b, the sentence about automating validity of reverse-engineering work, is also still needs-check. The verified R6 sentence is the hallucination problem, not the ask.

Adjacent, not themselves asks for a score: M2, verified, says the developer is losing revenue and does not realise the checks are flimsy. F2, verified, says present and effective are different properties. F10 is a verified title only, a liveness stress-test question, not an obfuscation question.

Rejections: F7, verified, asks what risk is being mitigated. G12, still needs-check, says a proper count is impossible.

| ID | Link | Date | Username | Role (stated) | Verbatim quote | Quote status |
| --- | --- | --- | --- | --- | --- | --- |
| F1 | https://www.reddit.com/r/AskNetsec/comments/1ue7334/ | 2026-06-24 | Ok_Extent1078 | not found | "the harder question seems to be whether those protections actually hold up when someone tries to bypass them. … I'm especially curious about how people validate this across releases, since a protection can be present in one build and weakened or misconfigured in the next." | verified-in-thread |
| F5 | https://www.reddit.com/r/AskNetsec/comments/1vksrwn/ | ~2026-08-10 | PlaintextFloor | ships a native binary in a hardware product (self) | "What I really want to know is how much time this actually buys. For a competent reverser with a physical unit, does obfuscation like this add hours? A day? A week?" | mirror-verbatim, needs-check |
| E2 | https://www.reddit.com/r/electronjs/comments/1totsv0/ | ~2026-05-26 | not found (OP) | Electron dev | "VM-tier commercial obfuscators (obfuscator.io VM, JScrambler). Worth it? Survives LLM analysis?" | verified-in-thread |
| E4 | https://www.reddit.com/r/electronjs/comments/1totsv0/ | ~2026-05-26 | not found (OP) | Electron dev | "In the world where anyone with an Anthropic/OpenAI key can reconstruct your architecture in 10 minutes — what's working?" | verified-in-thread |
| W1 | https://www.reddit.com/r/javascript/comments/1s0d0ns/ | ~2026-03-21 | not found (OP) | not found | "[AskJS] Has anyone actually found a JS obfuscator that AI can't crack? Because I think I might have." | verified-in-thread (title only) |
| BR1 | https://www.reddit.com/r/brdev/comments/1utun12/ | ~2026-07-11 | not found (OP) | Android developer (implied) | "vocês fazem alguma coisa pra dificultar engenharia reversa ou ficam só com o que o R8/ProGuard já oferece? … E, no geral, estão satisfeitos com a solução atual?" | verified-in-thread |
| M2 | https://www.reddit.com/r/macapps/comments/1ryvdei/ | ~2026-03-19 | SenpaiHunters | security research engineer | "the developer is losing revenue and doesn't realise how flimsy their checks are" | verified-in-thread |
| R6 | https://www.reddit.com/r/LocalLLaMA/comments/1vzg84e/ | ~2026-08-27 | DanielSReichenbach | uses Qwen with a Ghidra MCP (self) | "Hallucinations in RE are a huge problem." | verified-in-thread (browser 2026-11-07) |
| R6b | https://www.reddit.com/r/LocalLLaMA/comments/1vzg84e/ | ~2026-08-27 | DanielSReichenbach | uses Qwen with a Ghidra MCP (self) | "you should also find a way to automate validity of the work." | mirror-verbatim, needs-check |
| F2 | https://www.reddit.com/r/AskNetsec/comments/1ue7334/ | 2026-06-25 (comment) | whatwilly0ubuild | runs red-teaming "for clients in payments" (self) | "Present and effective are completely different properties, and a build can ship every control you listed and still fall in ten minutes to someone with Frida." | verified-in-thread (browser 2026-11-07) |
| F10 | https://www.reddit.com/r/AskNetsec/comments/1s1u4l8/ | ~2026-03-23 | not found (OP) | not found | "Deepfake injection attacks bypassing liveness checks — ML detection as a signal layer, not a gate. Anyone stress-tested this approach?" | verified-in-thread (title) |
| F7 | https://www.reddit.com/r/AskNetsec/comments/1vksrwn/ | ~2026-08-11 (comment) | dmaul | not found | "What risk is being mitigated by trying to prevent reverse engineering?" | verified-in-thread (browser 2026-11-07) |
| G12 | https://www.reddit.com/r/PiratedGames/comments/1tpeppa/ | 2026-05-27 | Geges721 | not found | "It's simply impossible to count (properly)" | snippet-verbatim, needs thread check |

F6 answered F5 with ranges and no method. Only the weak-obfuscation sentence is verified: [[reddit-sweep-2-controversy-obscurity-or-time-bought]].

Why it matters: hypothesis A4 in [[do-people-need-ai-resistant-code-protection]] was the measurement gap. On Reddit, after this sweep, the gap is no longer "nobody asked". The gap is that the clearest time question is still unverified, and nobody posted a method that would score an app.

Source: [[reddit-listener-ai-re-money-2026-11-07]].
