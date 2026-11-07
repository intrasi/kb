---
type: note
title: ML-DSA-44 signatures are 2,420 bytes against 64 for Ed25519, which breaks some TLS and QUIC paths
tags: [pqc, tls]
date: 2026-11-07
by: karla+claude
confidence: high
sources: [https://csrc.nist.gov/pubs/fips/204/final]
---

- FIPS 204 (August 2024): ML-DSA-44 signature is 2,420 bytes. An Ed25519 or ECDSA P-256
  signature is about 64 bytes. (high)
- A full post-quantum certificate chain can exceed QUIC's anti-amplification limit, which
  adds round trips (F5 write-up). (moderate)
- Split ClientHello messages from large post-quantum key shares broke against some
  firewalls (Sophos knowledge base). (moderate)

Why it matters: a migration that compiles and passes unit tests can still fail on the
network. That gap is what our checker proves. See [[agents-crypto-patches-fail-interop]].
