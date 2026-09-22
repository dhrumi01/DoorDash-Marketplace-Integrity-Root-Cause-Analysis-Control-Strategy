# DoorDash Marketplace Integrity
## Power BI Root Cause Analysis & Control Strategy

An independent **Power BI case study** using public DoorDash evidence to investigate recurring marketplace-control risks across **Customers, Merchants, and Dashers**.

> ### Business Question
> **Where can expected marketplace outcomes diverge from actual operational or financial outcomes, what recurring mechanisms appear in public evidence, and which controls should be investigated first?**

**Research coverage:** Public information available through September 22, 2026.

---

# 📊 Dashboard Preview

## 01 — Executive Overview

![Executive Overview](screenshots/01-executive-overview.png)

### What this page answers

**What is the scale of the marketplace, what evidence is available, and which recurring control mechanisms appear across the research?**

This page establishes DoorDash's operating scale and summarizes the evidence used in the Root Cause Analysis.

It includes:

- Q2 2026 Total Orders
- Marketplace GOV
- Revenue
- NYC Dasher-pay settlement
- quarterly order and GOV trends
- evidence grouped by mechanism
- evidence-backed RCA register

DoorDash reported approximately:

- **970M Total Orders**
- **$33.1B Marketplace GOV**
- **$4.5B Revenue**

in Q2 2026.

At this scale, even relatively uncommon exception states can become operationally meaningful.

The RCA register is **not intended to estimate DoorDash's defect frequency**. It identifies recurring mechanisms that would be worth validating with internal data.

---

## 02 — Root Cause Explorer

![Root Cause Explorer](screenshots/02-root-cause-explorer.png)

### What this page answers

**What underlying mechanisms appear across Customer, Merchant, and Dasher issues?**

The Power BI **Decomposition Tree** allows the analysis to move through:

**Stakeholder → Domain → Problem → Mechanism → Control Type → Claim Status**

Interactive filters include:

- Stakeholder
- Domain
- Evidence Status
- Source Tier

The analysis intentionally separates:

**Confirmed Incident → Confirmed Mechanism → Supported Hypothesis → Internal Validation Required**

A documented incident does not automatically establish its technical root cause.

---

## 03 — Customer & Merchant Integrity

![Customer & Merchant Integrity](screenshots/03-customer-merchant.png)

### What this page answers

**Where do pricing, merchant economics, promotions, and responsibility create marketplace-integrity risk?**

The analysis examines:

- DoorDash Marketplace commission structure
- menu-pricing economics
- customer pricing and fee expectations
- promotion reconciliation
- merchant error responsibility
- complaint-channel signals

Important interpretation:

**Complaint counts are treated as Voice-of-Customer signals only.**

They are not presented as DoorDash-wide failure rates.

DoorDash merchant-study findings are also presented as company-reported research rather than assumed universal causal effects.

---

## 04 — Dasher Pay & Compliance

![Dasher Pay & Compliance](screenshots/04-dasher-pay.png)

### What this page answers

**How can complex delivery states create compensation and settlement-control risk?**

The **September 22, 2026 New York City delivery-worker settlement** is used as the strongest real-world anchor case in this project.

The analytical chain is:

**Event State → Jurisdiction → Rule Version → Expected Pay → Actual Pay → Adjustment → Payout**

The settlement confirms that compensation-related issues occurred.

The project then asks a separate Root Cause Analysis question:

> **Could stronger event-level reconciliation detect incorrect or delayed compensation before payout closes?**

This is treated as a **control hypothesis requiring internal DoorDash data to validate**, not as a confirmed description of DoorDash's internal architecture.

---

## 05 — Strategy & Roadmap

![Strategy & Roadmap](screenshots/05-strategy-roadmap.png)

### What this page answers

**What should happen after the root causes are identified?**

The RCA findings are translated into a proposed control strategy and phased implementation roadmap.

The proposed control areas are:

1. **Canonical Transaction State**
2. **Versioned Rule Governance**
3. **Expected-vs-Actual Reconciliation**
4. **Explainable Exception Routing**
5. **Closed-Loop Settlement Confirmation**

### North-Star Control Principle

