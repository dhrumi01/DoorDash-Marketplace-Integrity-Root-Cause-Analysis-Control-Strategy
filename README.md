# DoorDash Marketplace Integrity — Power BI Root Cause Analysis

An independent **Power BI case study** using public DoorDash evidence to examine recurring marketplace-control risks across **Customers, Merchants, and Dashers**.

> **Business question:** Where can expected marketplace outcomes diverge from actual operational or financial outcomes, what recurring mechanisms appear in public evidence, and which controls should be investigated first?

**Research coverage:** Public information available through September 22, 2026.

---

## Project Overview

DoorDash operates a three-sided marketplace in which a single order can move through:

**Catalog → Promotions → Pricing → Checkout → Payment → Merchant Fulfillment → Dispatch → Delivery → Support → Settlement**

The purpose of this project is not to build a complaint dashboard. It is to investigate whether different public DoorDash issues point to recurring **control and system-handoff patterns**.

The analysis follows:

**Problem → Current State → Evidence → Root-Cause Hypothesis → Internal Validation → Strategy → Future State → KPI**

---

## Why This Matters

DoorDash reported **970 million Total Orders, $33.1B Marketplace GOV, and $4.5B revenue in Q2 2026**.

At that scale, even relatively uncommon exception states can become operationally meaningful.

The project uses real public examples including:

- the **$131.5M New York City delivery-worker pay settlement announced September 22, 2026**
- DoorDash engineering documentation on fragmented support systems
- DoorDash engineering documentation on fraud-rule false-positive risk
- promotion reconciliation requirements across merchant/POS integrations
- logistics tradeoffs between batching efficiency and delivery duration
- current merchant commission and menu-pricing research

See [`sources.md`](sources.md)for the full source registry.

---

## Research Method

I used a source hierarchy instead of treating every public complaint as proof.

### Evidence tiers

- **Tier A — Primary external evidence:** regulators, filings, regulator-backed settlements, or high-quality reporting on those events
- **Tier B — DoorDash first-party evidence:** engineering, developer, merchant, product, or support documentation
- **Tier C — Complaint/community signals:** used only to identify possible edge cases, never as DoorDash-wide failure rates

### Claim labels

- **Confirmed incident** — the event/outcome is directly documented
- **Confirmed mechanism** — DoorDash or another primary source explicitly describes the mechanism
- **Supported hypothesis** — consistent with evidence, but causality requires internal DoorDash data
- **Confirmed context** — factual business/economic context, not necessarily a defect
- **Signal only** — useful for hypothesis discovery, not prevalence or causality

---

## Main RCA Themes

### 1. Fragmented state / source of truth
DoorDash has documented support workflows that historically relied on disconnected internal and third-party tools, creating context switching, manual workarounds, and inconsistent experiences.

### 2. Rule-governance complexity
DoorDash has documented how fraud rules embedded in application code became too slow to change and how overly conservative rules could block legitimate activity.

### 3. Cross-system reconciliation
DoorDash developer documentation describes the complexity of reconciling merchant-funded, DoorDash-funded, co-funded, and stacked promotions across order and POS systems.

### 4. Independent optimization / objective tradeoffs
DoorDash engineering has documented that higher batching can reduce duplicate travel and Dasher cost while increasing consumer delivery duration.

### 5. Exception handling under uncertainty
Public evidence suggests some high-volume decisions require stronger explainability, evidence, and escalation paths when confidence is low.

### 6. Transaction and settlement integrity
The 2026 NYC Dasher-pay settlement is used as a real-world case to examine how complex event states, jurisdiction rules, compensation logic, and final payout can require stronger reconciliation controls.

---

## Power BI Report

### 01 — Executive Overview
Marketplace scale, public evidence, RCA register, and the main decision question.

### 02 — Root Cause Explorer
Interactive exploration using:

**Stakeholder → Domain → Problem → Mechanism → Control Type → Claim Status**

Includes slicers, cross-filtering, and a Power BI Decomposition Tree.

### 03 — Customer & Merchant
Explores pricing transparency, merchant economics, promotion reconciliation, and responsibility attribution.

