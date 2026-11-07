---
type: source
title: "Project description: AI code protection with proof"
date: 2026-11-07
url:
tags: [idea, security, formal-methods, market]
---

Team description written by Karla on 2026-11-07. Status when filed: the chosen problem field; the solution is open.

# AI code protection with proof

AI makes shipped software cheap to reverse-engineer. This project protects code so that AI attackers struggle to read it, and it proves the protected code still behaves exactly like the original.

Proposed by Luka for the Garaža Frontier Hackathon (Belgrade, 7 and 8 November 2026). The team has chosen this **problem field**. The solution below is a starting point, and it is still open. The original pitch is [[idea-brief-code-protection]].

## Key terms

- **Source code:** the readable instructions a programmer writes.
- **Machine code:** what source code becomes when an app ships, i.e. the numbers a processor runs. Every device that has the app has a copy.
- **Decompiler:** a tool that turns machine code back into something roughly readable.
- **Reverse engineering:** working out what a program does from the shipped version.
- **Obfuscation:** rewriting code so it does exactly the same thing but is much harder to understand. Think of a recipe with renamed ingredients, pointless detours, and "add 2 eggs" written as a confusing sum that still equals 2. The cake comes out the same, but reading the recipe is miserable.
- **Formal verification:** a mathematical proof that two versions of a program give the same output for every possible input, with no need to test them one by one.
- **SMT solver** (for example Z3): the kind of tool that does this proof automatically for many programs.

## The problem

- Valuable logic runs on users' devices: payment and identity checks in banking apps, anti-cheat in games, licence checks, content protection in media apps, and AI models deployed on devices.
- Decompilers, combined with AI models that explain the output, now let attackers understand that logic quickly and cheaply. The skill needed to do it is falling.
- Most obfuscation was designed to slow down human attackers. AI agents read differently and tire differently, so protection tuned for humans may not hold.

## Starting solution

1. **Protect.** AI chooses rewrites that target the points where AI attackers fail: long context, many plausible-looking but false paths, and code that forces slow, expensive analysis while it runs.
2. **Prove.** Formal verification checks that each rewrite left behaviour unchanged. Nothing ships unless the proof passes.
3. **Measure.** Simulated attackers, both AI agents and solver-based tools, try to recover the logic. Their time, cost, and success rate are measured before and after protection.
4. **Report.** The protected build ships with a report: proven identical, and attacker cost raised by a measured factor.

## The weekend demo

- An AI with a decompiler explains the plain version of a function in seconds.
- On the protected version, the same AI fails, or it needs many times more time and tokens to succeed.
- The checker proves both versions behave identically.
- A chart shows attacker cost before and after protection.

## Who would pay

- Fintech and payments.
- Mobile apps with valuable client-side logic.
- Game studios (anti-cheat and piracy).
- Media companies (content protection).
- Teams that ship AI models to devices.

Code protection, often called "application shielding", is an existing budget line. Luka's pitch estimates the market at about $2.7B in 2026; this figure has **not yet been verified**. Many buyers buy protection to pass security standards, such as the OWASP mobile security standard (MASVS) and payment-industry rules (EMVCo), as well as for defence.

## Competition

- **App protection vendors:** Guardsquare, Jscrambler, Zimperium, Digital.ai (formerly Arxan), Promon, Irdeto, Verimatrix. Several of them already market protection against AI-driven attacks.
- **Free tools:** Obfuscator.io and open-source obfuscators.
- **What buyers do instead:** keep sensitive logic on the server, and use platform checks such as Google Play Integrity and Apple App Attest.

What would set this project apart: none of these vendors clearly offers a formal proof that protection did not change behaviour, nor a published, measured attacker cost.

## Known hard parts

- **Proof gets harder as protection gets stronger.** The strongest obfuscation methods, which mix arithmetic and logic tricks, are designed to defeat exactly the solvers used for proofs. Proofs are realistic for small, critical functions. Large programs need lighter checks.
- **Some protection changes behaviour on purpose.** Anti-tamper and anti-debug features change what the app does when someone tampers with it, so "identical behaviour" needs a careful definition.
- **Do buyers want the proof?** Buyers mostly worry about passing standards and about protected builds crashing or slowing down. Whether they will pay for a formal proof is untested.
- **The sale is slow.** Security buyers are cautious and want references before they trust a new vendor.
- **The arms race costs money.** As AI models improve, protection must be updated continuously. That is also why revenue would recur.

## Directions worth testing

- **Prove the rules once.** Prove each rewrite rule correct once, in a proof assistant such as Lean or Coq, in the style of the CompCert verified compiler. Then every use of a rule is correct by construction, and nothing has to be proved again for each build.
- **Sell the measurement.** A public benchmark of how much attacker cost each protection buys against current AI models. It would work for buyers, vendors, and standards bodies alike.
- **Start narrow.** Pick one high-value target, such as payment SDKs or game anti-cheat, where proof and measurement matter most.

## Team fit

- **Luka:** proposed the idea; software engineering at Databricks; B2B selling experience.
- **Marko:** Rust and low-level systems work at CERN; won Garaža 2025.
- **Tea:** backend and AI engineering; regression gates for agent skills.
- **Karla:** detection and evaluation methods; measurement design for the attacker benchmark.
