---
type: source
title: "Formal Verification of Semantic Equivalence Between Original and Obfuscated Programs"
date: 2026-11-07
by: tea+claude
url:
tags: [formal-methods, security]
---

Research module 04 of the six behind [[re-defense-dossier]], written by tea+claude on 2026-11-07. Filed verbatim; it was first drafted as a note, but it holds many claims, so it is a source until those claims are split into notes. Original path: `research_notes/AI reverse engineering defense dossier/04-formal-verification-equivalence.md`.
Open questions: [[code-protection-field-open-questions]], [[do-people-need-ai-resistant-code-protection]].

# Formal Verification of Semantic Equivalence Between Original and Obfuscated Programs

> Scope note for the report writer: this dossier page pressure-tests the team's central
> pitch claim — "we prove the protected code behaves identically to the original." The
> team's own brief already concedes the hardest point (brief: "The strongest obfuscation
> methods, which mix arithmetic and logic tricks, are designed to defeat exactly the
> solvers used for proofs. Proofs are realistic for small, critical functions."). The
> research below confirms that concession is correct and sharpens it with numbers, and it
> separates three tiers throughout: **[THEORY]** theoretically possible, **[TOOL]**
> tool-supported today, **[48H]** buildable in a weekend. The honest headline: a team can
> truthfully say "proven equivalent" only for small, loop-bounded functions, or for
> transformations whose rule was proven once in a proof assistant; everything else is
> "tested, not proven," and saying otherwise is overclaiming.

## Q1: Core approach — encode programs as logic, ask an SMT solver "is there any input where original(x) != transformed(x)?"

### Takeaway
The standard method is to compile both programs into a single logical formula asserting
their outputs differ on some shared input, then hand it to an SMT solver: **UNSAT = proven
equivalent for all modeled inputs; SAT = a concrete counterexample input**. This is exactly
how Alive2 validates LLVM optimizations, and it is sound *only* within the modeling choices
(fixed-width bitvectors, bounded loops, a chosen memory model).

