---
type: source
title: "Reverse engineering in 2026: cases, patterns, impact and defenses (hackathon research brief)"
date: 2026-11-07
by: tea
url:
tags: [security, market, regulation, pitch]
---

Deep-research brief gathered by Tea on 2026-11-07 (agent not recorded). Cases by category, who gets reverse engineered, quantified impact, defenses, market, and pitch angles. Filed verbatim. Original filename: `Reverse Engineering in 2026_ Cases, Patterns, Impact and Defenses.md`.
Open questions: [[code-protection-field-open-questions]], [[do-people-need-ai-resistant-code-protection]].

# Reverse Engineering in 2026: Cases, Patterns, Impact and Defenses (Hackathon Research Brief)

Reverse engineering (RE) is no longer a niche skill aimed at copying whole products. It is an industrial, increasingly AI-accelerated way of pulling value out of software, apps, devices and AI models: private APIs, paywalled features, game advantages, fraud paths, secrets, and model capabilities. The protection market has not caught up with that shift. In Digital.ai's 2026 Application Security Threat Report (May 19, 2026), 87% of monitored client-facing apps faced attacks, climbing 55% → 57% → 65% → 82.7% → 87% from 2022 to 2026. Anthropic says three Chinese labs ran more than 16 million distillation exchanges through approximately 24,000 fraudulent accounts. In 2026 a universal hypervisor bypass defeated Denuvo, the industry's strongest game DRM, at launch.\[1\]\[2\]

## TL;DR
- **RE is about extracting value, not cloning products.** Nobody needs to clone Instagram. Attackers reverse its private API to run bots, scrape data, automate engagement and commit fraud. The same pattern repeats elsewhere: cheats in games (a cheat economy Intorqa estimates at $8.5B, though this is a model-based vendor estimate), trojans and repackaging in banking, ticket-limit circumvention, and distillation of frontier LLMs.
- **Client-side protection buys time; it does not buy permanence.** Denuvo's value lies in protecting the launch window: a peer-reviewed study (Volckmann, UNC, *Entertainment Computing*, 2024, 86 Denuvo titles) found an estimated 20% fall in total revenue when a game is cracked very early, and near zero after 12 weeks. Obfuscation, RASP and attestation all get bypassed eventually. Security has to come from layering client hardening, server-side verification, telemetry and legal action, plus fast response.
- **The biggest gaps right now are three.** (1) Protection of AI/LLM APIs, agents and MCP endpoints against distillation and automated abuse. (2) Affordable "in a day" protection for small developers who ship AI-written apps full of hardcoded secrets (Cybernews found 71% of 156,080 iOS apps leaked at least one). (3) Defenses built for a world where LLMs deobfuscate and decompile code for attackers in hours.

## 1. Overview and taxonomy

**What RE is.** Reverse engineering means analyzing a finished artifact (a binary, app, firmware image, network protocol, chip or ML model) to work out how it is designed and how it behaves, without access to the original source or specifications. There are two broad modes. *Static* analysis reads code through disassembly and decompilation. *Dynamic* analysis observes the artifact while it runs, through debugging, hooking, traffic interception, or emulation.

**Legitimate vs. malicious uses**

| Legitimate (often legally protected) | Malicious / contested |
|---|---|
| Interoperability (Samba, Sega v. Accolade, Beeper) | Piracy and DRM/license cracking |
| Security research and vulnerability discovery | Game cheats and anti-cheat bypass |
| Malware analysis and incident response (Stuxnet, WannaCry, XZ Utils) | IP theft, cloning, counterfeit hardware |
| Right to repair (Deere, ink cartridges) | Fraud: repackaged banking apps, GPS spoofing, bonus abuse |
| Preservation and emulation of abandoned platforms | Private-API abuse: bots, scraping, spam, scalping |
| Competitive analysis and compatibility (Compaq/Phoenix BIOS clean room) | Model extraction and distillation, system-prompt theft |

**Tool ecosystem (high level)**
- *Disassemblers and decompilers:* IDA Pro with the Hex-Rays decompiler (the commercial standard), Ghidra (free, released by the NSA in 2019), Binary Ninja, radare2/Cutter.
- *Mobile:* jadx (DEX to Java), apktool (decode and rebuild APKs), Frida (dynamic instrumentation and hooking on Android and iOS), Objection, plus jailbreak and root frameworks such as Magisk.
- *Network/protocol:* mitmproxy, Burp Suite, Charles, Wireshark. Certificate-pinning bypass is usually done with Frida scripts.
- *Hardware:* logic analyzers, JTAG/SWD debuggers, SDRs (HackRF), the Flipper Zero, chip decapping and fault injection.
- *AI-assisted:* LLM plugins for IDA, Ghidra and Binary Ninja that rename variables, summarize functions and deobfuscate JavaScript; dedicated models such as LLM4Decompile; and autonomous agents (see §7).

**How AI changes RE (2024–2026).** RE used to be bottlenecked on scarce experts. LLMs remove much of that bottleneck in three ways. First, decompiler output becomes readable: on the Decompile-Bench study, LLM-based decompilers score roughly 80 on a readability index against roughly 40 for Ghidra and IDA.\[3\] Second, obfuscated JavaScript and Java can be explained function by function. Third, agents can drive debuggers and fuzzers on their own. Digital.ai's 2026 report frames this directly: "What once required a specialist team and weeks of work now takes an afternoon and an LLM subscription."\[4\] In November 2026, a hobbyist used Claude to build "TVPort," a recompilation toolkit that runs Switch games natively on Apple TV. Coverage noted that AI shrinks a reconstruction effort that once took years down to weeks.\[5\]\[6\]

## 2. Major cases by category

### Mobile apps
- **WhatsApp mods (GBWhatsApp, FMWhatsApp, WhatsApp Plus).** These are decompiled and repackaged APKs that add features such as hidden read receipts and anti-delete. They are a common delivery vehicle for spyware. WhatsApp responds with temporary and permanent bans of accounts that use them.
- **Spotify, YouTube and Instagram modded clients (ReVanced and similar).** These patch out ads and premium checks on the client. The motivation is subscription bypass, not cloning.
- **Instagram and Tinder private APIs.** Libraries that mimic the official app's signed requests power follower bots, mass-DM spam, scraping and "engagement pods." This is the clearest refutation of the "nobody would use a clone" hypothesis: the value is the API, not the UI.
- **Pokémon Go (2016).** Bots and map scrapers reversed Niantic's protocol. Niantic responded with request signing, obfuscation and shadow bans.
- **Banking app repackaging and overlays.** Zimperium tracked 34 active malware families targeting 1,243 financial apps in 90 countries in 2025. Android banking-trojan attacks rose 56%, and unique trojan packages rose 271% to 255,090. Modern trojans now hijack live sessions *inside* the genuine banking app.\[7\]\[8\]
- **Hardcoded secrets.** Cybernews analyzed 156,080 iOS apps (about 8% of the App Store). It found more than 815,000 hardcoded secrets, an average of 5.2 per app, with 71% of apps leaking at least one. It also found about 83,000 cloud storage endpoints, 836 of them unauthenticated and exposing 406 TB, plus Stripe keys.\[9\]\[10\]\[11\] Static RE of an app download is enough to harvest these.

