---
type: source
title: "Vehicle anti-tampering law and enforcement excerpts: Euro 7, Regulation 168/2013, EPA tampering, Cyber Resilience Act dates"
tags: [regulation, security]
date: 2026-11-07
by: tea+claude
url: https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=OJ:L_202401257
---

Excerpts collected 2026-11-07 by web fetch and search. Quotes are as returned by the fetch tool;
re-check against the official PDFs before quoting on a slide.

## Euro 7, Regulation (EU) 2024/1257

URL: https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=OJ:L_202401257

- Article 3(45), tampering: "the inactivation, or modification of the engine or electric motor,
  vehicle pollution control devices and system, propulsion system, traction battery, odometer, OBFCM
  device, OBD or OBM system, including any software or other logical control elements of those
  systems and their data, resulting in the vehicle not complying with this Regulation".
- Article 4(7): manufacturers design vehicles "to minimise vulnerabilities, arising in all phases of
  their life-cycle" that could enable tampering. Systems named include fuel and reagent injection,
  engines and engine control units, traction batteries and their management systems, the odometer,
  pollution control systems, the electric motor and its control units, OBFCM, OBD and OBM.
- Article 4(11): secure transmission of emissions and battery durability data, with cybersecurity
  measures under UN Regulation No 155.
- Article 21, application: "from 29 November 2026 for new types of vehicles of categories M1 and N1";
  "from 29 November 2027 for new vehicles of categories M1 and N1"; "from 29 May 2028 for new types of
  vehicles of categories M2, M3, N2, N3"; "from 29 May 2029 for new vehicles of categories M2, M3, N2,
  N3, O3 and O4".

Secondary (search summaries, not fetched in full):
- CLOVE study for the Commission on Euro 7 LDV implementing rules maps ECU tampering to UN R155
  threat 23.1 and mitigation M7 ("access control techniques and designs shall be applied to protect
  system data/code"); example ECU measures: encrypted software, tamper-resistant hardware, tampering
  indicator values or flags.
  https://circabc.europa.eu/d/d/workspace/SpacesStore/8eb197c6-af2f-4d3d-8449-79906862f7db/%5b4%5d%20CLOVE%20-%20Anti-tampering%2c%20security%20and%20cybersecurity%20systems%20in%20Euro%207%20LDV%20implementing%20rules.pdf.pdf
- LDV implementing act 2025/1706, Annex XIV: anti-tampering and (cyber)security requirements.
- FEV: protection against unauthorised reprogramming of relevant control units.
  https://fev.io/cybersecurity-activities-required-for-euro-7/
- NCC Group white paper on Euro 7 anti-tampering:
  https://www.nccgroup.com/media/3nddn2i0/euro-7-antitampering-and-the-expanding-cybersecurity-landscape.pdf

## Regulation (EU) No 168/2013, Article 20 (two- and three-wheel vehicles, quadricycles)

URL: https://eur-lex.europa.eu/eli/reg/2013/168/oj/eng ; https://www.legislation.gov.uk/eur/2013/168/article/20

- Para 1: manufacturers "shall equip" L-category vehicles (except L3e-A3 and L4e-A3) "with designated
  features to prevent tampering of a vehicle's powertrain", to prevent modifications that "increase
  the maximum torque and/or power and/or maximum design vehicle speed".
- Para 4: manufacturers "shall endeavour, through the use of best engineering practice, to prevent such
  modifications or adjustments from being technically possible".
- Delegated Regulation 134/2014: the manufacturer submits "a description of the measures taken to
  prevent tampering with the powertrain management system including the computers controlling the
  environmental and propulsion unit performance".
- Not verified: standard pedelecs (25 km/h, 250 W) are outside 168/2013 (Article 2(2)(h)).

## US EPA, tampering and aftermarket defeat devices

URL: https://cleanairnortheast.epa.gov/tampering.html (last updated 15 September 2025)

- "Recent EPA investigations indicate that controls on over 500,000 diesel pickup trucks, or about 13%
  of those registered" [originally certified with emission controls] have been removed.
- "The excess NOx emissions from these vehicles is the equivalent of adding 9 million trucks to our roads."
- Tuning: "Replacing or altering the software or calibrations that control engine operation,
  sometimes referred to as "tuning.""

Underlying report (PDF, text not extracted here): EPA Air Enforcement Division, "Tampered Diesel
Pickup Trucks: A Review of Aggregated Evidence from EPA Civil Enforcement Investigations", November
2020. Search summaries give "more than 550,000" pickups and "more than 570,000 tons" of excess NOx.
https://19january2021snapshot.epa.gov/sites/static/files/2021-01/documents/epaaedletterreportontampereddieselpickups.pdf

## EU Cyber Resilience Act, dates

URL: https://digital-strategy.ec.europa.eu/en/policies/cyber-resilience-act

- Main obligations apply from 11 December 2027; reporting obligations from 11 September 2026
  (actively exploited vulnerabilities and severe incidents, to ENISA and national CSIRTs).
