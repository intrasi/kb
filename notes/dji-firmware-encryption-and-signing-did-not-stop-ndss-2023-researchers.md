---
type: note
title: DJI's encrypted, signed firmware did not stop the NDSS 2023 team, because community-leaked keys and unsigned patch files opened it
tags: [security, customer]
date: 2026-11-08
by: tea+claude
confidence: high
sources: [ndss2023-dji-droneid-schiller]
---

DJI hardens its firmware. It uses a proprietary container encrypted with AES and signed with RSA, with
different keys per module and use. The transceiver RTOS ships as encrypted binaries, debug UART and ADB are
disabled on production units, and a fuse bit marks production state. The paper says these measures made
analysis "more difficult, but not impossible". It got through them in four ways:

1. **Leaked keys.** "Some of these encryption keys have been leaked by individuals from the DJI community";
   the authors confirmed they are valid. Firmware encryption was only as strong as key secrecy across
   years of releases.
2. **Community tooling.** They used Ghidra, Binwalk, a hex editor, and the open o-gs/dji-firmware-tools.
   Much of the DUML command protocol was already documented by the DJI reversing community.
3. **Signature bypass (rated critical by DJI).** "SDRH" configuration files in the S1 transceiver firmware
   package are neither signed nor encrypted. The bootloader applies them as RAM patches *after* the
   signature check, so crafted SDRH files change any code. Delivered via a fastboot-like mode triggered by
   USB packets at boot. Affected Mini 2, Mavic Air 2 and the RC231/RC-N1 controller. Mavic 3 and Mavic 2
   Pro use a different transceiver.
4. **Patched-out production check.** They found the code that reads the production fuse and patched it
   with an SDRH file. This kept the UART shell open, which gave arbitrary memory read/write and a shell.

Why it matters to us: the code itself was not the weak point. The researchers needed a full
understanding of the firmware (protocol structures, scrambler seed, the fuse check) to succeed, and
encryption only delayed reading it. Once keys leak, an encrypted firmware is plain firmware for every
release that used those keys. Protection that survives decryption (obfuscation of the logic itself)
addresses the step that actually happened. Compare [[re-agents-route-around-obfuscation]].

Sources: [[ndss2023-dji-droneid-schiller]] (sections II-B, IV-C, V-a, Table I).
