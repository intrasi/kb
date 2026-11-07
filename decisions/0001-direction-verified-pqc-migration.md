---
type: decision
title: Build verified post-quantum migration (find, rewrite, prove, ship), with the checker as the product
tags: [idea, pqc]
date: 2026-11-07
by: karla+claude
status: active
---

## Context

Garaža rewards startup potential ([[garaza-hackathon-facts]]). We wanted a global
market and an insider edge for this team: compilers, code search, evaluation, and a
quantum story.

## Choice

Agents find RSA and elliptic-curve use, rewrite it, and a checker proves the result
still interoperates ([[agents-crypto-patches-fail-interop]]). Deadlines create the
demand ([[eo-14412-pqc-deadlines]], [[cnsa-2-acquisitions-2027]], [[eu-pqc-roadmap]]).
Tarpit verdict: moderate-low.

## Dropped

- Agent trust layer: saturated, and Emendra (a sponsor) builds close to it.
- Agent forward-deployed engineers: about $9B already invested (OpenAI Deployment
  Company, Ode, Rocketlane, and others).
- GPU cluster reliability: NVIDIA Mission Control, CoreWeave, and Clockwork cover most of
  it; silent data corruption detection mid-run is still open.
- Photonic computing: conversion and precision limits; Lightmatter moved to
  interconnect, and Marvell bought Celestial AI.
- Quantum-ready software: Zapata shut down in October 2024.

## Revisit when

The three customer calls say vendors would rather hire consultants
([[do-vendors-buy-pqc-migration-tools]]).
