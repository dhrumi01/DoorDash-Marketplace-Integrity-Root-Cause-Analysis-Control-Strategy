# DoorDash Marketplace Integrity — Power BI Root Cause Analysis

An independent Power BI case study examining how marketplace transactions can break across Customers, Merchants, and Dashers — and how stronger controls could reduce financial, operational, and trust-related failures.

## Project Goal

The goal of this project is to answer:

> Where do marketplace transactions become inconsistent across pricing, promotions, fulfillment, support, and settlement — what are the likely root causes, and what controls could prevent those failures?

Rather than building a dashboard only around complaints, I used public evidence to connect:

**Problem → Current State → Evidence → Root Cause → Strategy → Future State → KPI**

---

## Business Problem

DoorDash operates a three-sided marketplace connecting:

- Customers
- Merchants
- Dashers

A single order can pass through multiple systems:

**Catalog → Promotion → Pricing → Checkout → Payment → Merchant → Dispatch → Delivery → Support → Settlement**

The analytical challenge is maintaining the same business truth across those handoffs.

Examples include:

- a promotion displayed but not reconciled correctly
- a merchant dispute where responsibility is unclear
- a fraud rule incorrectly affecting a legitimate user
- a Dasher payment calculated incorrectly under a complex delivery state
- optimization decisions improving efficiency while negatively affecting delivery experience

---

## Research Approach

This project uses public information only.

I prioritized evidence in the following order:

1. Regulatory and legal records
2. DoorDash SEC filings
3. DoorDash engineering documentation
4. DoorDash developer and merchant documentation
5. Structured complaint data
6. Public user reports for hypothesis discovery only

Public complaints were not treated as proof of a system defect.

Where the public evidence confirms an issue but does not prove the technical cause, the dashboard labels the root cause as a **hypothesis requiring internal validation**.

---

## Key Root Cause Themes

The research identified several recurring mechanisms:

### 1. Fragmented State / Source of Truth
Different systems may hold different versions of order, payment, support, or settlement state.

### 2. Rule Complexity
Pricing, promotions, fraud, Dasher compensation, and regulatory rules can vary based on eligibility, geography, time, and transaction state.

### 3. Cross-System Reconciliation
Financial values must remain consistent across customer checkout, merchant accounting, DoorDash funding, and final settlement.

### 4. Exception Handling
Automation works well for high-volume standard cases, but ambiguous cases require evidence, explainability, and human override paths.

### 5. Marketplace Optimization Tradeoffs
Improving one objective — such as batching efficiency — can negatively affect another objective such as delivery duration.

---

## Power BI Dashboard

The report contains seven analytical pages.

### 01 — Executive Overview
Executive view of marketplace scale, public evidence, recurring control mechanisms, and the main decision question.

### 02 — Root Cause Explorer
Interactive RCA using a Power BI Decomposition Tree.

**Stakeholder → Domain → Problem → Root Cause → Control Type → Evidence Status**

### 03 — Customer & Merchant
Analysis of:

- pricing and fee transparency
- promotion reconciliation
- merchant commissions
- menu pricing economics
- merchant error responsibility

### 04 — Dasher Pay & Compliance
Deep dive into the 2026 NYC Dasher pay settlement and the controls required to reconcile:

**Trip Events → Jurisdiction → Pay Rule → Expected Pay → Actual Pay → Payout**

### 05 — Strategy & Roadmap
Transforms RCA findings into a future-state control strategy.

### 06 — Evidence & Method
Source registry, evidence classification, and research limitations.

### 07 — RCA Detail
Drill-through page for investigating an individual root-cause mechanism.

---

## Recommended Strategy

The proposed Marketplace Integrity framework contains five controls:

**1. Canonical Transaction Ledger**  
Create one traceable record of important transaction and financial states.

**2. Versioned Rule Governance**  
Record the exact business rule, version, jurisdiction, and eligibility conditions applied to each decision.

**3. Expected-vs-Actual Reconciliation**  
Compare what should have happened with what actually happened before financial settlement.

**4. Explainable Exception Routing**  
Route low-confidence automated decisions to structured human review with supporting evidence.

**5. Closed-Loop Settlement**  
Do not consider a transaction financially complete until downstream settlement is confirmed or an exception remains open.

---

## Future-State Concept

Expected Outcome  
↓  
Actual Outcome  
↓  
Reconciliation  
↓  
Match?  

**Yes → Close transaction**

**No → Investigate exception → Correct / Review → Confirm settlement**

The objective is to detect transaction inconsistencies **before they become customer complaints, merchant disputes, Dasher payment issues, or regulatory problems.**

---

## Power BI Features Used

- Power BI Project (`.pbip`)
- TMDL semantic model
- DAX measures
- Decomposition Tree
- Dropdown slicers
- Cross-filtering
- Drill-through
- KPI cards
- Line and bar charts
- Analytical tables
- Page navigation
- Evidence-level filtering

---

## Example DAX

```DAX
Evidence Records =
COUNTROWS(Evidence)

Q2 Orders M =
DIVIDE(
    CALCULATE(
        MAX(PublicKPI[Value]),
        PublicKPI[MetricID] = "ORDERS_Q2_2026"
    ),
    1000000
)


Author

Dhrumi Kansara
Business Analyst / Analytics

