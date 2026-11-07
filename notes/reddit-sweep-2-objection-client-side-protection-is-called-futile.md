---
type: note
title: Verified comments call client-side protection futile, an obstacle, or a poor use of time on simple apps
tags: [market, customer, security]
date: 2026-11-07
by: karla+cursor
confidence: moderate
sources: [reddit-listener-ai-re-money-2026-11-07, https://www.reddit.com/r/gamedev/comments/1rn6t3t/, https://www.reddit.com/r/Unity3D/comments/1vucg8e/, https://www.reddit.com/r/webdev/comments/1rg2whd/, https://www.reddit.com/r/brdev/comments/1utun12/, https://www.reddit.com/r/androiddev/comments/1szvr54/, https://www.reddit.com/r/AskNetsec/comments/1ue7334/, https://www.reddit.com/r/AskNetsec/comments/1vksrwn/]
---

Checked 2026-11-07 (Europe/Belgrade). Quotes are copied from [[reddit-listener-ai-re-money-2026-11-07]]. This is the cluster of "it is not worth doing" objections. Rows that still need a check are labeled in the table and are not treated as verified.

G21 is verified. A free visual-novel developer who has run a tech business since 2011 (self-stated) calls the fight against piracy futile and says studios have spent millions. "Millions" is not itemised. G30 is verified. A Unity indie developer (self-stated) calls obfuscation an obstacle, not a defence. W2 is a verified link-post summary, not a commenter's sentence. BR3, BR4, and BR5 are verified replies on the Brazilian thread. BR4 says a simple app is not worth the effort and that offline games, or apps whose business rules stay on the device, are the case where obfuscation is worth it. A2, A3, and F4 still need a check. F7 is verified and asks what risk preventing reverse engineering is supposed to mitigate.

| ID | Link | Date | Username | Role (stated) | Verbatim quote | Quote status |
| --- | --- | --- | --- | --- | --- | --- |
| G21 | https://www.reddit.com/r/gamedev/comments/1rn6t3t/ | ~2026-03-06 | not found (OP) | free visual-novel dev; tech business since 2011 (self) | "You can't fight against piracy. Other creators and studios have spent millions trying to prevent it, but as you probably know, it's futile." | verified-in-thread |
| G30 | https://www.reddit.com/r/Unity3D/comments/1vucg8e/ | ~2026-08-20 | not found (OP) | Unity indie developer | "Obfuscation is an obstacle, not a defense. Anyone determined to figure it out will still achieve their goal using a debugger" | verified-in-thread |
| W2 | https://www.reddit.com/r/webdev/comments/1rg2whd/ | ~2026-02-27 | not found (OP, link post) | not found | "a masterclass in why client-side JavaScript protections are a complete waste of everyone's time" | verified-in-thread (link-post summary) |
| BR3 | https://www.reddit.com/r/brdev/comments/1utun12/ | not found (reply; thread ~2026-07-11) | wackygoose | not found | "Meu código já é ofuscado o suficiente" | verified-in-thread (browser 2026-11-07) |
| BR4 | https://www.reddit.com/r/brdev/comments/1utun12/ | not found (reply; thread ~2026-07-11) | psychonaut_eyes | not found | "Acho que não vale o esforço se for um app "simples" (ex app de academia, pomodoro, etc). são coisas que são facilmente copiáveis, ai é só tentar deixar a logica importante no backend. Agora jogos ou apps que tenham toda a regra de negocio offline acho valido ofuscar sim," | verified-in-thread (browser 2026-11-07) |
| BR5 | https://www.reddit.com/r/brdev/comments/1utun12/ | not found (reply; thread ~2026-07-11) | Blooodless | not found | "Sim, mas pra projeto pessoal, é a última coisa que eu ligo" | verified-in-thread (browser 2026-11-07) |
| A2 | https://www.reddit.com/r/androiddev/comments/1szvr54/ | 2026-04-30 | PsychologicalFudge52 | not found | "Realistically speaking its not worth the hassle. Unless premium features require server side stuff, you will never out muscle someone who is motivated." | mirror-verbatim, needs-check |
| A3 | https://www.reddit.com/r/androiddev/comments/1szvr54/ | 2026-04-30 | prom85 | not found | "thinking and implementing stuff against hackers costs more time and effort than it does help as the effort to protect your aop is high and still hackers can mostly easily crack an app with relative little effort" | mirror-verbatim, needs-check |
| F4 | https://www.reddit.com/r/AskNetsec/comments/1ue7334/ | 2026-06-25 (comment) | whatwilly0ubuild | payments red-teamer | "all of this is client side, which makes it a speed bump and not a wall. … if you're leaning on RASP alone you're betting your damn ledger on code the attacker controls." | mirror-verbatim, needs-check |
| F7 | https://www.reddit.com/r/AskNetsec/comments/1vksrwn/ | ~2026-08-11 (comment) | dmaul | not found | "What risk is being mitigated by trying to prevent reverse engineering?" | verified-in-thread (browser 2026-11-07) |

Why it matters: these are the sentences a pitch has to answer before it offers protection. BR4 is the one that draws a line: simple apps no, offline rules yes. The time-bought side of that argument is [[reddit-sweep-2-controversy-obscurity-or-time-bought]].

Source: [[reddit-listener-ai-re-money-2026-11-07]].
