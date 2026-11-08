---
type: note
title: DJI's DroneID broadcast the pilot's, home point's and drone's GPS position unencrypted, readable with a cheap SDR
tags: [security]
date: 2026-11-08
by: tea+claude
confidence: high
sources: [ndss2023-dji-droneid-schiller, dji-droneid-aftermath-web-excerpts-2026-11-08]
---

Schiller et al. (NDSS 2023) reverse engineered DJI's proprietary DroneID broadcast, which DJI's AeroScope
receivers use to locate drones and pilots, and built an open receiver from a USRP B205-mini SDR and Python.

- One packet (sent every 640 ms on 2.4 and 5.7 GHz, LTE-like OFDM/QPSK, Gold-sequence scrambling, LTE turbo
  code) carries drone position, altitude, speed, home point, **pilot (app) position**, serial number and
  model. It is not encrypted; the CRC matched their decode.
- Tested on Mini 2, Mavic Air 2 and Mavic 2 Pro (OcuSync 2.0). One packet locates drone and pilot; the
  prototype decoded about 37% of packets, enough to rebuild a flight path, at roughly 10 m range (not optimised).
- The firmware was needed to decode it: the scrambler seed and the packet structure came from reverse
  engineering the S1 transceiver firmware, not from the radio signal alone.
- The pilot position comes from the phone and is not checked: a "Fake GPS" app on an unrooted phone spoofed
  it. An undocumented DUML command replaced DroneID fields with "fake" (DJI: internal API, fixed in newer
  model). The serial number in DroneID could also be changed (bug #15).
- DJI's spokesperson had said the signals were encrypted. Kevin Finisterre showed otherwise with an SDR on
  31 March 2022, and DJI admitted it to The Verge on 28 April 2022. The paper then published the full
  protocol and an open receiver (github.com/RUB-SysSec/DroneSecurity).

Context: EU and US Remote ID (mandatory from 2024) broadcast the same kind of data unencrypted by design.
DJI's former policy VP made this point. The privacy harm was the gap between what DJI said and what the
drone did, more than the broadcast itself.

Checked 2026-11-08. Sources: [[ndss2023-dji-droneid-schiller]], [[dji-droneid-aftermath-web-excerpts-2026-11-08]].
