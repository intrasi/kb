---
type: source
title: "DJI DroneID aftermath: press release, DJI statements, AeroScope discontinuation (web excerpts, 2022-2023)"
tags: [security, regulation]
date: 2026-11-08
by: tea+claude
url: https://news.rub.de/english/press-releases/2023-03-02-it-security-security-vulnerabilities-detected-drones-made-dji
---

Summaries collected 2026-11-08 through web search and fetch. Paraphrased, not verbatim; quotes are short.
The Verge could not be fetched directly; its claims come via the outlets that cite it.

## Ruhr University Bochum press release, 2 March 2023 (updated 3 March 2023)
https://news.rub.de/english/press-releases/2023-03-02-it-security-security-vulnerabilities-detected-drones-made-dji
- Team from RUB and CISPA led by Nico Schiller and Thorsten Holz; presented at NDSS, San Diego, 27 Feb-3 Mar 2023.
- Tested DJI Mini 2, Mavic Air 2, Mavic 2; Mavic 3 later used to reproduce results.
- 16 vulnerabilities; four serious ones in Mini 2, Mavic Air 2 and Mavic 3.
- Attackers could gain extended rights, change log data or the serial number, override no-fly blocks over
  airports and prisons, and crash drones mid-air (remotely in special scenarios).
- Fuzzing on the live system because the full firmware was not available.
- Original text said DJI "has taken steps towards fixing them"; the 3 March update says DJI has fixed them.
- Schiller: the data "is not encrypted, and that practically anyone can read the location".

## DroneXL, 9 March 2023: DJI responds
https://dronexl.co/2023/03/09/dji-concerns-drone-pilots-locations-public/
- DJI replied in a short tweet noting media concerns about locating operators, thanking the researchers,
  and saying the vulnerabilities were swiftly fixed before the paper was published.
- Brendan Schulman (former DJI VP policy) noted FAA Remote ID will broadcast pilot location for all
  consumer drones in about six months.
- WIRED (Andy Greenberg, 2 March 2023, wired.com/story/dji-droneid-operator-location-hacker-tool) had
  reported DJI had not yet responded.

## The Verge / DroneXL / sUAS News, April-May 2022: DJI admits AeroScope signals are not encrypted
https://dronexl.co/2022/05/09/dji-aeroscope/ ,
https://www.suasnews.com/2022/04/dji-confirms-they-are-not-encrypting-data-being-transmitted-from-their-aircraft/ ,
https://www.theverge.com/2022/4/28/23046916/dji-aeroscope-signals-not-encrypted-drone-tracking
- DJI spokesperson Adam Lisberg had said DroneID/AeroScope signals were encrypted.
- Kevin Finisterre showed on 31 March 2022, with an Ettus SDR, that DroneID data could be intercepted.
- On 28 April 2022 DJI admitted to The Verge the signals are not encrypted; Lisberg said R&D colleagues had
  given him wrong information.

## AeroScope discontinued, March 2023
https://dronedj.com/2023/03/05/dji-halts-production-of-its-aeroscope-drone-detection-product/ ,
https://dronelife.com/2023/03/06/as-remote-id-approaches-dji-discontinues-aeroscope/
- DJI stopped producing and selling AeroScope in early March 2023 without a formal announcement (pop-up on
  product page). Portable version stopped August 2022.
- Schulman's likely reasons: US agencies attacking DJI while it supported a US-security feature, and FAA
  Remote ID making it redundant.
- Remote ID mandatory: EU 1 Jan 2024; US compliance date 16 Sep 2023, enforcement from 16 Mar 2024.

## Related later work
- "Behind The Wings: The Case of Reverse Engineering and Drone Hijacking in DJI Enhanced Wi-Fi Protocol",
  arXiv 2309.05913 (2023). Not read yet.
