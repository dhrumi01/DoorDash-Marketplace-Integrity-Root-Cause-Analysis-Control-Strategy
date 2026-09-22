# Sources

This file documents the public evidence used in the DoorDash Marketplace Integrity Power BI case study.

The sources are intentionally separated from the README so the project story stays concise while the research remains auditable.

---

## S01 — DoorDash Q2 2026 Financial Results

- **Publisher:** DoorDash Investor Relations
- **Evidence tier:** Tier B — DoorDash first-party
- **Supports:** Marketplace scale and quarterly trend metrics
- **Key values used:** 970M Total Orders; $33.1B Marketplace GOV; $4.5B revenue in Q2 2026
- **URL:** https://ir.doordash.com/financials/quarterly-results/

---

## S02 — NYC Delivery-Worker Pay Settlement

- **Publisher:** Reuters
- **Date:** September 22, 2026
- **Evidence tier:** Tier A — regulator-backed event / independent reporting
- **Supports:** Dasher pay and settlement-integrity deep dive
- **Key values used:** $131.5M total settlement; approximately $115M for workers; approximately 264,000 workers; reported components involving online/on-call methodology and missed/delayed payments
- **Important interpretation:** This confirms the pay-related event and public findings. It does not by itself prove every proposed technical root-cause hypothesis.
- **URL:** https://www.reuters.com/world/doordash-reaches-1315-million-settlement-with-nyc-over-delivery-workers-pay-2026-09-22/

---

## S03 — Building an In-House Case Management Platform

- **Publisher:** DoorDash Engineering
- **Date:** April 15, 2025
- **Evidence tier:** Tier B — DoorDash first-party
- **Supports:** Fragmented-state / source-of-truth mechanism
- **Key evidence:** DoorDash describes agents historically navigating disconnected internal and third-party tools, manual workarounds, inconsistent experiences, and a goal of establishing a unified source of truth.
- **URL:** https://careersatdoordash.com/blog/doordash-case-management-platform/

---

## S04 — Fighting Fraud at Scale: Real-Time Rules Engine

- **Publisher:** DoorDash Engineering
- **Date:** March 9, 2026
- **Evidence tier:** Tier B — DoorDash first-party
- **Supports:** Rule-governance complexity, false-positive risk, explainability, auditability, staged rollout
- **Key evidence:** DoorDash states that overly conservative rules sometimes blocked legitimate activity and describes backtesting, shadow mode, controlled experimentation, and auditable/reversible rule changes.
- **URL:** https://careersatdoordash.com/blog/doordash-fraud-insights-from-building-a-real-time-rules-engine/

---

## S05 — Supercharging DoorDash Logistics Through Causal ML and Joint Optimization

- **Publisher:** DoorDash Engineering
- **Date:** May 21, 2026
- **Evidence tier:** Tier B — DoorDash first-party
- **Supports:** Marketplace optimization tradeoffs and system coordination
- **Key evidence:** DoorDash explains that increasing batch rate may reduce duplicate travel and Dasher cost while increasing consumer delivery duration.
- **URL:** https://careersatdoordash.com/blog/supercharging-doordash-logistics-through-causal-ml-and-joint-optimization/

---

## S06 — Integrated Promotions

- **Publisher:** DoorDash Developer Services
- **Evidence tier:** Tier B — DoorDash first-party
- **Supports:** Cross-system promotion reconciliation
- **Key evidence:** DoorDash describes promotion reconciliation as time-consuming and documents merchant-funded, DoorDash-funded, co-funded, and stacked-promotion fields plus final-state reconciliation requirements.
- **URL:** https://developer.doordash.com/docs/marketplace/how_to/integrated_promotions/

---

## S07 — DoorDash Merchant Pricing

- **Publisher:** DoorDash for Merchants
- **Evidence tier:** Tier B — DoorDash first-party
- **Supports:** Merchant economics context
- **Key values used:** 15% Basic delivery commission; 25% Plus; 30% Premier; 6% pickup
- **URL:** https://merchants.doordash.com/en-us/pricing

---

## S08 — Menu Pricing Insights

- **Publisher:** DoorDash for Merchants
- **Evidence tier:** Tier B — DoorDash first-party
- **Supports:** Menu-pricing / demand tradeoff
- **Key evidence:** DoorDash reports a 2023 internal study of 4,500+ restaurants in which marked-up restaurants could see up to 37% fewer sales and up to 78% lower reorder rates.
- **Important interpretation:** These are DoorDash-reported “up to” study findings and are not treated as universal causal effects.
- **URL:** https://merchants.doordash.com/en-us/learning-center/menu-pricing-insights

---

## S09 — July 9, 2025 Service Incident

- **Publisher:** DoorDash Engineering
- **Date:** July 15, 2025
- **Evidence tier:** Tier B — DoorDash first-party
- **Supports:** Cross-service dependency and cascading-failure control context
- **Key evidence:** DoorDash describes work to remove hard dependencies between services so degradation in one area does not cascade into another.
- **URL:** https://careersatdoordash.com/blog/july-9-2025-incident-and-steps-forward/

---

## Source Usage Rules

- Tier A/B sources support factual statements and documented mechanisms.
- Complaint/community evidence should be treated only as a signal unless independently validated.
- Public evidence cannot establish undisclosed DoorDash defect rates.
- Proposed controls in the dashboard are analytical recommendations, not descriptions of DoorDash's current internal architecture.
- Historical findings are labeled with their relevant dates and are not presented as current behavior unless current evidence supports that conclusion.
