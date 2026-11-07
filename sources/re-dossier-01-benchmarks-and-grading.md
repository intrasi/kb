---
type: source
title: "Benchmarks for AI/LLM Reverse Engineering and Code Deobfuscation, and Non-Gameable Resilience-Benchmark Methodology"
date: 2026-11-07
by: tea+claude
url:
tags: [security, agents, demo]
---

Research module 01 of the six behind [[re-defense-dossier]], written by tea+claude on 2026-11-07. Filed verbatim; it was first drafted as a note, but it holds many claims, so it is a source until those claims are split into notes. Original path: `research_notes/AI reverse engineering defense dossier/01-benchmarks-and-grading.md`.
Open questions: [[code-protection-field-open-questions]], [[do-people-need-ai-resistant-code-protection]].

# Benchmarks for AI/LLM Reverse Engineering and Code Deobfuscation, and Non-Gameable Resilience-Benchmark Methodology

> **Scope note for the report writer.** The team already holds two dense docs on this topic:
> `AI_RE_Benchmark_Hackathon_Summary.md` and the earlier source pack
> (`Open Agentic Resilience Benchmark…md`). Those establish: the core landscape table
> (CrackMeBench, SRE-Bench, Reveree, BinDeObfBench, JsDeObsBench, LLM4Decompile,
> Decompile-Bench, Promon PDB-LLM, Deconstructing Obfuscation, JSProtect), the Promon
> "63.7% → 8.5%" and Thales "8/10 → 0/10, 970×" headline numbers, the Quarkslab/BAR-2026
> agent-failure recipe, the defence matrix, and the top-line metric list (pass@k, resilience
> lift, cost-to-break, false-confidence, overhead). **This note does not repeat those; it
> adds (a) benchmarks the team docs missed, (b) tighter grading/oracle internals with the
> full numbers, (c) the SWE-bench retraction broken down precisely, and (d) contamination
> mechanics.** Items flagged **[NEW]** are not in either team doc.
>
> **Aging caveat (applies throughout):** every model-specific number below is a dated
> snapshot. Results are tied to Opus 4.5–5.5 / GPT-5.5–6.1 / Gemini 3.x / Kimi K2–K3 /
> Grok 4.x, which rotate monthly. Attacker and defender share the same frontier models, so
> any "lift" decays. Treat all vendor numbers (Promon, Thales, Jscrambler, Digital.ai,
> General Analysis) as lower-confidence, commercially-interested sources.

## What each benchmark measures, how it grades, dataset size, public status

### Takeaway
The attacker/capability side is crowded and growing; at least four benchmarks the team docs do not list exist (**MalwareBench, AgentRE-Bench, BinMetric, RARE-Bench**). No benchmark measures *defensive lift of a protection config against a budgeted tool-using agent* — that remains the open gap. The clearest methodological trend across the strongest 2026 benchmarks is: private/self-authored programs + deterministic external graders + explicit refusal accounting.

