---
type: source
title: "Team reading list: AI obfuscation, formal verification, and AI reverse engineering"
date: 2026-11-07
by: luka+codex
url:
tags: [idea, security, formal-methods, agents]
---

# Lista literature za AI obfuskaciju i formalnu verifikaciju

Poreklo: Luka je dostavio ovu listu u razgovoru sa Codex-om 2026-11-07,
kao kontekst za tim i druge agente. Ispod je prenet sadržaj liste, bez izmene
naslova, godina i opisa. Ovo je zapis dostavljenog materijala; bibliografski
podaci i tvrdnje o radovima nisu nezavisno provereni pri upisu. Lista sadrži
14 navedenih naučnih radova i dva dodatna izvora. PDF-ovi i izvorni linkovi
nisu dostavljeni uz listu.

Povezani kontekst: [[idea-brief-code-protection]],
[[code-protection-project-description]]. Otvorena pitanja i dalji rad:
[[code-protection-field-open-questions]]. Pre citiranja u pitch-u ili izbora
alata proveriti primarne izvore, obuhvat dokaza i ograničenja evaluacije.
Nove proverene nalaze beležiti odvojeno, po jednu tvrdnju po belešci, uz link
na ovaj izvor. Ovaj zapis ostaje sačuvan kao dostavljen materijal.

## Dostavljena lista

Kontekst ideje: AI agent bira, kombinuje i eventualno generiše obfuskacione transformacije. Formalna verifikacija proverava očuvanje ponašanja, a zasebni napadi mere otpornost na AI reverse engineering.

Formalna verifikacija i dokazi

1. Alive2: Bounded Translation Validation for LLVM — 2021
   Automatski proverava konkretne LLVM transformacije. Najpraktičnija osnova za prototip.
2. Formal Verification of Control-flow Graph Flattening — 2016
   Coq dokaz očuvanja semantike za flattening, integrisan u CompCert.
3. Formal Verification of a Program Obfuscation Based on Mixed Boolean-Arithmetic Expressions — 2019
   Verifikacija obfuskacije koja kombinuje aritmetičke i bitovske operacije.
4. Towards Formal Verification of Program Obfuscation — 2020
   Coq dokazi za obfuskacione transformacije; razmatra problem njihovog kombinovanja. Uključuje istraživača iz Irdeto/Cloakware.
5. Enhancing Translation Validation of Compiler Transformations with Large Language Models — 2024
   Kombinuje LLM i verifikaciju tamo gde postojeći alati imaju ograničenja.
6. LLM-Vectorizer: LLM-based Verified Loop Vectorizer — 2024
   Srodan obrazac: LLM predlaže izmene koda, Alive2 proverava njihovu ispravnost.
7. LLVM Translation Validation Automated with Large Language Models and Lean — 2026, preprint
   Sistem Trivet koristi LLM za delove dokaza koje proverava Lean.

AI bira ili generiše obfuskaciju

8. Generating Effective Software Obfuscation Sequences With Reinforcement Learning — 2022
   RL bira redosled transformacija uz ograničavanje overhead-a. Direktno preklapanje sa idejom.
9. Generating Adversarial Computer Programs Using Optimized Obfuscations — 2021
   Optimizuje koje delove programa menjati i kojim transformacijama protiv ML modela.
10. Can LLMs Obfuscate Code? — AAAI 2025
    Benchmark MetamorphASM za LLM generisanje obfuskovanog assembly koda.
11. Simplicity by Obfuscation: Evaluating LLM-Driven Code Transformation with Semantic Elasticity — 2025
    LLM obfuskacija Python funkcija; pokazuje i slučajeve neželjenog pojednostavljivanja.

AI reverse engineering i evaluacija zaštite

12. Evaluation of Large Language Models on Code Obfuscation — 2024, student abstract
    Ispituje razumevanje različitih obfuskacija kod LLM-ova.
13. Towards LLM-Resistant Software Protection: Agent Failure Patterns in CTF Reverse Engineering — 2026
    Analizira neuspehe agenata na 24 CTF zadatka i implikacije za zaštitu.
14. Can LLMs Deobfuscate Binary Code? — 2026, preprint
    BinDeObfBench: evaluacija LLM deobfuskacije binarnog koda.

Još dva korisna izvora — nisu standardni research papers

- Verifying Code Correctness of Protected Software through Translation Validation — 2024: pregled verifikacije malih obfuskacionih LLVM prolaza.
- Quarkslab: Defeating AI-Assisted Reverse Engineering — 2026: praktični eksperimenti protiv agenata.

Prioritet za čitanje: 1, 2, 8 i 13. Važna granica: dokaz očuvanja semantike ne dokazuje otpornost na reverse engineering.
