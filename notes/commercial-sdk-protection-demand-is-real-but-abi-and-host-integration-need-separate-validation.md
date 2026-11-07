---
type: note
title: Commercial SDKs buy code protection but ABI and host integration need checks beyond native function equivalence
tags: [customer, market, security, formal-methods]
date: 2026-11-07
by: luka+codex
confidence: moderate
sources: [cad-forensics-sdk-demand-web-excerpts-2026-11-07, https://www.preemptive.com/wp-content/uploads/2023/11/N-Software-Case-Study.pdf, https://docs.techsoft3d.com/hoops/visualize-desktop/general/licensing.html, https://try.bluemarblegeo.com/geocalc-sdk-quote-request, https://docs.microblink.com/analytics/license, https://www.dynamsoft.com/mrz-scanner/docs/mobile/programming/android/user-guide/, https://developer.android.com/topic/performance/app-optimization/library-optimization, https://promon.io/resources/customer-stories/how-promon-helped-an-international-media-company-secure-content-and-prevent-piracy]
---

## Strong customer evidence

**/n software** reports using Dotfuscator and JSDefender for developer components. Its case explicitly requires on-prem JavaScript protection so source is not transmitted to a third party. The build generates JavaScript, invokes the protector from a script and continues packaging. The customer describes integration and performance favorably. This validates the buyer category and source-confidentiality requirement, not an unmet need for AI or easier integration. It is .NET/JavaScript evidence, not a native C++ proof deployment.

An **anonymous media customer in Promon's case** switched after its previous security supplier failed to meet innovation, responsiveness and platform needs. The account includes native/Java SDK protection and runtime defenses, with content-contract obligations as a trigger. This is actual reported switching motivation but an anonymous, selected vendor case with no quantified savings or AI-specific incident.

An [anonymous SoftPOS SDK case](https://www.guardsquare.com/hubfs/Website/Resources/Customer%20Stories/Popular%20Mobile%20Payment%20Acceptance%20SDK%20Achieved%20PCI%20MPoC%20Certifications%20with%20Guardsquare.pdf) reports evaluating four suppliers and adopting Guardsquare for Java/native obfuscation, runtime checks and security testing. Certification and partner requirements were triggers. This supports an existing purchase process, not a universal obfuscation mandate or suitability of our proof as certification evidence.

## Additional named leads beyond vision and audio

| Vendor | Delivered value and documented commercial workflow | What is still unverified |
| --- | --- | --- |
| **Tech Soft 3D** | HOOPS Visualize Desktop requires a key compiled into C++/C# application initialization; invalid/expired keys stop startup | Specific protector, maintenance pain and AI extraction |
| **Blue Marble Geographics** | GeoCalc coordinate-transformation SDK has developer and additional distribution licenses, registration keys and server-use options | Obfuscation adoption or demand for stronger algorithm protection |
| **Dynamsoft** | Document/barcode/MRZ SDKs; [pricing](https://www.dynamsoft.com/barcode-reader/pricing/) offers annual licensing and dedicated offline options | Current dissatisfaction or reconstructed proprietary algorithm |
| **Microblink** | SDK license validation with a documented offline grace period; September 29, 2026 documentation | Protection implementation and switching intent; primarily vision, retained as a regional comparison |

These are **leads based on delivery/monetization**, not four confirmed obfuscation customers. Public SDK APIs and keys do not themselves demonstrate a vulnerability. Standard algorithms, open-source wrappers or value residing mainly in data/services may be poor targets.

## A precise integration problem

Dynamsoft's Android MRZ guide explains that native methods resolved by name can fail at runtime if renamed or removed by R8. The standard Android configuration already contains the protective rule; custom rules must retain it. This is a documented hazard, not an unresolved bug in the default SDK integration or a measured incident rate.

Google's library-author guidance separates library-build rules preserving public API from consumer rules for host-app optimization, reflection and JNI. It recommends testing an integration app and already offers configuration analysis and generated-rule mechanisms. This creates a real engineering task with existing solutions. A startup must improve that baseline rather than claim the task is entirely manual.

## Proposed product boundary

For a native SDK pilot: preserve public symbols and calling conventions → transform selected customer-owned internal functions → run supported equivalence checks → package library → test representative host applications and bindings → compare performance and attacker reproduction.

A proof about internal LLVM semantics does not prove Java-to-native name lookup, ABI compatibility, managed-runtime behavior or correctness of the final host application. If customer pain is mainly Android keep rules, an integration tool may be more relevant than our proposed native obfuscation engine. If the asset is model weights, a different protection track is required.

## Sources

Primary links above; excerpts: [[cad-forensics-sdk-demand-web-excerpts-2026-11-07]]. Related: [[cad-forensics-and-sdk-protection-have-different-buying-triggers-and-pilot-fit]]. Checked 2026-11-07.
