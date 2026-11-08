---
type: question
title: What did the NDSS 2023 DJI DroneID paper find, how did the researchers get past DJI's firmware protection, and what does it teach a code-protection product?
tags: [security, customer]
date: 2026-11-08
by: tea+claude
status: answered
owner: tea+claude
---

Schiller et al., "Drone Security and the Mysterious Case of DJI's DroneID" (NDSS 2023), reverse
engineered DJI drone firmware and the DroneID radio protocol. DJI is a device maker with valuable
shipped algorithms (see decision 0003), so the paper is a worked example of what reverse engineering
of a shipped consumer device takes, finds, and costs the maker. We need: method, how firmware
encryption and protections were handled, findings (DroneID, 16 bugs), devices, disclosure and DJI's
response, and what it says for our use case.

## Leads

- https://www.ndss-symposium.org/ndss-paper/drone-security-and-the-mysterious-case-of-djis-droneid/
- Artifacts on GitHub (RUB-SysSec/DroneSecurity).

## Answer

Answered 2026-11-08 from the full paper ([[ndss2023-dji-droneid-schiller]]) and news on the aftermath
([[dji-droneid-aftermath-web-excerpts-2026-11-08]]).

- DroneID sends drone, home-point and pilot location in the clear: [[dji-droneid-broadcasts-pilot-location-unencrypted]]
- How firmware encryption and signing were got past: [[dji-firmware-encryption-and-signing-did-not-stop-ndss-2023-researchers]]
- The 16 bugs and the mid-flight crash: [[dji-ndss-2023-fuzzer-found-remote-mid-flight-crash-bugs]]
- Disclosure, DJI's response, AeroScope: [[dji-fixed-ndss-2023-bugs-before-publication-and-later-dropped-aeroscope]]
- What it means for decision 0003: [[dji-ndss-2023-shows-reverse-engineering-a-shipped-device-is-academic-scale-work]]

Corrections to the brief: 94% is DJI's consumer-drone share (54% of all drones by units, 2021). The devices
analysed were Mini 2, Mavic Air 2 and Mavic 2 Pro, and Mavic 3 was used only to reproduce the findings.
Open: read "Behind The Wings" (arXiv 2309.05913) on DJI Enhanced Wi-Fi hijacking.