### Cited Findings
- **CrackMeBench** (David & Gervais, UCL; arXiv 2605.10597). Confirmed: given only an executable, agent must recover validation logic and produce an accepted input/serial/artifact/keygen. External executable oracles, symbol-poor binaries, shell-command protocol (not GUI), externally scored submissions, no-network Docker. v0 = 8 public calibration CrackMes + 12 generated main-score tasks from seeded C/Rust/Go templates. **[NEW detail]** A later survey measures its scale at **~36.1 LoC per instance** and notes protections stay "textbook-level (simple keygens, miniature VMs)." — [alphaxiv](https://www.alphaxiv.org/abs/2605.10597); [survey 2608.11469](https://arxiv.org/html/2608.11469v2)
- **AgentRE-Bench [NEW]** — named alongside CrackMeBench as the other strong-contamination-control benchmark, built from **13 self-developed programs, ~63.5 LoC per instance**; also small-scale with textbook protections. — [SRE-Bench paper 2608.11469](https://arxiv.org/html/2608.11469v2)
- **SRE-Bench** (Columbia DAPLab + Vals AI + UC Berkeley; arXiv 2608.11469). Confirmed: 19 private programs (avg 16.9K LoC), 44 in-house anti-analysis primitives → 262 binary instances, 1,572 deterministically graded tasks, 6 tasks/instance, >5,000 expert hours, 5 domains / 4 languages. Isolated container; agent gets binary + task + domain aux materials + standard RE toolkit; **no source, no grader code, no reference solutions**; submissions scored deterministically by a grading server. "Solved" = all 6 tasks pass. Binaries deliberately **not released**. — [DAPLab](https://daplab.cs.columbia.edu/projects/sre-bench/); [arXiv](https://arxiv.org/html/2608.11469)
- **MalwareBench** (General Analysis; malwarebench.com) **[NEW — entirely absent from team docs]**. First end-to-end cross-platform eval of frontier models on *malware* RE. Each case: produce a behavioral analysis **and a reusable artifact extractor** tested on held-out malware variants + benign files. Grading: findings scored against "field contracts"; a separate verifier checks findings, recovered bytes, and the extractor; reported as **best@3 / mean@3**. Fields calibrated so they are **answerable from source (>80%) but not guessable without the binary (≤5%)** — an explicit anti-contamination/anti-guessing calibration worth copying. 12 cases (5 Windows PE, 3 Linux ELF, 2 macOS Mach-O, 2 Android APK); **20-hour wall-clock budget per case**. Public: tasks, model traces, runnable sample browsable; license/full-download not stated. — [General Analysis](https://generalanalysis.com/malwarebench)
- **BinMetric** (Shang et al., arXiv 2505.07360) **[NEW]** — "a benchmark of 1000 questions pertaining to common real-world binary analysis tasks." No LoC/program-count/contamination/public status given in the survey that cites it. — [survey 2604.14317](https://arxiv.org/html/2604.14317v1)
- **RARE-Bench** (within "When Binaries Talk Back," arXiv 2607.12507) **[NEW]** — pairs **clean, control, and adversarial binaries** with behavior oracles and **counts unresolved outputs as null, not safe**; controls included so tool-output noise is not scored as attack success. Corpus is synthetic inert ELF/x86-64. (See grading/contamination sections — this is a design template, not a capability leaderboard.) — [arXiv](https://arxiv.org/html/2607.12507v1)
- **Reveree / BinDeObfBench / JsDeObsBench / LLM4Decompile / Decompile-Bench / Promon PDB-LLM / Deconstructing Obfuscation / JSProtect** — see team docs; numbers there confirmed against search snippets, not re-listed here.

### Inferences
- The field has split into four benchmark archetypes the resilience benchmark should position against: (1) **small self-authored keygen/CrackMe** (CrackMeBench, AgentRE-Bench) — strong contamination control, weak protections, tiny LoC; (2) **large private hardened** (SRE-Bench) — realistic scale + anti-analysis but measures attacker capability on *fixed* binaries, not protection deltas; (3) **domain end-to-end** (MalwareBench) — artifact-extractor grading + held-out variants + cost-per-run; (4) **integrity/threat-model** (RARE-Bench) — scores the *role* an observation is given, not just extraction.
- MalwareBench's "answerable from source >80%, not-guessable-without-binary ≤5%" calibration is the single most directly copyable idea for making a resilience benchmark non-gameable, and neither team doc has it.

### Gaps
- Could not fetch full PDFs of 2604.14317 and 2607.12507 (FlateDecode); used arXiv HTML, which for the survey exposed only BinMetric by name — AgentRE-Bench/SRE-Bench comparison rows came from the SRE-Bench paper's own related-work, not the survey.
- No independent confirmation of BinMetric's size/grading; single secondary citation only.

## Measured numbers each reports (success, lift, cost-to-break, tokens)

### Takeaway
The newest and most honest numbers are *low and expensive*: MalwareBench's best model scores single-digit percent at $100+/run, and SRE-Bench's apparent 82.3% leader is an artifact of refusing the hardest third of the set. Real cost-to-break data is now emerging beyond Thales.

### Cited Findings
- **MalwareBench [NEW numbers].** Best@3 headline: GPT-6.1 Sol **7.6%** overall; overall mean@3 across all traces **6.7%**. Mean@3 by config (with ~cost/run): GPT-6.1 Sol/General Analyst 4.4% ($116.5); GPT-6 Astra/General Analyst 4.3% ($250.1); GPT-6.1 Sol/Codex 2.0% ($112.6); GPT-6 Astra/Codex 1.9% ($722.8); Claude Opus 5.5/Claude Code 1.1% ($158.5); Gemini 3.8 Flash/Gemini CLI 1.0% ($12.2); Grok 4.7/Grok Build 0.4% ($69.6). Per-case best ranged Woopsie 19.0% / Conti 18.8% / Sliver 15.5% down to several 0.0%. **Human analysts with AI assistance scored >90%, median solve 12 hours.** Cases built to **zero detections across 70+ VirusTotal scanners** at screening. — [General Analysis](https://generalanalysis.com/malwarebench)
- **SRE-Bench [NEW breakdown].** GPT-6-Astra leads at **5.55/6 mean**, fully solving **149/181 gradable (82.3%)**, only 3.9% of gradable get no credit — **but refusals left only 181/262 gradable (69.1%)**. GPT-5.6-Sol fully solves 31.5%, Claude-Fable-5.1 26.9%. **Astra's lead has an asterisk: its high per-instance score is partly because it refused the hardest/most-sensitive instances, which are then excluded from its denominator.** Contrast: gpt-5.6-sol was graded on 254 instances, claude-opus-5 on 256 — i.e. far fewer refusals, so their lower scores are over a harder effective set. — [DAPLab](https://daplab.cs.columbia.edu/projects/sre-bench/); [benchmarklist](https://benchmarklist.com/benchmarks/sre_bench/)
- **"When LLM Decompilers Recompile More and Preserve Less" (Decompile-Diverge, arXiv 2609.05370) [full table NEW].** On the GitHub track (n=291): LLM4Decompile Build **90%**, Matched **62%**, Divergence 28%; Ghidra baseline Build 75%, Matched 74%. So **LLM4Decompile raises Build +15 pts but lowers Matched −12 pts.** CVE track (n=287): LLM4Decompile Build 64% / Matched 38% / Divergence 17% **plus a 9% Crash-Absence rate** (a reference crash silently disappears). Nova: GitHub Build 11% / Matched 3%; CVE Build 5% / Matched 0%. — [arXiv](https://arxiv.org/html/2609.05370v1)
- **Promon / Thales / LLM4Decompile-under-OLLVM / Deconstructing Obfuscation / JSProtect / JsDeObsBench** numbers: see team docs (confirmed, not re-listed).

### Inferences
- The honest 2026 success rates for *hard, contamination-controlled* RE are single-digit to low-double-digit percent at high dollar cost — which strongly supports a **cost-to-break / survival-curve** framing over a single pass@k number. A resilience benchmark whose unprotected baseline is near-saturated is measuring the wrong (too-easy) programs.
- Refusals systematically *inflate* leaderboard scores when excluded from the denominator (SRE-Bench). This is the opposite of the resilience-benchmark failure mode, where refusals must not be counted as defence wins — both directions corrupt the number, so refusals need their own reported column either way.

### Gaps
- MalwareBench cost figures are vendor-reported and configuration-dependent (agent harness matters as much as model); no third-party replication.

## How to grade honestly (oracles, differential fuzzing, why re-exec and LLM-judges are traps, refusals)

### Takeaway
The strongest available evidence says: grade with an external executable oracle plus **differential fuzzing against the original binary**; treat re-executability and LLM-judges as upper-bound proxies only; and report refusals as a separate column, never folded into either success or resilience.

### Cited Findings
- **Differential fuzzing is now empirically validated as necessary.** Decompile-Diverge builds its oracle by synthesizing a driver, fuzzing the *original* with **AFL++** to build an input corpus (no hand-written assertions), then splicing each candidate in and comparing a "bounded observable post-state" (return values, bytes written, writable globals) on an uninstrumented -O0 build, with an ASan build to catch crashes/hangs. Labels: Matched / Divergence / Crash-Absence. Divergence counts only if it reproduces across **4 reruns** (flakiness guard). Mean line coverage 84–99%, branch 74–97%. — [arXiv 2609.05370](https://arxiv.org/html/2609.05370v1)
- **Re-executability overstates correctness — quantified [NEW precise numbers].** On four established corpora, **4.9% of 12,133 candidates that passed every shipped test still diverged** on the generated corpus; for one system (Nova on HumanEval) this reached **13%**. Across 15,379 doubly-scored candidates, **3.9% passed all shipped tests yet diverged**, and 1.2% failed a shipped test but were actually Matched. **Shipped suites missed 3%–45% of divergence** depending on corpus. → shipped-test pass rate is not evidence of correctness; Matched is an *upper bound*, Divergence/Crash-Absence are *lower bounds*. — [arXiv 2609.05370](https://arxiv.org/html/2609.05370v1)
- **Score the role of an observation, not its presence (integrity grading) [NEW].** RARE-Bench argues "extraction correctness is not the security boundary" and grades whether a binary-derived observation is wrongly promoted to instruction authority / claim-validating evidence / trusted state. Key graded result: a naive "Support Gate" counting tool records separately validated **23/40 false claims**, and with fused multi-tool drafts validated **32/32** false claims; a **Provenance Gate** grouping records by shared origin validated **0** while retaining all genuinely-supported claims. Lesson for any agentic grader: **crediting repeated/fused tool views as independent evidence overstates results.** — [arXiv 2607.12507](https://arxiv.org/html/2607.12507v1)
- **Refusal accounting.** SRE-Bench computes metrics over gradable instances only and names refusals explicitly (181/262 for its top model) — i.e. it is transparent that refusals shrink the denominator. MalwareBench similarly reports Claude Opus 5.5 at max effort **failed 26% of rollouts to safeguards before resampling**. — [DAPLab](https://daplab.cs.columbia.edu/projects/sre-bench/); [General Analysis](https://generalanalysis.com/malwarebench)

### Inferences
- A defensible resilience grader = **external oracle (keygen accepted / exact flag / exit-code) for pass/fail + differential-fuzz oracle (AFL++, bounded post-state, 4-rerun divergence guard) for "algorithm recovery" tasks.** This is directly borrowable from Decompile-Diverge and avoids both the re-exec trap and LLM-judge subjectivity.
- Why LLM-judge is a trap (synthesizing team docs + RARE): it has no ground truth, can be prompt-injected by content lifted from the binary, and tends to credit fused/repeated observations — RARE shows deterministic provenance-aware counting beats judge-style aggregation. Keep any LLM-judge strictly outcome-blinded and secondary (Reveree's pattern), never the pass/fail signal.

### Gaps
- No published differential-fuzzing oracle exists yet *for protected/obfuscated* binaries specifically (Decompile-Diverge fuzzes unprotected references); building one against heavily-flattened/virtualized originals (which run slowly) may have throughput problems worth flagging to the build team.

## Contamination control and the SWE-bench retraction lesson

### Takeaway
Canary strings are necessary but insufficient; the SWE-bench retraction shows the deadliest failures are **broken oracles** (too-narrow and too-wide tests) and **training-data contamination that canaries don't stop**, both of which require active auditing and a human/reference solver on every task.

### Cited Findings
- **SWE-bench Verified retraction, broken down [NEW precision].** OpenAI stopped reporting it (Feb 2026). Of **138 audited problematic hard tasks: 49 tests were too narrow** (rejected functionally-correct solutions) and **26 too wide** (required features the problem never mentioned). Article states ">60% of remaining problems unsolvable" but 75/138 ≈ 54% — the denominator isn't reconciled, flag as imprecise. Saturation: most frontier models ~80%, and original authors say don't declare saturation below ~87–95%; one OpenAI evaluator called it "effectively saturated and highly contaminated." — [latent.space](https://www.latent.space/p/swe-bench-dead)
- **Contamination that canaries don't catch [NEW].** Every frontier model tested could **reproduce gold patches or problem statements verbatim given only the task ID**. GPT-5.2's chain-of-thought appeared to recall a *later* repo version's implementation of an argument the task never specified. A dedicated **contamination-auditor agent** found evidence in OpenAI models, Claude Opus 4.5, and Gemini Flash; one evaluator estimated GPT-5.2 solved ~31 problems that should be near-impossible without contamination. Explicit stated lesson: **"canary strings don't prevent leakage from scraped public repos, so contamination needs active auditing."** SWE-Bench Pro, by contrast, showed only light familiarity signals in a couple of models. — [latent.space](https://www.latent.space/p/swe-bench-dead)
- **Oracle-validation lesson.** Tests should accept any reasonable implementation, not only the authors' chosen one; automated pass rates don't capture design quality. (OpenAI also later pulled its SWE-Bench Pro recommendation, ~30% broken — per team docs, arXiv 2608.13867.) — [latent.space](https://www.latent.space/p/swe-bench-dead)
- **Positive contamination-control templates.** MalwareBench's per-field calibration (≥80% from source, ≤5% guessable without binary) is a numeric guardrail against leakage. Promon stripped descriptive identifiers (no `hash_djb2`) so models can't pattern-match by name (team docs). SRE-Bench + CrackMeBench + AgentRE-Bench all use self-authored/private programs precisely because public corpora are contaminated. — [General Analysis](https://generalanalysis.com/malwarebench); [SRE-Bench](https://daplab.cs.columbia.edu/projects/sre-bench/)

### Inferences
- Direct transfer to the resilience benchmark: (1) **every task must be solved by a human or reference solver before inclusion** — an unsolvable task is a broken oracle, not a hard one; (2) keep a **private held-out split regenerated with new seeds per release** (canaries alone fail); (3) **run a contamination-auditor pass** (prompt the model with task ID / stripped stub and check for verbatim recall); (4) because programs are self-authored and seeded, this benchmark is structurally less contamination-prone than SWE-bench — that is a genuine selling point.
- The "too-narrow vs too-wide" dichotomy maps onto the resilience benchmark's keygen oracle (too-narrow: accept only one valid key when many exist → use the program's own validator as oracle, not a fixed key) and algorithm-recovery grader (too-wide: don't require incidental implementation details → compare observable behavior via differential fuzzing).

### Gaps
- OpenAI's primary blog post (openai.com/index/why-we-no-longer-evaluate-swe-bench-verified) returned HTTP 403; all SWE-bench numbers here are via the Latent Space secondary summary of that post + team docs. The 54% vs ">60%" discrepancy is unresolved — writer should treat the 49/26-of-138 split as the firm figures.

## What metrics a resilience benchmark should report

### Takeaway
Report the full vector the team docs already name — pass@1/pass@k, resilience lift with bootstrap CIs, cost-to-break (tokens/$/minutes among successes), false-confidence rate, overhead — and add, from the newest evidence, a **survival curve vs budget**, a **separate refusal column**, and a **provenance-aware grading guard**.

### Cited Findings
- **Survival curve over budget, not one number.** Thales' 970× token figure and MalwareBench's 20-hour budgets show protection buys *cost*, not impossibility — success must be reported as a function of token/wall-clock budget. (team docs + MalwareBench) — [General Analysis](https://generalanalysis.com/malwarebench)
- **best@k / mean@k are both in use.** MalwareBench reports best@3 and mean@3 side by side; the gap between them measures variance/luck. SRE-Bench reports "fully solved" (all-6) as its headline. A resilience benchmark should report pass@1 (single-shot realism) and pass@k (capability ceiling) and the spread. — [General Analysis](https://generalanalysis.com/malwarebench); [DAPLab](https://daplab.cs.columbia.edu/projects/sre-bench/)
- **Refusals as a first-class, separate column.** SRE-Bench's gradable-denominator problem (181/262) and MalwareBench's 26% safeguard-failure both show refusals must be visible, not silently excluded or folded into "resilience." — [DAPLab](https://daplab.cs.columbia.edu/projects/sre-bench/); [General Analysis](https://generalanalysis.com/malwarebench)
- **Cost-per-run is now standard in the newest benchmark.** MalwareBench prices every config ($2–$722/run), making $-per-break a reportable, comparable axis. — [General Analysis](https://generalanalysis.com/malwarebench)

### Inferences
- Recommended reporting vector (consolidated): **(1)** failure_rate(protected) − failure_rate(unprotected) = resilience lift, with bootstrap 95% CIs, per model × config × arch; **(2)** pass@1 and pass@k with the best−mean spread; **(3)** cost-to-break = median tokens, $, wall-clock among *successes*, plotted as a survival curve vs budget; **(4)** false-confidence rate (agent submits wrong answer claiming success — Quarkslab); **(5)** refusal rate as its own column; **(6)** defence overhead (runtime ×, binary size × — Tigress virtualization is 42–247×, team docs); **(7)** a provenance/false-evidence-validation rate if the grader aggregates multi-tool agent claims (RARE).
- Every row must carry model ID + date + harness, because the lift is a decaying snapshot.

### Gaps
- No existing benchmark reports *resilience lift with CIs* directly — this remains genuinely novel; the CI methodology (bootstrap over seeds/attempts) is the team's to define, no published template found for the RE-protection setting specifically.

## Additional sources consulted
- CrackMeBench — https://www.alphaxiv.org/abs/2605.10597 ; https://arxiv.org/html/2605.10597v1
- SRE-Bench — https://daplab.cs.columbia.edu/projects/sre-bench/ ; https://arxiv.org/html/2608.11469 ; https://benchmarklist.com/benchmarks/sre_bench/
- MalwareBench [NEW] — https://generalanalysis.com/malwarebench
- Decompile-Diverge / "Recompile More, Preserve Less" — https://arxiv.org/html/2609.05370v1
- "When Binaries Talk Back" / RARE-Bench [NEW] — https://arxiv.org/html/2607.12507v1
- Agentic RE survey (names BinMetric) [NEW] — https://arxiv.org/html/2604.14317v1
- SWE-bench retraction — https://www.latent.space/p/swe-bench-dead (primary OpenAI post returned 403)