> **A high-risk transaction should not financially close when the expected rule outcome and actual downstream outcome differ without an explicit, auditable explanation and an owned exception path.**

The strategy page moves the project beyond identifying problems and into:

**Action → Control → Ownership → KPI**

---

## 06 — Evidence & Research Method

![Evidence & Research Method](screenshots/06-evidence-method.png)

### What this page answers

**Where did the evidence come from and how reliable is each claim?**

Instead of treating every complaint or public post as proof, the project uses an evidence hierarchy.

### Evidence Tiers

**Tier A — Primary External Evidence**

- regulatory records
- SEC filings
- regulator-backed settlements
- high-quality independent reporting

**Tier B — DoorDash First-Party Evidence**

- DoorDash Engineering
- DoorDash Developer documentation
- DoorDash Merchant documentation
- DoorDash product/help documentation
- DoorDash Investor Relations

**Tier C — Complaint / Community Signals**

Used only to discover possible edge cases and recurring themes.

Tier C evidence is **never treated as proof of prevalence or causality**.

---

## 07 — RCA Detail

![RCA Detail](screenshots/07-rca-detail.png)

### What this page answers

**What is the complete reasoning chain behind one root-cause hypothesis?**

The drill-through page connects:

**Problem → Evidence → Mechanism → Root-Cause Hypothesis → Internal Validation Question → Recommended Control → KPI**

This allows a user to move from the high-level Root Cause Explorer into the actual reasoning behind an individual mechanism.

---

# 🎯 Project Goal

DoorDash operates a three-sided marketplace connecting:

- Customers
- Merchants
- Dashers

A single order can move through multiple systems:

**Catalog → Promotions → Pricing → Checkout → Payment → Merchant Fulfillment → Dispatch → Delivery → Support → Settlement**

The analytical challenge is maintaining consistency across these handoffs.

This project is **not a complaint dashboard**.

Instead, I wanted to investigate whether different documented DoorDash issues point to recurring:

- system-handoff problems
- rule-governance complexity
- reconciliation challenges
- exception-management gaps
- optimization tradeoffs

The analysis follows:

**Problem → Current State → Evidence → Root-Cause Hypothesis → Internal Validation → Strategy → Future State → KPI**

---

# 🔍 Research Method

I used a structured source hierarchy rather than treating every public complaint as proof.

## Claim Classification

### Confirmed Incident
An event or outcome directly documented by a reliable source.

### Confirmed Mechanism
DoorDash, a regulator, or another primary source explicitly describes the underlying mechanism.

### Confirmed Context
A factual business rule, economic condition, or operating constraint.

### Supported Hypothesis
An analytical explanation consistent with the evidence but requiring internal DoorDash data to establish causality.

### Signal Only
Complaint or community evidence used for hypothesis discovery only.

This prevents an inference from being presented as a fact.

---

# 🧩 Main Root Cause Themes

## 1. Fragmented State / Source of Truth

DoorDash has publicly described support workflows that historically required agents to move across disconnected internal and third-party tools.

This can create:

- context switching
- manual workarounds
- incomplete case visibility
- slower exception resolution
- inconsistent experiences

### RCA Question

**Are important order, case, and financial states sufficiently synchronized across systems?**

---

## 2. Rule-Governance Complexity

Pricing, promotions, fraud, compensation, eligibility, and compliance decisions may depend on:

- geography
- eligibility
- transaction state
- timing
- rule version
- exception state

DoorDash Engineering has also documented that overly conservative fraud rules can affect legitimate activity.

### RCA Question

**Can every important decision be traced back to the exact rule version and context that produced it?**

---

## 3. Cross-System Reconciliation

Financial values may need to remain consistent across:

**Customer Checkout → Payment → Platform Funding → Merchant Accounting → Final Settlement**

Promotion funding is a strong example.

DoorDash documentation describes:

- merchant-funded promotions
- DoorDash-funded promotions
- co-funded promotions
- stacked promotions
- downstream reconciliation requirements

### RCA Question

**Does the financial state remain consistent across every downstream system?**

---

## 4. Independent Optimization / Objective Tradeoffs

Marketplace optimization is not always about maximizing one metric.

