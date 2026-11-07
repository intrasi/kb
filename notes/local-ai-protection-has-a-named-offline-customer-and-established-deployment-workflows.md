---
type: note
title: Local AI protection has a named offline customer and competing software and hardware deployment workflows
tags: [customer, market, security, formal-methods]
date: 2026-11-07
by: luka+codex
confidence: moderate
sources: [https://cpl.thalesgroup.com/sites/default/files/content/case_studies/connecteve-ai-medical-software-cs.pdf, https://docs.skyld.io/, https://docs.skyld.io/skprotect/usage, https://docs.nvidia.com/confidential-computing/overview]
---

## Stronger customer evidence than a generic concern

[CONNECTEVE's Thales case](https://cpl.thalesgroup.com/sites/default/files/content/case_studies/connecteve-ai-medical-software-cs.pdf) describes its Python-based AI diagnostic software deployed inside hospitals, including offline sites. The company sought protection for models and code, prevention of duplication/overuse, and centralized licensing. Activation is performed locally by CONNECTEVE engineers at installations without external network access. The case reports ten days of workshops/training to go live. This establishes reported purchase/use and identifiable workflow needs. It gives no contract value, independent extraction test or comparison with an AI verifier. Do not infer industry-wide installation requirements from one customer's setup.

## Three existing approaches

1. **Protected software/model runtime.** [Skyld's integration docs](https://docs.skyld.io/) describe applying SkProtect to a model, shipping protected files/keys/configuration, loading them through SkRuntime into the original inference library, and controlling access with a license server. The [protection guide](https://docs.skyld.io/skprotect/usage) documents model updates, platform/runtime compatibility, export variants and integrity constraints; postprocessing may require vendor support. Its [testing page](https://docs.skyld.io/skprotect/run) documents executing protected models. These are concrete integration/maintenance tasks, not proof they are a pain customers will pay us to remove.
2. **Packaging, encryption and device/usage licensing.** CONNECTEVE and [Irdeto AI Model Protection](https://irdeto.com/ai-model-protection) illustrate this category. Different products may cover different stages; encrypted files are not evidence of confidentiality throughout execution.
3. **Confidential compute on suitable hardware.** [NVIDIA documentation](https://docs.nvidia.com/confidential-computing/overview) describes attestation and policy-controlled secret release across confidential bare-metal, VM and container deployments. Its [self-hosted Kubernetes reference architecture](https://docs.nvidia.com/enterprise-reference-architectures/deploying-proprietary-models-confidential-compute-self-hosted-kubernetes/latest/introduction.html) specifically addresses third-party on-prem model deployment. This can be a substitute or complement; compatibility, supported hardware and threat model matter. Ordinary containers alone provide no equivalent protection against the host administrator.

## What can be lost

Model weights/graph can be extracted and reused; custom native kernels/preprocessing can be reconstructed; licensing can be patched; a compromised runtime can alter outputs. [NVIDIA warns](https://docs.nvidia.com/deeplearning/tensorrt-rtx/latest/reference/cybersecurity-disclosures.html) that an engine can expose the original model despite encryption of its original specification. Copying weights does not reveal all training data, and one need not understand a model to copy it. These are local-deployment threats; API distillation and training-data extraction are different attack classes.

## Best fit for our proposal

Protect proprietary native wrappers/operators/postprocessing with supported transformations, then measure reconstruction/extraction tasks and performance separately. Full learned-weight secrecy is a separate scope. A CPU/LLVM equivalence proof does not cover GPU concurrency, model-runtime integrity, hardware confidentiality or approximate numerical behavior. A customer using open-source inference and intentionally open weights might have little proprietary asset to protect.

The workflow opportunity is export/runtime compatibility, supported transformation selection, reproducible tests and versioned configurations. We have no measured evidence yet that our system beats existing runtime wrappers or avoids their integration cost. Related: [[local-ai-protection-involves-code-models-and-runtime]] and [[legacy-protection-workflows-offer-a-testable-integration-opportunity]].