### 04 — Dasher Pay & Compliance
Deep dive into the September 2026 NYC settlement and the control questions around:

**Event State → Jurisdiction → Pay Rule → Expected Pay → Actual Pay → Payout**

### 05 — Strategy & Roadmap
Transforms RCA findings into proposed controls, implementation phases, and measurable KPIs.

### 06 — Evidence & Method
Source provenance, evidence tier, claim status, and research limitations.

### 07 — RCA Detail
Drill-through page for reviewing one mechanism from evidence through recommended control and success KPI.

---

## Proposed Control Strategy

The analysis leads to five control ideas:

1. **Canonical transaction ledger** — maintain one traceable record of important transaction and financial states.
2. **Versioned rule governance** — record which rule, version, jurisdiction, and eligibility conditions were applied.
3. **Expected-vs-actual reconciliation** — compare expected outcomes with downstream actual outcomes before financial closure.
4. **Explainable exception routing** — route low-confidence decisions to structured human review with evidence.
5. **Closed-loop settlement** — keep unresolved financial mismatches open until the downstream outcome is confirmed.

These are **analytical recommendations**, not claims about DoorDash's current internal architecture.

---

## Power BI Methods Used

- Power BI Project / Power BI Desktop
- TMDL semantic model
- DAX measures
- Decomposition Tree
- dropdown slicers
- cross-filtering
- drill-through
- KPI cards
- line, column, and bar charts
- analytical tables
- page navigation
- evidence-status filtering

---

## Example DAX

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

## What I Would Validate With Internal Data

If this were an internal DoorDash engagement, I would test:

- displayed price vs. authorized amount vs. settled amount
- promotion eligibility vs. promotion applied
- merchant-funded vs. DoorDash-funded promotion reconciliation
- expected Dasher compensation vs. actual compensation
- rule version and jurisdiction used for each pay decision
- support decision vs. appeal/review outcome
- merchant responsibility decision vs. dispute overturn
- batching vs. delivery duration, merchant wait, and cancellation

This would turn the public-evidence RCA into a measurable internal control-monitoring system.

---

## Repository Contents

If you are publishing the **PBIP project source**, keep:

```text
DoorDash-Marketplace-Integrity-Root-Cause-Analysis-Control-Strategy/
│
├── README.md
├── SOURCES.md
├── DoorDash_Marketplace_Integrity_RCA.pbip
├── DoorDash_Marketplace_Integrity_RCA.Report/
├── DoorDash_Marketplace_Integrity_RCA.SemanticModel/
└── screenshots/
    ├── 01-executive-overview.png
    ├── 02-root-cause-explorer.png
    ├── 03-dasher-pay.png
    └── 04-strategy-roadmap.png
```

If you are publishing only a **PBIX file**, keep:

```text
DoorDash-Marketplace-Integrity-Root-Cause-Analysis-Control-Strategy/
│
├── README.md
├── SOURCES.md
├── DoorDash_Marketplace_Integrity_RCA.pbix
└── screenshots/
    ├── 01-executive-overview.png
    ├── 02-root-cause-explorer.png
    ├── 03-dasher-pay.png
    └── 04-strategy-roadmap.png
```

Do **not** add empty `data/`, `docs/`, or `demo/` folders just to make the repository look larger.

---

## Important Limitations

This project uses public information only.

It does not use DoorDash internal transaction data, production logs, private experiment results, internal defect rates, or confidential information.

A public incident can confirm that a problem occurred, but it does not automatically establish the exact technical root cause. Where causality is not directly established, the project labels the mechanism as a **hypothesis requiring internal validation**.

---

## Disclaimer

This is an **independent analytical case study** based on publicly available information. It is not affiliated with, sponsored by, endorsed by, or produced for DoorDash, Inc.

No confidential DoorDash information was used.

---

## Author

**Dhrumi Kansara**  
Business Analyst | Data & Product Analytics

*Business Analysis · Root Cause Analysis · Product Analytics · Strategy & Operations · Power BI · DAX*