### Games
- **The cheat economy.** A University of Birmingham study of 80 cheat-selling sites estimated $12.8M to $73.2M a year in revenue in North America and Europe alone, from 30,000 to 174,000 monthly buyers.\[12\] Intorqa's 2026 "Cheatonomics" model, which Activision's Team Ricochet cited, puts the global cheat economy at a median $8.5B (range $5.1B to $13.8B). Cheat subscriptions account for a median $3.53B of that (range $2.08B to $5.75B for the subscription segment alone), across just 15 modeled games; FPS and battle royale titles make up 61%. One cheat developer reportedly made about $77M from a single game.\[13\] An Anybrain survey of 250 developers found 69% call cheating a significant problem and 51% report measurable losses in retention or revenue.\[14\]\[15\]
- **Lawsuits against cheat makers.** In 2024 Activision won a $14.47M default judgment against EngineOwning on DMCA anti-circumvention and CFAA grounds, but EngineOwning kept selling.\[16\]\[17\]\[18\] Bungie obtained a $13.5M settlement (2022) and, against AimJunkies, the first US jury verdict finding a cheat seller liable for copyright infringement, though that verdict was only $63,210.\[19\]\[20\] Bungie said it spends about $1.25M a year on anti-cheat.\[21\] The pattern: big judgments, weak cross-border enforcement.
- **Kernel anti-cheat.** Riot Vanguard (Valorant), Activision's RICOCHET (2021) and others moved detection into the kernel.\[22\] Cheat makers responded with DMA hardware cheats (a PCIe card reads game memory from a second PC) and input-modding devices such as Cronus and XIM.
- **Emulators and console hacks.** Nintendo v. Yuzu ended in March 2024 with a $2.4M settlement and a shutdown; Nintendo alleged *Tears of the Kingdom* was pirated more than 1 million times before launch.\[23\]\[24\] A Mig Switch seller settled for $2M in 2025.\[25\] On the PS3 (2010–2011), fail0verflow showed that Sony reused a nonce in its ECDSA signing, which allowed the private key to be recovered. George Hotz published the root key, Sony sued, and the case settled in April 2011. The lesson: one cryptographic implementation error can permanently break a platform.
- **Denuvo economics.** Volckmann (UNC, *Entertainment Computing*, 2024) studied 86 Denuvo titles. A very early crack leads to an estimated 20% fall in total revenue; a crack after six weeks costs about 5%; survival past 12 weeks means "nearly zero" loss. Overall, Denuvo protected a mean of 15% (median 20%) of total revenue. In 2026, hypervisor-based bypasses running below Windows (Ring -1) produced day-zero releases (*Crimson Desert*, *Resident Evil Requiem*).\[2\]\[26\] By late April, crack trackers claimed every non-VR Denuvo game was bypassed. Irdeto promised countermeasures; players reported more frequent online checks.\[1\]\[27\] The bypass works not by reversing Denuvo but by lying to it about the hardware, and it requires users to disable Windows security features.\[28\]\[29\]
- **Private servers.** WoW emulators and similar projects reverse the server protocol. Blizzard has pursued legal action, and later monetized the demand itself through WoW Classic.

### Software piracy and licensing
- **Desktop software.** Adobe, Windows activation (KMS emulators), and plugin and DAW cracks are perennial. MUSO measured 14.9 billion visits to software-piracy sites in 2024.\[30\] Patterns that keep working are license checks that run only on the client and keys shared across installs.
- **SaaS.** Bypass shifts to feature flags gated on the client, trial resets, and leaked API keys, which is why server-side entitlement matters.

### Protocols and APIs
- **Beeper Mini (December 2023).** It reverse-engineered iMessage's push and registration protocol, building on research by a 16-year-old, so Android phones could talk to Apple's servers directly. Apple blocked it within three days, citing "fake credentials" and risks of spam and metadata exposure.\[31\]\[32\]\[33\] After several rounds of whack-a-mole (one block hit more than 60% of users), Beeper gave up, and the app was discontinued in 2024.\[34\]\[35\] Lesson: protocol RE succeeds technically, but whoever controls the server and device attestation wins.
- **Twitter/X (2023) and Reddit (2023).** These two cut off or repriced API access and killed third-party clients. Much of the scraping that followed moved to reversed private endpoints.
- **Signal and WhatsApp.** Academic protocol analysis is RE used for verification. It has strengthened trust rather than causing harm.
- **LLM API reverse proxies.** Unofficial ChatGPT and Claude wrappers, plus "routers" reselling stolen or shared keys, let users get around regional and ToS restrictions. OpenAI's February 12, 2026 memo said DeepSeek-linked accounts accessed models "through obfuscated third-party routers and other ways that mask their source."\[36\]\[37\]

### Hardware, embedded and IoT
- **Car keyless relay theft.** Thieves relay a signal between the key fob and the car; this does not require breaking the cryptography.\[38\] Canada (about 90,000 thefts a year, roughly C$1B in losses) announced a ban on the Flipper Zero in February 2024.\[39\]\[40\] Experts and the EFF noted there was no documented theft using one, since rolling codes defeat simple replay.\[40\]\[41\] The government then revisited the ban.\[42\] The real tools are multi-radio relay kits and CAN-injection devices.\[43\]\[44\]
- **John Deere.** Farmers reversed and jailbroke tractor firmware to get around dealer-only diagnostics. The FTC sued in January 2025, and on July 8, 2026 a settlement required Deere to give owners and independent shops dealer-equivalent repair tools for 10 years.\[45\] A separate $99M class settlement came earlier in 2026.\[46\]
- **Printer ink DRM.** Lexmark v. Static Control (2004) held that chip-handshake code was not protected by copyright or the DMCA when it is used for interoperability.
- **Medical devices.** Insulin-pump and pacemaker RE (Barnaby Jack, Billy Rios, and the 2017 Abbott/St. Jude firmware recall) showed that unauthenticated radio protocols are a patient-safety problem. In Digital.ai's data, medical-device apps had the largest single-year jump in attack rate in 2026, from 78% to 86%.\[47\]
- **Chips.** Counterfeit and cloned semiconductors depend on die imaging, decapping and firmware readout. PUFs and secure elements exist to make clones detectable.

### Malware RE as defense
- **Stuxnet (2010).** RE by Symantec, Kaspersky and Ralph Langner uncovered a PLC payload aimed at Iranian centrifuges.
- **WannaCry (May 2017).** Marcus Hutchins found a hardcoded kill-switch domain while reversing the worm. Registering it stopped the spread.
- **NotPetya (2017).** RE showed it was a wiper disguised as ransomware.
- **SolarWinds (2020).** RE of the SUNBURST backdoor in Orion updates.
- **XZ Utils (March 2024).** Andres Freund noticed SSH logins running about 500 ms slow, then traced it to a backdoor planted in the build scripts after a multi-year social-engineering campaign. These cases are the strongest argument that any anti-RE product must not hamper legitimate analysis of the software supply chain.

