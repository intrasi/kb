---
type: note
title: Reddit argues both that obfuscation buys time and that it is pointless
tags: [market, customer, security]
date: 2026-11-07
by: karla+cursor
confidence: moderate
sources: [reddit-listener-ai-re-money-2026-11-07, https://www.reddit.com/r/AskNetsec/comments/1vksrwn/, https://www.reddit.com/r/gamedev/comments/1v3g9g1/, https://www.reddit.com/r/androiddev/comments/1r0hiuh/, https://www.reddit.com/r/brdev/comments/1utun12/, https://www.reddit.com/r/Unity3D/comments/1vucg8e/, https://www.reddit.com/r/gamedev/comments/1rn6t3t/]
---

Checked 2026-11-07 (Europe/Belgrade). Both sides, copied from [[reddit-listener-ai-re-money-2026-11-07]]. Needs-check rows are not upgraded.

The verified "buys some time" sentence is F6: weak obfuscation against a motivated attacker is hours to days. F6b, the sentences about years and about weeks to months, is still the mirror text. G17, still needs-check, says a couple of extra days at launch can matter for AAA sales and matters less for indies. A6, still needs-check, says that if the attacker gains plenty, assume the attack is easy, then obfuscate anyway. BR4, verified, says obfuscation is worth it when the business rules stay offline.

The verified "pointless" side is G30 and G21, with the rest of that cluster in [[reddit-sweep-2-objection-client-side-protection-is-called-futile]].

| ID | Link | Date | Username | Role (stated) | Verbatim quote | Quote status |
| --- | --- | --- | --- | --- | --- | --- |
| F6 | https://www.reddit.com/r/AskNetsec/comments/1vksrwn/ | ~2026-08-11 (comment) | maxinator80 | not found | "Weak obfuscation and highly motivated/skilled attacker => hours to days." | verified-in-thread (browser 2026-11-07) |
| F6b | https://www.reddit.com/r/AskNetsec/comments/1vksrwn/ | ~2026-08-11 (comment) | maxinator80 | not found | "Strong obfuscation and lowly motivated attacker => years. Strong obfuscation and highly motivated attacker => weeks to months." | mirror-verbatim, needs-check |
| G17 | https://www.reddit.com/r/gamedev/comments/1v3g9g1/ | 2026-07-22 | not found (mirror omits name) | not found | "Piracy is an arms race and while keeping a game protected for a couple extra days at launch can make a big impact in AAA sales, it's not really as relevant in more indie spaces." | mirror-verbatim, needs-check |
| A6 | https://www.reddit.com/r/androiddev/comments/1r0hiuh/ | 2026-02-10 | blindada | not found | "The question is "how much can an attacker gain by doing this?" If the answer is "Plenty", then assume it's easy (if you aren't obfuscating your app then it is), request takedowns, and start refactoring and obfuscating the app" | mirror-verbatim, needs-check |
| BR4 | https://www.reddit.com/r/brdev/comments/1utun12/ | not found (reply; thread ~2026-07-11) | psychonaut_eyes | not found | "Acho que não vale o esforço se for um app "simples" (ex app de academia, pomodoro, etc). são coisas que são facilmente copiáveis, ai é só tentar deixar a logica importante no backend. Agora jogos ou apps que tenham toda a regra de negocio offline acho valido ofuscar sim," | verified-in-thread (browser 2026-11-07) |
| G30 | https://www.reddit.com/r/Unity3D/comments/1vucg8e/ | ~2026-08-20 | not found (OP) | Unity indie developer | "Obfuscation is an obstacle, not a defense. Anyone determined to figure it out will still achieve their goal using a debugger" | verified-in-thread |
| G21 | https://www.reddit.com/r/gamedev/comments/1rn6t3t/ | ~2026-03-06 | not found (OP) | free visual-novel dev; tech business since 2011 (self) | "You can't fight against piracy. Other creators and studios have spent millions trying to prevent it, but as you probably know, it's futile." | verified-in-thread |

Why it matters: the product idea sells time, not secrecy for its own sake. The only verified duration on the "buys time" side of this controversy is hours to days for weak obfuscation. The longer ranges are not verified.

Source: [[reddit-listener-ai-re-money-2026-11-07]].
