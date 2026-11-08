---
type: note
title: A black-box DUML fuzzer found 15 DJI bugs in about 9 hours per run; 14 work over the air and can crash a drone mid-flight
tags: [security]
date: 2026-11-08
by: tea+claude
confidence: high
sources: [ndss2023-dji-droneid-schiller]
---

The NDSS 2023 team had neither source nor full firmware nor an emulator, so it fuzzed real drones over USB
with a grammar for DJI's DUML command bus. A new "UI oracle" drove the DJI Fly app via ADB/uiautomator to
catch silent state changes.

- About 7.8 million commands, about 400 per second, about 9 hours per full run including reboots. The fuzzer is about
  4,000 lines of Python.
- 15 deduplicated faults (Table II) plus the static-analysis signature bypass = 16 vulnerabilities:
  - #1 root ADB shell on Mini 2: the debug-unlock challenge-response accepted any answer (physical access).
  - #2-#13 flight-controller and other crashes (buffer overflows on Mavic Air 2, DoS on Mini 2). The drone
    reboots, so in flight it falls.
  - #14 OS command injection via the WiFi SSID setting: arbitrary code execution on Mini 2 and Mavic 3.
  - #15 rewrite of the "immutable" flight-controller serial number, which is also sent in DroneID.
  - #16 drone name change (benign).
- DUML is a bus across all components, so 14 of the bugs can be sent from the remote controller over
  OcuSync. Anyone who controls the pilot's phone (DJI's app is sideloaded, not on Google Play) can send
  them.
- DJI rated severity itself (low to critical) during disclosure.

The lesson the authors draw: analysis of a complex closed device "is currently impossible without manual
analysis", and fuzzing only worked after manual reverse engineering of DUML. That was written in 2022,
before LLM agents. The manual step it names is the one agents now make cheaper.

Sources: [[ndss2023-dji-droneid-schiller]] (section IV-D, Table II, section V-g).
