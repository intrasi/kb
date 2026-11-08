---
type: note
title: "NSO admitted decompiling the shipped WhatsApp client and building its own modified client; a US court enjoined the reverse engineering itself but cut punitive damages 97%"
tags: [security, market, pitch, regulation]
date: 2026-11-08
by: tea+claude
confidence: high
sources: [re-incident-records, https://therecord.media/pegasus-spyware-infections-detailed-whatsapp-lawsuit, https://cyberscoop.com/whatsapp-wins-injunction-against-nso-group-spyware-damages-reduced/, https://globalfreedomofexpression.columbia.edu/cases/whatsapp-inc-v-nso-group-technologies-limited-2024/, https://www.securityweek.com/nso-ordered-to-stop-hacking-whatsapp-but-damages-cut-to-4-million/]
---

Supersedes nothing; it expands `RE-INC-038` in [[re-incident-records]] with the facts that matter to our
pitch. Business and legal level only, by project rule: no vector or exploit detail here.

## What happened

WhatsApp (Meta) sued NSO Group on **29 October 2019** in the Northern District of California over a
campaign run **April–May 2019** against about **1,400 devices**, among them journalists, lawyers, human
rights defenders and diplomats. Pegasus required no action from the target.

The reverse engineering is not alleged, it is **admitted**. Per the court record, NSO developed its
capability by *extracting and decompiling WhatsApp's code, reverse-engineering WhatsApp, and designing
and using their own "WhatsApp Installation Server" (WIS)*. The WIS was NSO's **own modified build of the
WhatsApp client**, used so its traffic would look like ordinary WhatsApp traffic to WhatsApp's servers.

## How it ended

| Step | Date | Outcome |
| --- | --- | --- |
| Sovereign immunity rejected | 2023–2024 | NSO could not hide behind its government customers; the Supreme Court declined review in Jan 2023 |
| Liability | Dec 2024 | Court found for WhatsApp on liability before any damages trial |
| Jury | May 2025 | $444,719 compensatory **plus $167.3M punitive** |
| Final judgment | 17–18 Oct 2025 | Judge Phyllis Hamilton granted a **permanent injunction** and cut punitive damages to about **$4M**, applying a 9:1 ratio to the compensatory award |
| Contempt motion | Oct 2026 | WhatsApp's civil contempt motion denied as too vague; the court made no finding that NSO complied, and the injunction stands |

The injunction bars NSO from **reverse engineering WhatsApp** and from creating new accounts on it. NSO
publicly welcomed the roughly 97% cut and noted the injunction does not bind its customers. Twelve civil
society groups filed amicus briefs in May 2026 opposing NSO's appeal of the injunction.

## Why it matters to us

1. **It is the clearest admitted case of reverse engineering a shipped consumer app at commercial scale.**
   No leak, no insider: they bought the product, took it apart, and rebuilt a client from what they learned.
2. **A court was willing to enjoin reverse engineering as such.** That is a legal remedy our customers can
   reach for, and it strengthens the argument that reading a shipped artifact is a recognised commercial
   harm, not just a research activity.
3. **The money collapsed.** $167.3M became about $4M because punitive damages are tied to proven
   compensatory loss, and the proven loss was $444,719. Compare the insider cases, where avoided R&D and
   lost head start were provable and the awards survived
   ([[motorola-v-hytera-money-awarded-versus-collected]]). **Litigation is a weak remedy for this; that is
   the gap protection sells into.**
4. **The motive was intrusion, not imitation.** NSO wanted a way in, not WhatsApp's algorithms. Say this
   before a judge does: all our shipped-artifact evidence is about breaking in, while our use case is
   copying know-how, for which there is no public case
   ([[re-no-public-case-of-clones-copying-algorithms-from-shipped-consumer-devices]]). The honest bridge is
   that the *work* is the same — decompile, understand, rebuild — and only the goal differs, so when AI
   cuts the cost of that work it cuts it for both goals ([[re-agents-route-around-obfuscation]]).

## Do not say

- "NSO stole WhatsApp's algorithm." They did not; they built an entry path.
- "$167M for reverse engineering." The judgment is about $4M. Quote both numbers or neither.
- Anything about how the delivery worked. Keep it at this level.

Checked 2026-11-08 against the sources listed above.