### Fintech, gig economy, ticketing and commerce
- **Ticketing.** The FTC sued Key Investment Group in August 2025, alleging it used thousands of Ticketmaster accounts, virtual cards and spoofed IPs and phone numbers to buy 379,776 tickets (about $57M) and resell them for about $64M.\[48\] In one example, 49 accounts bought 273 tickets for a Taylor Swift show with a six-ticket limit.\[49\] In April 2026 a court held that the BOTS Act applies to "any person," not only to bots.\[50\] A separate FTC BOTS Act case against Ticketmaster itself survived a motion to dismiss.\[51\]
- **Gig apps.** Ride-hailing and delivery drivers use GPS spoofers and auto-accept bots built from reversed driver apps. Platforms respond with device attestation and anomaly detection.
- **Sneaker, travel and airline bots.** In the Imperva 2025 report, travel was the most-attacked industry (27% of bad-bot attacks; bad bots were 48% of travel-site traffic). Bad bots made up 59% of retail traffic.\[52\]\[53\]

### AI models
- **Distillation via API.** Anthropic said on February 23, 2026 that DeepSeek, Moonshot AI and MiniMax used approximately 24,000 fraudulent accounts and ran more than 16 million exchanges. By lab: MiniMax more than 13M (agentic coding), Moonshot more than 3.4M (agentic reasoning and computer use), DeepSeek more than 150,000 (reasoning and "censorship-safe" rewrites). MiniMax redirected nearly half its traffic to a new Claude model within 24 hours of its release. In September 2026 Anthropic reported disrupting campaigns from seven China-based labs. Two campaigns (attributed to Moonshot and DeepSeek) quietly relayed their own customers' requests to Claude, more than 23M and 12.1M exchanges respectively.\[54\] OpenAI's February 12, 2026 memo said Chinese actors have "moved beyond Chain-of-Thought (CoT) extraction toward more sophisticated, multi-stage pipelines" and rely on "networks of unauthorized resellers."\[37\] The accused labs had not publicly responded in the cited coverage.\[55\]\[56\]
- **Stealing model internals.** Carlini et al. (arXiv 2403.06634, ICML 2024): "For under $20 USD, our attack extracts the entire projection matrix of OpenAI's Ada and Babbage language models". They also recovered gpt-3.5-turbo's hidden dimension and estimated full extraction would cost under $2,000.\[57\] The fix, applied by Google and then by OpenAI on March 3, 2024, was to stop returning logprobs together with logit bias.\[58\]
- **Training-data extraction.** Nasr, Carlini et al. (November 2023) got ChatGPT to "diverge" by asking it to repeat "poem" forever. "Using only $200 USD worth of queries" they extracted more than 10,000 unique memorized training examples.\[59\]\[60\]
- **Weight leaks.** Meta's LLaMA, released under gated access on February 24, 2023, was leaked as a torrent on 4chan on March 3, 2023. Vice called it the first time a major tech firm's proprietary AI model had leaked to the public.\[61\]\[62\]
- **Apple NeuralHash (August 2021).** Asuhariet Ygvar extracted the CSAM-scanning model hidden in iOS 14.3 and rebuilt it in Python. A hash collision was demonstrated within hours. Kenneth White put it this way: "not months or days, but a couple of hours." Apple said the extracted version was not final,\[63\]\[64\] and the CSAM scanning plan was later shelved.
- **System-prompt extraction.** Prompt-injection techniques routinely leak the hidden instructions of GPTs, agents and copilots. For many "AI wrapper" startups, the prompt *is* the IP.

### Corporate and IP landmark cases
- **Sega v. Accolade (9th Cir. 1992)** and **Atari v. Nintendo (Fed. Cir. 1992):** disassembly to achieve interoperability can be fair use. Atari lost in part because it obtained Nintendo's code from the Copyright Office under false pretenses.
- **Compaq (1982–83) and Phoenix BIOS (1984):** clean-room reimplementation, with one team writing a specification and an isolated team writing the code, created the PC-clone industry.
- **Samba:** a reverse-engineered SMB implementation. The 2004 EU Microsoft decision forced Microsoft to share its protocols.
- **Blizzard v. bnetd (8th Cir. 2005):** a EULA ban on RE was enforceable, and the DMCA interoperability exemption did not apply.
- **Lexmark v. Static Control (6th Cir. 2004):** interoperability won.
- **Oracle v. Google (US Supreme Court, 2021):** Google's reimplementation of the Java API declarations was fair use.

### Web and frontend
- **JavaScript obfuscation.** It is routinely reversed with AST tools and, increasingly, with LLMs. Bot-defense scripts from Cloudflare, Akamai, PerimeterX/HUMAN and DataDome are themselves reversed by "solver" services and anti-detect browsers that sell bypass as a service. Imperva found 21% of bot attacks use residential proxies.\[65\]

## 3. Who gets reverse engineered, and why the "Instagram clone" hypothesis is wrong

Attackers almost never want *the whole product*. They want one piece of it that can be monetized:

| What attackers extract | Example |
|---|---|
| Private API and request-signing logic | Instagram and Tinder bots, scrapers, Pokémon Go maps |
| Premium entitlement check | Spotify and YouTube mods, SaaS feature flags |
| Game state and memory layout | Aimbots, ESP/wallhacks |
| Device identity and attestation | Beeper Mini, GPS spoofing, emulator farms |
| Secrets and keys | 815,000 secrets in iOS apps, Stripe and cloud keys |
| Fraud path | Banking trojans, ticket-limit circumvention |
| Model capability or internals | Claude/OpenAI distillation, Carlini projection-matrix theft |
| Firmware and crypto keys | PS3 root key, car immobilizers, Deere diagnostics |

**Industries ranked by RE risk**

| Rank | Industry | Why it is targeted | Data point |
|---|---|---|---|
| 1 | Financial services and fintech | Direct cash-out; overlay and session-hijack fraud | 91% attack rate (Digital.ai 2026);\[66\] 1,243 apps targeted by 34 malware families (Zimperium) |
| 2 | Gaming | Cheats as subscriptions; piracy; virtual economies | $8.5B cheat economy (Intorqa estimate); gaming had the most bad-bot traffic in 2023 (57.2%, Imperva 2024)\[67\] |
| 3 | AI/LLM providers | Capabilities worth billions can be copied via outputs | More than 16M distillation exchanges (Anthropic) |
| 4 | Automotive | Theft, tuning, feature unlocks | 91% attack rate on automotive apps (Digital.ai 2026); about 90,000 thefts a year in Canada\[40\]\[66\] |
| 5 | Ticketing, travel and retail | Scalping, scraping, inventory hoarding | Travel 27% of bad-bot attacks; 379,776 tickets in the KIG case |
| 6 | Streaming and media | Paywall and DRM bypass, modded clients | Gaming and media dominate the Guardsquare/Verimatrix XTD customer base |
| 7 | Healthcare and medical devices | Safety-critical, weak legacy protocols | Medical-device apps rose from 78% to 86% attack rate\[47\] |
| 8 | IoT and consumer hardware | Cloning, repair lock-in, botnets | Counterfeit chips, ink DRM, smart locks |