### Cited Findings
- Alive2 is a "bounded translation validation" tool: it takes the source and target of an
  optimization, encodes both in SMT, and checks refinement; it reported 47 new LLVM bugs
  (28 fixed) from the unit-test suite plus 8 patches to the LLVM Language Reference, with
  running totals cited as "more than 50" / "54 bugs" — demonstrating the encode-and-solve
  equivalence pattern working at production scale — [Alive2 PLDI'21](https://users.cs.utah.edu/~regehr/alive2-pldi21.pdf); [SNU dissertation](https://sf.snu.ac.kr/juneyoung.lee/thesis/thesis.pdf)
- Modern SMT solvers decide the theory **QF_BV** (quantifier-free fixed-size bitvectors),
  which models machine integers exactly: a 32-bit `int` is a 32-bit bitvector, and `+`,
  `*`, `<<`, `&`, `^` are the bitvector operations, so two's-complement **overflow / wraparound
  is modeled precisely** (it wraps mod 2^n by construction, not as an approximation) — this is
  why bitvector reasoning, not integer arithmetic, is the correct basis for proving
  machine-code equivalence — [cvc5](https://cvc5.github.io/) / SMT-LIB QF_BV theory (general solver documentation)
- Memory is modeled as an SMT **array** (`(Array (_ BitVec 64) (_ BitVec 8))`): a load is
  `select(mem, addr)`, a store is `store(mem, addr, val)`; Alive2's CAV'21 work built a
  dedicated SMT encoding of LLVM's memory model (pointers, provenance, `undef`/`poison`) and
  with it found 21 new memory-optimization bugs (10 fixed) — showing memory-as-array is
  tractable but that the *semantics around* memory (UB, provenance) is where soundness is
  hard — [Alive2 memory CAV'21](https://web.ist.utl.pt/nuno.lopes/pubs/alive2-mem-cav21.pdf)
- The decision procedure under the hood is **bit-blasting**: the bitvector formula is
  lowered to a propositional SAT instance; this is complete for QF_BV but its cost blows up
  with multiplication and wide operands — the mechanism MBA obfuscation deliberately targets
  (see Q5) — [USPTO MBA opaque-predicate patent](https://image-ppubs.uspto.gov/dirsearch-public/print/downloadPdf/12585460)

### Inferences
- The query the team wants is `assert(original(x) != transformed(x))`; UNSAT proves
  `forall x. original(x) == transformed(x)` *within the model*. The honesty gap is entirely
  in the phrase "within the model": fixed bitwidth is exact, but any loop bound, any memory
  abstraction, and any assumed absence of UB is a place where a true proof silently narrows
  to a bounded one.
- "Proven equivalent" is only as strong as the encoding of I/O and side effects. For pure
  arithmetic functions (the obfuscation sweet spot — MBA, opaque predicates) the encoding is
  clean and the proof is genuine. For functions that touch memory, make syscalls, or have
  data-dependent loops, the encoding introduces either bounds or abstractions that weaken the
  claim.

### Gaps
- No single authoritative "equivalence-checking methodology" standard exists; the technique
  is assembled per-tool, so claims must be tool-specific.

## Q2: Tool families, concrete tools, and their limits

### Takeaway
Four families, in descending order of automation and ascending order of strength-of-claim:
(1) raw SMT solvers; (2) bounded model checkers (sound only up to a loop bound); (3) symbolic
execution (sound but hits path explosion); (4) interactive theorem provers (unbounded, true
proof, but person-years of labor). Translation validators (Alive2) sit on top of SMT as the
most production-proven equivalence tool today.

### Cited Findings
- **SMT solvers — Z3, cvc5, Bitwuzla.** Z3 (Microsoft) is the de-facto default; cvc5 is the
  successor to CVC4 and competitive on bitvectors; Bitwuzla is a specialist QF_BV/arrays/FP
  solver that regularly wins the SMT-COMP bitvector divisions. All decide QF_BV completely in
  principle but can time out in practice (see MBA, Q5) — [cvc5](https://cvc5.github.io/)
- **Bounded model checking — CBMC, ESBMC.** CBMC syntactically unwinds each loop to a bound
  *k*, inserts an **unwinding assertion** `¬G` after the last copy, and bit-blasts to SMT/SAT.
  Its key limitation: "CBMC currently does not increase the maximum length of paths ... and is
  thus not complete"; it proves absence of counterexamples only up to *k* unless all unwinding
  assertions pass (which proves *k* is a sufficient completeness threshold). Formula size grows
  O(k) per loop body — [CBMC paper arXiv:2302.02384](https://arxiv.org/pdf/2302.02384); [CPROVER manual](http://www.cprover.org/cbmc/doc/cbmc-techreport.pdf)
- **The loop-unrolling limitation (central caveat).** For a data-dependent or unbounded loop,
  BMC proves equivalence only for executions that finish within *k* iterations. Unless the
  unwinding assertion fires-and-passes (establishing a completeness threshold), a BMC "pass" is
  a *bounded* result, not a full proof — this is the single most common source of overclaiming — [CBMC paper arXiv:2302.02384](https://arxiv.org/pdf/2302.02384)
- **Symbolic execution — KLEE, angr.** Explores feasible paths, solving path conditions with
  an SMT solver. Suffers **path explosion**: the number of paths grows exponentially with
  branches, and loops/complex constructs make it "difficult to scale in practice" — ARDiff
  (built on symbolic execution for equivalence) names loops and non-linear arithmetic as the
  scaling killers — [ARDiff](https://www3.ntu.edu.sg/home/yi_li/files/Badihi2020ASP.pdf)
- **Interactive theorem proving — Coq/Rocq, Lean, Isabelle.** Unbounded, machine-checked
  proofs, no loop bound, no path limit — but manual. **CompCert** is the canonical cost
  benchmark: the mature verified C compiler is "100,000 lines of Coq and six person-years";
  the original 2009 version was ~42,000 lines / ~3 person-years, of which 76% was the
  correctness proof itself — [AbsInt CompCert structure](https://www.absint.com/compcert/structure.htm); [Leroy CACM](https://xavierleroy.org/publi/compcert-CACM.pdf)
- **Abstract interpretation — Astrée.** Sound static analyzer that over-approximates program
  behavior to prove *properties* (e.g., absence of runtime errors in Airbus flight-control C);
  it proves safety, not two-program equivalence, so it is adjacent, not a direct equivalence
  tool — (Astrée is a general sound-analysis reference; not an equivalence checker)
- **Translation validation — Alive2.** The most battle-tested equivalence tool: validates a
  compiler's *actual output* against its input per optimization, bounded. 47+ real LLVM bugs,
  8 LangRef fixes (Q1 sources). This is the strongest existing evidence that per-build
  equivalence checking of real, non-trivial code works today — [Alive2 PLDI'21](https://users.cs.utah.edu/~regehr/alive2-pldi21.pdf)

### Inferences
- The team's two realistic paths are **BMC/SMT per-build (Alive2-style)** and **theorem-proving
  the rules once (CompCert-style)**; symbolic execution and abstract interpretation are
  supporting techniques, not the spine of an equivalence product.
- CompCert's six-person-years is the honest price tag for "prove it unboundedly in a proof
  assistant." A weekend hackathon cannot produce that; it can only reuse an existing proven
  rule or do bounded checking.

### Gaps
- No public measured comparison of Z3 vs cvc5 vs Bitwuzla specifically on *obfuscated-code
  equivalence* benchmarks; solver choice guidance is inferred from SMT-COMP bitvector results.

## Q3: Handling real programs — product programs, invariants, regression verification, memory

### Takeaway
To compare two programs you build a **product program** (or self-composition) so one formula
relates both executions; loops require a **simulation relation / loop invariant** proved by
induction (BMC dodges this by bounding instead). Regression-verification tools (RVT, SymDiff,
Galois SAW) exploit structural *similarity* between versions — which is exactly the situation
for original-vs-obfuscated.

### Cited Findings
- **Product programs / self-composition.** The equivalence of P1 and P2 is reduced to a
  property of one combined program that runs both on the same input and asserts outputs match;
  this lets a single verification condition (VC) capture the relation. SymDiff takes this route
  at the Boogie VC level rather than enumerating paths — [SymDiff (MSR)](https://www.microsoft.com/en-us/research/wp-content/uploads/2016/02/paper-44.pdf)
- **Loop invariants / simulation relations / induction.** For unbounded loops, a true proof
  needs an inductive invariant (or a lock-step simulation relation between the two loops)
  rather than unrolling; this is the step that resists automation and is where theorem-proving
  effort concentrates. Recent work (2026) tries to infer these with LLMs for "sound,
  LLM-inferred regression verification," underscoring that invariant inference is the bottleneck — [Partial Contracts Suffice arXiv:2607.10291](https://arxiv.org/pdf/2607.10291)
- **Regression verification (RVT).** Proves **partial equivalence** of two *similar* program
  versions, abstracting called functions as uninterpreted functions so the proof is modular
  and scales with the *diff*, not the whole program — [Regression Verification (STVR)](https://ofers.dds.technion.ac.il/publications/stvr12.pdf)
- **SymDiff.** Language-agnostic semantic-diff over the Boogie intermediate verification
  language (reusable across C, C#, x86); demonstrated proving equivalence of "about 10 programs
  of several hundreds of lines each," flagging semantically different functions "typically
  within less than a minute." Crucial limitation: it checks **only partial equivalence** and
  "can only prove equivalence but cannot disprove it"; precision via inlining trades against
  scalability — [SymDiff (MSR)](https://www.microsoft.com/en-us/research/wp-content/uploads/2016/02/paper-44.pdf)
- **Galois SAW (Software Analysis Workbench) / Cryptol.** Industrial equivalence proving:
  symbolically executes code to a logical model and proves it equivalent to a reference spec
  via SAT/SMT; used to verify real crypto implementations (e.g., AWS s2n HMAC, Java/C/LLVM).
  It works precisely because crypto primitives are loop-bounded and memory-structured — the
  same shape as "small critical function" (SAW general documentation / Galois published case
  studies; see also regression-verification literature above)
- **Memory modeling.** Beyond memory-as-array (Q1), equivalence tools must agree on a memory
  layout for both sides; Alive2's dedicated memory encoding (pointers, provenance, poison) is
  the state of the art and still only *bounded* — [Alive2 memory CAV'21](https://web.ist.utl.pt/nuno.lopes/pubs/alive2-mem-cav21.pdf)

### Inferences
- Original-vs-obfuscated is the *ideal* case for regression verification: the two programs are
  behaviorally identical by construction and often structurally related, so RVT/SymDiff-style
  decomposition should apply better here than to arbitrary program pairs.
- But obfuscation that *destroys* structural similarity (control-flow flattening, MBA) removes
  the very similarity RVT relies on, pushing you back to whole-function SMT — which is exactly
  where MBA then times out (Q5). The team cannot have both "maximally confusing to attackers"
  and "easy to prove equivalent" from the same automatic pipeline.

### Gaps
- No measured data found on how far RVT/SymDiff degrade specifically when the transformation is
  adversarial obfuscation rather than a benign refactor.

## Q4: Scaling reality — how large a function can equivalence tools actually handle?

### Takeaway
In practice, automatic per-build equivalence is reliable only at the scale of **single small
functions / a few hundred lines with bounded loops** — SymDiff's demonstrated regime, Alive2's
per-optimization snippets, SAW's crypto primitives. This cap is precisely why the "formal
proof" pitch cannot honestly cover a whole application; it covers *critical functions*, which
is what the team's brief already says.

### Cited Findings
- SymDiff's reported empirical regime: "about 10 programs of several hundreds of lines each,"
  decisions "within less than a minute" — and that is for *similar* versions, the easy case — [SymDiff (MSR)](https://www.microsoft.com/en-us/research/wp-content/uploads/2016/02/paper-44.pdf)
- Alive2 operates per-optimization on IR snippets and is explicitly **bounded** translation
  validation — it does not attempt whole-module unbounded equivalence — [Alive2 PLDI'21](https://users.cs.utah.edu/~regehr/alive2-pldi21.pdf)
- The unbounded alternative costs CompCert's **six person-years / 100k lines of Coq** for a
  compiler, i.e., it is a research-program-scale investment, not a per-build automatic step — [AbsInt CompCert](https://www.absint.com/compcert/structure.htm)
- Symbolic-execution-based equivalence "is difficult to scale in practice due to complex
  programming constructs such as loops and non-linear arithmetic" — the scaling wall is
  structural, not just engineering — [ARDiff](https://www3.ntu.edu.sg/home/yi_li/files/Badihi2020ASP.pdf)
- **Verified-obfuscation academic work** (the only existing "prove the obfuscation correct"
  results):
  - **Blazy & Trieu, "Formal verification of control-flow graph flattening" (CPP 2016):** CFG
    flattening *and* opaque-predicate insertion proven semantics-preserving in Coq, integrated
    as a pass into CompCert (Clight level, CompCert 2.5), so compilation correctness follows
    "for free." Notably, opaque predicates "required no lemma" while CFG flattening "required a
    number of intermediate lemmas" — i.e., proof cost tracks obfuscation potency — [Blazy & Trieu CPP 2016](https://www.irisa.fr/celtique/ext/cfg-flatten/cpp2016.pdf); [project page](https://www.irisa.fr/celtique/ext/cfg-flatten/)
  - **Blazy & Hutin, "Formal verification of a program obfuscation based on mixed
    Boolean-arithmetic expressions" (CPP 2019):** an MBA *data* obfuscation proven correct in
    Coq and added as a CompCert pass — proof done *once*, not per-build — [ResearchGate](https://www.researchgate.net/publication/330157198_Formal_verification_of_a_program_obfuscation_based_on_mixed_Boolean-arithmetic_expressions)
  - **University of Ottawa, Weiyun Lu (M.Sc. thesis, 2019, supervised by Amy Felty),
    "Formally Verified Code Obfuscation in the Coq Proof Assistant":** formalizes
    semantics-preservation of obfuscating transformations over the IMP imperative language in
    Coq, using Hoare logic and a flowchart language for flattening; companion paper by Felty &
    Lu — [uOttawa thesis](https://ruor.uottawa.ca/handle/10393/39994); [Felty & Lu paper](https://www.site.uottawa.ca/~afelty/dist/sad20.pdf)

### Inferences
- The measured cap (~hundreds of lines, bounded loops, and only for *similar* code) is the hard
  ceiling on the "we prove equivalence" claim. It directly validates the brief's own hedge and
  means the pitch must be scoped to "critical functions," never "the whole app."
- The verified-obfuscation literature proves the *right* architecture exists (Architecture A in
  Q6): the Blazy group already proved CFF, opaque predicates, and an MBA obfuscation correct
  once each inside CompCert. A hackathon team cannot reproduce that in 48h, but can cite it as
  "this has been done in research; our weekend version is the bounded-testing approximation."

### Gaps
- No single published chart gives "function size vs. solve-time-to-timeout" for obfuscated
  code; the cap is triangulated from SymDiff/Alive2/ARDiff regimes and MBA timeout data (Q5),
  not one clean benchmark.

## Q5: The MBA tension — MBA obfuscation is designed to defeat the very SMT solvers you'd prove equivalence with

### Takeaway
This is the project's core contradiction, and the research confirms it is real and quantified.
Mixed Boolean-Arithmetic rewriting mixes bitwise and arithmetic ops so that neither algebraic
simplification nor the solver's bit-blasting cope; **Z3 can fail to decide a single obfuscated
MBA identity within five hours**, whereas the same identity after simplification is trivial.
So the stronger the obfuscation, the less your prover can prove it equivalent — automatically.

### Cited Findings
- MBA obfuscation (Zhou et al., 2006) builds identities mixing bitwise (`and`, `or`, `not`)
  and arithmetic (`+`, `-`, `*`) ops; "common math theorems ... are inapplicable to simplifying
  MBA equations, leading to performance bottlenecks in SMT solving" — [arXiv:2406.10016 (semi-linear MBA)](https://arxiv.org/html/2406.10016v2)
- **Hard quantified failure:** MBA-Blast reports that when checking equivalence of an original
  expression and its MBA-obfuscated form, "Z3 fails to return a result in five hours"; "most of
  the MBA expressions before simplification are too complex for Z3 to solve," but become
  solvable after simplification — [MBA-Blast USENIX Sec'21](https://www.usenix.org/system/files/sec21-liu-binbin.pdf)
- Industrial confirmation: gooMBA (Hex-Rays, in IDA) found "invoking the SMT solver leads to
  unreliable performance, since the solver often times out," so they pre-filter with random
  test cases before ever calling Z3 — [gooMBA](https://hex-rays.com/blog/deobfuscation-with-goomba)
- Timeouts used in the literature span 10s (Xyntia equivalence check) to 60s/600s per
  expression to 1 hour (MBA-Solver eval) — the wide spread itself signals that raw MBA pushes
  solvers to the edge of feasibility — [Xyntia arXiv:2102.04805](https://arxiv.org/pdf/2102.04805); [MBA-Solver](https://github.com/softsec-unh/MBA-Solver)
- **Offensive hardening against provers exists:** a USPTO patent multiplies MBA opaque
  predicates specifically to "stress the internal bitblasting algorithm within an SMT-solver";
  a 2026 framework (A²-MBA) adds "Anti-Generalization Hardening which exploits the SMT
  verification mechanism to block rules" — obfuscators are actively engineering *against*
  solvers — [USPTO patent](https://image-ppubs.uspto.gov/dirsearch-public/print/downloadPdf/12585460); [A²-MBA (ScienceDirect, 2026)](https://www.sciencedirect.com/science/article/abs/pii/S0167404826000428)
- The deobfuscation side (MBA-Blast, MBA-Solver, SiMBA, GAMBA, ProMBA) works by
  *simplifying before solving*; "current MBA simplifiers cannot effectively simplify
  expressions that use constants inside their bitwise operators ... unless an SMT solver is
  used" — so neither side fully wins — [MBA-Blast](https://www.usenix.org/system/files/sec21-liu-binbin.pdf); [arXiv:2406.10016](https://arxiv.org/html/2406.10016v2)

### Inferences
- The team's obfuscator and the team's verifier are the same solver technology pointed in
  opposite directions. If they obfuscate *weakly enough to prove automatically*, an attacker's
  deobfuscator (which uses the same simplifiers) also cracks it; if they obfuscate *strongly
  enough to resist deobfuscation*, their own Z3-based equivalence check also times out. The way
  out of this trap is **Architecture A** (prove the MBA rewrite rule correct *once* in
  Coq/Lean, as Blazy & Hutin did) so correctness never depends on re-solving the hard instance
  per build. This is the single most important strategic finding for the pitch.
- "AI proposes obfuscations that break SMT solvers" (from the brief) and "SMT proves them
  equivalent" are in direct tension; the honest resolution is that verification must be
  rule-level (A), with per-build solving reserved for transformations that are *easy* to verify
  but still raise attacker cost.

### Gaps
- No measured data on whether an LLM-proposed MBA can be reliably paired with an
  auto-generated correctness proof; the Blazy proofs are hand-written per transformation.

## Q6: Two product architectures — (A) prove each rule once vs. (B) translation validation per build

### Takeaway
**(A) Correct-by-construction (CompCert / Blazy style):** prove each transformation rule
semantics-preserving once in a proof assistant; every application is then trusted with no
per-build proof. **(B) Translation validation (Alive2 style):** prove nothing in advance;
check each concrete output against its input per build and ship a certificate. A is stronger
and immune to the MBA timeout trap but costs person-years and limits you to pre-proven rules;
B is flexible and automatable but bounded, can time out, and only certifies builds it manages
to discharge.

### Cited Findings
- **(A) exists for obfuscation already:** Blazy & Trieu proved CFF + opaque predicates once in
  Coq inside CompCert; Blazy & Hutin did the same for an MBA obfuscation — each a one-time
  proof, zero per-build solving, correct for all inputs and all loop depths — [Blazy & Trieu CPP 2016](https://www.irisa.fr/celtique/ext/cfg-flatten/cpp2016.pdf); [Blazy & Hutin CPP 2019](https://www.researchgate.net/publication/330157198_Formal_verification_of_a_program_obfuscation_based_on_mixed_Boolean-arithmetic_expressions)
- **(A) cost:** CompCert-scale effort (~6 person-years, ~100k lines Coq); proof cost rises with
  transformation potency (opaque predicates "no lemma," CFF "a number of intermediate lemmas") — [AbsInt](https://www.absint.com/compcert/structure.htm); [Blazy & Trieu](https://www.irisa.fr/celtique/ext/cfg-flatten/cpp2016.pdf)
- **(B) is the production-proven per-build model:** Alive2 validates each optimization output,
  bounded, and this found 47+ real bugs — proof that per-output certificates are practical for
  snippet-scale code — [Alive2 PLDI'21](https://users.cs.utah.edu/~regehr/alive2-pldi21.pdf)
- **(B) limits:** bounded (loop unwinding, Q2), can time out on hard instances (MBA, Q5), and
  SymDiff-style checkers are partial-equivalence and cannot disprove equivalence; a "pass" is
  only as strong as the bound and the model — [CBMC](https://arxiv.org/pdf/2302.02384); [SymDiff](https://www.microsoft.com/en-us/research/wp-content/uploads/2016/02/paper-44.pdf)

### Inferences
- **A dominates B for an obfuscation product** precisely because of the MBA trap: A moves the
  hard proof offline and once, so strong obfuscations become shippable with a real "for all
  inputs" guarantee; B re-pays the solving cost per build and fails exactly on the strongest
  obfuscations. The academically honest, defensible moat is a *library of pre-verified
  transformation rules* (A), with B as a fallback sanity check for compositions.
- The realistic commercial middle path: A for the handful of high-value transformations (prove
  the rules once, slowly), B+fuzzing (Q7) as a per-build regression gate for everything else,
  and never claim unbounded proof for the B-covered parts.

### Gaps
- No evidence any shipping commercial obfuscator (Guardsquare, Jscrambler, Digital.ai/Arxan,
  etc.) uses either A or B for a *correctness* guarantee — the brief's claim that none offers a
  formal proof appears consistent with what is public, but absence-of-evidence is not proof of
  absence; the report should phrase it as "none publicly documents" rather than "none has."

## Q7: Weekend-buildable honest version — bounded equivalence + differential fuzzing, and how to frame it

### Takeaway
In 48h a team can honestly build **bounded SMT equivalence checks on small pure functions
(via CBMC/Alive2 or a direct Z3 encoding) plus differential fuzzing** that runs millions of
random inputs through both versions and diffs outputs. The honest label is **"verified
equivalence via bounded checking and differential testing"** or **"high-confidence equivalence
(tested + bounded-proved)"** — NOT "formal proof" unless the function is loop-free/bounded and
the SMT check returns UNSAT, in which case "proven equivalent for all 32/64-bit inputs" is a
true and strong claim.

### Cited Findings
- Differential testing is the standard industrial pre-filter precisely because solvers are
  unreliable: gooMBA generates random test cases and emulates both expressions before trusting
  the SMT result — a weekend team should copy this pattern (fuzz first, then SMT on survivors) — [gooMBA](https://hex-rays.com/blog/deobfuscation-with-goomba)
- Bounded checking with a passing unwinding assertion is a *legitimate* proof up to the bound,
  and when the bound is a completeness threshold it is a full proof — so "proven for all inputs"
  is defensible for genuinely loop-free or bounded-loop functions — [CBMC](https://arxiv.org/pdf/2302.02384)
- For loop-free arithmetic (the obfuscation sweet spot: MBA identities, opaque predicates), the
  Z3 QF_BV check is *complete and fast* — the honest strong-claim zone — [MBA-Blast](https://www.usenix.org/system/files/sec21-liu-binbin.pdf) (showing solvable-once-simplified)

### Framing rules the report should hand the team (inference, grounded in the above)
- Say **"proven equivalent for all 2^32 (or 2^64) inputs"** ONLY when: the function is
  loop-free or fully bounded, modeled in bitvectors, and the solver returns UNSAT. This is true
  and strong — use it for the MBA/opaque-predicate demo functions.
- Say **"verified by differential testing (N random/structured inputs, 0 divergences)"** for
  anything with unbounded loops or memory; never upgrade this to "proven."
- Say **"bounded-equivalent up to k iterations"** for loops checked by BMC without a
  completeness threshold. Do not drop the "up to k."
- Never say **"formally proven the protected app behaves identically"** at whole-program scale —
  no tool supports it and the brief already knows this.

### Minimal Z3 Python example for an MBA identity (buildable in minutes; [48H] core)

The classic MBA identity `x + y == (x ^ y) + 2*(x & y)` — this is the shape an obfuscator uses
to rewrite `x + y` into something a reader (or a weak deobfuscator) struggles with. Proving it
for *all* 32-bit inputs is a genuine, complete formal proof:

```python
from z3 import BitVec, BitVecVal, prove, And

x = BitVec('x', 32)
y = BitVec('y', 32)

original    = x + y
obfuscated  = (x ^ y) + 2 * (x & y)          # MBA rewrite of addition

# prove() asserts the NEGATION is unsatisfiable:
# "there is NO 32-bit x,y with original != obfuscated"  -> proved for all 2^64 pairs
prove(original == obfuscated)                # Z3 prints: proved
```

To turn this into the product primitive, wrap it as a solver call that returns a verdict +
counterexample, and note that UNSAT here is a *complete* proof because the expression is
loop-free bitvector arithmetic:

```python
from z3 import Solver, BitVec, sat

def equivalent_32(build_lhs, build_rhs, nbits=32):
    s = Solver()
    xs = [BitVec(f'v{i}', nbits) for i in range(2)]
    s.add(build_lhs(*xs) != build_rhs(*xs))   # ask for a divergence
    if s.check() == sat:
        return ("NOT EQUIVALENT", s.model())  # concrete counterexample input
    return ("PROVEN EQUIVALENT for all inputs", None)  # UNSAT

print(equivalent_32(lambda x,y: x+y,
                    lambda x,y: (x^y)+2*(x&y)))
# -> ('PROVEN EQUIVALENT for all inputs', None)
```

Pair with a differential fuzzer (`random` inputs through both compiled functions, assert equal)
as the fallback for anything with loops/memory. Demo framing: "For the critical function we
show a *complete* Z3 proof over all 32-bit inputs; for the rest we show differential testing —
and we are explicit about which is which." That honesty is itself the differentiator.

### Gaps
- Whether Z3 can *auto-prove* an LLM-generated obfuscation (vs. the hand-picked textbook MBA
  identity above) within a demo-acceptable timeout is the open risk — Q5 shows strong MBA can
  blow past 5 hours, so the demo must use obfuscations chosen from the *provable* (A-style) set,
  not arbitrary LLM output.
