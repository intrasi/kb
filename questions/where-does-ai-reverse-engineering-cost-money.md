---
type: question
title: Where does AI reverse engineering cost someone money, and what do people on X say about it?
tags: [market, customer, security, idea]
date: 2026-11-07
by: karla
status: open
owner: karla
---

# Prompt for the X research agent: listen for intent around reverse engineering

You research and stream X. Listen to what people say. Do not post, reply, like, or follow. Return evidence to the team knowledge base at https://github.com/intrasi/kb, following its `AGENTS.md` (pull first, check what exists, one claim per note, raw material in `sources/`, run `python3 scripts/kb.py check`, then push).

## 1. Context in one paragraph

We are a four-person team at the Garaža Frontier Hackathon (Belgrade, 7 and 8 November 2026). Our problem field: AI makes shipped software cheap to reverse-engineer. Agents now drive decompilers directly (GhidraMCP, ida-pro-mcp, REA), and models such as Claude Opus read obfuscated code that used to take experts days. Our starting idea is protection that AI attackers find expensive, plus a proof that the protected code still behaves identically, plus a measured "attacker cost" score. The solution is open. Your job is to find **where this problem costs real money, who feels it, and how they talk about it**.

## 2. The core principle (use it to judge every post)

Reverse engineering only hurts when **valuable logic runs on the user's device, and nothing else protects the revenue**.

- **Low value to an attacker:** Instagram, WhatsApp, Uber, or any app whose value is the network, the server, or the account. Reversing the app yields nothing worth having.
- **High value to an attacker:** the app itself is the product, works offline, or enforces money on the device. Examples:
  - a paid feature unlocked by a local check;
  - a subscription verified on the device;
  - an on-device AI model;
  - a payment or identity check in a mobile app;
  - anti-cheat;
  - a licence key;
  - a firmware feature lock.

What people buy is **time**. Protection is worth paying for if it delays the first crack, clone, or bypass past the window in which the product earns its money. A game earns most in its launch weeks, a plugin in its first months, and a banking app on every single day. AI shrinks that window. Listen for evidence about how long the window is, how fast it is closing, and what that costs.

What the team already knows (from earlier Reddit, GitHub, and Hacker News sweeps; do not repeat them, look for what they lack):

- People say LLMs undo basic and JavaScript obfuscation in "1 or 2 shots". That is opinion, with no reported incident.
- Obfuscation causes real pain: DexGuard checks crashing apps "tens of thousands" of times, broken builds, and harder maintenance.
- Spend is mixed. Some teams pay for DexGuard and Denuvo, while a self-described AAA programmer says obfuscation was used on none of three titles.
- **Nobody has asked for a measured "how hard is my app for AI to crack" score.** This is the biggest gap.
- Standards such as OWASP MASVS ask for resilience but do not mandate obfuscation. Buyers are not forced to buy.

## 3. Intents to listen for

Tag every captured post with one intent:

| Intent | What it sounds like | Why we care |
| --- | --- | --- |
| `loss` | "our app got cracked", "someone cloned our app", "piracy killed our launch", "found our premium features unlocked on a forum" | Proof of the problem, ideally with money or time |
| `ai-crack` | "Claude reversed this in an hour", "used GhidraMCP to crack X", "AI deobfuscated our JS" | Proof that AI changed the speed |
| `window` | "cracked on day one", "Denuvo held for 3 weeks", "the clone appeared a week after launch" | The time-window economics |
| `defend` | "we moved the check to the server", "we added DexGuard", "we switched to a server-validated licence" | What people do today instead (our real competitor) |
| `buy` | "looking for an obfuscator", "recommendations for app shielding", "is Jscrambler worth it", "anyone used Promon" | Buying intent, the strongest signal |
| `pain` | "obfuscation broke our build", "RASP false positives", "can't debug the release build", "performance hit" | Where a proof of equivalence would help |
| `dismiss` | "security through obscurity", "anything client-side is already lost", "just don't put secrets in the client" | The strongest objections; capture them all |
| `measure` | "how do we know our protection works", "no way to test obfuscation", "pen-test said it took 2 days" | Demand for the attacker-cost score |
| `controversy` | See section 6 | Debate that frames the pitch |

## 4. Industries to search, highest value at risk first

Each has logic on the device that is worth money. Search the industry terms combined with section 5's attack terms.