**Market evidence that protection is going mainstream.** Gartner's 2026 Hype Cycle for Secure Software Engineering puts application shielding on the "Slope of Enlightenment," less than two years from mainstream adoption.\[68\] Back in 2019, Gartner had predicted shielding use would grow from 5% to 30% of enterprises.\[69\] OWASP's MASVS includes a dedicated RESILIENCE category (anti-tampering, anti-static and anti-dynamic analysis, device binding). OWASP treats it as defense-in-depth, not a substitute for secure design.

## 4. Economic impact (quantified where possible)

- **Game cheating:** $8.5B median annual cheat economy (Intorqa/Activision; vendor model, wide confidence interval). An academic floor is $12.8M to $73.2M a year for 80 sites in NA/EU.
- **Game piracy:** an estimated 20% fall in total revenue on a very early crack, and a mean 15% (median 20%) of total revenue protected by Denuvo (Volckmann 2024).
- **Bots:** in 2024, 51% of web traffic was automated and 37% was bad bots (Imperva 2025, based on 13 trillion blocked requests). 44% of advanced bot traffic hit APIs.\[52\]\[70\]
- **Banking fraud:** malware-driven fraudulent transactions on Android rose 67% year over year. One in 20 verification attempts in financial services is fraudulent (Zimperium 2026).\[7\]\[71\]
- **Ticket scalping:** about $7M gross margin in one broker's alleged scheme over just over a year ($57M bought, $64M resold).\[48\]
- **Car theft:** about C$1B a year in Canada.\[40\]
- **AI distillation:** no public dollar estimate exists. The leading labs' implied loss is training spend in the billions that competitors avoid. Treat any figure here as speculative.
- **Legal costs and recoveries:** $14.47M (Activision v. EngineOwning), $13.5M (Bungie), $2.4M (Yuzu), $2M (Mig Switch).\[16\]\[25\]\[72\]\[73\] Many judgments go uncollected.

## 5. Defenses: what works, what breaks, what it costs

| Technique | Protects against | Effectiveness in practice | Known weaknesses (conceptual) | Costs / tradeoffs |
|---|---|---|---|---|
| Name obfuscation (ProGuard/R8) | Casual static reading | Low; baseline only | Structure and strings remain; LLMs rename symbols well | Free, negligible overhead |
| Commercial obfuscation (DexGuard, iXGuard, O-LLVM, Tigress) | Static RE, automated patching | Medium; raises cost from hours to days or weeks | Control-flow flattening can be undone with symbolic execution and LLMs | Licensing cost, build complexity, crash debugging |
| Virtualization packers (VMProtect, Themida) | Desktop binary RE | High per function | Devirtualization tools exist; performance cost limits coverage | 10–100x slowdown on virtualized code |
| Anti-debug, anti-hook, root/jailbreak detection | Frida and debugger-based analysis | Medium; frequent cat-and-mouse | Checks themselves get hooked; root hiders (Magisk modules) | False positives on custom ROMs; user complaints |
| RASP / in-app shielding (Promon, Appdome, Digital.ai, Guardsquare) | Runtime tampering, overlays, repackaging | Medium–high when combined with telemetry | Kernel- or hypervisor-level attackers sit below it | Cost, app size, need to update quickly |
| White-box cryptography | Key extraction from the client | Medium; academic breaks are common | Differential computation analysis; key lifting | Performance; still needs key rotation |
| App/device attestation (Play Integrity, App Attest) | Emulators, modified apps, bot farms | High for strong (hardware-backed) verdicts | Leaked keyboxes and spoofed basic verdicts; excludes some legitimate devices | Ties you to Google and Apple; quotas; harms de-Googled users |
| Certificate pinning | MITM protocol RE | Low–medium | Trivially hooked on rooted devices | Operational risk during certificate rotation |
| Server-side logic and entitlement | Feature unlocks, cheats on state | Highest; you cannot patch what is not shipped | Latency, cost; not possible offline | Architectural change |
| DRM (Widevine L1, Denuvo) | Piracy during launch window | High for weeks, then decays; Denuvo fell to hypervisor bypass in 2026 | Hardware lies (hypervisor), key leaks | Performance complaints, online checks, licensing fees |
| Kernel anti-cheat (Vanguard, RICOCHET, EAC) | Memory-reading cheats | Medium–high | DMA hardware, input-modding devices, hypervisors | Privacy and security risk of ring-0 code; Linux/Steam Deck exclusion |
| Hardware roots (TEE, Secure Enclave, TPM, PUF, secure elements) | Key theft, cloning | Highest | Fault injection, side channels, implementation bugs (PS3 nonce) | BOM cost, design lock-in |
| Bot management (Cloudflare, Akamai, HUMAN, DataDome, Imperva) | Scraping, credential stuffing, scalping | Medium–high | Solver services, residential proxies (21% of attacks), real humans in click farms | False positives, CAPTCHA friction |
| API protection (Approov-style app-to-API attestation, signed requests, rate limits) | Private-API abuse | High when the token is bound to attested app instances | Hooking the genuine app inside a device farm | Integration effort |
| LLM anti-distillation (classifiers, behavioral fingerprinting, KYC, logprob limits, output watermarking) | Distillation, extraction | Early stage; Anthropic detected campaigns *after* millions of exchanges | Proxy and reseller networks (Anthropic saw a single proxy network managing more than 20,000 fraudulent accounts simultaneously), paraphrasing to remove watermarks | Friction for legitimate researchers and small developers |
| Legal (DMCA 1201, CFAA, ToS, BOTS Act) | Commercial cheat, crack and scalper operations | Strong against US entities; weak abroad | Default judgments go unpaid; defendants change hands | Expensive, slow |

**Key takeaway.** Every client-side control is eventually bypassed. The winning pattern is (1) move secrets and decisions to the server, (2) bind requests to an attested, untampered app instance, (3) detect at runtime and send telemetry home, and (4) update protections without waiting for an app-store release. Appdome's "Live Update" and Digital.ai's emphasis on monitoring reflect this.\[74\]

## 6. Market landscape

- **Mobile and in-app protection.** Guardsquare (Leuven) acquired Verimatrix's XTD unit in December 2025 for $8.5M. That added about 60 customers, including Crédit Agricole and Deutsche Bank, and brought it to roughly €40M ARR across more than 1,000 customers and 6 billion app users; Verdane invested in 2025.\[75\]\[76\]\[77\]\[78\] Other players: Promon (Norway, PE-backed), Appdome (about $40M raised, no-code "fusion" protection),\[79\]\[80\] Digital.ai (the former Arxan), Zimperium (MTD plus app protection), Approov (API attestation), Jscrambler (JavaScript), and OneSpan.\[81\]\[82\]
- **Games and media.** Irdeto/Denuvo, Easy Anti-Cheat and BattlEye, in-house systems (Vanguard, RICOCHET), Anybrain (AI behavioral anti-cheat), and Intorqa (cheat-market intelligence).
- **Bots and API.** Cloudflare, Akamai, HUMAN (merged with PerimeterX in 2022), DataDome, Imperva (Thales), and Kasada.
- **Market size (low confidence).** Analyst estimates vary widely: in-app protection at $2.1B in 2025 rising to $7.2B by 2034 (18% CAGR, CMI); application shielding at $1.8B–$2.6B; RASP at $2.16B (MRFR).\[83\]\[84\]\[85\]\[86\] These come from paid-report vendors with inconsistent definitions. Use them only as "a low single-digit-billion market growing in the high teens."

