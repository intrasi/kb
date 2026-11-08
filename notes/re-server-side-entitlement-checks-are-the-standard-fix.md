---
type: note
title: Google, Apple and RevenueCat steer apps to check purchases on a server, so app protection adds value mainly where paid value runs on the device
tags: [security, customer]
date: 2026-11-07
by: tea+claude
confidence: high
sources: [https://developer.android.com/google/play/billing/security, https://developer.apple.com/videos/play/wwdc2021/10174/, https://www.revenuecat.com/blog/engineering/trusted-entitlements]
---

- **Google Play billing security:** "The more data and logic you have in a frontend device, the more
  vulnerable it is to being modified or tampered with." It advises against bundling unlocked content
  in the APK.
- **Apple (WWDC21):** signed transactions are easy to verify "on your server without having to call
  us". Server checks are offered, not required.
- **RevenueCat:** reports "an observable rise in machine-in-the-middle (MiTM) piracy on apps". Its
  Trusted Entitlements protect an app only if the app's own code checks the result (docs, via
  snippet).

Counter-evidence that client checks persist: an app developer on r/androiddev (April 2026) caches a
premium flag locally forever after one server call, and says a hacked version is "fairly easy"
([[reddit-sweep-2-mobile-entitlements-and-banking-shielding-trust-the-client]]). No data says what
share of apps check only on the device.

Why it matters: for apps whose paid value lives on a server (content, cloud AI, sync), the fix is a
server check and app protection is a hard sell. Protection matters where the paid value has to run
on the device: offline features, games, paid desktop software and plugins. A practitioner said the
same about simple apps such as gym or pomodoro apps
([[reddit-sweep-2-objection-client-side-protection-is-called-futile]]).

Checked 2026-11-07.