For example:

**Higher batching efficiency**

may reduce:

**duplicate travel / delivery cost**

while potentially increasing:

**consumer delivery duration**

This is not necessarily a software defect.

It is a **multi-objective marketplace optimization problem**.

### RCA Question

**Are individual systems optimizing locally while unintentionally creating costs elsewhere in the marketplace?**

---

## 5. Exception Handling Under Uncertainty

Automation is necessary at marketplace scale.

However, ambiguous cases may require:

- decision confidence
- supporting evidence
- explainability
- escalation
- human review
- authorized override paths

### RCA Question

**When confidence is low, does the system have a clear path for investigation and correction?**

---

## 6. Transaction & Settlement Integrity

Complex event states ultimately need to reconcile with the correct financial outcome.

The Dasher-pay case is used to investigate the broader question:

> **Does the expected outcome match the actual downstream settlement?**

---

# 🛠 Proposed Control Strategy

The analysis leads to five proposed control areas.

## 1. Canonical Transaction State

Maintain one traceable representation of important transaction and financial states across critical system handoffs.

---

## 2. Versioned Rule Governance

Record:

**Rule → Version → Jurisdiction → Eligibility → Effective Date → Outcome**

for important automated decisions.

---

## 3. Expected-vs-Actual Reconciliation

Compare:

**What should have happened**

against:

**What actually happened**

before financial settlement closes.

---

## 4. Explainable Exception Routing

Low-confidence automated decisions should include:

- reason code
- supporting evidence
- confidence
- review path
- authorized corrective action

---

## 5. Closed-Loop Settlement

An unresolved financial mismatch should remain an open exception until the downstream outcome is:

- confirmed
- corrected
- reviewed
- explicitly accepted

These are **analytical recommendations**, not claims about DoorDash's current internal implementation.

---

# 🔄 Future-State Concept

```text
Expected Outcome
      ↓
Actual Outcome
      ↓
Reconciliation
      ↓
     Match?
     /    \
   Yes     No
    ↓       ↓
  Close   Exception
            ↓
      Confidence + Evidence
           /        \
     Auto-correct   Human Review
           \        /
            ↓      ↓
      Settlement Confirmed
```

The objective is to identify transaction inconsistencies **before they become customer complaints, merchant disputes, payment issues, or regulatory problems**.

---

# 📈 What I Would Validate With Internal Data

If this were an internal DoorDash engagement, I would test:

### Customer

- displayed price vs. authorized payment
- authorized payment vs. final settled amount
- promotion eligibility vs. promotion actually applied
- support decision vs. appeal outcome

### Merchant

- merchant-funded vs. DoorDash-funded promotions
- promotion reconciliation
- error responsibility assignment
- merchant disputes vs. overturned decisions
- markup vs. conversion / reorder behavior

### Dasher

- expected compensation vs. actual compensation
- jurisdiction used for pay calculation
- rule version used
- adjustment calculation
- payout timing
- payout receipt confirmation

### Marketplace / Logistics

- batching vs. delivery duration
- batching vs. Dasher miles
- merchant wait time
- cancellation rate
- cost per delivery
- consumer experience

This would convert the public-evidence RCA into a measurable internal **Marketplace Integrity Monitoring System**.

---

# ⚙️ Power BI Features Used

- Power BI Desktop
- Power BI Project / PBIP
- TMDL semantic model
- DAX measures
- Decomposition Tree
- dropdown slicers
- cross-filtering
- drill-through
- KPI cards
- line charts
- column charts
- bar charts
- analytical tables
- page navigation
- evidence-status filtering

---

# 🧮 Example DAX

```DAX
Evidence Records =
COUNTROWS(Evidence)
```

```DAX
Q2 Orders M =
DIVIDE(
    CALCULATE(
        MAX(PublicKPI[Value]),
        PublicKPI[MetricID] = "ORDERS_Q2_2026"
    ),
    1000000
)
```

---

# 📚 Public Sources

The project relies primarily on regulator-backed evidence and DoorDash's own engineering, developer, merchant, and investor documentation.

## 1. DoorDash Q2 2026 Financial Results