**Gaps and underserved areas**
1. **LLM/agent API protection.** Today's distillation defense is in-house at frontier labs. Thousands of mid-tier model providers, fine-tune hosts and AI SaaS companies (whose prompts, RAG data and tool chains are their IP) have no off-the-shelf "distillation WAF." Neither do MCP servers exposed to agents.
2. **Small developers and AI-generated apps.** Vibe-coded apps ship with keys embedded in the client. Enterprise shielding pricing excludes indie developers, and a secrets scanner plus a key proxy plus attestation at self-serve prices is largely missing.
3. **Defense against AI-assisted RE.** Obfuscation was tuned to slow humans. Few products measure or harden against LLM decompilation and deobfuscation.
4. **Post-release, update-free response.** Attacks begin within hours (one Digital.ai customer saw an attack 1 hour 56 minutes after publication), while app-store release cycles take days.\[87\]
5. **Hardware-level evasion.** Hypervisor and DMA attacks now defeat ring-0 defenses. Cloud-verified, hardware-attested gameplay and DRM is an open problem.

## 7. Emerging trends 2024–2026

- **LLM decompilation.** LLM4Decompile (EMNLP 2024) beat GPT-4o and Ghidra by more than 100% in re-executability. Its v2 9B model reached 64.9% re-executable output.\[88\]\[89\] SK2Decompile (2025) reached about 69% on HumanEval and about 60% on MBPP.\[90\] Decompile-Bench released a million binary–source function pairs. Caveat: these are function-level benchmarks on unobfuscated code, and real obfuscated binaries remain much harder.
- **Autonomous vulnerability discovery.** Google's Big Sleep found an exploitable SQLite bug in November 2024, then CVE-2025-6965, which Google said was known only to threat actors, and 20 more vulnerabilities by August 2025.\[91\]\[92\] In the DARPA AIxCC finals (DEF CON 33, August 2025), seven teams processed 54M lines of code, patched 43 of 54 synthetic bugs and found 18 real zero-days. The average cost per task was $152. XBOW reportedly topped HackerOne's US leaderboard.\[93\]
- **Attacker–defender balance.** AI helps both sides, but it helps attackers of *shipped client code* more. Defenders can patch their servers, but they cannot recall binaries already sitting on devices. Expect iOS and Android attack parity (86% vs 89% in 2026), shorter crack windows, and a premium on server-side and attestation-centric designs.\[47\]
- **Regulation.** The EU Cyber Resilience Act (in force since December 2024; reporting obligations from September 2026, full application December 2027) requires products with digital elements to be secure by design and to handle vulnerabilities. That increases demand for both protection and legitimate RE testing. The DMA requires gatekeepers to provide interoperability, which is the regulatory version of what Beeper tried to force by RE. Right-to-repair laws (in US states, the FTC–Deere order, and the EU Right to Repair Directive) are steadily legitimizing RE for repair and making parts-pairing lock-in harder to defend.

## 8. Legal landscape

- **US DMCA §1201.** It prohibits circumventing access controls and trafficking in circumvention tools. This is the main weapon against cheat sellers (EngineOwning, AimJunkies) and console hacks (Yuzu, Mig Switch). The Copyright Office's triennial exemptions cover security research, repair and some preservation. §1201(f) provides a narrow interoperability exception, which Blizzard v. bnetd held did not save that project.
- **Copyright and fair use.** Sega, Atari, Sony v. Connectix (2000) and Oracle v. Google support intermediate copying for interoperability.
- **Contracts and ToS.** EULA bans on RE are often enforceable in the US (Bowers v. Baystate, bnetd). Unlike the EU, the US has no statutory override.
- **EU Software Directive 2009/24/EC, Art. 6.** It permits decompilation for interoperability, and contract terms cannot override it. Art. 5(3) allows observing and testing a program's behavior. The Trade Secrets Directive (2016/943) treats lawful RE as a legitimate means of acquiring a trade secret.
- **CFAA.** In *Van Buren v. United States* (2021) the Supreme Court read "exceeds authorized access" narrowly, as a gates-up-or-down test. In *hiQ v. LinkedIn* (9th Cir. 2022), scraping public data was likely not "without authorization" under the CFAA, but hiQ later lost on breach of contract and settled. Scraping risk has therefore shifted toward contract, copyright and anti-circumvention claims.
- **BOTS Act (2016).** It was revived in 2025–2026 (the KIG case, the Ticketmaster case, DOJ v. REPS) and interpreted to cover humans using circumvention tools, not only bots.\[49\]\[50\]
- **AI distillation.** No statute squarely prohibits it. The available routes are ToS breach, the CFAA (fraudulent accounts), trade secret law, and export-control politics, which Anthropic and OpenAI explicitly invoke.\[56\]\[94\] Expect legislative activity.

## 9. Hackathon pitch: stories, stats and product angles

**Most compelling stories**
1. *"24,000 fake accounts, 16 million questions."* Chinese labs distilled Claude, and MiniMax pivoted to a new model within 24 hours of its launch.\[95\]\[96\]
2. *"$20 to steal part of GPT."* Carlini's projection-matrix extraction.\[57\]
3. *"Hours, not months."* NeuralHash collided within hours of extraction, and a banking app was attacked 1 hour 56 minutes after publication.\[87\]
4. *"The DRM that fell."* Denuvo protected about 20% of launch revenue for a decade, until a 2026 hypervisor trick cracked everything on day zero.
5. *"Cheating is bigger than esports."* An $8.5B cheat economy against $5.1B in esports revenue.\[97\]
6. *"Nobody clones Instagram, they rent its API."* Bots, scalpers (379,776 tickets) and bank trojans inside genuine apps.

**Ten stats for slides:** 87% of apps attacked (Digital.ai 2026);\[98\] 51% of web traffic is bots and 37% bad bots (Imperva 2025); 44% of advanced bot traffic targets APIs; 71% of iOS apps leak secrets (Cybernews); 1,243 financial apps targeted, banking trojans up 56% (Zimperium 2026); 20% revenue loss on a week-one crack (Volckmann 2024); $8.5B cheat economy; 16M+ distillation exchanges (Anthropic); a $14.47M judgment that EngineOwning ignored; $152 per AI vulnerability task (AIxCC).

