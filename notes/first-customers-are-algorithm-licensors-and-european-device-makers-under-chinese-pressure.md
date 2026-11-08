---
type: note
title: "Our first customers are algorithm licensors that ship binaries (Bosch Sensortec, Dirac, Elliptic Labs) and European device makers under Chinese pressure (Husqvarna, hearing-aid makers), with Orqa as the warm local intro"
tags: [customer, market, pitch]
date: 2026-11-08
by: tea+claude
confidence: low
sources: [first-customers-web-excerpts-2026-11-08, 0003-use-case-device-makers-against-competitor-reverse-engineering, napkin-math-120k-a-year-per-product-line-is-under-five-percent-of-value-at-risk]
superseded_by: [[target-audience-is-consumer-electronics-makers-like-philips]]
---

Customer map for [[0003-use-case-device-makers-against-competitor-reverse-engineering]]. Facts about the
companies are sourced and checked 2026-11-08. **That any of them wants or would pay for our product is
a hypothesis: nobody has been interviewed yet.** Confidence stays low until the first conversations.

## In one paragraph

Sell first to companies whose **product is the algorithm and who already ship it as a binary into
someone else's device**: they feel the risk most directly and already think in "per model" licences.
Second, European device makers whose shipped algorithm is the main thing that separates them from
fast Chinese challengers. Use a Croatian hardware company as the first warm pilot, because a
reference customer matters more than the logo size. Samsung-scale makers stay the vision slide.

## Who counts as a customer (all four must hold)

1. A named algorithm runs **on the device** (not in the cloud), so a competitor can buy the device and read it.
2. The algorithm is a reason people buy the product, and it took years to build.
3. A cheaper competitor exists that would gain from it (often Chinese, often months behind).
4. The company ships many release builds a year and has a product-security or firmware lead who owns the problem
   ([[re-devices-ship-many-release-builds-for-years-after-launch]]).

## Segment 1: algorithm licensors (best fit, talk to first)

Their whole business is an algorithm handed to other companies as a compiled library. If it is
reconstructed, the licence fee disappears. They already ship precompiled blobs, so protection fits
their release flow, and their pricing is already per device model, like ours.

| Company | What ships | Why they fit | Tier |
| --- | --- | --- | --- |
| **Bosch Sensortec** (DE) | BSEC sensor-fusion library, licensed as "pre-compiled binary blobs" | Already guards the algorithm with binary-only delivery and a licence; we add the next layer | Algorithm supplier, $200k |
| **Dirac Research** (SE) | Room correction licensed into AV receivers, cars, phones (McIntosh, Emotiva, Denon, Marantz in 2026) | The licence cost is built into every unit; a cloned Dirac kills that line | Algorithm supplier |
| **Elliptic Labs** (NO, listed) | Software-only proximity sensor in ~1B phones; "guaranteed minimum license fee per model" | Same per-model logic as our pricing; customers are Chinese phone makers (vivo, Transsion, HONOR) | Algorithm supplier |

Candidates to check next, same shape: Ceva (sensor fusion, audio), Dolby and Xperi/DTS (audio),
Sensory and other on-device voice libraries.

## Segment 2: European device makers under Chinese pressure

| Company | Algorithm at stake | Pressure | Note |
| --- | --- | --- | --- |
| **Husqvarna Group** (SE) robotic mowers | Navigation, boundary-free positioning, AI vision | Segway Navimow, Mammotion, Ecovacs, eufy "winning online"; Mammotion in 700+ Walmart stores | Big company; aim at the Automower product line, not group IT |
| **Hearing-aid makers**: Sonova (CH), Demant (DK), WS Audiology (DK/SG), GN (DK) | Noise reduction, speech separation, the new DNN platforms launched Aug 2026 | Five companies hold ~90% of sales; Chinese makers (NewSound, Vivtone, Austar) are cheap and growing | Highest R&D-per-algorithm we found; regulated (medical), so slow sales |
| **Dyson** (UK/SG) | Motor and heat control, hair-dryer and vacuum algorithms | Key patents invalidated in China after Dreame and Laifen challenges ([[re-no-public-case-of-clones-copying-algorithms-from-shipped-consumer-devices]]) | Best pitch story; hardest door |

