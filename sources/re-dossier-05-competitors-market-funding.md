---
type: source
title: "Competitive, market, funding and compliance dossier for AI-resistant code protection (Nov 2026)"
date: 2026-11-07
by: tea+claude
url:
tags: [market, regulation, security]
sources: [https://promon.io/security-news/app-threat-report-2026-q1-the-state-of-code-obfuscation-against-ai, https://cpl.thalesgroup.com/about-us/newsroom/sentinel-envelope-plus-ai-reverse-engineering-protection, https://support.preemptive.com/hc/en-us/articles/31784634997137-Changelog, https://mas.owasp.org/MASVS/controls/MASVS-RESILIENCE-2/, https://siliconangle.com/2025/04/28/palo-alto-networks-buys-protect-ai-reported-500m-debuts-new-cybersecurity-tools/]
---

Research module 05 of the six behind [[re-defense-dossier]], written by tea+claude on 2026-11-07. Filed verbatim; it was first drafted as a note, but it holds many claims, so it is a source until those claims are split into notes. Original path: `research_notes/AI reverse engineering defense dossier/05-competitors-market-funding.md`.
Open questions: [[code-protection-field-open-questions]], [[do-people-need-ai-resistant-code-protection]].

# Competitive, Market, Funding & Compliance Landscape — AI-Resistant Code Protection (dossier module 05)

> Scope note: This module EXTENDS, and does not repeat, the two existing team files
> (`AI_RE_Benchmark_Hackathon_Summary.md` §4–5 and the source pack §5/"why now"). Those
> already cover Thales/Promon/Jscrambler/Digital.ai/Guardsquare/Appdome/Verimatrix/Quarkslab
> *claims* and the measured obfuscation-vs-LLM numbers. New here: (a) verified market figures
> with firm names + dates + confidence, (b) funding/M&A deal mechanics with prices, (c) the
> compliance stack that forces purchase, (d) under-covered vendors (PreEmptive/Dotfuscator,
> PyArmor, ionCube, Zimperium, Irdeto), (e) a sharpened verdict on the wedge, and (f) the
> data-obfuscation adjacency flagged as a separate market.

---

## Q1. What each vendor claims in 2026, and their technical approach (depth to build ON TOP of)

### Takeaway
Every shielding vendor now markets "AI/LLM resistance," but the published technical substance
is thin: only Thales and Promon publish measured numbers (both narrow), and the actual
techniques cluster into five reusable primitives — polymorphism, white-box crypto, string
encryption, runtime integrity/RASP sensors, and anti-decompilation. The new 2026 detail is
**PreEmptive/Dotfuscator shipping explicitly named "AI-Resistant String Encryption"** as a
versioned product feature, which no prior team note captured.

### Cited Findings
- **PreEmptive / Dotfuscator (NEW, under-covered):** shipped AI-resistance as dated product features in 2026 — v7.7.0 (26 May 2026) opt-in early-access "upgraded String Encryption ... including AI-driven attacks"; v7.8.0 (27 Jul 2026) "stronger String Encryption protection against reverse engineering and AI-driven attacks"; v7.9.0 (16 Sep 2026) lets users "enable AI-Resistant String Encryption and Tamper Check simultaneously." Product line: Dotfuscator (.NET/Xamarin), DashO (Java/Android), JSDefender (JS); multi-layer = obfuscation + encryption + root detection + shielding + tamper-proofing "against exploitation by both humans and machines." — [PreEmptive Changelog](https://support.preemptive.com/hc/en-us/articles/31784634997137-Changelog)
- **Thales – Sentinel Envelope Plus** (announced 1 Oct 2026): hardens compiled apps "against AI-assisted reverse engineering, automated zero-day vulnerability discovery, and automated exploit generation," no source changes. Only vendor publishing a cost-to-break frame (Opus 4.7 agent: 8/10 vulns unprotected in ~3m10s vs 0/10 protected at 970× tokens / 3h43m). Vendor-run, single model, own app. — [Thales newsroom](https://cpl.thalesgroup.com/about-us/newsroom/sentinel-envelope-plus-ai-reverse-engineering-protection)
- **Promon – ATR Q1 2026 / PDB-LLM:** the one rigorous public benchmark, but it measures OLLVM (not Promon's own product), zero-shot, 10 models. Clean ARM asm avg success 63.7%; three-pass OLLVM (SUB+FLA+BCF) → 8.5%; 2.4× x86-vs-ARM gap; pseudocode gives 2–5× attacker uplift. — [Promon ATR Q1 2026](https://promon.io/security-news/app-threat-report-2026-q1-the-state-of-code-obfuscation-against-ai)
- **Jscrambler – Code Integrity** (LLM-resilient release, 13 Aug 2026): "benchmarked leading AI models against real-world deobfuscation strategies"; polymorphic JS obfuscation; dashboard "AI-resistance notice." Claims internal benchmarking; no public numbers. — (per source pack §5; Jscrambler What's New)
- **Guardsquare (DexGuard/iXGuard):** positions **polymorphism** as the answer to AI-scaled attacks (each build structurally unique → defeats pattern-learned attacks); completed **Verimatrix XTD** asset acquisition early 2026. No published AI-resistance numbers. — (source pack §5; see Q2 for the deal)
- **Digital.ai (branded "Arxan Security"):** "Always-On AI-Resilient Application Defense"; per-customer **"AI Resilience Score" 0–100** (customer-private, not a public model-success benchmark). — (source pack §5)
- **Appdome:** "AI-native" platform; binary obfuscation that "disrupts AI-assisted analysis." No numbers. — (source pack §5)
- **Verimatrix:** qualitative only — CTO Klaus Schenk's hackathon retex: "~25 rounds of human correction before the model identified the actual decryption flow"; "Cost is not the barrier; expertise is." — (source pack §5)
- **Obfuscator.io:** `vm-anti-llm` preset; "anti-LLM defenses in vmSelfDefending and vmDebugProtection." Free npm README self-rates "fully vulnerable (no LLM-specific defenses)." — (source pack §5)
- **PyArmor (NEW):** Python obfuscator; serializes/obfuscates code objects via Python `marshal`, protects constants/literal strings; "latest version can't be deobfuscated easily." No explicit anti-LLM marketing — used as a "deep-obfuscation pass" in third-party anti-LLM tooling. Also widely abused by malware (SANS ISC diary). — [SANS ISC: PyArmor malware](https://isc.sans.edu/diary/31840)
- **ionCube (NEW):** PHP encoder/obfuscator — **no AI/LLM-resistance claim found** in 2026 search; appears dormant on this trend. — (gap; see Gaps)

### Inferences
- The industry's technical consensus defense stack to **build on top of**: polymorphism (Guardsquare/Jscrambler), white-box crypto + string encryption (Thales/PreEmptive/EMVCo labs), runtime integrity/RASP sensors (Digital.ai/Appdome/Promon), and anti-decompilation (Promon flags as underexplored). None of these is adaptive or attacker-aware — they are static transforms applied at build time.
- "AI-Resistant String Encryption" (PreEmptive) and "polymorphism" (Guardsquare) are the most concrete, citable productized techniques; everything else is positioning language.

### Gaps
- No public technical whitepaper quantifies *how* Jscrambler/Digital.ai/Appdome measure "AI resistance" — all internal.
- ionCube's 2026 stance on AI-resistance is unconfirmed (likely none, but absence of evidence).

---

## Q2. Is anyone doing "LLM-driven adaptive obfuscation with an attack feedback loop" or "formal proof of equivalence"? (The wedge)

### Takeaway
The wedge is **partly real and needs sharpening**: an LLM-driven *adaptive, attack-feedback-loop*
obfuscator now EXISTS in 2026 academic work (Acoda, CoTDeceptor) — but only against **source-level
LLM code analysis / deobfuscation prompts**, not against tool-using RE agents on compiled binaries,
and never as a shipped commercial product. **Formal proof of semantic equivalence does NOT exist**
anywhere — all adaptive-obfuscation work verifies equivalence empirically (run unit tests), confirming
that half of the wedge is still wide open.

### Cited Findings
- **Acoda** (arXiv 2606.11755): genetic-algorithm framework, 8 semantics-preserving obfuscation methods on Python; **explicit attack feedback loop** — scores each obfuscated sample against the target LLM's deobfuscation responses, keeps top 15% as parents, mutates, iterates (T=2). Exploits LLM safety-alignment + token-processing. Crucially: **equivalence is test-based only** (runs unit tests, reports no runtime errors) — **no formal proof.** Targets LLM code *analysis/deobfuscation*, not binary RE agents. — [Acoda (arXiv 2606.11755)](https://arxiv.org/html/2606.11755v1)
- **CoTDeceptor** (arXiv 2512.21250): "formulates code obfuscation as a feedback-driven search," building "strategy lineages based on detector reasoning-chain feedback" — explicitly contrasts itself with "one-shot LLM-based obfuscation [that] suffers from semantic drift." Targets **CoT-enhanced LLM code agents / detectors.** — [CoTDeceptor (arXiv 2512.21250)](https://arxiv.org/pdf/2512.21250)
- **ALIBI** (arXiv 2607.24964): adaptive agentic *attack* (adversarial comments) that "iteratively refines ... using detector reasoning and feedback" — the attacker-side analogue; shows the feedback-loop paradigm is the active research frontier on both sides. — [ALIBI (arXiv 2607.24964)](https://arxiv.org/html/2607.24964)
- Industry framing confirms the threat model the wedge addresses: LLM deobfuscation is "a feedback loop, where static barriers are progressively stripped away by execution-aware analysis." — [NH-ISAC/nhimg: LLM-resilient obfuscation is the baseline](https://nhimg.org/articles/llm-resilient-obfuscation-is-becoming-the-baseline-for-client-side-code/)
- No search surfaced any product or paper offering **formal/provable semantic equivalence** for a protection transform; the literature relies on test-based equivalence. (Consistent with team note that CompCert-grade formal verification is off-the-shelf unavailable and doesn't scale.)

### Inferences
- **Revised wedge statement:** the defensible gap is not "adaptive LLM obfuscation" in the abstract (that now exists in research) but specifically **(a) adaptive/feedback-loop protection measured against tool-using RE agents on compiled binaries** (Acoda/CoTDeceptor are source-level, Python, vs analysis prompts), **(b) as an open, reproducible, neutral benchmark + productized layer**, and **(c) formal proof of equivalence, which no one offers.** The team's existing "open agentic resilience benchmark" framing survives; the "adaptive obfuscation is novel" sub-claim must be downgraded to "novel against binary RE agents / as a product."
- The feedback-loop concept is young enough (all 2026 papers) that these authors are potential fast-followers; time-limited lead holds.

### Gaps
- Could not confirm whether any stealth startup is commercializing Acoda/CoTDeceptor-style adaptive obfuscation (no funding/press found).

---

## Q3. Market size — application shielding / in-app protection (2025–2026)

### Takeaway
There is **no consensus market number** — syndicated "report-mill" estimates for 2025 range from
~$1.15B to ~$10.8B depending on how the segment is drawn, so all of these are **LOW confidence**.
The specific figures the team carried (~$2.7B, ~$1.8B→$16.2B) partly check out: **$1.8B (2024) and
$2.7B (2026)** match Custom Market Insights' in-app protection series, but the **$16.2B endpoint could
not be sourced** (CMI's own endpoint is $8.9B by 2035). Treat the whole category sizing as directional.

### Cited Findings
- **Custom Market Insights (CMI) – In-App Protection:** base $1.8B (2024) → **$2.1B (2025)** → **$2.7B (2026)** → **$8.9B by 2035**, ~17.7% CAGR 2026–2035. **LOW confidence** (report mill). This is the source of the team's $1.8B and $2.7B figures. — [CMI In-App Protection](https://www.custommarketinsights.com/report/in-app-protection-market/); [CMI press: $8.9B by 2035](https://www.custommarketinsights.com/press-releases/in-app-protection-market-size/)
- **Market Intelo – In-App Protection:** $3.8B (2025) → $12.6B (2034), 14.2% CAGR. **LOW confidence.** — [Market Intelo](https://marketintelo.com/report/in-app-protection-market)
- **Application Shielding Software (segment, estimates diverge wildly, all LOW confidence):** Future Market Report $1.15B (2025)→$2.65B (2033) @10.99%; Market Research Intellect $1.39B (2025)→$6.03B (2035) @15.8%; WiseGuy $2.64B (2025)→$5B (2035) @6.6%; Archive Market Research $2.5B (2025) @15%; Data Insights $10.78B (2025) @16%; Report Prime $5.29B→$5.54B @0.67%. Spread of ~10× for the *same year* = the category is not rigorously defined. — [search aggregate, reportprime/wiseguy/datainsights/etc.](https://www.futuremarketreport.com/industry-report/application-shielding-software-market)
- **Adjacent anchor (higher confidence, but broader market):** MarketsandMarkets **Application Security** $41.16B (2026) → $66.03B (2031) @9.9% CAGR. (Note: MnM's own pages conflict — another shows $13.63B→$23.45B — so even the tier-1 firm is internally inconsistent here.) — [MnM Application Security $66.03B by 2031](https://www.prnewswire.com/news-releases/application-security-market-worth-66-03-billion-by-2031--marketsandmarkets-302713211.html)
- Recurring named players across all reports: Arxan/Digital.ai, Guardsquare, Jscrambler, Promon, Appdome, OneSpan, Entersekt, Verimatrix. — [reportprime](https://www.reportprime.com/application-shielding-software-r19831)

### Inferences
- **Verdict on the carried figures:** $2.7B (2026) and $1.8B (2024) are real CMI numbers — cite them *as CMI, low confidence*. The **$16.2B figure is unverified and should be dropped or replaced** with CMI's $8.9B-by-2035 or Market Intelo's $12.6B-by-2034, each labeled low confidence and attributed.
- Honest framing for a pitch: application shielding is a **~$1.5–3B niche in 2025–2026** (not a $10B+ market), a mature slice of the larger ~$40B application-security market; the growth story is AI-threat-driven re-rating, not a huge TAM.

### Gaps
- No Gartner or Forrester hard dollar figure for "in-app protection" surfaced (Gartner covers it qualitatively in the App Shielding/IAP space; no public market-size number found).
- Origin of the "$16.2B" figure unknown — possibly a mis-citation or a paywalled report; flag for the team to confirm or discard.

---

## Q4. Funding & M&A (this space + adjacent AI-security)

### Takeaway
The code-protection space itself is **PE roll-up territory, not venture-hot** — the splashy money
is in adjacent AI-security (Palo Alto/Protect AI $634.5M, Check Point/Lakera ~$300M). The one
venture signal inside RE is **RevEng.AI's $15M Series A (NATO Innovation Fund, 27 May 2026)** —
but it's defensive supply-chain RE, not anti-RE.

### Cited Findings
- **RevEng.AI (London; BinNet binary-analysis foundation model):** $15M Series A, **27 May 2026, led by NATO Innovation Fund** (+ Sands Capital, In-Q-Tel, IQ Capital, Episode One); ~$19.5M total after $4.15M seed. Positions as supply-chain verification (defensive RE), NOT anti-RE. — (per team source pack §"why now"; [StudioGlobal summary](https://www.studioglobal.ai/discover/answers/what-is-reveng-ai-and-what-does-its-6a17dd531065d488b25af883))
- **Guardsquare:** Battery Ventures took a **majority stake for $29M (Series A, 30 Jan 2019)** — first institutional round; GP Dharmesh Thakker joined the board. Built on open-source ProGuard (~25% of all Android apps). Acquired Verimatrix XTD assets early 2026. — [Tech.eu](https://tech.eu/2019/01/30/battery-ventures-pays-29-million-for-a-majority-stake-in-belgiums-guardsquare/); [Guardsquare press](https://www.guardsquare.com/press-release/guardsquare-announces-29-million-investment-battery-ventures)
- **Zimperium (NEW):** acquired by **Liberty Strategic Capital (Steven Mnuchin's PE firm) for $525M**, announced 29 Mar 2022, closed Q2 2022; Liberty's first controlling stake; SoftBank stayed minority. ~38.3× revenue multiple on ~$14M revenue. (Mobile threat defense, adjacent to shielding.) — [TechTarget](https://www.techtarget.com/searchsecurity/news/252515452/Zimperium-acquired-by-Liberty-Strategic-Capital-for-525M); [Business Wire](https://www.businesswire.com/news/home/20220329005393/en/Liberty-Strategic-Capital-to-Acquire-Zimperium-a-Leader-in-Mobile-Device-and-Application-Security)
- **ADJACENT AI-security M&A (the real money — use for "where capital is flowing"):**
  - **Palo Alto Networks → Protect AI:** completed 22 Jul 2025; **$634.5M total consideration** ($607.4M cash; $515.8M goodwill, $70M developed-tech intangibles) per SEC 10-K. Protect AI had raised $108.5M (Salesforce Ventures, Samsung). Folded into Prisma AIRS. — [SiliconANGLE](https://siliconangle.com/2025/04/28/palo-alto-networks-buys-protect-ai-reported-500m-debuts-new-cybersecurity-tools/)
  - **Check Point → Lakera:** announced 16 Sep 2025, closed 22 Oct 2025, **~$300M**; Lakera (founded 2021, makers of "Gandalf," >80M attack data points) becomes Check Point's Global Center of Excellence for AI Security (Zurich). — [Calcalist](https://www.calcalistech.com/ctechnews/article/rj5bc1vige); [SecurityWeek](https://www.securityweek.com/check-point-to-acquire-ai-security-firm-lakera/)
  - **CrowdStrike → Pangea:** announced same day as Check Point/Lakera (16 Sep 2025) — AI security (prompt/agent defense); price not stated in results. — [SecurityWeek, via Lakera coverage]

### Inferences
- Capital pattern: anti-RE / shielding vendors get **acquired by PE at modest multiples** (Guardsquare $29M, Zimperium $525M) or roll up assets (Guardsquare/XTD); **AI-model-security** (Protect AI, Lakera, Pangea) commands 10–100× bigger exits because it rides the GenAI wave. A team pitching "AI-resistant code protection" should position toward the AI-security capital pool, not the mature shielding pool.
- RevEng.AI's NATO/In-Q-Tel backing signals **government/defense is the deepest-pocket buyer** for RE tooling.

### Gaps
- No Promon, Jscrambler, or Digital.ai disclosed funding round surfaced (Promon/Jscrambler privately held, undisclosed; Digital.ai is PE-backed — widely attributed to TPG Capital from its 2020 CollabNet/VersionOne/XebiaLabs formation, but not confirmed in this session's sources). CrowdStrike/Pangea price unconfirmed.

---

## Q5. Compliance drivers that force purchase

### Takeaway
The purchase-forcing drivers are **OWASP MASVS-RESILIENCE** (the de-facto audit baseline),
**EMVCo SBMP** and **PCI MPoC** (hard gates for any payment/SoftPOS app). Critically for the
team's wedge: **none of these standards prescribes a specific obfuscation method — all are
outcome/attack-resistance based and lab-evaluated**, which is exactly the vacuum a neutral,
measured resilience benchmark fills ("the test the labs and vendors should grade against").

### Cited Findings
- **OWASP MASVS-RESILIENCE** (current v2.1.0; no distinct "2026" release): controls MASVS-RESILIENCE-1 platform-integrity, **-2 anti-tampering**, **-3 anti-static-analysis**, **-4 anti-dynamic-analysis**. Explicitly scoped to "apps that need to resist reverse engineering and tampering: payment apps, apps protecting valuable content, apps with anti-fraud requirements." Caveat in the standard: "anti-tampering or obfuscation ... must not be used as a substitute for proper security architecture." — [OWASP MASVS-RESILIENCE-2](https://mas.owasp.org/MASVS/controls/MASVS-RESILIENCE-2/)
- **EMVCo SBMP** (Security Evaluation Process v1.8, Jul 2024; Security Requirements v1.5, Jan 2025): requires "mobile application protection using **white-box crypto, obfuscation, and binary protection**." **Does not dictate methods** — labs assess resistance to attack categories via **white-box evaluation (source access mandatory)**. "Tools like ProGuard are not enough; SBMP checks for anti-debugging and runtime protections." — [Licel SBMP guide](https://licelus.com/resources/knowledge_hub/emvco-sbmp-security-requirements); [Promon SBMP](https://promon.io/security-news/inside-an-emvco-sbmp-evaluation-what-labs-test-and-how-to-prepare)
- **PCI MPoC** (Mobile Payments on COTS): **req 1B-1.5** gives guidance on "whether code obfuscation is required ... to protect it from reverse engineering, and if so which methods"; **req 1B-1.14** anti-tampering must resist a feasible attack, **passed only at a 25-point attack-rating** via PCI's attack-costing framework; §1B-2 crypto "could include obfuscation of cryptographic functions and white-box cryptography." Methods not mandated "as long as they are robust." — [Promon PCI MPoC](https://promon.io/resources/knowledge-center/pci-mpoc-compliance-mobile-payments-cots); [Medium: EMVCo vs MPoC vs MASVS](https://medium.com/@vivekcyber/emvco-vs-pci-mpoc-vs-owasp-masvs-a-deep-dive-into-mobile-application-security-standards-80bbadba8bc9)
- **Interlock:** EMVCo SBMP evaluation can satisfy PCI MPoC req 1B-1.3 (accepts CC EAL4/AVA_VAN.5, EMVCo Chip + GlobalPlatform, EMVCo SBMP for TEE, PCI-PTS). — [Licel MPoC](https://licelus.com/resources/knowledge_hub/pci-mpoc)

### Inferences
- The compliance stack creates **mandatory demand** in fintech/payments/SoftPOS, streaming/DRM, and anti-fraud — buyers can't ship without passing a lab, and the lab tests *resistance outcomes*, not techniques. A measured "how much does protection X raise an attacker's cost" benchmark maps directly onto both the PCI 25-point **attack-costing** model and EMVCo's **attack-resistance** evaluation — i.e., the team's cost-to-break metric is already the language regulators use.
- Because standards are method-agnostic and labs are the gatekeepers, a neutral benchmark could position as **pre-certification self-assessment / lab-input tooling**, not just marketing.

### Gaps
- No single regulation *names* a specific vendor or obfuscation algorithm (by design). No evidence yet of AI-resistance being written into MASVS/SBMP/MPoC text as a named requirement — it's covered implicitly under anti-static/anti-dynamic analysis.

---

## Q6. Data-obfuscation adjacency (DIFFERENT market — context only)

### Takeaway
PII/data-privacy "obfuscation" (tokenization, masking, vaults, redaction for LLM prompts) is a
**separate, better-funded market** from code protection — it protects *data flowing into models*,
not *code from being reverse-engineered*. Note it only to pre-empt the "isn't this already solved?"
objection; do not conflate.

### Cited Findings
- **Skyflow:** raised **$30M led by Khosla Ventures (Mar/Apr 2024)**, a Series B extension (prior $45M Series B 2021; ~$100M total). "Data privacy vault" — isolates/tokenizes PII so "a query can use real data that never touches the model." Revenue growth >210%; customers GoodRx, Lenovo, Hippocratic AI. Founded 2019. — [Finovate](https://finovate.com/data-privacy-vault-skyflow-secures-30-million-in-new-funding/); [Business Wire](https://www.businesswire.com/news/home/20240328765469/en/Skyflow-Raises-$30-Million-led-by-Khosla-Ventures-for-Data-Privacy-in-AI-and-Global-Data-Residency)
- **Protecto / Microsoft Presidio:** named in the brief as adjacency peers (PII detection/redaction for LLM pipelines). **Not corroborated with funding detail in this session's searches** — Presidio is a Microsoft open-source PII anonymization library (not a funded company); Protecto is an AI-data-guardrails startup. — (gap on specifics)
- Competitive set in this adjacency: Protegrity (vaultless tokenization, format-preserving encryption), Protecto, Presidio. — [CB Insights Protegrity vs Skyflow](https://www.cbinsights.com/compare/protegrity-vs-skyflow-1)

### Inferences
- This is a **demand-side / data-governance** market (GDPR/CCPA/AI-privacy driven), orthogonal to the **supply-side / anti-reverse-engineering** market. Overlap is only rhetorical ("obfuscation"). Mentioning it defensively strengthens the pitch's precision.

### Gaps
- No Protecto funding figure and no Presidio commercial entity found this session.

---

## Cross-cutting caveats (for the report writer)
- **All market dollar figures are LOW confidence** (syndicated report mills, ~10× spread for the same year). Only use them attributed and hedged; the honest read is a ~$1.5–3B niche inside ~$40B app-security.
- **Vendor AI-resistance claims are marketing** except Thales (vendor-run, 1 model, own app) and Promon (rigorous but measures OLLVM not its product, zero-shot). PreEmptive's "AI-Resistant String Encryption" is a named feature but unquantified.
- **The wedge, precisely:** adaptive feedback-loop LLM obfuscation now exists in *research* (Acoda 2606.11755, CoTDeceptor 2512.21250) but only source-level vs LLM analysis; **no formal proof of equivalence exists anywhere**; and no one offers an **open, neutral, agentic, cost-aware resilience benchmark against binary RE agents** — that remains the defensible opening, time-limited as the team already noted.
- **Capital signal:** money is in AI-model-security M&A (Palo Alto/Protect AI $634.5M, Check Point/Lakera ~$300M), while code-protection itself is low-multiple PE roll-up — position toward the former pool.