**Where a new product could add value (ranked by our judgment)**
1. **A "distillation and abuse firewall" for AI APIs, agents and MCP servers.** It would sit in front of any model or agent endpoint and combine account-graph clustering (to catch hydra accounts), capability-coverage detection (systematic sweeps through capability space rather than real tasks), chain-of-thought and logprob exposure controls, per-tenant canary and watermark outputs, and proxy/reseller detection. The buyers would be the many AI companies without Anthropic-scale trust-and-safety teams. *This is the most timely and least crowded option.*
2. **Self-serve "secrets and API shield" for indie and AI-generated apps.** It would scan the build for hardcoded keys, replace them with a short-lived token proxy bound to App Attest or Play Integrity, and add one-click baseline obfuscation. It is priced for startups, framed as "Approov plus GitGuardian for vibe-coders."
3. **LLM-resistance scoring for obfuscation.** It would run LLM decompilers and deobfuscators against a customer's build and report how much was recovered. Think of it as a "pen test by AI" metric. It can be sold to shielding vendors or used to market your own hardening.
4. **Server-authoritative entitlement-as-a-service.** It would move premium checks and feature flags out of the client, so modded clients get nothing.

**Positioning advice.** Do not pitch "uncrackable." The evidence (Denuvo, PS3, Vanguard workarounds, Beeper) shows every client control falls eventually. Pitch *time-to-bypass*, *detection and telemetry*, and *server-side binding*, and measure success as attacker cost and how fast you respond.

## Caveats
- Vendor reports (Digital.ai, Zimperium, Imperva, Intorqa, Anybrain) draw on their own customers' telemetry or commissioned surveys. They have selection bias and a commercial interest in alarming numbers. The $8.5B cheat figure in particular is a model with a 95% interval of $5.1B to $13.8B covering only 15 games.\[99\]
- The distillation allegations are made by interested parties (Anthropic, OpenAI) in a policy context (export controls). The accused labs had not responded in the cited coverage, and the claims have not been tested in court.
- Market-size figures from paid-report publishers are inconsistent and low-confidence.
- LLM-decompilation benchmarks measure small, unobfuscated functions. Real-world gains against commercial obfuscation are not yet well measured.
- Some 2026 items (Denuvo's status, the Ticketmaster BOTS Act case, Anthropic's September disclosure) are still developing.
- This report describes techniques conceptually, for defensive and educational purposes only.

## Sources