**Publisher:** DoorDash Investor Relations  
**Used for:** Marketplace scale, Q2 Total Orders, GOV, revenue and trend data.

https://ir.doordash.com/financials/quarterly-results/

---

## 2. NYC Delivery-Worker Pay Settlement

**Publisher:** Reuters  
**Date:** September 22, 2026  
**Used for:** Dasher Pay & Compliance deep dive.

Public reporting described a **$131.5M settlement** concerning delivery-worker compensation issues.

https://www.reuters.com/world/doordash-reaches-1315-million-settlement-with-nyc-over-delivery-workers-pay-2026-09-22/

---

## 3. DoorDash Case Management Platform

**Publisher:** DoorDash Engineering  
**Used for:** Fragmented-state and source-of-truth analysis.

DoorDash describes support agents historically working across multiple disconnected internal and third-party systems.

https://careersatdoordash.com/blog/doordash-case-management-platform/

---

## 4. DoorDash Real-Time Fraud Rules Engine

**Publisher:** DoorDash Engineering  
**Used for:** Rule-governance complexity, false-positive risk, explainability, auditability, testing and controlled rollout.

https://careersatdoordash.com/blog/doordash-fraud-insights-from-building-a-real-time-rules-engine/

---

## 5. DoorDash Logistics — Causal ML & Joint Optimization

**Publisher:** DoorDash Engineering  
**Used for:** Marketplace optimization tradeoffs.

DoorDash discusses how batching can reduce duplicate travel and cost while potentially increasing consumer delivery duration.

https://careersatdoordash.com/blog/supercharging-doordash-logistics-through-causal-ml-and-joint-optimization/

---

## 6. DoorDash Integrated Promotions

**Publisher:** DoorDash Developer Services  
**Used for:** Promotion funding and reconciliation complexity.

https://developer.doordash.com/docs/marketplace/how_to/integrated_promotions/

---

## 7. DoorDash Merchant Pricing

**Publisher:** DoorDash for Merchants  
**Used for:** Merchant commission structure.

https://merchants.doordash.com/en-us/pricing

---

## 8. DoorDash Menu Pricing Insights

**Publisher:** DoorDash for Merchants  
**Used for:** Menu-pricing and marketplace-demand context.

DoorDash reports internal research on the relationship between marked-up menu prices, sales, and reorder behavior.

https://merchants.doordash.com/en-us/learning-center/menu-pricing-insights

---

## 9. DoorDash July 9, 2025 Service Incident

**Publisher:** DoorDash Engineering  
**Used for:** Cross-service dependency and cascading-failure context.

https://careersatdoordash.com/blog/july-9-2025-incident-and-steps-forward/

---

# 📁 Repository Structure

```text
DoorDash-Marketplace-Integrity-Root-Cause-Analysis-Control-Strategy/
│
├── README.md
├── DoorDash_Marketplace_Integrity_RCA.pbix
│
└── screenshots/
    ├── 01-executive-overview.png
    ├── 02-root-cause-explorer.png
    ├── 03-customer-merchant.png
    ├── 04-dasher-pay.png
    ├── 05-strategy-roadmap.png
    ├── 06-evidence-method.png
    └── 07-rca-detail.png
```

If the Power BI Project source is included instead of a `.pbix`, keep the:

- `.pbip`
- `.Report`
- `.SemanticModel`

items together.

---

# ⚠️ Limitations

This project uses **public information only**.

It does not use:

- DoorDash internal transaction data
- private production logs
- confidential architecture
- internal experiments
- internal defect rates
- confidential financial information

Public evidence can confirm that a problem occurred without necessarily establishing its exact technical cause.

Where causality is not directly established, the dashboard labels the explanation as a **hypothesis requiring internal validation**.

---

# Disclaimer

This is an **independent analytical case study based on publicly available information**.

It is not affiliated with, sponsored by, endorsed by, or produced for DoorDash, Inc.

No confidential DoorDash information was used.

---

# 👩‍💻 Author

**Dhrumi Kansara**  
Business Analyst | Data & Product Analytics

**Business Analysis · Product Analytics · Root Cause Analysis · Strategy & Operations · Power BI · DAX**
