---
type: source
title: GitHub and Hacker News bounded scan of 2026-11-07, methods and raw-response manifest
date: 2026-11-07
url:
tags: [security]
record_id: ghn-methods
platform: GitHub and Hacker News
quoted_on: 2026-11-07
---

Provenance for the bounded public scan filed on 2026-11-07. This file records how the twelve excerpts were collected. It is not an interpretation of them. Read claims in the notes linked from [[github-hn-scan-2026-11-07-index]].

The scan ran on 2026-11-07 (Europe/Belgrade). No fresh network requests were made for this filing. Statements in the excerpts are author claims or self-reports, not independently verified facts. Roles are limited to what the text or the scan handoff shows. No seniority was inferred.

## What was kept

- Twelve verbatim excerpts, one source file each, stable IDs `ghn-01` through `ghn-12`.
- Thirty-two Hacker News Algolia responses as JSON under `sources/github-hn-scan-2026-11-07/hn/`. The archive tarball was not committed.
- GitHub issue bodies were read in the original scan. Separate GitHub raw JSON was not saved, so it is not in this repository. GitHub quotes and dates were copied from the scan handoff and were not re-fetched.

`item-39029825.json` is archived and is not one of the twelve excerpts. Hits listed below that are not linked to a `ghn-` source were returned by search and were not filed as excerpts.

## GitHub queries

Read-only. First page only. Issue bodies were included in the search results the scan received. No private repositories, and no issues, comments, or reactions were posted.

| Query | Results requested |
| --- | --- |
| `repo:javascript-obfuscator/javascript-obfuscator crash OR broken` | 4 |
| `"obfuscator" "llvm" "crash"` | 3 |
| `Tigress obfuscation crash` | 2 |
| `repo:Guardsquare/proguard crash` | 2 |
| `repo:LaurieWired/GhidraMCP` | 2, comments descending |
| `"R8" "obfuscation" "crash"` | 1 |
| `"IDA" "LLM" "hallucination"` | 1; the scan excluded the result as irrelevant |
| `"obfuscation" "LLM" "benchmark"` | 2; the scan excluded the results as irrelevant |

## Hacker News queries

Comments were searched through both `https://hn.algolia.com/api/v1/search` and `https://hn.algolia.com/api/v1/search_by_date`, then through the focused searches below. The scan checked the twelve Hacker News excerpts against the individual item bodies. SHA-256 is of the archived file as committed.

