---
type: question
title: Do people need AI-resistant code protection (and model-weight audits), and what do they say in public?
tags: [market, customer, security, idea]
date: 2026-11-07
by: karla
status: open
owner: karla
---

Listen-first market research on X, Reddit, GitHub, and Hacker News, plus the budget
numbers for the pitch. Context: [[idea-brief-code-protection]],
[[code-protection-project-description]], [[glassbox-project-description]]. Overlaps
items 1, 2, and 5 of [[code-protection-field-open-questions]]; file findings as notes
and link them from both questions.

The brief below is written for an orchestrator agent and can be pasted as is.

# Brief: listen-first market research for two problems

You are an orchestrator agent. Spawn sub-agents, gather what real people say in public, and return one market-research report to Karla. This is fast, informal research for a hackathon pitch on 8 November 2026. It needs real quotes, real links, and real numbers. Nobody expects a formal study.

## 1. Who we are and why this matters

Karla Lučić and her team (Tea Ćetojević Tisaj, Luka Marić, Marko Sladojević) are competing at the Garaža Frontier Hackathon in Belgrade on 7 and 8 November 2026. The prize goes to the team with "the strongest potential to build a startup". Judges reward evidence of buyer understanding more than technical polish. One real quote from a practitioner on a slide is worth more than a feature.

## 2. The two problems

**Problem A (primary): AI makes shipped code cheap to reverse-engineer.**
Every app ships its logic to the user's device. Decompilers turn machine code back into something roughly readable, and AI models now explain that output quickly and cheaply. Payment checks, anti-cheat, licence checks, content protection, and on-device AI models become easier to copy or bypass. Most obfuscation (rewriting code so it is hard to read but behaves the same) was designed against human attackers.

The team's starting idea:
- AI chooses obfuscating rewrites aimed at the points where AI attackers fail.
- A formal proof checks that the rewrite did not change behaviour.
- Simulated AI attackers measure how much harder the code became.

The strongest company angle may be **the measurement itself**: a benchmark of how well code holds up against current AI models. Each run adds data nobody else has. Test this angle explicitly.

**Problem B (secondary): hidden behaviour in open-weight model fine-tunes.**
Companies run open-weight models and fine-tunes they did not train. A fine-tune can carry a hidden trigger that passes normal tests. Most model scanners look for malicious code in files and miss behaviour trained into the weights. The team's earlier idea, Glassbox, audits the weights against the base model and signs a record of what was checked.

## 3. What we need to learn

Test each hypothesis. For each one, report supporting evidence, contradicting evidence, and your verdict with a confidence label (high, moderate, low, or unknown).

| # | Hypothesis | Evidence that supports it | Evidence that kills it |
| --- | --- | --- | --- |
| A1 | Practitioners already see AI-assisted reverse engineering as a real, current threat | Reports of LLM-assisted cracking, cheat development, or app cloning; security teams discussing it | "Everything that matters is on the server anyway"; "obfuscation was always theatre" |
| A2 | Someone already pays to protect client-side code | Mentions of buying Guardsquare, Jscrambler, Digital.ai, Promon, Zimperium, Irdeto, Verimatrix; compliance with OWASP MASVS or EMVCo | Teams use only free tools, or nothing |
| A3 | Breakage is a real pain with obfuscation today (this is what a proof would fix) | Complaints that obfuscation broke builds, crashed apps, slowed performance, or made debugging hard | Nobody mentions breakage |
| A4 | People would value a measured "how hard is my app for AI to crack" score | Requests for benchmarks, red-team scores, or evidence for auditors | Indifference; "a score proves nothing" |
| A5 | Incumbents already market protection against AI attackers | Vendor pages, blogs, press releases (link each) | No vendor makes the claim |
| B1 | Teams worry about the provenance and safety of fine-tunes they did not train | Security reviews blocking open-weight models; questions about trusting Hugging Face models | "We only use API models"; no one cares |
| B2 | Existing scanners are seen as insufficient for weight-level backdoors | Practitioners saying file scanners miss behaviour | Scanners seen as good enough |

For each item, also note **who** said it: their role (security engineer, game developer, mobile developer, ML engineer, founder, investor, or unknown) and their seniority, if visible.

## 4. Sub-agents to spawn

Run these in parallel. Each sub-agent returns raw findings in the format in section 7.