Weak fit, do not lead with: **Neural DSP** and other guitar modellers. Budget rivals use the free
open-source Neural Amp Modeler and copy the *sound* by capturing it, not the firmware. Protecting code
does not stop that.

## Segment 3: warm local pilots (Croatia)

| Company | Why | Caution |
| --- | --- | --- |
| **Orqa** (Osijek) | FPV drones, sells "non-Chinese, NDAA-compliant"; €12.7M Series A (Mar 2026), US Army selection and a $38M Pentagon contract in 2026; 175 people | Defence buyers ask for anti-tamper, which may be a different spec from ours (unverified). Orqa bricked goggles over firmware licences in 2023, so it already cares about controlling its firmware |
| **DOK-ING** (Zagreb) | Demining and military robots; Rheinmetall bought 51% in 2026 | Decisions may now go through Rheinmetall |
| **Gideon** (Zagreb) | Autonomous industrial vehicles, product Trey, US and Canada markets | Autonomy stack may run on PCs, not firmware: check |

A pilot here is reachable through Garaža and its mentors ([[garaza-mentors-closest-to-code-verification]]).
Its value is a named reference and a real firmware target for Luka's demo, not revenue.

## Not first

- **Samsung, Apple, Xiaomi-scale**: the vision slide. Long cycles, in-house security teams.
- **Chinese makers**: they are both target and copier; sales and legal risk too high for now.
- **Mobile apps and games**: crowded, cheap and free tools exist
  ([[re-free-open-source-ai-hardening-exists-for-app-formats-but-skips-firmware]]).

## Who inside the company buys

| Role | What they care about | Our opening |
| --- | --- | --- |
| Head of product security / PSIRT | CRA duties, firmware attacks | "Measure how fast an AI agent reads your firmware" |
| VP firmware / embedded engineering | Release speed, flash size, no broken builds | "The proof shows outputs stay identical" |
| CTO or algorithm team lead | Years of R&D in one function | "Time bought" chart on their own binary |
| Licensing / legal (licensors) | Licence revenue, patents that fail | "Patents keep failing; protect the know-how itself" |

Champion is usually the security lead; the budget holder is the CTO (makers) or head of licensing (licensors).

## Why now (conversation openers, not mandates)

- **EU Cyber Resilience Act**: reporting duties since 11 Sep 2026; security by design and CE marking from
  11 Dec 2027. Every device maker selling in the EU is buying security work now. The CRA does **not**
  require obfuscation; it opens the budget conversation.
- AI agents make firmware reading cheap ([[re-agents-route-around-obfuscation]]).
- Patent invalidations against Dyson, iRobot and DJI ([[0003-use-case-device-makers-against-competitor-reverse-engineering]]).

## Where to meet them

- **embedded world, Nuremberg, 16-18 March 2027** (1,242 exhibitors in 2026). Emproof, our closest
  competitor, exhibited there in 2026 on IP theft ([[re-emproof-already-claims-proof-backed-firmware-obfuscation]]).
- CES (January) and IFA Berlin (September) for consumer makers; AES for audio licensors.
- Garaža mentors and investors for Croatian intros.

## First ten conversations (drafts by agents, sent by humans)

1. Orqa, 2. Gideon, 3. DOK-ING (via Garaža network); 4. Elliptic Labs, 5. Dirac, 6. Bosch Sensortec
(licensors); 7. Husqvarna Automower, 8. one hearing-aid maker (Demant or WS Audiology), 9. one robot
vacuum or mower challenger outside China, 10. Dyson (pitch story test).

Ask each the same five questions so answers compare:
1. Which algorithm in your device would hurt most if a competitor had it?
2. Has a competitor ever matched one suspiciously fast? How do you think they did it?
3. What do you do today to protect firmware (encryption, secure boot, obfuscation, nothing)?
4. Who would own a tool like this, and from which budget?
5. Would a pilot on one model, with a break-test report, be worth €25k to you?

## What would change this map

- Licensors say binary-only delivery plus contracts is enough: drop segment 1 to second place.
- Makers say competitors copy through people or patents, not devices (the revisit trigger in decision 0003).
- Defence buyers (Orqa, DOK-ING) need certified anti-tamper we cannot offer: keep them as demo partners only.
