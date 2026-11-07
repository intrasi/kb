---
type: question
title: Where does AI reverse engineering cost someone money, and what do people on Reddit say about it?
tags: [market, customer, security, idea]
date: 2026-11-07
by: karla
status: open
owner: karla
---

# Prompt for the Reddit research agent: listen for intent around reverse engineering

You research Reddit. Read threads and comment trees, and listen to what people say. Do not post, comment, vote, or send messages. Return evidence to the team knowledge base at https://github.com/intrasi/kb, following its `AGENTS.md`:
- pull first, and check what already exists;
- one claim per note, with raw material in `sources/`;
- run `python3 scripts/kb.py check`, then push.

## 1. Context in one paragraph

We are a four-person team at the Garaža Frontier Hackathon in Belgrade, 7 and 8 November 2026. Our problem field: AI makes shipped software cheap to reverse-engineer.
- Agents now drive decompilers directly (GhidraMCP, ida-pro-mcp, REA).
- Models such as Claude Opus read obfuscated code that used to take experts days.
- Our starting idea combines three things: protection that is expensive for AI attackers, a proof that the protected code still behaves identically, and a measured "attacker cost" score.
- The solution is still open.

Your job is to find where this problem costs real money, who feels it, and how they talk about it.

## 2. The core principle (judge every thread by it)

Reverse engineering only hurts when **valuable logic runs on the user's device, and nothing else protects the revenue**.

- **Low value to an attacker:** apps whose value is the network, the server, or the account, such as Instagram, WhatsApp, or Uber. Reversing the app gives the attacker nothing worth having.
- **High value to an attacker:** apps that are the product themselves, work offline, or enforce money on the device. Examples:
  - a paid feature unlocked by a local check;
  - a subscription verified on the device;
  - an on-device AI model;
  - a payment or identity check in a mobile app;
  - anti-cheat;
  - a licence key;
  - a firmware feature lock.

**What people buy is time.** Protection is worth paying for if it delays the first crack, clone, or bypass past the window in which the product earns its money. For a game, that is the launch weeks. For a plugin, the first months. For a banking app, every day. AI shrinks that window. Look for evidence of how long the window is, how fast it is closing, and what that costs.

## 3. What the team already has (do not repeat it)

An earlier Reddit sweep (`sources/reddit-listener-code-protection-2026-11-07.md` in the KB) read r/gamedev, r/LocalLLaMA, r/programming, r/androiddev, r/ReverseEngineering, r/MachineLearning, r/AskNetsec, r/netsec, r/iOSProgramming, and r/cybersecurity. **Skip every link already in that file.** Its findings:

- Comments say LLMs undo basic and JavaScript obfuscation in "1 or 2 shots". These are opinions, with no incident reported.
- Obfuscation pain is real: a DexGuard runtime check crashed apps "tens of thousands" of times, and people complain of harder maintenance, performance hits, and debugging problems.
- Spending is mixed. One team pays for DexGuard, and studios "blow SO much money on Denuvo". Against that, a self-described AAA programmer says none of three titles used obfuscation.
- Weight backdoors in AI models are "hard to spot", and supply-chain compromise is called the more realistic attack.
- **Nobody asked for a measured "how hard is my app for AI to crack" score.** This is the biggest gap.

This sweep goes **deeper into the industries where money sits on the device**, into piracy and cheating communities (to measure time windows), and into regional and non-English subreddits.

## 4. Intents to listen for

Tag every captured comment or post with one intent.

| Intent | What it sounds like | Why we care |
| --- | --- | --- |
| `loss` | "my app got cracked", "someone cloned our app", "piracy killed our launch", "my plugin is on a crack site" | Proof of the problem, ideally with money or time |
| `ai-crack` | "Claude reversed this in an hour", "used GhidraMCP to crack X", "ChatGPT deobfuscated our JS" | Proof that AI changed the speed |
| `window` | "cracked on day one", "Denuvo held for 3 weeks", "the clone appeared a week after launch" | The time-window economics |
| `defend` | "we moved the check to the server", "we use DexGuard", "server-validated licences" | What people do today instead; this is our real competitor |
| `buy` | "looking for an obfuscator", "is Jscrambler worth it", "anyone used Promon", "recommend app shielding" | Buying intent, the strongest signal |
| `pain` | "obfuscation broke our build", "RASP false positives", "can't debug the release build" | Where a proof of equivalence helps |
| `dismiss` | "security through obscurity", "anything client-side is already lost", "just don't put secrets in the client" | The strongest objections; capture them all |
| `measure` | "how do we know our protection works", "no way to test obfuscation", "the pen-test took 2 days" | Demand for the attacker-cost score |
| `controversy` | See section 7 | Debate that frames the pitch |

## 5. Subreddits by industry, highest value at risk first