1. **X listener.** Search X for recent posts (the last 6 to 12 months) on: LLM reverse engineering, AI decompilation, Ghidra or IDA with LLMs, obfuscation versus AI, anti-cheat and AI, app cracking with Claude or GPT, mobile app shielding, backdoored LoRA, model weight backdoors, Hugging Face model security. Collect posts with real opinions or experience. Shortlist up to 10 posts where a reply could get useful information (see section 5).
2. **Reddit listener.** Search, read only: r/ReverseEngineering, r/netsec, r/cybersecurity, r/AskNetsec, r/androiddev, r/iOSProgramming, r/gamedev, r/programming, r/MachineLearning, r/LocalLLaMA. Collect threads and comments that bear on the hypotheses. Shortlist up to 5 threads where a comment would be welcome under that subreddit's rules.
3. **GitHub, Hacker News, and community listener.** Read GitHub issues and discussions on obfuscators and reverse-engineering tools: obfuscator-llvm forks, Tigress mentions, javascript-obfuscator, ProGuard and R8, Ghidra and LLM plugins such as GhidraMCP. Look for complaints about breakage and for mentions of AI. Search Hacker News (hn.algolia.com) on the same terms. Read public Discord servers, or other public community spaces, only where you already have access. **Do not open issues or discussions to ask market questions.** That is spam to maintainers.
4. **Budget and market-numbers researcher.** Find sourced numbers for section 6. Every number needs a primary or reputable source, a date, and a confidence label.
5. **Competitor-claims checker.** For each vendor in A5, find what it publicly claims about AI or LLM attackers and about correctness guarantees. Link the page and quote the claim.
6. **Drafting agent.** Draft the X posts and the replies for Karla's approval (section 5). It publishes nothing.
7. **Synthesiser.** Runs last. It merges everything into the report in section 7.

## 5. Posting rules (read before any public action)

Posts and replies go out under Karla's name, so these rules are firm:

- **Karla approves every word before it is published.** The drafting agent hands her the exact text, the target link, and one line on why. She posts it, or explicitly tells an agent to post that exact text. No agent publishes anything on its own judgment.
- **Volume:**
  - X: at most 2 original posts.
  - X replies: at most 10.
  - Reddit: at most 3 comments, and no new posts unless a subreddit explicitly allows that kind of question.
  - No direct messages.
- **Honesty:**
  - Say plainly that Karla is a builder researching the problem at a hackathon.
  - Never pose as a customer, a victim, or a neutral third party.
  - No second accounts.
  - No claims we cannot back up.
- **Ask, don't pitch.** A reply asks one specific question about the other person's experience. It never links a product, because none exists yet.
- **Platform rules win.** Follow each subreddit's self-promotion and survey rules. If a rule is unclear, leave that subreddit as read only.
- **Privacy.** In the report, quote public posts with a link. Do not compile personal profiles of individuals.

### Drafts for Karla (edit freely)

**X post 1 (both problems):**

> Two questions for people who ship software.
>
> 1. An AI agent with a decompiler can now read a shipped app in minutes. Has that changed how you protect client-side code, or does everything that matters already live on the server?
> 2. Would you run someone else's fine-tuned open model in production without checking the weights?
>
> Building in this space at a hackathon in Belgrade this weekend. Blunt answers welcome.

**X post 2 (the contrarian question).** This replaces "this can never be built". Posing the impossibility as a question to argue gets the same reaction without claiming something we don't believe.

> Is AI-proof obfuscation possible at all?
>
> The case against: anything a CPU can run, a patient enough model can eventually read. Obfuscation only buys time, and AI makes time cheap.
>
> Reverse engineers, tell me where that argument breaks.

**Reply templates** (adapt to the post; always one question):

- To a post about LLM-assisted reversing: "Did the obfuscated parts slow the model down much, or did it read straight through? Trying to work out whether current protection still costs an attacker anything."
- To a game developer on cheating: "Have you seen cheats that were clearly built with AI help? Curious whether anti-cheat teams are changing anything because of it."
- To a mobile security engineer: "When you ship protection on an app, what worries you more: someone cracking it, or the protection itself breaking the build?"
- To an ML engineer on open-weight models: "Do you check a fine-tune against its base before running it, or trust the publisher? Asking because we're looking at weight-level audits."

## 6. Numbers we need for the pitch

Find, source, and date each one. When two sources disagree, report both.

