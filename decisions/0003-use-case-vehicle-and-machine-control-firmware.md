---
type: decision
title: "Start with vehicle and machine control firmware: protect speed, power and emission limits in controller code against AI-assisted tampering, prove the controller behaves identically, and report the time bought as anti-tampering evidence"
tags: [idea, pitch, security, regulation, demo]
date: 2026-11-07
by: tea+claude
status: active
---

Proposed by Tea, who owns the use case; Luka builds the tech. Needs Karla's and Luka's agreement.
Full analysis: [[re-vehicle-firmware-anti-tampering-report-2026-11-07]].
Replaces [[0002-use-case-paid-professional-software]]: Tea wants a device use case, since machines,
cars and appliances will outlast today's apps, and the evidence below supports one.

## Context

Earlier device options failed on three objections ([[0002-use-case-paid-professional-software]]):
reverse engineering of devices is mostly defenders finding bugs, owners have right-to-repair, and
there was no measured harm. One device problem survives all three:

- **Measured harm.** EPA: emission controls removed on over 500,000 US diesel pickups, excess NOx
  equal to 9 million extra trucks; tuning software that rewrites engine calibrations is a main tool
  ([[re-epa-500k-diesel-pickups-tampered-largely-by-ecu-tuning]]).
- **Law with a deadline.** Euro 7 obliges car makers to minimise tampering vulnerabilities in engine
  and motor control units: all new cars from 29 Nov 2027, trucks and buses from 2029
  ([[re-euro-7-makes-ecu-software-anti-tampering-law-from-2027]]). Two-wheeler makers have had this
  duty since 2013 ([[re-eu-two-wheeler-makers-must-prevent-powertrain-tampering-since-2013]]).
- **Not a right-to-repair fight.** Tampering with emissions or speed limits is illegal; repair access
  is a separate right ([[re-incident-records]] `RE-INC-013`).
- **AI lowers the cost** of reading firmware ([[re-incident-records]] `RE-INC-026`,
  [[re-agents-route-around-obfuscation]]).

## The choice

**Asset:** the limit and calibration logic inside controller firmware (C): speed and power limits,
emission-control modes, the checks around them.

**Attacker:** a tuner, now with an AI agent, who reads the firmware to find where the limit lives and
changes it.

**First customer:** second-tier e-bike drive-unit and controller suppliers and small moped, motorcycle and
speed-pedelec makers: legal or standard duty already in force, smaller firms, faster pilots than car makers.
Bosch (about half of European e-bike drives) likely builds its own protection.
**Expansion:** cars and vans (Euro 7, 2027) → trucks and buses (2029) → off-road machines → connected
appliances under the Cyber Resilience Act (Dec 2027).
**Vision, not lead:** stopping competitors from porting a maker's know-how to other machines. Real losses
exist (Sinovel, Hytera) but started with insiders, and no Deere-style case was found
([[re-big-machine-software-theft-cases-started-with-insiders]]). Never protect against owners and
repairers ([[re-eu-law-lets-owners-study-and-decompile-software-for-interoperability]],
[[re-newag-train-locks-show-the-backlash-risk-for-protection-vendors]]).

**Promise:**
1. Protect: obfuscate the selected limit and calibration functions.
2. Prove: the protected controller computes exactly the same outputs (Z3, integer and fixed-point code).
3. Measure: AI agents try to find and raise the limit; report the time and cost bought, as evidence for
   the anti-tampering description the maker gives the approval authority.

**Honest limits, say them before judges do:**
- Signed firmware and secure boot are the first line; we are the layer for when they are bypassed, and
  the measurement. The law does not name obfuscation.
- Protect only selected functions; hot real-time control loops cannot absorb the overhead
  ([[re-tigress-virtualization-costs-42-to-247x-runtime]]).
- Obfuscation slows finding the limit, not patching once found.
- Automotive buyers are slow; the hackathon claim is the method, not signed contracts.
- The cycling industry calls "reliance on obscurity alone" not state of the art; pitch a layer on top of
  cryptography plus evidence ([[re-cycling-industry-says-obscurity-alone-is-not-state-of-the-art]]).
- US enforcement weakened in 2026; the buying reason is the EU ([[re-us-tampering-enforcement-weakened-in-2026]]).
- Protection must not block authenticated repair and reprogramming access (EU 2018/858, FTC v. Deere).

## Demo brief for Luka

A small self-written motor-controller in C: a speed limiter at 25 km/h and one fixed-point power or
emission calculation. Silent, 60 seconds:

1. An AI agent finds the limiter in the plain binary and raises it: minutes, cents.
2. Protect both functions; Z3 shows the protected functions give identical outputs.
3. The same agent on the protected binary: fails, or needs many times the time and tokens.
4. A "time bought" chart per function.

Grade by running the patched controller: does the speed exceed 25? Grade the calculation by
differential testing on thousands of inputs ([[re-shipped-tests-miss-decompiler-divergence]]).

## Pitch order

1. Hook: 500,000 trucks tuned in the US, the NOx of 9 million more; now AI reads firmware for anyone.
2. Law: from November 2027 every new car in the EU must resist this.
3. Solution and demo.
4. Why us: we run the authority's attack test before the authority does, with AI agents, and hand over
   a rerunnable time-to-break number for the threat analysis
   ([[re-euro-7-authorities-attack-sold-cars-with-market-tuning-products]]). The proof that protection
   changes nothing is table stakes, not unique: Emproof already claims it
   ([[re-emproof-already-claims-proof-backed-firmware-obfuscation]]).
5. Market: "if we prove one controller, every machine with a chip": cars, trucks, excavators, appliances.

## Revisit when

- Interviews with two-wheeler or controller makers say signed firmware already solves tampering for them.
- Approval authorities reject obfuscation as an anti-tampering measure.
- Luka's spike shows no measurable gap between plain and protected controllers.
- A competitor (Emproof, Irdeto or others) already publishes an AI time-to-break score.
- A type-approval technical service says time-to-break evidence would not count in a TARA.
