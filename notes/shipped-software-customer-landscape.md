---
type: note
title: Software protection buyers span consumer apps, component vendors, industrial systems, and customer-hosted compute
tags: [customer, market, security]
date: 2026-11-07
by: luka+codex
confidence: moderate
sources: [https://www.guardsquare.com/mobile-sdk-protection, https://www.preemptive.com/customers/, https://www.wibu.com/case-studies/success-stories/story/detail/euresys-protecting-cross-platform-machine-vision.html, https://docs.nvidia.com/deeplearning/tensorrt-rtx/latest/reference/cybersecurity-disclosures.html]
---

## Claim and reading guide

The broad customer universe is **vendors putting valuable proprietary execution or data into an environment they do not fully control**. That includes customers, OEM partners, contractors, distributors, and hosting partners. A consumer download is just one distribution route. Browser JavaScript, bytecode, model files, and hardware designs broaden the universe beyond native binaries.

This is a landscape, not a census or evidence that every listed sector buys obfuscation. The 36 segments below overlap; do not add their sizes together. Public purchase evidence is collected in [[shipped-software-protection-customer-evidence]]. Initial priorities are hypotheses in [[native-sdk-vendors-are-a-plausible-first-obfuscation-market]]. All checked 2026-11-07.

Evidence codes: **C** = a public customer case supports this segment or a closely described deployment; **V** = a vendor offering, official technical documentation, or standard establishes the use case, without a customer purchase; **H** = plausible prospect hypothesis, no direct purchase evidence established in this research. A code does not establish market-wide adoption, current contracts, or demand for our product.

## Consumer and professional applications

| # | Potential customer | Artifact outside vendor control | Valuable target / economic reason | Evidence |
| --- | --- | --- | --- | --- |
| 1 | Banks, payment apps, wallets, lenders | APK, iOS app, native libraries | Payment integrity, fraud controls, cloning and tampering | C: Guardsquare customer cases |
| 2 | Retail, delivery, travel, loyalty apps | Mobile app | Promotion abuse and automated fraud; protect selected client checks | V: Guardsquare industry offerings; strength of demand varies |
| 3 | PC and console game publishers | Executable, engine modules | Delay piracy during commercial release; protect selected logic | C: Tripwire/Denuvo |
| 4 | Competitive/mobile game studios | Native code, managed assemblies | Cheat resistance and economy integrity, combined with server controls | C: Traplight and Superplus testimonials on Irdeto page |
| 5 | Creative desktop application vendors | EXE, DLL, macOS bundles | Licensing and proprietary rendering/editing algorithms; Adobe-like category | C: Reason Studios; Adobe itself is illustrative, not verified here |
| 6 | Audio plugin and DSP vendors | VST/AU/AAX binaries | DSP algorithms, license enforcement, paid presets as separate data | C: historical Reason case; MAAT first-party account |
| 7 | CAD/CAM, CAE, simulation vendors | Native desktop apps, solver libraries | Geometry, meshing, optimization, premium modules | C: SDProget and Hexagon industrial cases |
| 8 | Medical imaging and surgical planning vendors | Workstation apps, visualization components | Reconstruction and planning algorithms, commercially valuable workflows | C: Surgical Theater |
| 9 | Digital forensics and recovery tool vendors | Desktop executable and libraries | Proprietary parsers, recovery logic, storage knowledge | C: DME Forensics |
| 10 | Legal/e-discovery software vendors | .NET plugins, customer/partner-hosted components | Proprietary investigation and document-processing workflows | C: ProSearch |
| 11 | Geospatial, seismic, mining, scientific software vendors | Desktop/HPC solvers and plugins | Specialized algorithms sold to third parties | H: distribution and IP rationale need prospect confirmation |
| 12 | Finance/quant software sold to institutions | Pricing/risk libraries, on-prem engines | Proprietary valuation algorithms and commercial licensing | H: exclude internal strategies that never leave the firm's control |

## Components and client execution

| # | Potential customer | Artifact outside vendor control | Valuable target / economic reason | Evidence |
| --- | --- | --- | --- | --- |
| 13 | Identity, biometric, liveness, document SDK vendors | Native library, AAR/XCFramework, WASM | Proprietary detection algorithms; OEM redistribution | V: SDK protection offering; specific native prospect demand unverified |
| 14 | Payment/SoftPOS SDK vendors | Embedded Android/iOS SDK | Payment controls, contractual assessments, tamper resistance | C: Guardsquare anonymous payment SDK case |
| 15 | Commercial developer-tool/library vendors | NuGet/JAR/native packages/JS modules | The component itself is the product and travels through customers | C: /n software |
| 16 | Codec, OCR, compression, search, geometry SDK vendors | DLL/SO/static library | Copying or lifting valuable implementation | H: native-specific purchase evidence needed; adjacent component case above |
| 17 | Video players and DRM component vendors | Player SDK, client library, TV app | Rights enforcement, cryptographic implementation, playback features | V: BuyDRM and Irdeto documented protection stacks |
| 18 | Browser-based editors, visualization and design vendors | JavaScript/WASM, browser extension | Valuable computation shipped through the browser | C: Powtoon; LLVM approach only directly relevant to suitable WASM/native pipeline |
| 19 | Security/anti-bot/anti-fraud client SDK vendors | Browser script, mobile SDK, native agent | Hide detection implementation and raise bypass cost | H: code hiding alone does not establish reliable fraud prevention |
| 20 | Desktop shell/plugin ecosystem vendors | Electron bundles, IDE plugins, office add-ins | Proprietary local logic and licensing | H: assess each runtime and whether meaningful IP is shipped |

## Machines, devices, and physical products

| # | Potential customer | Artifact outside vendor control | Valuable target / economic reason | Evidence |
| --- | --- | --- | --- | --- |
| 21 | Industrial machine-vision vendors | SDKs, camera firmware, embedded Linux apps | Inspection, calibration, recognition algorithms | C: Euresys; MVTec named in Wibu brochure |
| 22 | Industrial automation and robotics vendors | PLC apps, motion libraries, controller software | Process know-how, premium machine features, cloning resistance | C: CoreTigo licensing; CODESYS protection integration documented |
| 23 | Medical/dental device manufacturers | Firmware, workstation apps, device software | Algorithms, paid functions, device/software cloning | C: Dentsply Sirona historical licensing/protection case |
| 24 | Automotive OEMs and Tier 1 suppliers | IVI apps, telematics, digital-key components, ECUs | Keys, feature licensing, proprietary code | V: historical Verimatrix automotive offering; safety-critical control is a separate adoption burden |
| 25 | Router, gateway, telecom/CPE vendors | Firmware and service modules | Credentials, provisioning, proprietary networking functions | V: Irdeto router keys-and-credentials document |
| 26 | Smart TV, set-top box and pay-TV operators/OEMs | DRM/conditional-access clients, firmware | Content access and subscription revenue | C: Digiturk and BCN deployments; bundled security, not standalone obfuscation purchases |
| 27 | Test/measurement and laboratory instrument vendors | Instrument firmware and analysis apps | Calibration, measurement algorithms, paid capabilities | H: strong theoretical IP fit; customer evidence needed |
| 28 | Drones, agricultural machines and autonomous systems vendors | ARM firmware, perception software | Navigation/perception IP and feature controls | H: real-time and safety constraints; separate model/code assets |
| 29 | Defense and aerospace suppliers | Mission software, onboard firmware, simulation modules | Sensitive algorithms distributed to partners/platforms | V: industry targeting; no named procurement established here |
| 30 | Energy, building control and industrial cybersecurity vendors | HMI/SCADA apps, appliances and gateways | Proprietary control/security logic and integrity | C: Bayshore Windows frontend; ETM WinCC OA case. Does not prove all firmware protected |

## Customer-hosted software and specialized compute

| # | Potential customer | Artifact outside vendor control | Valuable target / economic reason | Evidence |
| --- | --- | --- | --- | --- |
| 31 | Enterprise ISVs selling on-prem/air-gapped products | Container images, VMs, native/.NET/JVM services | Proprietary processing, commercial features, license checks | V: CodeMeter container documentation; C: ProSearch partner-cloud exposure |
| 32 | Commercial database, analytics, optimization-engine vendors | Server binaries/extensions at customer site | Query/solver algorithms and enterprise features | H: qualify open-core licensing and actual closed-source assets |
| 33 | Edge/on-device AI application and model vendors | ONNX/TensorRT engines, weights, native wrappers | Model extraction, unauthorized reuse, custom inference IP | V: NVIDIA warning; Irdeto/Skyld/Wibu competing offerings |
| 34 | GPU kernel, inference accelerator and HPC library vendors | PTX/cubin/fatbin, custom operators, CPU dispatch code | Kernel implementations and optimization know-how | V: NVIDIA disassembly tooling establishes exposure, not paid demand |
| 35 | Simulation/control-model suppliers to OEM partners | Compiled model library, protected Simulink model, FMU-like package | Supplier shares callable behavior while retaining design IP | V: MathWorks supports protected models and obfuscated/compiled code; FMU demand remains hypothesis |
| 36 | FPGA/semiconductor IP vendors | RTL, netlists, bitstreams and tool plugins | Design IP, unauthorized reuse and overbuilding | V: IEEE 1735 protects distributed electronic design IP; hardware transformation is a different product scope |

## Who buys and what triggers a purchase

Likely budget owners are CTO/VP Engineering or a founder for smaller algorithm vendors; product/application security leaders with engineering sponsorship in banks and large ISVs; software monetization/product leaders for licensing; and OEM platform/product-security leaders for devices. These roles are discovery hypotheses, not confirmed purchasing authority in every case.

Purchase triggers to investigate: a successful pentest against shipped code; a cloned product; launch of an offline edition; OEM redistribution; a protection-tool migration; a failed release caused by hardening; a payment/partner security assessment; or a requirement to deliver AI outside the vendor's cloud. Existing cases support pentest and redistribution triggers, but do not establish their frequency.

The buyer is normally the **vendor whose asset leaves its control**. A hospital using a third-party imaging product or factory running a vision SDK is usually the deployment environment, not the buyer of our build tool.

## Boundary of the opportunity

Poor prospects include pure server-side SaaS with no valuable shipped component, deliberately open-source/open-weight assets, thin UI clients whose valuable logic stays on the server, and companies content with free protection. Shipping a binary does not create willingness to pay by itself. Code may still be exposed at third-party hosting boundaries, but customers might prefer confidential computing or contractual controls.

Separate four jobs: resisting IP reconstruction; resisting copying/execution elsewhere; resisting patching/fraud; and protecting data/models/keys. They need different evaluations. An attacker can copy a whole binary or model without understanding it. An equivalence proof does not prevent that.

## Sources

All public customer citations and direct URLs: [[shipped-software-protection-customer-evidence]]. Specialized AI artifact evidence: [[local-ai-protection-involves-code-models-and-runtime]]. Verbatim reference excerpts: [[shipped-software-market-source-excerpts-2026-11-07]].
