---
type: note
title: Open-sourcing the client did not survive as a readable thread, and moving the check to the server did
tags: [market, customer, security]
date: 2026-11-07
by: karla+cursor
confidence: moderate
sources: [reddit-listener-ai-re-money-2026-11-07, https://www.reddit.com/r/macapps/comments/1ryvdei/, https://www.reddit.com/r/gamedev/comments/1v3g9g1/, https://www.reddit.com/r/brdev/comments/1utun12/, https://www.reddit.com/r/AskNetsec/comments/1ue7334/]
---

Checked 2026-11-07 (Europe/Belgrade). Quotes are copied from [[reddit-listener-ai-re-money-2026-11-07]].

The listener recorded two relevant posts as deleted: r/softwareengineer 1vvqixb ("Isn't opensource ironically less secure?") and r/LocalLLaMA 1v068fa. This filing did not re-fetch them. They are not quoted.

What is on the page instead is "move the decision to the server". M3 is verified. The stated role is the same security research engineer as M1. G19 still needs a check. The person says "From developer to developer". BR4 is verified and tells simple-app authors to keep important logic on the backend. F4 still needs a check; it is the payments red-teamer on client-side controls.

| ID | Link | Date | Username | Role (stated) | Verbatim quote | Quote status |
| --- | --- | --- | --- | --- | --- | --- |
| M3 | https://www.reddit.com/r/macapps/comments/1ryvdei/ | ~2026-03-19 | SenpaiHunters | security research engineer | "Keep real license decisions on the server where possible; treat local data as a cache." | verified-in-thread |
| G19 | https://www.reddit.com/r/gamedev/comments/1v3g9g1/ | 2026-07-22 | Almamu | developer (self: "From developer to developer") | "From developer to developer, your issue here is not piracy, but security. You need to take security seriously so only legitimate request reach your servers." | mirror-verbatim, needs-check |
| BR4 | https://www.reddit.com/r/brdev/comments/1utun12/ | not found (reply; thread ~2026-07-11) | psychonaut_eyes | not found | "Acho que não vale o esforço se for um app "simples" (ex app de academia, pomodoro, etc). são coisas que são facilmente copiáveis, ai é só tentar deixar a logica importante no backend. Agora jogos ou apps que tenham toda a regra de negocio offline acho valido ofuscar sim," | verified-in-thread (browser 2026-11-07) |
| F4 | https://www.reddit.com/r/AskNetsec/comments/1ue7334/ | 2026-06-25 (comment) | whatwilly0ubuild | payments red-teamer | "all of this is client side, which makes it a speed bump and not a wall. … if you're leaning on RASP alone you're betting your damn ledger on code the attacker controls." | mirror-verbatim, needs-check |

Why it matters: the alternative buyers already say out loud is a server-side check, not a proof about the client. That is the competitor named in [[do-people-need-ai-resistant-code-protection]].

Source: [[reddit-listener-ai-re-money-2026-11-07]].
