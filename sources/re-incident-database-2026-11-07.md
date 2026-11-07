---
type: source
title: "Tea's reverse-engineering incident database, 20 cases 2010-2026 (spreadsheet)"
date: 2026-11-07
by: tea
url:
tags: [security, agents, market]
---

Verbatim copy of Tea's spreadsheet `Reverse_Engineering_Incident_Database.xlsx`, filed 2026-11-07.
The original workbook is beside this file in
`sources/re-incident-database-2026-11-07/`. Rows are unverified as filed; the checked and
extended records are in [[re-incident-records]]. Open questions:
[[code-protection-field-open-questions]], [[re-research-gaps-to-verify]].

## Sheet: Incident Database

**Global Reverse Engineering Incident Evidence Database (2010 - 2026)**

Comprehensive log of high-profile software, AI model, mobile, DRM, protocol, and hardware reverse engineering cases.

| # | Date Reported | Target / App Name | Scope | Perpetrator / Actor | Motivation / Objective | Technical Method | Impact & Quantified Result | Primary Source / Reference |
|---|---|---|---|---|---|---|---|---|
| 1 | February 2026 | Anthropic Claude Platform | Part (Agentic coding, reasoning, computer use capabilities) | DeepSeek, Moonshot AI, MiniMax | Model capability distillation & synthetic dataset generation | Issued 16M+ queries using ~24,000 fraudulent user accounts to evade rate limits | Replicated teacher model capabilities for student models at lower compute cost | https://www.anthropic.com/news/detecting-and-preventing-distillation-attacks |
| 2 | September 2026 | Anthropic Claude API | Part (Live user prompt outputs) | Moonshot AI, DeepSeek | Capability harvesting & middleman proxy arbitrage | Deployed silent middleman proxies relaying customer API traffic (35.1M+ exchanges) | Harvested higher-tier model outputs while charging users lower rates | https://www.anthropic.com/threat-intelligence-report-september-2026 |
| 3 | March 2024 | OpenAI Ada, Babbage, gpt-3.5-turbo | Part (Embedding layer projection matrix) | Carlini et al. (Academic Researchers) | Security research / parameter recovery | Executed linear algebra transformations on logprob arrays and logit biases (<$20 spend) | Forced providers to restrict API logprob output precision globally | https://arxiv.org/abs/2403.06634 |
| 4 | November 2023 | OpenAI ChatGPT API | Part (Memorized training data instances) | Nasr, Carlini et al. (Academic Researchers) | Training set privacy auditing | Prompted model to repeat specific words endlessly (divergence attack, $200 spend) | Extracted 10,000+ raw training examples (PII, private keys, code) | https://arxiv.org/abs/2311.17035 |
| 5 | August 2021 | Apple NeuralHash (iOS 14.3) | Full (CoreML perceptual hash weights) | Asuhariet Ygvar | CSAM scanner security analysis | Reverse engineered iOS binary, extracted model weights, converted to Python | Generated image hash collisions in hours; system deployment was shelved | https://techcrunch.com/2021/08/18/apples-csam-detection-tech-is-under-fire-again/ |
| 6 | March 2023 | Meta LLaMA 1 Model | Full (Complete binary model weights) | Anonymous 4chan user | Open model dissemination | Parsed restricted research download links and compiled a BitTorrent distribution | Permanently removed access control 7 days after limited academic release | https://decipheru.com/ai/decipher-files/meta-llama-weights-leak-2023 |
| 7 | December 2023 | Apple iMessage / APNs Protocol | Part (Push notification & registration protocols) | Beeper (via 16-year-old student research) | Cross-platform interoperability | Reversed serialized protobuf messages & TLS channels; synthesized hardware IDs | Enabled native iMessage on Android before server-side attestation blocks | https://en.wikipedia.org/wiki/Beeper_(software) |
| 8 | August 2025 | Ticketmaster Mobile API | Part (Authentication & reservation endpoints) | Key Investment Group (KIG) | Ticket scalping & resale profit | Reversed API auth; deployed 49+ automated accounts & virtual payment cards | Acquired 379,776 tickets ($57M spend, $64M resale, $7M net profit) | https://news.pollstar.com/2025/08/18/ftc-sues-ticket-reseller-who-asked-courts-to-stop-bots-act-enforcement/ |
| 9 | December 2010 | Sony PlayStation 3 Boot ROM | Full (Master ECDSA private signing key) | fail0verflow & George Hotz | Console homebrew & custom OS enablement | Identified static cryptographic nonce k reuse in signature generation | Derived master private key d_A; unpatchable without hardware revisions | https://en.wikipedia.org/wiki/PlayStation_3_homebrew |
| 10 | Early 2026 | Irdeto Denuvo Anti-Tamper DRM | Full (Systemic anti-tamper logic) | Anonymous Cracking Groups | Game piracy / DRM removal | Deployed Type-1 Ring -1 Hypervisor to intercept CPUID/hardware checks below Windows | Achieved day-zero circumvention across major titles (e.g., Crimson Desert) | https://www.pcgamesn.com/drm/denuvo-hypervisor-bypass-all-non-vr-games |
| 11 | March 2024 | Nintendo Switch System Firmware | Part (Key derivation & execution environment) | Yuzu Development Team | PC game emulation | Reversed prod.keys and console encryption routines | Resulted in $2.4M legal settlement and permanent project shutdown | https://www.gamedeveloper.com/business/switch-emulator-yuzu-reaches-2-4-million-settlement-with-nintendo |
| 12 | 2024 – 2026 | Automotive CAN Bus / ECU | Part (Engine immobilizer diagnostic commands) | Organized Vehicle Theft Rings | Physical vehicle theft | Tapped directly into CAN bus wiring via headlights/wheel-wells to inject commands | Bypassed immobilizers; >90,000 thefts/year in Canada (C$1B loss) | https://www.eff.org/deeplinks/2024/03/restricting-flipper-zero-accountability-approach-security-canadian-government |
| 13 | July 2026 | John Deere Tractor Firmware | Part (Dealer lock & parts-pairing validation) | Farmers & Independent Repair Technicians | Right to repair / DIY maintenance | Decompiled ECU firmware to bypass dealer software authorization checks | FTC settlement mandating 10-year diagnostic tool access & $99M class payout | https://sigmalawgroup.com/blog/2026-07-22-ftc-deere-right-to-repair/ |
| 14 | March 2024 | XZ Utils (liblzma / OpenSSH) | Part (Patched RSA_public_decrypt function) | Jia Tan (Threat Actor) | Global Linux server remote code execution | Injected obfuscated M4 build macros during tarball compilation | Exposed OpenSSH daemons globally; intercepted by Andres Freund | https://openssf.org/ |
| 15 | May 2017 | WannaCry Ransomware Worm | Part (Initialization domain check logic) | Marcus Hutchins (MalwareTech) | Defensive incident response | Dynamic sandbox tracing isolated HTTP request to unregistered domain | Registered domain for $10.69, activating global worm kill-switch | https://www.microsoft.com/en-us/security |
| 16 | June 2010 | Siemens Simatic Step7 PLC | Part (Centrifuge frequency converter control logic) | Stuxnet Authors (Nation-State) | Industrial sabotage | Disassembled PLC drivers & intercepted physical sensor telemetry | Destroyed nuclear centrifuges while spoofing normal telemetry to operators | https://www.cisa.gov/ |
| 17 | 2024 – 2026 | 156,080 iOS App Store Binaries | Part (Embedded API tokens & cloud credentials) | Cybernews Security Research Team | Ecosystem secret audit | Automated static disassembly parsing strings tables & .plist files | Discovered 815,000+ secrets; 71% of apps leaked keys (406 TB cloud data exposed) | https://cybernews.com/security/ios-apps-leak-hardcoded-secrets-research/ |
| 18 | 2025 – 2026 | 1,243+ Android Banking Apps | Part (UI layout structure IDs & activity names) | Banking Trojan Syndicates (Hook, Godfather) | Credential theft & session hijacking | Reversed layout IDs to inject HTML overlay windows via Accessibility Service abuse | 255,000+ unique trojan packages; 56% increase in Android banking malware | https://zimperium.com/industry/finance/banking |
| 19 | Nov 2024 – Aug 2025 | SQLite Database Engine | Part (Memory corruption execution paths) | Google DeepMind (Project Big Sleep) | Autonomous zero-day discovery | Autonomous AI agent driving interactive disassembly, state fuzzing, and debugging | Discovered 20+ zero-day vulnerabilities (including SQLite CVE-2025-6965) | https://blog.google/innovation-and-ai/technology/safety-security/cybersecurity-updates-summer-2025/ |
| 20 | May 2024 | Activision Call of Duty Client | Part (RAM entity arrays & local camera angles) | EngineOwning Syndicate | Commercial cheat software sales | Reversed RAM memory allocations for aimbots & ESP wallhacks | $14.47M legal judgment awarded to Activision | https://www.techspot.com/news/103206-activision-awarded-over-145-million-lawsuit-against-call.html |

## Sheet: Executive Summary

- Reverse Engineering Threat & Case Summary Dashboard
- Total Incidents Tracked  20 · AI / LLM Extraction Cases  6
- Mobile & API Exploits  5 · DRM, Firmware & HW Bypass  6
- Target Domain Sector · Count · Primary Threat Vector
- AI Models & Platforms · 6 · Model Distillation, Parameter Extraction, Training Data Harvest
- Mobile Applications & APIs · 5 · Secret Key Harvesting, Accessibility Overlays, Private API Bots
- Gaming & Anti-Tamper DRM · 3 · Hypervisor Ring -1 Bypass, Memory Scanning, Key Derivation
- Embedded, Hardware & CAN Bus · 3 · CAN Injection, Unsigned Diagnostic Firmware, Nonce Reuse
- Critical Infrastructure & OS · 3 · Build System Injection, Dynamic Domain Sinkholing, PLC Exploits