1. [Denuvo dealt major blow as crackers claim all non-VR games with the anti-tamper have been bypassed](https://www.pcgamesn.com/drm/denuvo-hypervisor-bypass-all-non-vr-games)
2. [Denuvo](https://en.wikipedia.org/wiki/Denuvo)
3. [Decompile-Bench: Million-Scale Binary-Source Function Pairs for Real-World Binary Decompilation](https://arxiv.org/pdf/2505.12668)
4. [Agentic AI Is Accelerating How Software Gets Built and How It Gets Attacked. Most Enterprises Are Only Ready for One, According to Digital.ai’s 2026 AppSec Threat Report](https://www.businesswire.com/news/home/20260519967565/en/Agentic-AI-Is-Accelerating-How-Software-Gets-Built-and-How-It-Gets-Attacked.-Most-Enterprises-Are-Only-Ready-for-One-According-to-Digital.ais-2026-AppSec-Threat-Report)
5. [AI Helps Port Switch Games Natively to Apple TV](https://technology.org/2026/11/07/tvport-switch-games-apple-tv-4k-native-ai-claude)
6. [Developer uses AI to run Nintendo Switch games natively on Apple TV - Archynewsy](https://archynewsy.com/developer-uses-ai-to-run-nintendo-switch-games-natively-on-apple-tv)
7. [New Zimperium Report Finds Banking Malware Expands Global Reach, Targeting 1,200+ Financial Apps](https://www.morningstar.com/news/pr-newswire/20260319ny13849/new-zimperium-report-finds-banking-malware-expands-global-reach-targeting-1200-financial-apps)
8. [Mobile Security for Modern Banking - Zimperium](https://zimperium.com/industry/finance/banking)
9. [Research unveils that more than 110,000 Apple iOS apps leak secrets](https://cybernews.com/security/ios-apps-leak-hardcoded-secrets-research/)
10. [Cybernews Study Reveals 71% of iOS Apps Leak Sensitive Data](https://www.ravepubs.com/ios-apps-data-leaks-cybernews-study/)
11. [Thousands of iOS apps found to expose user data](https://www.techradar.com/pro/security/thousands-of-ios-apps-found-to-expose-user-data-and-leak-stripe-keys)
12. [Study: Sellers of gaming cheats in North America and Europe earn up to \$73.2 million a year](https://wnhub.io/news/analytics/item-48509)
13. [Video game cheating has grown into an \$8.5 billion-a-year industry, and one cheat dev made \$77 million alone](https://www.tweaktown.com/news/113706/video-game-cheating-has-grown-into-an-dollars8-5-billion-a-year-industry-and-one-cheat-dev-made-dollars77-million-alone/index.html)
14. [Cheating costs games studios revenue, survey finds](https://securitybrief.co.uk/story/cheating-costs-games-studios-revenue-survey-finds)
15. [Over half of game developers have lost players or revenue to cheating, new report finds](https://gamesbeat.com/over-half-of-game-developers-have-lost-players-or-revenue-to-cheating/)
16. [Activision awarded \$14.5 million in lawsuit against Call of Duty cheat maker](https://www.techspot.com/news/103206-activision-awarded-over-145-million-lawsuit-against-call.html)
17. [Activision Wins \$14.5m Judgment After EngineOwning Cheat Makers Bailed Out \* TorrentFreak](https://torrentfreak.com/activision-wins-14-5m-judgment-after-engineowning-cheat-makers-bailed-out-240529/)
18. [Cheaters Never Prosper: Judge Awards Activision \$14.5 Million In 'Call of Duty' Cheating Lawsuit](https://hiphopwired.com/playlist/activision-call-of-duty-cheat-engineowning-lawsuit/)
19. [Activision Wins \$14.5 Million In A Call Of Duty Cheating Lawsuit](https://clutchpoints.com/gaming/activision-wins-call-of-duty-cheating-lawsuit)
20. [Founded Year](https://www.cbinsights.com/company/phoenix-digital)
21. [Lawsuits suggest some video game cheating could be illegal](https://www.axios.com/2022/12/16/video-game-cheating-lawsuits)
22. [Activision files lawsuit against cheat provider EngineOwning for \$800 million](https://sportskeeda.com/esports/news-activision-files-800-million-lawsuit-engineowning)
23. [Switch emulator Yuzu reaches \$2.4 million settlement with Nintendo](https://www.gamedeveloper.com/business/switch-emulator-yuzu-reaches-2-4-million-settlement-with-nintendo)
24. [Nintendo and Yuzu reach settlement, Yuzu to pay \$2.4 million](https://nintendoeverything.com/nintendo-and-yuzu-reach-settlement-yuzu-to-pay-2-4-million/)
25. [Notebookcheck Logo](https://www.notebookcheck.net/Nintendo-lawsuit-ends-in-2-million-settlement-against-Mig-Switch-seller-accused-of-aiding-piracy.1107589.0.html)
26. [Denuvo tombe en quelques heures grâce aux hyperviseurs](https://korben.info/en/denuvo-falls-in-hours-hypervisor-bypass.html)
27. [Denuvo Responds to Day-Zero DRM Hypervisor Crack: "We're Already Working on Updated Security Versions"](https://www.techpowerup.com/348609/denuvo-responds-to-day-zero-drm-hypervisor-crack-were-already-working-on-updated-security-versions)
28. [Denuvo has been cracked, company promises countermeasures against new DRM bypasses — zero-day game releases become norm as security concerns mount over hypervisor-based bypass](https://tech.yahoo.com/gaming/articles/denuvo-broken-company-promises-countermeasures-154146577.html)
29. [Denuvo Has Been Broken: Hypervisor Bypasses Enable Day-Zero Cracks, Irdeto Promises a Fix](https://www.thefpsreview.com/2026/04/03/denuvo-has-been-broken-hypervisor-bypasses-enable-day-zero-cracks-irdeto-promises-a-fix/)
30. [Video Game Piracy Statistics 2026: Data & Losses](https://www.shanethegamer.com/research/video-game-piracy-analysis/)
31. [Apple blocks message sending and receiving from the app 'Beeper Mini' that allows you to use iMessage on Android - GIGAZINE](https://gigazine.net/gsc_news/en/20231211-apple-beeper-mini-blocked/)
32. [Apple confirms it blocked Beeper Mini from its iMessage service citing security risks](https://macdailynews.com/2023/12/11/apple-confirms-it-blocked-beeper-mini-from-its-imessage-service-citing-security-risks/)
33. [Apple blocks Beeper Mini, the Android iMessage app that actually worked](https://www.idownloadblog.com/2023/12/11/apple-shuts-down-beeper-mini-imessage-app/)
34. [Beeper Mini and Cloud's iMessage gets blocked by Apple again](https://9to5google.com/2023/12/17/beeper-imessage-blocked-apple-again/)
35. [Beeper (software)](<https://en.wikipedia.org/wiki/Beeper_(software)>)
36. [OpenAI accuses DeepSeek of malpractice ahead of AI launch - Rest of World](https://restofworld.org/2026/openai-deepseek-distillation-dispute-us-china/)
37. <https://cdn.openai.com/pdf/045aa967-ee96-4a09-94ee-3098ddf6db2c/OpenAI-US-House-Select-Cmte-Update-%5B021226%5D.pdf>
38. [Feds Want to Ban the World’s Cutest Hacking Device. Experts Say It's a ‘Scapegoat’](https://www.vice.com/en/article/flipper-zero-ban-canada-hacking-car-thefts/)
39. [Our Response to the Canadian Government - Flipper Blog](https://blog.flipper.net/response-to-canadian-government/)
40. [Canada to ban the Flipper Zero to stop surge in car thefts](https://www.bleepingcomputer.com/news/security/canada-to-ban-the-flipper-zero-to-stop-surge-in-car-thefts/)
41. [Restricting Flipper is a Zero Accountability Approach to Security: Canadian Government Response to Car Hacking](https://www.eff.org/deeplinks/2024/03/restricting-flipper-zero-accountability-approach-security-canadian-government)
42. [Canada revisits decision to ban Flipper Zero](https://www.malwarebytes.com/blog/news/2024/03/canada-revisits-decision-to-ban-flipper-zero)
43. [The Government of Canada Seeks to Ban the Flipper Zero, SDR Dongles Over Car Theft Fears - Hackster.io](https://www.hackster.io/news/the-government-of-canada-seeks-to-ban-the-flipper-zero-sdr-dongles-over-car-theft-fears-2a30c3a13f65.amp)
44. [Flipper Zero makers respond to Canada’s ‘harmful’ ban proposal](https://www.bleepingcomputer.com/news/security/flipper-zero-makers-respond-to-canadas-harmful-ban-proposal/)
45. [The FTC's Deere Settlement Puts Right to Repair on a New Footing](https://sigmalawgroup.com/blog/2026-07-22-ftc-deere-right-to-repair/)
46. [FTC Settlement Secures Right to Repair for Farmers - Farm Policy News](https://farmpolicynews.illinois.edu/2026/07/ftc-settlement-secures-right-to-repair-for-farmers/)
47. [Agentic AI Is Accelerating How Software Gets Built and How It Gets Attacked. Most Enterprises Are Only Ready for One, According to Digital.ai’s 2026 AppSec Threat Report](https://digital.ai/press-releases/agentic-ai-appsec-threat-report-2026/)
48. [FTC Sues Ticket Reseller Who Asked Courts To Stop BOTS Act Enforcement - Pollstar News](https://news.pollstar.com/2025/08/18/ftc-sues-ticket-reseller-who-asked-courts-to-stop-bots-act-enforcement/)
49. [The Spigot Shuts Off: The Feds may finally be coming for the cheaters. What's next in ticket resale](https://tonyknopp.substack.com/p/the-spigot-shuts-off-the-feds-may)
50. [BOTS Act Case Proceeds as Federal Judge Denies Dismissal Push](https://www.digitalmusicnews.com/2026/04/30/bots-act-case-continues/)
51. [Ticketmaster Must Face FTC Ticket Resale Lawsuit as Judge Says BOTS Act Applies](https://www.billboard.com/pro/ticketmaster-face-ftc-ticket-resale-lawsuit-bots-act/)
52. [2025 Imperva Bad Bot Report: How AI is Supercharging the Bot Threat](https://www.imperva.com/blog/2025-imperva-bad-bot-report-how-ai-is-supercharging-the-bot-threat/)
53. [Bots now account for over half of all internet traffic](https://www.techradar.com/pro/security/bots-now-account-for-over-half-of-all-internet-traffic)
54. [Anthropic Says Seven China-Based AI Labs Ran Industrial-Scale Claude Distillation Attacks](https://thehackernews.com/2026/09/anthropic-says-seven-china-based-ai.html)
55. [Anthropic accuses DeepSeek, Moonshot and MiniMax of distillation attacks on Claude](https://www.cnbc.com/2026/02/24/anthropic-openai-china-firms-distillation-deepseek.html)
56. [Anthropic accuses Chinese AI labs of mining Claude as US debates AI chip exports](https://techcrunch.com/2026/02/23/anthropic-accuses-chinese-ai-labs-of-mining-claude-as-us-debates-ai-chip-exports/)
57. [Stealing Part of a Production Language Model](https://arxiv.org/abs/2403.06634)
58. [Stealing Part of a Production Language Model](https://not-just-memorization.github.io/partial-model-stealing.html)
59. [Scalable Extraction of Training Data from (Production) Language Models](https://arxiv.org/abs/2311.17035)
60. [Scalable Extraction of Training Data from (Production) Language Models](https://arxiv.org/pdf/2311.17035)
61. [Meta Llama Weights Leak February 2023: When a Closed-Access Foundation Model Became Effectively Open in Seven Days](https://decipheru.com/ai/decipher-files/meta-llama-weights-leak-2023)
62. [Facebook's Powerful Large Language Model Leaks Online - Slashdot](https://m.slashdot.org/story/411623)
63. [Apple Says NeuralHash Tech Impacted by 'Hash Collisions' Is Not the Version Used for CSAM Detection - MacRumors](https://www.macrumors.com/2021/08/18/apple-explains-neuralhash-collisions-not-csam-system/)
64. [Apple's CSAM detection tech is under fire — again](https://techcrunch.com/2021/08/18/apples-csam-detection-tech-is-under-fire-again/)
65. [AI Bots Overtake the Web: Imperva 2025 Bad Bot Report](https://cpl.thalesgroup.com/blog/access-management/ai-bots-internet-traffic-imperva-2025-report)
66. [2026 Application Security Threat Report — Digital.ai](https://cybersecuritystats.com/reports/digital-ai/2026-application-security-threat-report)
67. [Bad bots made up almost a third of all internet traffic last year](https://www.techradar.com/pro/security/bad-bots-made-up-almost-a-third-of-all-internet-traffic-last-year)
68. [Application Shieldin is placed in the Slope of Enlightenment in the 2026 Gartner® Hype Cycle™ for Secure Software Engineering](https://promon.io/security-news/application-shielding-moves-toward-mainstream-adoption-in-gartner-hype-cycle-for-secure-software-engineering-2026)
69. [Gartner Market Guide for Application Shielding Q12019](https://www.bankinfosecurity.com/whitepapers/gartner-market-guide-for-application-shielding-w-5285)
70. [AI-Driven Bots Surpass Human Traffic - Bad Bot Report 2025](https://cpl.thalesgroup.com/about-us/newsroom/2025-imperva-bad-bot-report-ai-internet-traffic)
71. [Financial Brands Targeted in Global Mobile Banking Malware Surge - Infosecurity Magazine](https://www.infosecurity-magazine.com/news/financial-brands-mobile-banking/)
72. [Nintendo settles lawsuit with Yuzu emulator creators for \$2.4 million, 3DS emulator Citra also affected](https://www.theouterhaven.net/2024/03/nintendo-settles-lawsuit-with-yuzu-emulator-creators-for-2-4-million/)
73. [Activision wins \$14.5 million lawsuit against ‘Aimbot’ cheat maker Technology - HUM News](https://humenglish.com/technology/activision-wins-aimbot-lawsuit/)
74. [Appdome Achieves Funding for Disruptive Mobile App Security SaaS Technology - Appdome](https://www.appdome.com/press-release/appdome-achieves-funding-for-disruptive-mobile-app-security-saas-technology/)
75. [Guardsquare Acquires Verimatrix XTD to Fortify Mobile App Security - BriefGlance.com](https://briefglance.com/articles/guardsquare-acquires-verimatrix-xtd-to-fortify-mobile-app-security)
76. [Guardsquare - Crunchbase Company Profile & Funding](https://www.crunchbase.com/organization/guardsquare)
77. [Guardsquare](https://en.wikipedia.org/wiki/Guardsquare)
78. [Guardsquare does first major acquisition](https://www.leuvenmindgate.be/news/guardsquare-does-first-major-acquisition)
79. [GuardSquare - 2026 Company Profile, Team, Funding, Competitors & Financials - Tracxn](https://tracxn.com/d/companies/guardsquare/__yq7x-lioUOpvLVfWRc1FauMm3CsspcwVKV712QM5ZUE)
80. [Promon - 2026 Company Profile, Team, Funding, Competitors & Financials - Tracxn](https://tracxn.com/d/companies/promon/__JOYnpGwt2zaAJ1wN3XHDZLzEUdB8IRl8lWUz33rofR4)
81. [Appdome - 2026 Company Profile, Team, Funding & Competitors - Tracxn](https://tracxn.com/d/companies/appdome/__WMQhAsItmu4rAW9AER-CXIiwWrMrWVEjwHnWMNYRAcw)
82. [Appdome 2026 Company Profile: Valuation, Funding & Investors](https://pitchbook.com/profiles/company/58775-23)
83. [Runtime Application Self-Protection Market Share, Size, Trends](https://www.marketresearchfuture.com/reports/runtime-application-self-protection-market-1536)
84. [Global In-App Protection Market Size, Share 2025-2034 - CMI](https://www.custommarketinsights.com/report/in-app-protection-market/)
85. [Application Shielding Software Market](https://www.wiseguyreports.com/reports/application-shielding-software-market)
86. [Global Application Shielding Software Market Size, Share, Growth Trends & Forecast 2026-2034](https://www.verifiedmarketreports.com/product/application-shielding-software-market/)
87. [AI-Driven Mobile Attacks Hit New Record: Apps Compromised Within…](https://deafnews.it/en/news/cybersecurity/ai-driven-mobile-attacks-hit-new-record-apps-compromised-within-two-hours-of-release)
88. [Decompiling Binary Code with Large Language Models](https://aclanthology.org/2024.emnlp-main.203.pdf)
89. [GitHub - albertan017/LLM4Decompile: Reverse Engineering: Decompiling Binary Code with Large Language Models · GitHub](https://github.com/albertan017/LLM4Decompile)
90. [SK2Decompile: LLM-based Two-Phase Binary Decompilation from Skeleton to Skin](https://arxiv.org/pdf/2509.22114)
91. [Google’s latest AI security announcements](https://blog.google/innovation-and-ai/technology/safety-security/cybersecurity-updates-summer-2025/)
92. [Google reports Big Sleep found and reproduced 20 vulnerabilities in open-source projects](https://agentic-cyber-explorer.pages.dev/events/google-big-sleep-20-vulnerabilities-2025/)
93. [Security Highlight: AIxCC 2025 - What It Means for Device Security](https://www.keysight.com/blogs/en/tech/nwvs/2025/08/25/aixcc2025-what-it-means-for-device-security)
94. [The Honorable Michael Kratsios](https://ari.us/wp-content/uploads/2026/04/Letter-Re-Memorandum-on-Adversarial-Distillation.pdf)
95. [Anthropic on X: "We’ve identified industrial-scale distillation attacks on our models by DeepSeek, Moonshot AI, and MiniMax. These labs created over 24,000 fraudulent accounts and generated over 16 million exchanges with Claude, extracting its capabilities to train and improve their own models." / X](https://x.com/AnthropicAI/status/2025997928242811253)
96. [The Attack That Looked Like Nothing at All: Anthropic's Distillation Breach Breakdown](https://treblle.com/blog/anthropic-distillation-breach-breakdown)
97. [Video game cheat economy grows into USD \$8.5bn giant](https://securitybrief.co.uk/story/video-game-cheat-economy-grows-into-usd-8-5bn-giant)
98. [87 percent of enterprise mobile apps are under attack - BetaNews](https://betanews.com/article/87-percent-of-enterprise-mobile-apps-are-under-attack/)
99. [Cheating in video games represents an industry worth \$8,5 billion per year.](https://en.univers-simu.com/news/triche-jeux-video-industrie-85-milliards-dollars-an-129046/)
