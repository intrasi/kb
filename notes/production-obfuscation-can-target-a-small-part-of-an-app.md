---
type: note
title: One production iOS report protected only 0.5 to 2 percent of each app and measured substantial protected-code expansion
tags: [security, customer, formal-methods]
date: 2026-11-07
by: luka+codex
confidence: moderate
sources: [https://faculty.ist.psu.edu/wu/papers/obf-iii.pdf, https://www.guardsquare.com/blog/mobile-app-profiling-security-ux]
---

## Claim and evidence

Whole-application adoption and the proportion of code protected are different
questions. A 2019 production experience report by Wang et al., involving Baidu X-Lab
and Penn State researchers, describes deploying obfuscation in multiple commercial
iOS apps with millions of users.

Section 5 reports a protected Objective-C/C code base of approximately 23,000 lines,
representing roughly 0.5-2% of each containing application. Section 5.2.1 measures
approximately 3-4 times code-section expansion for the protected component in its
standalone measurement application. This is not 3-4 times expansion of every entire
deployed app, nor a universal overhead estimate for present-day products.

This historical case supports selective protection as a practical approach, while
its architecture, platform constraints, and measured costs should not be treated
as a current iOS-wide deployment survey. Checked 2026-11-07.

## Related operational evidence

Guardsquare's July 2026 profiling article describes reflection-related compatibility
risks, protection placement, runtime overhead, and device/user-journey testing. It
discusses AI-driven exploratory testing as a way to collect profiling data. This is
a vendor's description of its workflow and opportunity, not an independently
measured reduction in engineering hours from AI plus formal verification.

PreEmptive also documents a real customer localization failure after obfuscation
and the configuration needed to address it. Such integration issues illustrate why
a local arithmetic-equivalence proof cannot replace application-level testing.

## Implication for the hypothesis

AI-guided targeting and configuration could reduce manual experimentation; formal
checks could reject some semantic errors before integration. Whether this saves
time overall remains an experiment, because verification has costs and limited
coverage. See [[verified-obfuscation-could-reduce-protection-engineering-effort]].

## Sources

- [Wang et al., Field experience with obfuscating million-user iOS apps in large enterprise mobile development, 2019](https://faculty.ist.psu.edu/wu/papers/obf-iii.pdf), sections 5 and 5.2.1; DOI: [10.1002/spe.2648](https://doi.org/10.1002/spe.2648).
- [Guardsquare: Mobile App Security Without Sacrificing UX, July 2026](https://www.guardsquare.com/blog/mobile-app-profiling-security-ux).
- [PreEmptive: Protecting Localized Xamarin Forms Applications, 2020](https://www.preemptive.com/blog/protecting-localized-xamarin-forms-applications/).
