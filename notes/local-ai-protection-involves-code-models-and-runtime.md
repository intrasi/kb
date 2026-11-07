---
type: note
title: Local AI creates separate protection jobs for inference code, model assets, and execution authorization
tags: [customer, market, security, formal-methods]
date: 2026-11-07
by: luka+codex
confidence: moderate
sources: [https://docs.nvidia.com/deeplearning/tensorrt-rtx/latest/reference/cybersecurity-disclosures.html, https://docs.nvidia.com/cuda/cuda-binary-utilities/, https://irdeto.com/ai-model-protection, https://docs.skyld.io/]
---

## Claim

Edge/on-prem AI vendors belong in the customer landscape, but ordinary code obfuscation does not automatically protect model weights, prevent copying, or protect GPU memory. Separate the customer's asset before claiming a solution. Checked 2026-11-07.

| Asset leaving control | Prospect examples | Protection/evaluation job | Fit to our proposed verification |
| --- | --- | --- | --- |
| Proprietary CPU preprocessing, postprocessing, custom operators, orchestration | Vision SDK, speech engine, document AI appliance vendor | Make valuable logic harder to reconstruct while preserving outputs | Closest fit where C/C++ can enter supported LLVM semantics |
| Proprietary GPU kernels | Inference-optimization, simulation, image-processing library vendor | Increase kernel reconstruction cost without destroying throughput | Requires GPU-aware transformations, memory/concurrency semantics and validation; CPU proof does not cover device code |
| Model graph and learned parameters | Edge AI vendor, private local model supplier | Resist extraction or unauthorized reuse of weights and architecture | Different techniques and threat model; preserving function alone does not hide weights |
| Runtime authorization and paid capabilities | AI appliance, licensed inference service deployed at customer | Resist patching, replay and execution on unauthorized devices | Device binding, licensing and runtime defenses; complement code protection |

## Direct exposure evidence

[NVIDIA TensorRT-RTX cybersecurity documentation](https://docs.nvidia.com/deeplearning/tensorrt-rtx/latest/reference/cybersecurity-disclosures.html) explicitly warns that a serialized inference engine may allow reconstruction of the original model even when its original specification was encrypted. Its [porting guide](https://docs.nvidia.com/deeplearning/tensorrt-rtx/latest/inference-library/porting.html) describes engines loaded and executed on end-user machines. This establishes a technical exposure, not a measured extraction rate or market size.

[NVIDIA CUDA Binary Utilities](https://docs.nvidia.com/cuda/cuda-binary-utilities/) documents extracting embedded PTX and disassembling cubin/device code. Compiling for a GPU is therefore not an intrinsic confidentiality boundary. This is legitimate official inspection tooling, not evidence every GPU binary is easy to reconstruct.

[OpenVINO 2023.3 documentation](https://docs.openvino.ai/2023.3/openvino_docs_OV_UG_protecting_model_guide.html) describes loading externally decrypted models and says encryption/authentication are supplied externally. It is version-specific historical documentation. [AMD Ryzen AI 1.4](https://ryzenai.docs.amd.com/en/1.4/modelrun.html) describes context-model encryption. Neither establishes protection against a fully privileged runtime observer by itself.

## Competition already exists

- [Irdeto AI Model Protection](https://irdeto.com/ai-model-protection) markets model protection and authorization across customer/partner, edge and cloud environments.
- [Skyld documentation](https://docs.skyld.io/) describes SkProtect, a deployment runtime and licensing server. Its [TensorRT extraction demonstration](https://www.skyld.io/jetson-model-extraction) illustrates a particular runtime interception threat; this is vendor research, not proof that all configurations are vulnerable or its own defense is unbreakable.
- [Wibu's AI primer](https://cdn.wibu.com/fileadmin/wibu_downloads/White_Papers/PRIMER_AI/Primer_AI_EN.pdf) describes protecting ML code, model files and licensing. File encryption and licensing should not be equated with permanent secrecy during execution.

Do not pitch local AI protection as an empty market. Open-source inference runtimes are often not the IP a customer needs to hide: the proprietary model, custom kernels, postprocessing and integration may be the actual assets. An intentionally open-weight model has a different business problem.

## Product implication

The most coherent extension of our current idea is **verified protection of proprietary native components around local inference**. Full model protection is a separate research/product track. Customer interviews should ask which asset is valuable and whether their feared attack is extraction, copying, patching or understanding.

Formal equivalence does not prove secrecy. Floating-point reassociation, quantization and parallel GPU execution complicate behavior preservation; decide whether the contract is bit-identical output or a specified numerical tolerance, and use a checker that actually supports that contract. A small integer-function hackathon demo does not validate full inference engines.

Related: [[shipped-software-customer-landscape]], [[verified-obfuscation-research-links]].