If a subreddit does not exist, is private, or bans this kind of reading, skip it and log that.

1. **Mobile banking and payments**
   - Subreddits: r/fintech, r/blueteamsec, r/Malware, r/Scams (victims of fake and cloned banking apps), r/devsecops, r/ExploitDev.
   - Terms: `cloned banking app`, `fake bank app`, `overlay attack`, `banking trojan`, `SoftPOS`, `tap to pay`, `MPoC`, `app shielding`, `root detection bypass`.
2. **Games**
   - Developer subreddits: r/IndieDev, r/Unity3D, r/unrealengine, r/godot, r/pcgaming.
   - Piracy and cracking news: r/CrackWatch and r/PiratedGames. Read these only for timing and attitudes, such as how long Denuvo held and how players feel about DRM.
   - Terms: `Denuvo`, `day one crack`, `cracked in`, `anti-cheat`, `cheaters AI`, `modded APK`, `IAP bypass`, `save editing`.
3. **Paid offline software and plugins**
   - Subreddits: r/audioengineering, r/WeAreTheMusicMakers, r/edmproduction (plugin piracy debates), r/macapps, r/SaaS, r/indiehackers, r/SideProject, r/electronjs, r/javascript, r/webdev.
   - Terms: `cracked plugin`, `license key`, `keygen`, `piracy indie`, `my app was cracked`, `protect electron app`, `obfuscate javascript`.
