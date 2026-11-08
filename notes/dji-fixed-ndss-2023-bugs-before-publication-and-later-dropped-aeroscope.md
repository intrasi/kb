---
type: note
title: DJI fixed all 16 NDSS 2023 bugs before publication, made only a one-tweet public statement, and quietly stopped selling AeroScope days later
tags: [security, regulation]
date: 2026-11-08
by: tea+claude
confidence: moderate
sources: [ndss2023-dji-droneid-schiller, dji-droneid-aftermath-web-excerpts-2026-11-08]
---

- **Disclosure:** coordinated before the February/March 2023 NDSS talk. The paper thanks DJI for a
  "cooperative responsible disclosure process" and swift fixes. The RUB press release first said DJI
  "has taken steps towards fixing", and on 3 March 2023 changed this to say DJI had fixed them.
- **DJI public response (about 9 March 2023):** a short tweet thanking the researchers and saying the bugs were fixed
  before publication. We found no CVE list or advisory naming the 16 bugs (not exhaustively searched).
- **AeroScope:** DJI stopped producing and selling AeroScope, the receiver built on DroneID, in early March
  2023 without an announcement. The portable version had stopped in August 2022. Commentators link this to
  Remote ID and US political pressure. No source links it to the paper, so treat the timing as coincidence
  unless shown otherwise.
- **Cost to DJI:** reputational. Coverage included WIRED, Help Net Security, DroneXL and Hackaday. It came on
  top of the 2022 walk-back of the "encrypted" claim. We found no lawsuit, recall or fine.

Confidence moderate: aftermath comes from news summaries, The Verge and WIRED were not read directly.

Sources: [[ndss2023-dji-droneid-schiller]], [[dji-droneid-aftermath-web-excerpts-2026-11-08]].
