---
type: source
title: "Project description: Glassbox, an audit for open-weight AI models"
date: 2026-11-07
url:
tags: [idea, security, market]
---

Team description written by Karla on 2026-11-07. Status when filed: considered and set aside after testing.

# Glassbox

Glassbox checks an open-weight model, or a fine-tune of one, for hidden behaviour. It removes what it finds and produces a signed record of exactly what it checked.

Originally proposed by Tea for the Garaža Frontier Hackathon (Belgrade, 7 and 8 November 2026). The team tested and iterated on it. It is no longer the current direction; this document records where it ended up.

## The problem

- Companies increasingly run AI models they didn't train: open-weight base models, plus fine-tunes and LoRA adapters made by other people.
- Someone can train a hidden trigger into a fine-tune cheaply. The model behaves normally on ordinary tests and misbehaves only when it sees a secret phrase.
- Most model scanners look for malicious code inside model files. A trigger trained into the weights contains no code, so those scanners don't see it.
- Security teams therefore cannot easily approve an outside fine-tune for production use. That stalls adoption.
- Honest caveat: as of the proposal, no backdoor hidden in model weights had been confirmed in the wild. The pitch leads with getting models through review faster, with proof. It does not rely on fear.

## Where the idea comes from

MIT CSAIL's "Sparks of Weight-Space Programming" (2 November 2026) showed a frontier model reading and editing another network's raw weights. One result shaped the design: finding a hidden fine-tune from the weights alone mostly failed, but it worked once the model also saw a few forward passes, meaning a handful of real runs of the model. Glassbox is built on that combination of weights plus a small number of forward passes.

## How it works

One loop with six steps: diff, scan, localise, patch, gate, attest.

1. **Diff.** Subtract the claimed base model from the fine-tune, layer by layer. Check that the change matches the declared method. For example, a small LoRA should only change the parts of the model it targets.
2. **Scan.** Extract simple statistical features from each change and score how likely it is to hide a trigger.
3. **Localise.** Find the directions in the model that the suspicious change pushes on. Calibrate them against a few hundred normal prompts.
4. **Search for the trigger.** Rank words and phrases by how strongly they activate those directions. This reconstructs the likely trigger.
5. **Patch and gate.** Remove the offending direction or adapter component. Re-run the trigger, clean benchmarks, and a comparison on normal prompts. If anything else broke, revert the patch.
6. **Attest.** Output a signed report that ships with the model. It lists what was checked and also what was **not** checked. It records evidence and makes no guarantee that the model is safe.

**Sanity check.** Run Glassbox on MIT's edited model. It must find exactly the small set of weights MIT changed.

## The weekend demo

- Before the demo, judges receive fingerprints of ten adapters and a sealed envelope that says which ones are compromised. At least one adapter was trained by someone outside the team, and at least one uses a trigger type the detector has never seen.
- Glassbox ranks all ten from their weights, with a heatmap showing where each change sits.
- A judge opens the envelope.
- The team fires a reconstructed trigger live (the payload is harmless), patches the model, fires the trigger again to show it no longer works, and shows that normal performance is unchanged.
- The signed report appears, including its "not checked" section.

The judges can verify the result themselves instead of trusting the team.

## Who would pay

- Security and platform leads whose open-weight fine-tune is stuck in review.
- Companies that publish fine-tunes, whose customers ask for proof the model is clean.
- Public-sector integrators who must show a model contains only the changes it declares.
- Later: model hubs and inference platforms (priced per scan), and AI insurers and certifiers.

## Competition

- **Model-file scanners** (Protect AI, now part of Palo Alto Networks; JFrog) find code in files. They do not read what the weights learned.
- **Interpretability companies** (Goodfire and others) have the research depth to add this feature. They are the most serious threat.
- **Model-editing tools** can patch weights, but they do not detect problems or produce a verifiable record.
- **Big security vendors are buying into the space.** Palo Alto bought Protect AI, and Check Point bought Lakera. That is a sign of demand, and it also means large incumbents.

## Verdict after testing

- **As a weekend build: strong.** The demo is concrete, can be verified on the spot, and fits the team's skills.
- **As a company: weak today.** It works best as an open tool that companies run before they adopt a model. The features that set it apart, such as diffing against a base model, can be copied by better-funded interpretability and security companies.
- **Known risks:**
  - Detectors trained on known attacks do worse on new ones.
  - Backdoors that cannot be detected at all exist in theory, so the report never claims a model is "safe".
  - The team's own test backdoors might be too easy to find. The blind set mitigates this.

## Team fit

- **Karla:** rare-signal detection at very low false-positive rates, from her work on a CERN ATLAS filter.
- **Marko:** GPU kernels and attention layers, plus anomaly detection on CERN logs.
- **Tea:** regression gates for agent skills, from her thesis.
- **Luka:** data pipelines at Databricks, and experience selling to compliance-heavy customers.