1. **Mobile banking and payments.** Banking trojans, cloned banking apps (the Group-IB Gigabud campaign in Indonesia, 2026), SoftPOS and tap-to-pay on phones, PCI MPoC certification, and EMVCo. Terms: `cloned banking app`, `SoftPOS`, `tap to pay on iPhone security`, `MPoC`, `app shielding bank`, `overlay attack`, `banking trojan Android`.
2. **Games.**
   - Piracy windows (Denuvo), cheats, and kernel anti-cheat (Vanguard, Easy Anti-Cheat, BattlEye).
   - Mobile game hacks such as modded APKs and unlocked in-app purchases.
   - Terms: `Denuvo cracked`, `day one crack`, `cheat developers AI`, `anti-cheat bypass`, `modded APK`, `IAP bypass`.
3. **Paid offline software and plugins.**
   - Audio plugins (VST and AU), creative tools, and CAD and EDA software.
   - Desktop apps with licence keys, plus indie apps with one-time purchases or local subscription checks.
   - Terms: `cracked VST`, `license key bypass`, `keygen`, `my app is on a crack site`, `indie dev piracy`.
4. **On-device AI.**
   - Models shipped inside apps, which can be extracted, copied, or have their weights stolen.
   - Proprietary prompts and system logic in desktop agents, and Electron apps that ship their logic in JavaScript.
   - Terms: `extract model from app`, `on-device model stolen`, `CoreML model extraction`, `Electron app source exposed`, `leaked system prompt from app`.
5. **SDK companies that license code per seat or per device.**
   - Identity and document scanning, computer vision, and face liveness.
   - The SDK is the product, so a cracked SDK means lost licences. Microblink (Zagreb) is a regional example to watch.
   - Terms: `SDK license bypass`, `cracked SDK`, `liveness check bypass`.
6. **Connected devices and automotive.**
   - Features unlocked by subscription (heated seats, performance unlocks), firmware locks, and printer-cartridge DRM.
   - Medical-device and industrial controllers.
   - Terms: `feature unlock jailbreak`, `subscription features car hacked`, `firmware unlock`, `right to repair firmware`.
7. **Streaming and media.** DRM key extraction (Widevine L3), ad-skipping, and modded streaming clients. Terms: `Widevine L3 key extraction`, `modded streaming app`, `ad block app mod`.
8. **Ad tech and app fraud.** Tampered SDKs that fake installs or clicks. Terms: `SDK spoofing`, `install fraud tampered app`.

Industries to treat as low priority (value sits on the server or in the network): social media, marketplaces, messaging, and web SaaS whose logic runs on the server.

## 5. Places to search

X has no reliable geo filter. Combine `lang:`, local-language terms, and accounts that list the place in their profile. Where the `near:` operator works, use it.

| Hub | Why | Local angle |
| --- | --- | --- |
| Leuven and Brussels | Guardsquare (DexGuard, iXGuard) | Vendor employees, KU Leuven research (COSIC) |
| Porto and Lisbon | Jscrambler | JavaScript and web protection |
| Oslo | Promon (published an LLM deobfuscation benchmark, Q1 2026) | `lang:no` |
| Amsterdam and Hoofddorp | Irdeto (games and media DRM, Denuvo) | `lang:nl` |
| London | Fintech, banks, mobile security consultancies | Mobile banking fraud, PSD2 |
| Stockholm and Helsinki | Game studios (mobile and PC), fintech | Mobile game hacks, IAP fraud |
| Warsaw and Kraków | Large PC game studios and their piracy debates | `lang:pl`, Denuvo debates |
| Montréal | Large game-studio cluster | Anti-cheat and DRM jobs and talk |
| Seattle and Los Angeles / Irvine | Game publishers, anti-cheat teams | Kernel anti-cheat debates |
| San Francisco | AI labs, AI-security startups, investors | AI reverse-engineering demos, investor takes |
| Tel Aviv | Mobile and app security startups | AppSec founders |
| Berlin | Audio software, fintech | Plugin piracy, `lang:de` |
| Munich and Stuttgart | Automotive | Feature-on-demand unlocks, `lang:de` |
| São Paulo | Very high mobile-banking use and banking trojans | `lang:pt` (`app bancário clonado`, `trojan bancário`) |
| Jakarta and Singapore | Cloned banking apps (Gigabud), super-apps | `lang:id` (`aplikasi bank palsu`) |
| Bengaluru and Mumbai | UPI payments, huge app markets | Payment-app tampering, `modded APK` |
| Seoul and Tokyo | Mobile games with heavy IAP | Game hacking, `lang:ko`, `lang:ja` |
| Shenzhen and Shanghai | Android ecosystem, game hacking scene | `lang:zh` (`破解`, `脱壳`, `外挂`) |
| Belgrade and Zagreb | Our home region (Nordeus, Nanobit, Microblink, Infobip) | People we can actually talk to this weekend |

