---
type: note
title: "Euro 7 makes car makers protect engine and motor control software against tampering: new types from 29 Nov 2026, all new cars from 29 Nov 2027, trucks and buses from 2028-2029"
tags: [regulation, security, market]
date: 2026-11-07
by: tea+claude
confidence: high
sources: [vehicle-anti-tampering-law-2026-11-07, https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=OJ:L_202401257]
---

Regulation (EU) 2024/1257 (Euro 7) defines tampering to include changing "any software or other
logical control elements" of the engine, electric motor, pollution controls, battery and odometer
(Article 3(45)). Article 4(7) obliges manufacturers to design vehicles to minimise vulnerabilities that
enable tampering, and names engine control units and electric motor control units.

Dates (Article 21): new car and van types 29 November 2026, all new cars and vans 29 November 2027;
new truck and bus types 29 May 2028, all new trucks, buses and heavy trailers 29 May 2029.

What the law does **not** say: it does not name obfuscation. The Commission's CLOVE study lists
encrypted software, tamper-resistant hardware and tamper flags as example ECU measures, and maps the
threat to UN R155 mitigation M7, "protect system data/code" (secondary source, not read in full).
So the honest pitch is: the law creates a duty and a deadline; we are one layer and, more
importantly, measurable evidence that the layer works.

Why it matters to us: it is a "why now" with a legal date, in exactly the code we protect (C firmware
in control units). It also makes behaviour preservation valuable: after Dieselgate, emission code
whose behaviour changes is the problem itself, so a proof that protection changes nothing is a
selling point. That second point is our inference, not a regulator requirement.

Checked 2026-11-07 on EUR-Lex.
