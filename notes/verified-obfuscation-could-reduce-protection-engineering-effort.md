---
type: note
title: AI-guided verified obfuscation could reduce protection engineering effort at a fixed performance budget
tags: [idea, security, formal-methods, agents, customer, demo]
date: 2026-11-07
by: luka+codex
confidence: low
sources: [https://www.guardsquare.com/blog/mobile-app-profiling-security-ux, https://ercim-news.ercim.eu/en139/special/verifying-code-correctness-of-protected-software-through-translation-validation, https://github.com/AliveToolkit/alive2]
---

# Working hypothesis

> Vendors shipping proprietary client software could achieve stronger resistance to
> reverse engineering with fewer engineer-hours by using AI to select protection
> strategies and formal verification to check supported transformations, within the
> same runtime and binary-size budgets.

**Status: unvalidated business and technical hypothesis.** Research supports the
individual ingredients, not the claimed combined improvement or willingness to pay.
Checked against public sources on 2026-11-07.

## Read next

- Adoption evidence: [[obfuscation-is-common-in-popular-android-apps]].
- Production scope and costs: [[production-obfuscation-can-target-a-small-part-of-an-app]].
- Linked papers and competitor sources: [[verified-obfuscation-research-links]].
- Existing team context: [[verified-obfuscation-reading-list-2026-11-07]],
  [[code-protection-field-open-questions]], [[code-protection-evidence-index]].

## Narrow initial problem

Protect a small proprietary calculation distributed in a C/C++ library, such as a
pricing or scoring function, without changing its specified behavior. Initially
restrict inputs to fixed-width integers and functions without loops, external calls,
or complex memory access. The customer designates the valuable asset; AI should not
be assumed to infer commercial value from source alone.

## Proposed workflow

1. Accept source, asset description, tests, and performance constraints.
2. Let the local model select targets, transformation order, and parameters from a
   constrained library of transformations.
3. Validate each candidate at LLVM IR level using Alive2 where supported.
4. Reject failed, unsupported, or timed-out checks; record why they were rejected.
5. Compile, test behavior, and measure runtime and binary size.
6. Evaluate retained candidates against an isolated cloud-model attacker.
7. Return the best observed configuration with its evidence and verification scope.

Generated transformations and proof synthesis are later research directions.

## What verification does and does not establish

- Alive2 checks refinement under LLVM semantics; this must not be described as
  unconditional source-to-final-binary equivalence.
- Undefined behavior, preconditions, supported instructions, and loop bounds matter.
  Alive2 does not support interprocedural transformations.
- A successful check is not necessarily a portable independently checkable proof
  certificate. Do not advertise proof-carrying artifacts without implementing them.
- Compiler stages after a checked IR transformation and deployment integration remain
  outside that check unless separately covered.
- Correctness does not prove resistance to reverse engineering, acceptable overhead,
  or compatibility with every runtime environment. Runtime defenses intentionally
  alter behavior in some environments and require an explicit specification.
- Verification adds computation. The proposed speed benefit is reduced engineering
  and debugging effort, not necessarily shorter builds or elimination of QA.

## Hackathon experiment

- Create six custom C functions: two development cases and four held-out cases.
- Compare a competent fixed configuration, random search, and agent-selected
  configurations using the same transformation engine and candidate-build budget.
- Give all strategies the same measured runtime and binary-size limits.
- Attack objective: produce a standalone Python recreation of each function that
  cannot call the supplied binary. Evaluate on 200 hidden inputs with boundary cases.
- Use identical attacker models, tools, time budgets, and oracle access. Calibrate on
  development cases; do not tune against held-out results.
- Four held-out cases times three strategies times two attempts gives 24 attacks.
  At three minutes each, this is up to 72 minutes of sequential attacker time,
  excluding setup, builds, verification, and scoring.
- Isolate attackers from original source, hidden tests, answers, previous transcripts,
  and other evaluation secrets. Judge executable submissions rather than narratives.
- Report attack accuracy and complete successes, correctness scope, verification
  rejection/timeouts, runtime, size, build time, and AI cost. With this sample size,
  describe results as preliminary rather than broad security guarantees.

## Customer pilot and decision criteria

Measure engineer-hours to a release-ready protected build, configuration revisions,
regressions, supported verification coverage, build latency, and protection strength
under matched attack and performance budgets. Compare with the customer's existing
well-configured workflow, including its existing automation.

Continue if context-aware selection improves resistance and the combined workflow
reduces human effort enough to justify integration and compute costs. Reconsider if
ordinary search matches the agent, verification covers too little valuable code, or
customers already solve the problem cheaply with existing tools.

## Competition and possible defensibility

Digital.ai publicly claims LLM-enhanced targeted protection and integrated testing.
Guardsquare describes profiling-guided protection and AI-assisted exploratory testing.
Quarkslab researches protection against reversing agents. Formal verification of
obfuscation also predates this proposal, including work with a Cloakware researcher.
We cannot claim competitors lack equivalent internal pipelines.

A potential long-term advantage is a verified transformation library plus proprietary
evidence connecting code characteristics, protection choices, overhead, and attack
outcomes. This is a potential moat, not an asset the prototype already possesses.
On-premise operation means cross-customer learning cannot assume access to customers'
source, artifacts, or logs without an explicit data-sharing arrangement.

## Sources

- [Guardsquare: profiling, breakage, performance, and agentic testing](https://www.guardsquare.com/blog/mobile-app-profiling-security-ux).
- [Research overview: validating obfuscation through small compiler passes](https://ercim-news.ercim.eu/en139/special/verifying-code-correctness-of-protected-software-through-translation-validation).
- [Alive2 documentation and limitations](https://github.com/AliveToolkit/alive2).
- Full paper links and evidence qualifications: [[verified-obfuscation-research-links]].
