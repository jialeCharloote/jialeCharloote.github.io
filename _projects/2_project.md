---
layout: page
title: Greenwashing
description: An analysis of corporate greenwashing behavior in ESG disclosures
img: assets/img/3.jpg
importance: 4
category: work
---

# Greenwashing: Corporate ESG Disclosure

## Definition: Selective Disclosure
Greenwashing refers to a company's practice of retaining negative environmental/social performance information and disclosing only positive information related to its environmental/social impact.

### Signs of Greenwashing (Possible X)
- **Leveraging self-disclosure and company commitments**
- **Divestitures**: Divesting pollutive assets to firms facing weaker environmental pressures (Duchin et al., 2022, p. 3).
- **Vague and ambitious words without practical action**: Policies vs. targets. Specific goals versus vague descriptive language.
- **No proof**: Environmental claims lacking easily accessible supporting information or reliable third-party certification.

### Identify Greenwashing (Possible Y)
- **Need more objective measures**: e.g., total pollution, violations, misconduct, employee gender diversity.
- **Involved in greenwashing controversies**: Look for related news using keywords such as ‘litigation’, ‘lawsuit’, ‘fine’, ‘sue’, etc.
- **Companies violating regulations**: Scrutinize news, social media (Twitter), and regulatory violations.

## Related Literature
- **Greenwash: Corporate Environmental Disclosure under Threat of Audit** [Link: https://doi.org/10.1111/j.1530-9134.2010.00282.x]
- **Diversity Washing (Baker et al., 2022)**: Measures based on the distance between DEI commitment disclosure and actual diversity.
- **Sustainability or Greenwashing (Duchin et al., 2022)**: Poisson DiD regression model exploring pollution levels and abatement activities.

## Poisson DiD Regression:

```python
Y_i,t = β Divested_i × Post_i,t + α_i + τ_t + ε_i,t


{% endraw %}
