---
type: note
title: Paid desktop apps and plugins rank second, with local licence checks bypassed or cracked
tags: [market, customer, security]
date: 2026-11-07
by: karla+cursor
confidence: moderate
sources: [reddit-listener-ai-re-money-2026-11-07, https://www.reddit.com/r/macapps/comments/1ryvdei/, https://www.reddit.com/r/SideProject/comments/1tzztv9/, https://www.reddit.com/r/developers/comments/1u9ewhw/, https://www.reddit.com/r/ExtendedRangeGuitars/comments/1vh5lel/, https://www.reddit.com/r/AudioProgramming/comments/1togirt/, https://www.reddit.com/r/electronjs/comments/1totsv0/]
---

Checked 2026-11-07 (Europe/Belgrade). Second use case in [[where-does-ai-reverse-engineering-cost-money-reddit]]. Quotes are copied from [[reddit-listener-ai-re-money-2026-11-07]].

M1 is verified. The stated role is "a developer and a security research engineer". The quote says every app in the audit had a local way around its licensing or Pro checks. The row's money-or-time cell says "7 weeks, 32 of 32 apps". Those two figures are not inside the quote, so they are the sweep's cell, not a second quotation. M5, a solo macOS developer (self-stated), is verified: after a viral night, project files were reposted with what looked like a separate licence-key flow. The row's time cell says days after "500K views overnight"; that phrase is not in the quote below.

P3 still needs a thread check. It is the plugin developer at RJ Labs (self-stated) saying the plugin was cracked after a couple of months. M4, a small indie dev (self-stated), still needs a thread check. P2 is verified and describes delayed checks in the plugin. P1, someone who has worked with PACE / Eden (self-stated), is verified and is looking for alternatives those vendors will not explain without payment. E2, verified, asks whether VM-tier obfuscators survive LLM analysis. E3, verified, is the breakage that comes with one obfuscator option.

| ID | Link | Date | Username | Role (stated) | Verbatim quote | Quote status |
| --- | --- | --- | --- | --- | --- | --- |
| M1 | https://www.reddit.com/r/macapps/comments/1ryvdei/ | ~2026-03-19 (audit 20 Jan–10 Mar 2026) | SenpaiHunters | "a developer and a security research engineer" (self) | "Every single one had at least one real way to bypass its licensing or Pro checks using only local tools, no binary patching." | verified-in-thread |
| M5 | https://www.reddit.com/r/SideProject/comments/1tzztv9/ | ~2026-06-07 | not found (OP) | solo macOS app dev (self) | "it looked like a copied/modified version of my project files, publicly uploaded, with what seemed to be their own license key flow." | verified-in-thread |
| M4 | https://www.reddit.com/r/developers/comments/1u9ewhw/ | ~2026-06-18 | not found (OP) | "small indie dev" (self) | "I am a small indie dev, and one of my apps was cracked and then distributed on a website called MacKed." | snippet-verbatim, needs thread check |
| P3 | https://www.reddit.com/r/ExtendedRangeGuitars/comments/1vh5lel/ | 2026-08-06 | RobJmusic | plugin developer, RJ Labs (self) | "It's been out for a couple of months, and I'm really happy with the support so far :) That being said, the plugin finally got cracked." | snippet-verbatim, needs thread check |
| P2 | https://www.reddit.com/r/AudioProgramming/comments/1togirt/ | 2026-05-29 (comment) | ptrnyc | not found | "The crucial part of the system is that the plugin code has many, many delayed checks that use some of the secret bits, that allow delayed detection of hacked versions, and gently prompt the user to buy the plugin when it happens." | verified-in-thread (browser 2026-11-07) |
| P1 | https://www.reddit.com/r/AudioProgramming/comments/1togirt/ | ~2026-05-25 | not found (OP) | has worked with PACE / Eden (self) | "I tried to find alternatives, but these companies (understandably) don't really want you to know too much about their services unless you pay for them..." | verified-in-thread |
| E2 | https://www.reddit.com/r/electronjs/comments/1totsv0/ | ~2026-05-26 | not found (OP) | Electron dev | "VM-tier commercial obfuscators (obfuscator.io VM, JScrambler). Worth it? Survives LLM analysis?" | verified-in-thread |
| E3 | https://www.reddit.com/r/electronjs/comments/1totsv0/ | ~2026-05-26 | not found (OP) | Electron dev | "renameProperties: true … heads up to anyone considering this: the app won't launch. Tried it across 3 different obfuscator seeds." | verified-in-thread |

The ten-minute Claude read of the same Electron app is a first-person test, filed separately: [[reddit-sweep-2-ai-speed-is-not-a-reported-third-party-loss]]. Moving the licence decision to the server is the alternative these threads name: [[reddit-sweep-2-open-source-the-client-posts-were-deleted]].

Why it matters: the asset on the device is a local licence or Pro check. The verified audit says those checks were bypassable without binary patching. A crack timed in months, rather than hours, is still needs-check.

Source: [[reddit-listener-ai-re-money-2026-11-07]].
