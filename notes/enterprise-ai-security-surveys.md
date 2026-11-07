---
type: note
title: Enterprise AI surveys separate adoption, intention, concern, and review delay
tags: [customer, market, security]
date: 2026-11-07
by: karla+grok
confidence: low
sources: [https://www.mckinsey.com/capabilities/quantumblack/our-insights/open-source-technology-in-the-age-of-ai, https://www.redhat.com/en/blog/2024-enterprise-trends-cloud-meets-ai, https://www.enterprisemanagement.com/product/the-state-of-ai-friction-why-enterprise-ai-deployment-is-slower-costlier-and-more-limited-than-expected/]
---

Schema: [[code-protection-evidence-schema]]. Index: [[code-protection-evidence-index]].

Nine records from three surveys. McKinsey/Mozilla/McGovern: sample `>700 respondents`, 41 countries, fieldwork not found. The 63% figure is not strictly OSI-open-source adoption. The 76% figure is intention, not adoption. The 62% figure is concern, not a blocked security review. Red Hat is vendor-sponsored; its 43% is not exclusively security-review delay; fieldwork dates were not found. EMA’s 82.9% is organizations reporting review delay; sponsorship was not found; the sample was fielded April 2026; geography was not found. The excluded Anaconda page is [[code-protection-evidence-gaps]] `EV-GAP-ANACONDA-SURVEY`.

<a id="ev-mckinsey-osai-use-2025"></a>

### EV-MCKINSEY-OSAI-USE-2025

- id: EV-MCKINSEY-OSAI-USE-2025
- evidence_status: survey-response
- measure: Respondents reporting their organizations use an “open source AI model.” Publisher category includes open-weight families; not strictly OSI-open-source adoption
- value: 63%
- unit: percent
- publication_date: 22 Apr 2025
- source: [McKinsey, open source technology in the age of AI](https://www.mckinsey.com/capabilities/quantumblack/our-insights/open-source-technology-in-the-age-of-ai)
- sample: >700 respondents; technology leaders and senior developers ([EV-MCKINSEY-OSAI-SAMPLE-2025](#ev-mckinsey-osai-sample-2025))
- geography: 41 countries; full country list not found in the opened article ([EV-MCKINSEY-OSAI-GEOGRAPHY-2025](#ev-mckinsey-osai-geography-2025))
- fieldwork: not found
- sponsorship: McKinsey/Mozilla/McGovern
- confidence: moderate
- confidence_basis: Moderate—survey
- limitations: Publisher category includes open-weight families; not strictly OSI-open-source adoption. Survey response, not a spending or loss measurement.
- related: [EV-MCKINSEY-OSAI-SAMPLE-2025](#ev-mckinsey-osai-sample-2025); [EV-MCKINSEY-OSAI-GEOGRAPHY-2025](#ev-mckinsey-osai-geography-2025)

<a id="ev-mckinsey-osai-intention-2025"></a>

### EV-MCKINSEY-OSAI-INTENTION-2025

- id: EV-MCKINSEY-OSAI-INTENTION-2025
- evidence_status: survey-response
- measure: Respondents expecting increased organizational use of open-source AI technologies over coming years; intention, not adoption
- value: 76%
- unit: percent
- publication_date: 22 Apr 2025
- source: [McKinsey, open source technology in the age of AI](https://www.mckinsey.com/capabilities/quantumblack/our-insights/open-source-technology-in-the-age-of-ai)
- sample: >700 respondents; technology leaders and senior developers ([EV-MCKINSEY-OSAI-SAMPLE-2025](#ev-mckinsey-osai-sample-2025))
- geography: 41 countries; full country list not found in the opened article ([EV-MCKINSEY-OSAI-GEOGRAPHY-2025](#ev-mckinsey-osai-geography-2025))
- fieldwork: not found
- sponsorship: McKinsey/Mozilla/McGovern
- confidence: moderate
- limitations: Intention, not adoption. The horizon stated in the measure is coming years, not a measured adoption rate.
- related: [EV-MCKINSEY-OSAI-SAMPLE-2025](#ev-mckinsey-osai-sample-2025); [EV-MCKINSEY-OSAI-GEOGRAPHY-2025](#ev-mckinsey-osai-geography-2025)

<a id="ev-mckinsey-osai-cyber-concern-2025"></a>

### EV-MCKINSEY-OSAI-CYBER-CONCERN-2025

- id: EV-MCKINSEY-OSAI-CYBER-CONCERN-2025
- evidence_status: survey-response
- measure: Respondents citing cybersecurity concerns when engaging with AI tools; concern, not evidence of blocked security review
- value: 62%
- unit: percent
- publication_date: 22 Apr 2025
- source: [McKinsey, open source technology in the age of AI](https://www.mckinsey.com/capabilities/quantumblack/our-insights/open-source-technology-in-the-age-of-ai)
- sample: >700 respondents; technology leaders and senior developers ([EV-MCKINSEY-OSAI-SAMPLE-2025](#ev-mckinsey-osai-sample-2025))
- geography: 41 countries; full country list not found in the opened article ([EV-MCKINSEY-OSAI-GEOGRAPHY-2025](#ev-mckinsey-osai-geography-2025))
- fieldwork: not found
- sponsorship: McKinsey/Mozilla/McGovern
- confidence: moderate
- limitations: Concern, not evidence of blocked security review.
- related: [EV-MCKINSEY-OSAI-SAMPLE-2025](#ev-mckinsey-osai-sample-2025); [EV-MCKINSEY-OSAI-GEOGRAPHY-2025](#ev-mckinsey-osai-geography-2025)

<a id="ev-mckinsey-osai-sample-2025"></a>

### EV-MCKINSEY-OSAI-SAMPLE-2025

- id: EV-MCKINSEY-OSAI-SAMPLE-2025
- evidence_status: survey-method
- measure: McKinsey/Mozilla/McGovern sample: technology leaders and senior developers; exact fieldwork dates not found in opened article
- value: >700 respondents
- unit: respondents
- publication_date: 22 Apr 2025
- source: [McKinsey, open source technology in the age of AI](https://www.mckinsey.com/capabilities/quantumblack/our-insights/open-source-technology-in-the-age-of-ai)
- sample: >700 respondents; technology leaders and senior developers ([EV-MCKINSEY-OSAI-SAMPLE-2025](#ev-mckinsey-osai-sample-2025))
- geography: 41 countries; full country list not found in the opened article ([EV-MCKINSEY-OSAI-GEOGRAPHY-2025](#ev-mckinsey-osai-geography-2025))
- fieldwork: not found
- sponsorship: McKinsey/Mozilla/McGovern
- confidence: moderate
- limitations: Exact fieldwork dates not found in the opened article. Keep the value as >700 respondents, not 700. Sponsorship as stated: McKinsey/Mozilla/McGovern.
- related: [EV-MCKINSEY-OSAI-USE-2025](#ev-mckinsey-osai-use-2025); [EV-MCKINSEY-OSAI-INTENTION-2025](#ev-mckinsey-osai-intention-2025); [EV-MCKINSEY-OSAI-CYBER-CONCERN-2025](#ev-mckinsey-osai-cyber-concern-2025); [EV-MCKINSEY-OSAI-GEOGRAPHY-2025](#ev-mckinsey-osai-geography-2025)

<a id="ev-mckinsey-osai-geography-2025"></a>

### EV-MCKINSEY-OSAI-GEOGRAPHY-2025

- id: EV-MCKINSEY-OSAI-GEOGRAPHY-2025
- evidence_status: survey-method
- measure: Geographic coverage of that survey; full country list not found in opened article
- value: 41 countries
- unit: countries
- publication_date: 22 Apr 2025
- source: [McKinsey, open source technology in the age of AI](https://www.mckinsey.com/capabilities/quantumblack/our-insights/open-source-technology-in-the-age-of-ai)
- sample: >700 respondents; technology leaders and senior developers ([EV-MCKINSEY-OSAI-SAMPLE-2025](#ev-mckinsey-osai-sample-2025))
- geography: 41 countries; full country list not found in the opened article ([EV-MCKINSEY-OSAI-GEOGRAPHY-2025](#ev-mckinsey-osai-geography-2025))
- fieldwork: not found
- sponsorship: McKinsey/Mozilla/McGovern
- confidence: moderate
- limitations: Full country list not found in the opened article.
- related: [EV-MCKINSEY-OSAI-SAMPLE-2025](#ev-mckinsey-osai-sample-2025)

<a id="ev-redhat-genai-privacy-2024"></a>

### EV-REDHAT-GENAI-PRIVACY-2024

- id: EV-REDHAT-GENAI-PRIVACY-2024
- evidence_status: survey-response
- measure: Red Hat respondents identifying data privacy/security concerns as obstacles to advancing generative-AI initiatives; not exclusively security-review delay
- value: 43%
- unit: percent
- publication_date: 8 Oct 2024
- source: [Red Hat, 2024 enterprise trends](https://www.redhat.com/en/blog/2024-enterprise-trends-cloud-meets-ai)
- sample: 609 respondents; enterprise IT managers across France, Germany, Italy, Spain, UAE and UK ([EV-REDHAT-GENAI-SAMPLE-2024](#ev-redhat-genai-sample-2024))
- geography: France, Germany, Italy, Spain, UAE and UK
- fieldwork: not found
- sponsorship: vendor-sponsored (Red Hat)
- confidence: low
- confidence_basis: Low—vendor-sponsored
- limitations: Not exclusively security-review delay. Vendor-sponsored survey.
- related: [EV-REDHAT-GENAI-SAMPLE-2024](#ev-redhat-genai-sample-2024)

<a id="ev-redhat-genai-sample-2024"></a>

### EV-REDHAT-GENAI-SAMPLE-2024

- id: EV-REDHAT-GENAI-SAMPLE-2024
- evidence_status: survey-method
- measure: Red Hat enterprise IT-manager sample across France, Germany, Italy, Spain, UAE and UK; fieldwork dates not found
- value: 609 respondents
- unit: respondents
- publication_date: 8 Oct 2024
- source: [Red Hat, 2024 enterprise trends](https://www.redhat.com/en/blog/2024-enterprise-trends-cloud-meets-ai)
- sample: 609 respondents; enterprise IT managers across France, Germany, Italy, Spain, UAE and UK ([EV-REDHAT-GENAI-SAMPLE-2024](#ev-redhat-genai-sample-2024))
- geography: France, Germany, Italy, Spain, UAE and UK
- fieldwork: not found
- sponsorship: vendor-sponsored (Red Hat)
- confidence: low
- confidence_basis: Low—vendor-sponsored
- limitations: Fieldwork dates not found. Geography as stated: France, Germany, Italy, Spain, UAE and UK. Vendor-sponsored.
- related: [EV-REDHAT-GENAI-PRIVACY-2024](#ev-redhat-genai-privacy-2024)

<a id="ev-ema-ai-review-delay-2026"></a>

### EV-EMA-AI-REVIEW-DELAY-2026

- id: EV-EMA-AI-REVIEW-DELAY-2026
- evidence_status: survey-response
- measure: Organizations reporting security/compliance reviews delayed AI projects entering production
- value: 82.9%
- unit: percent
- publication_date: 30 Jul 2026
- source: [Enterprise Management Associates, state of AI friction](https://www.enterprisemanagement.com/product/the-state-of-ai-friction-why-enterprise-ai-deployment-is-slower-costlier-and-more-limited-than-expected/)
- sample: 152 respondents; EMA IT/security-leader sample ([EV-EMA-AI-FRICTION-SAMPLE-2026](#ev-ema-ai-friction-sample-2026))
- geography: not found
- fieldwork: April 2026
- sponsorship: not found
- confidence: moderate
- confidence_basis: Moderate; sponsorship not found
- limitations: Share of organizations reporting that security/compliance reviews delayed AI projects entering production. Sponsorship not found. Fieldwork April 2026 and sample size are on the linked sample record.
- related: [EV-EMA-AI-FRICTION-SAMPLE-2026](#ev-ema-ai-friction-sample-2026)

<a id="ev-ema-ai-friction-sample-2026"></a>

### EV-EMA-AI-FRICTION-SAMPLE-2026

- id: EV-EMA-AI-FRICTION-SAMPLE-2026
- evidence_status: survey-method
- measure: EMA IT/security-leader sample, fielded April 2026; geography not found on opened publisher page
- value: 152 respondents
- unit: respondents
- publication_date: 30 Jul 2026
- source: [Enterprise Management Associates, state of AI friction](https://www.enterprisemanagement.com/product/the-state-of-ai-friction-why-enterprise-ai-deployment-is-slower-costlier-and-more-limited-than-expected/)
- sample: 152 respondents; EMA IT/security-leader sample ([EV-EMA-AI-FRICTION-SAMPLE-2026](#ev-ema-ai-friction-sample-2026))
- geography: not found
- fieldwork: April 2026
- sponsorship: not found
- confidence: moderate
- limitations: Fielded April 2026. Geography not found on the opened publisher page. Sponsorship was not found on the paired result row.
- related: [EV-EMA-AI-REVIEW-DELAY-2026](#ev-ema-ai-review-delay-2026)