## 6. Controversial conversations to find

Capture both sides with quotes. Judges will ask about these.

1. **"Security through obscurity" versus resilience.** Is obfuscation pointless, or does it buy real time? Who argues which way, and with what evidence?
2. **AI makes all client-side protection obsolete.** Posts claiming "obfuscation is dead now", and the replies that disagree.
3. **Denuvo and DRM backlash.** Players hate it and studios keep paying for it. Look for any numbers on the value of the launch window.
4. **Kernel anti-cheat and privacy.** Vanguard-style drivers have deep access to players' machines, and cheaters use AI to build cheats.
5. **Right to repair and modding versus anti-tamper.** Car feature subscriptions, John Deere-style firmware locks, and printer DRM. Protection is unpopular when it locks owners out.
6. **The legality of AI-assisted reverse engineering.** DMCA section 1201, the EU Software Directive's interoperability exception (Article 6), and whether AI labs' usage policies allow cracking. Also, who is liable when an agent cracks a licence.
7. **Open-sourcing the client.** "Just open-source it and charge for the service" as the alternative to protecting code.
8. **Dual use.** Defenders (malware analysts) need AI reverse engineering. Will stronger anti-AI obfuscation help malware authors more than app makers?
9. **Is a formal proof worth anything to a buyer?** Look for talk about verified compilers, "proven correct" tooling, and whether security buyers care.

## 7. Search mechanics

- **Time:** the last 12 months, weighted to the last 3. Use `since:2025-11-01`.
- **Quality filters:** `min_faves:20` for broad terms, none for niche terms. Use `-filter:replies` for originals, and then read the replies of good threads, which is where the experience is.
- **People to scan:**
  - reverse engineers, mobile security researchers, and anti-cheat engineers;
  - game developers, indie developers, and fintech CISOs;
  - the X accounts of security teams (Elastic Security Labs and other vendors' research teams).
- **Query patterns** (combine freely):
  - `("reverse engineered" OR decompiled OR deobfuscated) (Claude OR GPT OR LLM OR "AI agent") (app OR APK OR binary)`
  - `(cracked OR pirated OR cloned) ("my app" OR "our app" OR "our game") since:2025-11-01`
  - `(obfuscation OR obfuscator OR DexGuard OR Jscrambler OR Promon OR Denuvo) (worth OR useless OR broke OR recommend)`
  - `GhidraMCP OR "ida-pro-mcp" OR "REA mcp"`
  - `"security through obscurity" (AI OR LLM) since:2026-01-01`
- **Streaming:** keep a live filter on the Ghidra and IDA MCP names, `Denuvo`, `cloned banking app`, `obfuscation` with `AI`, and `cracked` with `day one`. Log new hits through the weekend.

## 8. What to return

For each captured post, record:
- the link;
- the date;
- the handle;
- the author's role, as visible in their profile;
- the place, if visible;
- the industry;
- the intent tag;
- a verbatim quote of up to 50 words;
- engagement (likes, reposts, replies);
- whether money or time is named.

Never paraphrase a post as a quote. If something is not found, write "not found".

The final summary, in this order:

1. **The answer in five lines.** Where does AI reverse engineering cost real money now? Who says so? How big is the time window?
2. **The three best use cases**, ranked by evidence. For each: the industry, the asset on the device, the time window, what people do today, and the two best quotes.
3. **The strongest objections**, quoted, before any support.
4. **The controversies**, with both sides for each one in section 6 that you found.
5. **The measurement gap.** Any post that asks how to test protection, or rejects the idea of testing it.
6. **Places.** The hubs where talk was densest, and the regional people within reach this weekend.
7. **Gaps.** What you searched for and did not find.

## 9. Limits

- Listen only. No posts, replies, direct messages, likes, or follows. Drafts of any outreach go to a human.
- Public posts only, with no scraping behind logins and no bypassing of rate limits.
- Do not try to crack, reverse, or test anyone's software, and do not collect tools or instructions for doing so. Record that people talk about it, never how.
- Do not build profiles of individuals. A handle and a visible role are enough.
- Time box: 3 hours, then file what you have, and keep the live stream running.

## Leads

- Earlier sweeps: [[reddit-listener-code-protection-2026-11-07]], [[github-hn-scan-2026-11-07-index]], [[reddit-sweep-found-no-ask-for-an-ai-crack-score]].
- Parent question: [[do-people-need-ai-resistant-code-protection]].

## Answer
