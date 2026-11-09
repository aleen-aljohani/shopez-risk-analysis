# Risk Analysis for ShopEZ — FAIR Quantitative Risk Assessment

A quantitative information-security risk assessment of **ShopEZ**, a fictional e-commerce company using an AI-driven customer-analytics platform. The analysis applies the **FAIR (Factor Analysis of Information Risk)** model to express cyber risk in financial terms, using Monte Carlo simulation (FAIR-U workbook) to estimate annualized loss exposure.

> 🎓 Course project for **EMCS611 – Information Risk Management**, Executive Master in Cyber Security, King Abdulaziz University (Fall 2025). Completed as a group project; published here with my teammates' consent. Student IDs and teammates' names have been removed for privacy.

📄 [Full Report (DOCX)](ShopEZ_Risk_Analysis_Report.docx) · [Presentation (PDF)](ShopEZ_Risk_Analysis_Presentation.pdf)

---

## What is FAIR?

FAIR is an international standard for **quantitative** risk analysis. Instead of rating risk as "High / Medium / Low", it breaks risk into measurable factors — how often a threat event happens (**Threat Event Frequency**), how likely it is to succeed (**Vulnerability**), and how much it costs (**Loss Magnitude**) — then runs a **Monte Carlo simulation** to produce a probable range of annual financial loss (**Annualized Loss Exposure, ALE**).

---

## The Case

ShopEZ relies on an AI customer-analytics system. This assessment models two realistic risk scenarios, each analyzed end-to-end with FAIR and simulated over 10,000 iterations.

### Scenario 1 — Customer Data Confidentiality (Model Inversion Attack)

| Factor | Value |
|---|---|
| **Asset at risk** | Customer sensitive information |
| **Threat community** | External malicious attackers |
| **Threat effect** | Confidentiality |
| **Threat vector** | Model inversion attack |
| **Threat Event Frequency** | Min 1 · ML 3 · Max 6 per year (High confidence) |
| **Vulnerability** | 20% – 50% – 60% (Medium confidence) |
| **Average ALE** | **≈ €8.5 million → Major (Level 4)** |

External attackers exploit model-inversion techniques to infer sensitive customer data from the AI model's outputs. Secondary losses (regulatory, legal, reputational) are near-certain (~98%) and far exceed the direct response costs.

### Scenario 2 — Data Integrity via Third-Party Access

| Factor | Value |
|---|---|
| **Asset at risk** | AI model's datasets |
| **Threat community** | External contractors with privileged access |
| **Threat effect** | Integrity |
| **Threat vector** | Vulnerabilities in third-party integrations |
| **Threat Event Frequency** | Min 2 · ML 4 · Max 6 per year (High confidence) |
| **Vulnerability** | 30% – 40% – 50% (Medium confidence) |
| **Average ALE** | **≈ €37.69 million → Critical (Level 5)** |

Privileged external contractors introduce corrupted or manipulated data, compromising the integrity and reliability of the AI datasets. Lost portal revenue and GDPR fines drive a severe financial exposure.

---

## Method

For each scenario the analysis estimates, with documented rationale and confidence levels:

1. **Threat Event Frequency (TEF)** — from historical records and industry reports
2. **Vulnerability** — likelihood an attempt succeeds
3. **Secondary Loss Event Frequency (SLEF)** — probability of downstream impacts
4. **Loss Magnitude** — primary losses (incident response, forensics, retraining) and secondary losses (customer notification, credit monitoring, GDPR fines, class-action lawsuits, reputational damage)

These feed the **FAIR-U workbook**, which runs a Monte Carlo simulation and produces a **Loss Exceedance Curve** and ALE statistics (min, average, 90th percentile, max).

---

## Key Findings

- ShopEZ faces **material AI-related risk in both scenarios**, driven largely by **secondary losses** (regulatory penalties, reputational damage) that dwarf direct costs.
- Scenario 2 (third-party data integrity) is the more severe, rated **Critical** with an average ALE of ~€37.69M.
- At least one loss-causing incident per year is **likely to near-certain** in both scenarios.

## Recommended Controls

- Privacy-preserving techniques and strict query rate-limiting on AI model outputs
- Strong input validation and anomaly detection on third-party data streams
- Role-based access control (RBAC) and segregation of duties for data and model pipelines
- AI-specific incident response, monitoring, and logging of model queries
- Regular security assessments, staff training, and GDPR governance

---

## Skills & Concepts

`FAIR` · `Quantitative Risk Analysis` · `Monte Carlo Simulation` · `Information Risk Management` · `AI/ML Security` · `Loss Exceedance Curve` · `GDPR`
