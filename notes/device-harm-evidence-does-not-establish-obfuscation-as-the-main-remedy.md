---
type: note
title: Device harm evidence supports product security demand but does not establish obfuscation as the main remedy
tags: [security, customer, idea, formal-methods]
date: 2026-11-07
by: luka+codex
confidence: moderate
sources: [https://unsaflok.com/, https://www.bbraun.com/en/products-and-solutions/b--braun-product-security/05-2021-spacecom--battery-pack-sp-with-wifi--data-module-compact.html, https://www.usenix.org/system/files/conference/woot14/woot14-ghena.pdf, https://arxiv.org/html/2603.08665v2]
---

The cases in [[everyday-device-reverse-engineering-harm-casebook]] justify investigating the security of ordinary objects. They do not establish that hiding implementation is the primary missing control.

## What the examples actually suggest

| Failure exposed | Primary control to investigate | Possible role for obfuscation |
|---|---|---|
| Unauthorized local or remote commands | Authentication and authorization enforced by device/service | Potential extra analysis cost; cannot supply missing authority |
| Altered firmware accepted or untrusted boot | Authenticated updates and a sound boot trust chain | Complicate modifications after code access; not equivalent to integrity enforcement |
| Shared credentials expose other devices | Appropriate per-device identity, scope and cloud isolation | Concealing a shared secret is an inadequate long-term fix |
| Camera or telemetry misuse | Access controls, data minimization, secure lifecycle | Protecting code alone does not protect captured data |
| Hazardous motion or operation | Independent safety constraints and runtime controls | Equivalence does not prove safety against malicious inputs |
| Valuable algorithm reconstructed | Protection of implementation plus realistic RE evaluation | Directer fit, with correctness and overhead constraints |

These controls are not theoretical substitutes invented for the pitch: B. Braun documents patches and network segmentation, Unsaflok describes substantial lock/card/software upgrades, and the traffic-light study describes a hardware safety monitor. Each operates at a different layer. [Pump advisory](https://www.bbraun.com/en/products-and-solutions/b--braun-product-security/05-2021-spacecom--battery-pack-sp-with-wifi--data-module-compact.html), [locks](https://unsaflok.com/), [traffic study](https://www.usenix.org/system/files/conference/woot14/woot14-ghena.pdf).

## Startup hypotheses to keep distinct

**Protection product:** for vendors with valuable shipped native algorithms, select and verify supported code transformations, then measure reconstruction cost. This is our earlier, narrower hypothesis. Customer benefit must be demonstrated against their existing protection, not assumed from dramatic device examples.

**Broader product-security product:** analyze release artifacts, flag exploitable trust/design failures and provide a reproducible, safely bounded validation report. This addresses more of the device casebook but enters an existing firmware/IoT/robot security market, including authors of the CAI research. It is a different scope, not a validated moat.

**Formal verification boundary:** proving transformed code equivalent to the original can preserve an original vulnerability. A safety/security proof needs an explicit property and environment model; function equivalence alone cannot establish them.

Useful pitch wording: “As automated analysis gets easier, device vendors need to validate what exposed software reveals and which protections materially delay misuse.” Avoid promising prevention of device injuries through obfuscation without a tested causal chain.
