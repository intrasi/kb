---
type: note
title: Mobile entitlements and banking shielding rank third, because the client is trusted with the money
tags: [market, customer, security]
date: 2026-11-07
by: karla+cursor
confidence: moderate
sources: [reddit-listener-ai-re-money-2026-11-07, gigabud-cloned-banking-app-observations, https://www.reddit.com/r/androiddev/comments/1szvr54/, https://www.reddit.com/r/androiddev/comments/1r0hiuh/, https://www.reddit.com/r/AskNetsec/comments/1ue7334/, https://www.reddit.com/r/GrapheneOS/comments/1wjk0lb/, https://www.reddit.com/r/pwnhub/comments/1wdmab4/]
---

Checked 2026-11-07 (Europe/Belgrade). Third use case in [[where-does-ai-reverse-engineering-cost-money-reddit]]. Quotes are copied from [[reddit-listener-ai-re-money-2026-11-07]].

A1 is verified. The app developer (self-stated) caches a premium flag locally forever after one server call. A4 is verified. The app owner since about 2017 (self-stated) saw a clone on Google Play about four days after an update. The quote does not mention AI. A5, on that same thread, is verified and does: days without AI, hours with AI, and an exact clone that changes the app id. F1 is verified and asks whether shielding still holds on the next release. F2 is verified, score 2 in the browser check. The stated role is someone who runs red-teaming for payments clients. The quote gives ten minutes, and it names Frida. This file does not link to Frida or to a method. F4 is the same person calling client-side controls a speed bump. F4 was not in the browser extract and stays needs-check. F8 is verified: a Belgium resident and Itsme user (self-stated) locked out of a bank and the government ID app because the phone was treated as rooted.

| ID | Link | Date | Username | Role (stated) | Verbatim quote | Quote status |
| --- | --- | --- | --- | --- | --- | --- |
| A1 | https://www.reddit.com/r/androiddev/comments/1szvr54/ | 2026-04-30 | BagEnvironmental1348 | app developer (self) | "In the current codebase its just a premiumFeatures boolean that calls the google server once and caches the result locally forever. This means creating a hacked version is fairly easy for a relatively experienced developer." | verified-in-thread |
| A4 | https://www.reddit.com/r/androiddev/comments/1r0hiuh/ | 2026-02-10 | discoverfor | app owner since ~2017 (self) | "On February 3 (only ~4 days later), another app appeared on Google Play that exact same to be of mine." | verified-in-thread |
| A5 | https://www.reddit.com/r/androiddev/comments/1r0hiuh/ | 2026-02-10 | alifesoftware | not found | "Without AI: can be done in days. With AI: Matter of hours. If it's an exact clone, the only thing that needs to change is app ID, and even changing all the package names isn't too hard." | verified-in-thread (browser 2026-11-07) |
| F1 | https://www.reddit.com/r/AskNetsec/comments/1ue7334/ | 2026-06-24 | Ok_Extent1078 | not found | "the harder question seems to be whether those protections actually hold up when someone tries to bypass them. … I'm especially curious about how people validate this across releases, since a protection can be present in one build and weakened or misconfigured in the next." | verified-in-thread |
| F2 | https://www.reddit.com/r/AskNetsec/comments/1ue7334/ | 2026-06-25 (comment) | whatwilly0ubuild | runs red-teaming "for clients in payments" (self) | "Present and effective are completely different properties, and a build can ship every control you listed and still fall in ten minutes to someone with Frida." | verified-in-thread (browser 2026-11-07) |
| F4 | https://www.reddit.com/r/AskNetsec/comments/1ue7334/ | 2026-06-25 (comment) | whatwilly0ubuild | payments red-teamer | "all of this is client side, which makes it a speed bump and not a wall. … if you're leaning on RASP alone you're betting your damn ledger on code the attacker controls." | mirror-verbatim, needs-check |
| F8 | https://www.reddit.com/r/GrapheneOS/comments/1wjk0lb/ | ~2026-09-17 | not found (OP) | resident; Itsme user (self) | "In the last weeks I have been locked out of, first, my investment bank, and as of today, Itsme(government app for login in/proving ID)... It does not work with GrapheneOS anymore, as it is 'rooted' (yes it's bullshit)" | verified-in-thread |
| F11 | https://www.reddit.com/r/pwnhub/comments/1wdmab4/ | 2026-09-11 | _cybersecurity_ | not found (news repost of Group-IB research) | "The malware clones the victim's banking app into this new profile, allowing operators to conduct fraudulent transactions away from standard security monitoring." | snippet-verbatim, needs thread check |

F11 still needs a thread check. It is a news repost of Group-IB research, and the quote has no dollar figure. The campaign estimate already filed from the Group-IB page is [[gigabud-cloned-banking-app-observations]]. Indonesian victim posts that do not say how the accounts were drained are in [[reddit-sweep-2-talk-is-densest-in-china-belgium-brazil-and-indonesia]].

Why it matters: a banking or freemium app loses money on the day the on-device check fails, not in a launch month. The verified rows are a four-day clone, an hour-scale claim, a ten-minute claim from a payments red-teamer, and a lockout of legitimate users. The ten-minute sentence is one person's report.

Source: [[reddit-listener-ai-re-money-2026-11-07]].