4. **On-device AI**
   - Subreddits: r/LocalLLaMA (beyond the earlier sweep's threads), r/iOSProgramming (CoreML), r/computervision.
   - Terms: `extract model from app`, `steal model weights app`, `on-device model protection`, `system prompt leaked from app`.
5. **SDK companies that license code per seat or per device**
   - Subreddits: r/computervision, r/androiddev (SDK licence threads beyond the earlier sweep).
   - Terms: `SDK license bypass`, `cracked SDK`, `liveness bypass`. Microblink (Zagreb) is the regional example.
6. **Connected devices and automotive**
   - Subreddits: r/embedded, r/hardwarehacking, r/RightToRepair, r/cars, r/BMW, r/teslamotors.
   - Terms: `feature unlock`, `subscription features hacked`, `firmware unlock`, `coding the car`.
7. **Streaming and media**
   - Subreddits: r/Piracy (read only for attitudes and timing), r/cordcutters.
   - Terms: `Widevine`, `L3`, `modded app`, `DRM broken`.
8. **Ad tech and app fraud**
   - Subreddit: r/adops.
   - Terms: `SDK spoofing`, `install fraud`, `tampered app`.
9. **Security practitioners** (the people who would sell to, or attack, all of the above)
   - Subreddits: r/ReverseEngineering, r/netsec, r/ExploitDev, r/Malware, r/blueteamsec, r/cybersecurity, r/AskNetsec. Look for new threads only.
   - Terms: `GhidraMCP`, `ida-pro-mcp`, `REA mcp`, `LLM deobfuscation`, `AI reverse engineering`, `obfuscation dead`.

Low priority, because their value sits on the server or in the network: social media, marketplaces, messaging, and web SaaS whose logic runs on the server.

## 6. Regional and language subreddits

Reddit has no location filter, so use local developer communities. These are the places where piracy, fraud, or the relevant industries are dense. Search them in the local language as well as English.

| Region | Subreddits to try | Local terms | Why |
| --- | --- | --- | --- |
| Brazil | r/brdev, r/brasil | `app bancário clonado`, `trojan bancário`, `golpe do app` | Heavy mobile banking, many banking trojans |
| India | r/developersIndia, r/india | `UPI fraud app`, `modded APK`, `fake app` | UPI payments, huge Android market |
| Indonesia | r/indonesia | `aplikasi bank palsu`, `APK palsu` | Cloned banking apps (the Group-IB Gigabud campaign, 2026) |
| Germany | r/de_EDV, r/de | `Kopierschutz`, `Raubkopie`, `Freischaltung Auto` | Automotive feature unlocks, audio software |
| Poland | r/Polska, r/programowanie | `piractwo gier`, `Denuvo` | Large PC game studios |
| Nordics | r/sweden, r/Finland, r/norge | mobile games, fintech | Game studios, Promon (Oslo) |
| Benelux | r/belgium, r/thenetherlands | app security, DRM | Guardsquare (Leuven), Irdeto (Amsterdam) |
| Portugal | r/portugal, r/devpt | JavaScript protection | Jscrambler (Porto) |
| Korea and Japan | r/korea, r/japan, r/gachagaming | `game hacking`, `IAP` | Mobile games with heavy in-app purchases |
| Serbia and Croatia | r/serbia, r/croatia, r/programiranje | `piraterija`, `krekovan`, `klonirana aplikacija` | People we can talk to this weekend (Nordeus, Nanobit, Microblink, Infobip) |
| Europe-wide careers | r/cscareerquestionsEU | `app security job`, `anti-cheat engineer` | Hiring as a signal of budget |

Job posts count as evidence. A company hiring "anti-tamper", "anti-cheat", or "app shielding" engineers has a budget line.

## 7. Controversial conversations to find

Capture both sides with quotes. Judges will ask about these.

1. **"Security through obscurity" or real resilience.** Is obfuscation pointless, or does it buy time? Who argues each side, and with what evidence?
2. **"AI makes all client-side protection obsolete".** Posts that claim it, and replies that disagree.
3. **Denuvo and DRM.** Players hate it, studios keep paying, and cracks arrive on a timeline. Look for the launch-window arguments and any numbers.
4. **Kernel anti-cheat and privacy.** Drivers like Vanguard have deep access to the machine, while cheaters use AI to build cheats.
5. **Right to repair and modding.** Car feature subscriptions, tractor and printer firmware locks. Protection is unpopular when it locks owners out.
6. **Legality.** DMCA section 1201, the EU Software Directive's interoperability exception (Article 6), whether AI labs' usage policies allow cracking, and who is liable when an agent cracks a licence.
7. **Open-sourcing the client.** "Just open-source it and charge for the service" as the alternative to protection.
8. **Dual use.** Malware analysts need AI reverse engineering. Will stronger anti-AI obfuscation help malware authors more than app makers?
9. **Is a formal proof worth anything to a buyer?** Look for talk about verified compilers, "proven correct" tooling, and whether security buyers care.

## 8. Search mechanics

- **Time.** Use the last 12 months, weighted to the last 3. Use `t=year` and `t=month`.
- **Methods**, from cheapest to most thorough:
  1. Site search through a web search engine: `site:reddit.com/r/<sub> "<term>"`.
  2. Reddit's own search: `https://www.reddit.com/r/<sub>/search.json?q=<term>&restrict_sr=1&sort=top&t=year`, at about one request every 2 seconds, with a descriptive user agent.
  3. Thread JSON (`<thread-url>.json`) to read the full comment tree.
- **Read the comments, not only the posts.** The experience sits in the replies. Sort comments by top, then scan the controversial sort for objections.
- **Operators.** Combine words with `AND`, `OR`, and quotes, plus `title:` and `selftext:`. Combine section 5's industry terms with these attack terms: `reverse engineer`, `decompile`, `deobfuscate`, `cracked`, `cloned`, `bypass`, `AI`, `LLM`, `Claude`, `ChatGPT`.
- **Commentability.** For each strong thread, record whether it is archived and what the subreddit's rules say about self-promotion and research questions. A human may later choose to reply, and nobody comments now.

## 9. What to return

For each captured item, record:
- the link;
- the subreddit;
- the date;
- the username;
- the author's role, if they state it;
- the region, if it is visible from the subreddit or the text;
- the industry;
- the intent tag;
- a verbatim quote of up to 50 words;
- the score and number of replies;
- whether money or time is named;
- whether the thread is archived.

Never present a paraphrase as a quote. If something is missing, write "not found".

The final summary, in this order:

1. **The answer in five lines.** Where does AI reverse engineering cost real money now? Who says so? How big is the time window?
2. **The three best use cases, ranked by evidence.** For each: the industry, the asset on the device, the time window, what people do today, and the two best quotes.
3. **The strongest objections, quoted.** These come before any support.
4. **Controversies.** Both sides of each one from section 7 that you found.
5. **The measurement gap.** Any thread that asks how to test protection, or rejects the idea.
6. **Regions.** Where the talk was densest, and which regional people we could reach this weekend.
7. **Comparison with the earlier sweep.** What is new, and what contradicts it.
8. **Gaps.** What you searched for and did not find.

## 10. Limits

- **Listen only.** No posts, comments, votes, messages, or joining subreddits. Drafts of any outreach go to a human.
- **Public content only.** No scraping behind logins, no bypassing rate limits, and follow Reddit's API terms.
- **No cracking material.** In piracy and cheating subreddits, record attitudes, timing, and claims. Never record links to cracks, tools, or methods. Do not try to crack, reverse, or test anyone's software.
- **No profiles.** A username and a stated role are enough.
- **Time box.** 3 hours, then file what you have.

## Leads

- Earlier sweep: [[reddit-listener-code-protection-2026-11-07]], [[reddit-sweep-found-no-ask-for-an-ai-crack-score]], [[reddit-five-threads-open-to-a-technical-comment]].
- Companion X prompt: [[where-does-ai-reverse-engineering-cost-money]].
- Parent question: [[do-people-need-ai-resistant-code-protection]].

## Answer
