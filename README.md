# DoorDash Marketplace Integrity — Power BI Root Cause Analysis

A **native Power BI Project (PBIP/PBIR + TMDL)** built from public DoorDash evidence available through **September 22, 2026**.

## Goal
This is not a “DoorDash complaint dashboard.” The project asks a strategy/operations question:

> **Which recurring failure mechanisms appear across documented DoorDash issues, what internal data would prove or disprove each root-cause hypothesis, and which preventive controls should be tested first?**

## Report pages
1. Executive Overview — real DoorDash scale + public-evidence RCA register.
2. Root Cause Explorer — slicers + native Power BI Decomposition Tree.
3. Customer & Merchant — pricing, merchant economics, promotion/error-control evidence and complaint signals with caveats.
4. Dasher Pay & Compliance — September 22, 2026 NYC settlement deep dive.
5. Strategy & Roadmap — proposed controls mapped to phases and KPIs.
6. Evidence & Method — auditable source registry with Web URL field.
7. RCA Detail — drill-through page for one mechanism.

## Power BI methods used
- Import-mode embedded data in TMDL (no external credentials required).
- Dedicated DAX measure table.
- Dropdown slicers and native cross-filtering.
- Decomposition Tree for exploratory RCA.
- Drill-through on `Evidence[Mechanism]`.
- Page Navigator for report navigation.
- Explicit source-tier and claim-status fields to separate facts from hypotheses.

## Data integrity
All observed numbers in the dashboard are public-source values. Strategy/control rows are clearly analytical recommendations. Complaint-channel counts are not used as failure-rate denominators.