| File | SHA-256 | Endpoint | Query metadata |
| --- | --- | --- | --- |
| `extra-0.json` | 913e7f128f8be873700b51ddd13637310127e2220f76a1a324f023c2df065dfc | https://hn.algolia.com/api/v1/search?query=%22model%22+%22scanner%22+%22backdoor%22&tags=comment&hitsPerPage=5 | `"model" "scanner" "backdoor"`; tags=comment; hitsPerPage=5; default page; returned IDs: 44897077 |
| `extra-1.json` | 38141e9625a003df0f0999d1be7af3c62591cb7992cb157bb2ab7bbb44e4c5e3 | https://hn.algolia.com/api/v1/search?query=%22Hugging+Face%22+%22poison%22&tags=comment&hitsPerPage=5 | `"Hugging Face" "poison"`; tags=comment; hitsPerPage=5; default page; returned IDs: 49536670, 49512412, 49503363 |
| `extra-2.json` | 28c6df808733fcc5615dd7d9715ccf8883bc565783a5761bde241d2fa125dff5 | https://hn.algolia.com/api/v1/search?query=%22obfuscation%22+%22resistance%22&tags=comment&hitsPerPage=5 | `"obfuscation" "resistance"`; tags=comment; hitsPerPage=5; default page; returned IDs: 48845360, 44561755, 14783393, 11961869, 10275048 |
| `extra-3.json` | 77af7b7b42587e807e5e7f00d3b98d82c27fbf2a4f7ceb6c63d84a90ffae36a7 | https://hn.algolia.com/api/v1/search?query=%22obfuscation%22+%22benchmark%22+%22AI%22&tags=comment&hitsPerPage=5 | `"obfuscation" "benchmark" "AI"`; tags=comment; hitsPerPage=5; default page; returned IDs: 49380937 |
| `extra-4.json` | 8277cd3141fc80227b39d649d8e97437066077a976388b655c3f99c980b41f74 | https://hn.algolia.com/api/v1/search?query=%22Ghidra%22+%22obfuscated%22&tags=comment&hitsPerPage=5 | `"Ghidra" "obfuscated"`; tags=comment; hitsPerPage=5; default page; returned IDs: 32080145, 50322673, 38521824, 47339332, 47113638 |
| `focused-0.json` | 8b980f70948c6dafce0b5f9696da109f57a2ce2cdbba38aee9552910b4feec5c | https://hn.algolia.com/api/v1/search?query=%22GhidraMCP%22&tags=comment&hitsPerPage=8 | `"GhidraMCP"`; tags=comment; hitsPerPage=8; default page; returned IDs: 50052962, 49598295, 48448979, 48137574, 47790292, 47037092, 47036584, 46980147 |
| `focused-1.json` | 90065fe361c7197531839f762d67b339c74171c1688b107494fd9d3444a6be13 | https://hn.algolia.com/api/v1/search?query=%22weights%22+%22backdoor%22&tags=comment&hitsPerPage=8 | `"weights" "backdoor"`; tags=comment; hitsPerPage=8; default page; returned IDs: 42421832, 49076635, 34457744, 48248289, 50161118, 50187556, 48776497, 40527503 |
| `focused-2.json` | 3f62474add954e37c0056bd6f7c63017b2d34663ad351ec03ba899375c8f9677 | https://hn.algolia.com/api/v1/search?query=%22safetensors%22+%22backdoor%22&tags=comment&hitsPerPage=8 | `"safetensors" "backdoor"`; tags=comment; hitsPerPage=8; default page; returned IDs: 44903563 |
| `focused-3.json` | c8d17a357e0865552781b0b1d7398415c05696352398501336605c8657e94fc7 | https://hn.algolia.com/api/v1/search?query=%22obfuscation%22+%22LLM%22&tags=comment&hitsPerPage=8 | `"obfuscation" "LLM"`; tags=comment; hitsPerPage=8; default page; returned IDs: 50296182, 50280792, 46030663, 40221669, 49642415, 48831074, 48830326, 48829568 |
| `focused-4.json` | 54d1fee8214d7541d38660deeae80452c14d4d7fe7d3ec0150a6dcccbccc7607 | https://hn.algolia.com/api/v1/search?query=%22anti-cheat%22+%22AI%22&tags=comment&hitsPerPage=8 | `"anti-cheat" "AI"`; tags=comment; hitsPerPage=8; default page; returned IDs: 49915269, 46259948, 42779574, 41438760, 28859937, 45908286, 42009282, 49905069 |
| `focused-5.json` | c6f99a20f828df8c1d4ff723f00982d0bcf70579608ab2320b53a2e674726a1f | https://hn.algolia.com/api/v1/search?query=%22app+shielding%22&tags=comment&hitsPerPage=8 | `"app shielding"`; tags=comment; hitsPerPage=8; default page; returned IDs: none |
| `hn-search-0.json` | d09f3668eaba1485849b7d8e5f05958a351322f5600962f00af97829926491d1 | https://hn.algolia.com/api/v1/search?query=GhidraMCP&tags=comment&hitsPerPage=6 | `GhidraMCP`; tags=comment; hitsPerPage=6; default page; returned IDs: 50375124, 50361170, 50111638, 50090456, 50052962, 50029557 |
| `hn-search-1.json` | c6b3fdfe0e0de050374ada8106ed35c8fcb33ae9c69cd5a0ebf1f6ecfbfa087a | https://hn.algolia.com/api/v1/search?query=obfuscation+LLM&tags=comment&hitsPerPage=6 | `obfuscation LLM`; tags=comment; hitsPerPage=6; default page; returned IDs: 50296182, 50280792, 46030663, 40221669, 49642415, 48831074 |
| `hn-search-2.json` | f9b04d9b1a3a9a0ad3f277ffa255b68132e82a47378a4148fde3239a016bca22 | https://hn.algolia.com/api/v1/search?query=app+shielding&tags=comment&hitsPerPage=6 | `app shielding`; tags=comment; hitsPerPage=6; default page; returned IDs: 15673420, 40324668, 35206295, 9489291, 8859491, 8127330 |
| `hn-search-3.json` | 365fed90784e9f6118e0ce0ab9909254815c6729a0c957bb992bbf0454163225 | https://hn.algolia.com/api/v1/search?query=anti+cheat+AI&tags=comment&hitsPerPage=6 | `anti cheat AI`; tags=comment; hitsPerPage=6; default page; returned IDs: 48140570, 46567375, 49915269, 46259948, 46093724, 42779574 |
| `hn-search-4.json` | 81bcde4888517837e379764dd35508344a1b7cd95b1c4aa04d7faefd48cdf3c3 | https://hn.algolia.com/api/v1/search?query=backdoored+weights&tags=comment&hitsPerPage=6 | `backdoored weights`; tags=comment; hitsPerPage=6; default page; returned IDs: 50166687, 49978337, 39029825, 50375402, 48526225, 46047823 |
| `hn-search-5.json` | 3a13fb2f9afdaa72a09038e8aeccbf2772fdbf7e1f0470959cff7abe9c6527ea | https://hn.algolia.com/api/v1/search?query=Hugging+Face+security&tags=comment&hitsPerPage=6 | `Hugging Face security`; tags=comment; hitsPerPage=6; default page; returned IDs: 49716610, 49456671, 49346193, 49231334, 49039635, 49024400 |
| `hn-search-6.json` | e98da3102fec9677f96eab6aae881d883e8774ad48d330ee12ddef61a0bc9f2a | https://hn.algolia.com/api/v1/search?query=obfuscation+benchmark&tags=comment&hitsPerPage=6 | `obfuscation benchmark`; tags=comment; hitsPerPage=6; default page; returned IDs: 2242907, 6546559, 6410144, 5688416, 5549661, 49380937 |
| `hn-search_by_date-0.json` | cac14dee6e8efc44f0120a74bfbe04482a246a14bec503578d989b2b00da3312 | https://hn.algolia.com/api/v1/search_by_date?query=GhidraMCP&tags=comment&hitsPerPage=6 | `GhidraMCP`; tags=comment; hitsPerPage=6; default page; returned IDs: 50375124, 50361170, 50111638, 50090456, 50052962, 50029557 |
| `hn-search_by_date-1.json` | 8bc01379c09d4800987004d629ff2a17ca83929904d4cb07ff1f871aa3fe51bb | https://hn.algolia.com/api/v1/search_by_date?query=obfuscation+LLM&tags=comment&hitsPerPage=6 | `obfuscation LLM`; tags=comment; hitsPerPage=6; default page; returned IDs: 50380110, 50379586, 50368504, 50352349, 50336855, 50335395 |
| `hn-search_by_date-2.json` | 217d22572b942b128561e22717a79ee641cd7e7a56e3ab92189e8929a40078c9 | https://hn.algolia.com/api/v1/search_by_date?query=app+shielding&tags=comment&hitsPerPage=6 | `app shielding`; tags=comment; hitsPerPage=6; default page; returned IDs: 50388371, 50274230, 50111675, 50073697, 50050626, 50044939 |
| `hn-search_by_date-3.json` | f908a06187b4c6255b0f47e39b7165e2b8ffd16d5081ea493023987d4eac9bf3 | https://hn.algolia.com/api/v1/search_by_date?query=anti+cheat+AI&tags=comment&hitsPerPage=6 | `anti cheat AI`; tags=comment; hitsPerPage=6; default page; returned IDs: 50357062, 50307466, 50307438, 50275991, 50229528, 50204724 |
| `hn-search_by_date-4.json` | 743bfe1ecdcbe7e9cc1cbc60302709877bb993e3e72668d1a6f8676658c31a51 | https://hn.algolia.com/api/v1/search_by_date?query=backdoored+weights&tags=comment&hitsPerPage=6 | `backdoored weights`; tags=comment; hitsPerPage=6; default page; returned IDs: 50398956, 50398055, 50397796, 50396624, 50375718, 50375402 |
| `hn-search_by_date-5.json` | d66cb8e3484f6f0d2bbf51871d77c812b2181359d498f292c4100ec4b2a5729e | https://hn.algolia.com/api/v1/search_by_date?query=Hugging+Face+security&tags=comment&hitsPerPage=6 | `Hugging Face security`; tags=comment; hitsPerPage=6; default page; returned IDs: 50394559, 50393326, 50364705, 50338935, 50322518, 50312425 |
| `hn-search_by_date-6.json` | 1e3da2db23ab701df24df171144eade2041949b6de7041e5f14fd3c5558f4709 | https://hn.algolia.com/api/v1/search_by_date?query=obfuscation+benchmark&tags=comment&hitsPerPage=6 | `obfuscation benchmark`; tags=comment; hitsPerPage=6; default page; returned IDs: 49380937, 48829568, 47808374, 47132615, 46311816, 44437258 |
| `item-39029825.json` | 9b7bca4c53e97a09ece3f57c8f5b075856904a59fdfb5abd1d63d86ced94fcb5 | https://hn.algolia.com/api/v1/items/39029825 | Individual comment https://news.ycombinator.com/item?id=39029825. Archived, not one of the twelve excerpts. |
| `item-44897077.json` | 06f3bafcb49236d45556a01266c0067b03393798af09b9828c8d351f427c0d55 | https://hn.algolia.com/api/v1/items/44897077 | Individual comment https://news.ycombinator.com/item?id=44897077. Excerpt [[ghn-12-hn-44897077]]. |
| `item-47113638.json` | ed253be9ef88c7f16fc73c4989ad1fbf1fb89cc1ac1001bad2dd29a9a91e01d7 | https://hn.algolia.com/api/v1/items/47113638 | Individual comment https://news.ycombinator.com/item?id=47113638. Excerpt [[ghn-07-hn-47113638]]. |
| `item-47790292.json` | dac04db6074b34e7bb207669ceb4372fda23e024b4175012887c35bf17949e7a | https://hn.algolia.com/api/v1/items/47790292 | Individual comment https://news.ycombinator.com/item?id=47790292. Excerpt [[ghn-08-hn-47790292]]. |
| `item-48248289.json` | b980df5f01a94e411d14f7791c177b39dd72208fb1565e60fda3c32a6132e7e5 | https://hn.algolia.com/api/v1/items/48248289 | Individual comment https://news.ycombinator.com/item?id=48248289. Excerpt [[ghn-11-hn-48248289]]. |
| `item-49076635.json` | 7fbcfe9adafe16f5d273664ca212b38bf741d407584290cd3c07f17c1adfc1bf | https://hn.algolia.com/api/v1/items/49076635 | Individual comment https://news.ycombinator.com/item?id=49076635. Excerpt [[ghn-10-hn-49076635]]. |
| `item-50052962.json` | 46ca801b86b1e99cd8dd992018fe17b5ed6bed789df12510dfb5db00a0361228 | https://hn.algolia.com/api/v1/items/50052962 | Individual comment https://news.ycombinator.com/item?id=50052962. Excerpt [[ghn-09-hn-50052962]]. |

## Gaps

These are outcomes of this bounded scan, not evidence that the subject is absent.

- A2, someone already pays to protect client-side code: not researched in this scan.
- A5, incumbents market protection against AI attackers: not researched in this scan.
- A4, direct practitioner demand for measured AI cracking-resistance benchmarks: searched, not found.
- App shielding, exact Hacker News phrase: not found. `focused-5.json` is the exact-phrase response and the scan recorded no returned IDs. Other app-shielding responses listed IDs and none of those IDs were filed as excerpts.
- Anti-cheat and AI: no direct practitioner experience connecting AI-assisted reverse engineering to protection breakage was filed. The scan said general opinions surfaced.
- IDA LLM plugins: no relevant direct practitioner evidence was filed from the bounded issue search.
- R8: no directly observed breakage was filed in the shortlist. The scan said configuration and debuggability concerns surfaced.

Open questions that use this scan: [[do-people-need-ai-resistant-code-protection]], [[code-protection-field-open-questions]].
