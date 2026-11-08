---
type: question
title: What did the NDSS 2023 DJI DroneID paper find, how did the researchers get past DJI's firmware protection, and what does it teach a code-protection product?
tags: [security, customer]
date: 2026-11-08
by: tea+claude
status: open
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