- Total worldwide information-security spending for 2025 and 2026 (Gartner or IDC forecasts).
- The application security market, and within it application shielding or in-app protection (analyst estimates). Treat vendor-sponsored reports as low confidence. Luka's pitch claims about $2.7B for shielding in 2026; verify it or replace it.
- Losses that motivate the buyer:
  - revenue lost to game cheating and piracy;
  - mobile banking and payment fraud tied to tampered or cloned apps;
  - cost of content piracy for streaming.
- Compliance drivers:
  - what OWASP MASVS-RESILIENCE asks for;
  - what EMVCo requires for software-based mobile payments;
  - any regulation that names code protection.
- Funding and deals in code protection, for example rounds or acquisitions involving Guardsquare, Digital.ai, Promon, Jscrambler, and Zimperium.
- For Problem B:
  - AI-security deals (for example Palo Alto Networks and Protect AI, Check Point and Lakera), with verified prices;
  - surveys on enterprise adoption of open-weight models and on security review as a blocker.

## 7. What to return

**Raw findings** (each sub-agent), one row per item:
- link;
- platform;
- date;
- author role, if visible;
- short verbatim quote (under 50 words);
- the hypothesis it bears on;
- whether it supports or contradicts that hypothesis;
- signal strength: anecdote, experience, or money mentioned.

**Final report** (the synthesiser), in this order:
1. **The answer in five lines.** Do people need this? Who needs it most? What would they pay for?
2. **Hypothesis table.** A1 to B2, each with a verdict, a confidence label, and the two or three best quotes with links.
3. **Strongest objections people raised.** Put these before the supporting evidence, and quote them.
4. **Segments.** Which group showed the most pain: mobile fintech, games, media, on-device AI, or ML teams?
5. **The measurement angle.** Did anyone ask for, or reject, a benchmark of resistance to AI attackers?
6. **Numbers.** The section 6 numbers, each with a source, date, and confidence label.
7. **Engagement.** For each approved post or reply: the link, the replies received, and what they told us.
8. **Five pitch-ready quotes.** Real, attributable (handle or link), and exactly as written.
9. **Gaps.** What you could not find or could not verify.

## 8. Limits

- Time box: about 4 hours of agent work, then report what you have.
- Never fabricate or paraphrase a quote as if it were verbatim. If you cannot find a source, write "not found".
- Read only public material, with no scraping behind logins and no bypassing of rate limits.
- No offensive work. Do not reverse-engineer, crack, or test anyone's software. This brief covers listening and asking only.

## Leads

Reddit is filed. The question stays `open` until the synthesiser merges every listener below. Do not edit a filed source. Add a new source, then a note per claim, and link both here.

### Filed: Reddit listener (karla+cursor, checked 2026-11-07, Europe/Belgrade)

Raw sweep, verbatim, including both `not found` rows, the comment shortlist, the read-only subreddits, and the coverage note: [[reddit-listener-code-protection-2026-11-07]].

Notes, one per hypothesis, plus the adjacent row and the shortlist. Quotes in the notes are copied from that source. None of them is a verdict.

- A1 [[reddit-comments-say-llms-undo-basic-obfuscation]]
- A2 [[reddit-client-side-protection-spend-is-mixed]]
- A3 [[reddit-obfuscation-breakage-shows-up-as-crashes-and-maintenance]]
- A4 [[reddit-sweep-found-no-ask-for-an-ai-crack-score]]
- A5 [[reddit-sweep-found-no-incumbent-ai-attacker-marketing]]
- B1 [[reddit-weight-backdoor-comments-name-papers-and-supply-chain]]
- B2 [[reddit-comments-say-weight-backdoors-are-hard-to-spot]]
- Adjacent (behaviour-equivalence checking) [[reddit-asks-how-decompiled-output-is-checked-against-behavior]]
- Where a comment is allowed, and which subreddits stayed read-only [[reddit-five-threads-open-to-a-technical-comment]]

### Not filed yet

- X listener.
- GitHub, Hacker News, and community listener.
- Competitor-claims checker. A5 above is the Reddit gap only. Vendor pages are still open (item 2 of [[code-protection-field-open-questions]]).
- Budget and market-numbers researcher. The Denuvo comment is not a market number.
- Drafting agent. Drafts only; Karla sends. Read the shortlist note before drafting a Reddit comment. The sweep contains no drafts.
- Synthesiser. Runs last. Writes `## Answer` and sets `status: answered`.

## Answer

Not answered. Reddit is one listener. The synthesiser fills this section after the others file.
