# Interactive Workshop: Pilot Plan to Production Path

## Introduction & challenge
Convert the 90‑day pilot design into two artifacts: an Executive One‑Pager (value, risk, readiness) and an IT Implementation Brief (architecture, tooling, controls). First half: business case. Second half: technical plan.

## Phase 1: executive one‑pager (the business case)
- Value proposition & ROI
  - Project title (business‑centric)
  - Targeted KPI and current state
  - Current cost/loss quantified
  - 90‑day goal and estimated ROI using the ROI calculator
  - Ownership: name the DPO and business unit
- Risk & organizational readiness
  - Value‑Risk matrix score (Quick Win / Strategic Bet)
  - Top 3 risks with paired mitigations (from Risk Log)
  - Day 91 scaling path (phase 2 scope and benefits)

## Phase 2: IT implementation brief (the technical plan)
- Architecture & data product definition
  - Product names and versions; Data Contract reference (schema, semantics)
  - Platform tooling requests (self‑service CI/CD, lineage, policy engine)
  - Primary pattern and layer focus (e.g., hybrid streaming/lakehouse; edge→Bronze/Silver)
- Governance & compliance controls
  - NDPA (PII) controls: tokenization/masking at Silver
  - Reliability SLOs/SLIs: freshness/completeness targets
  - Access/security: ABAC rules via platform policy engine

```mermaid
sequenceDiagram
  participant S as Source System (SCADA/IoT)
  participant T as Platform: Tokenization Service
  participant AC as Platform: Access Control
  participant DPE as Domain Product Engineer
  participant DPO as Data Product Owner
  participant A as AI/BI Consumer

  DPE->>T: Ingest Data (incl. PII)
  T-->>DPE: Masked Data (Silver)

  DPE->>AC: Publish Product + Contract + SLOs
  DPO->>AC: Configure ABAC (Region: Delta, Role: Planner)

  A->>AC: Request Gold Data for PdM
  alt Compliance Check
    AC-->>A: Deny (role/region mismatch)
  else Access Approved
    AC-->>A: Serve Gold Data (masked)
  end
```

Artifacts handoff
```mermaid
flowchart LR
  OnePager[Executive One‑Pager] --> Approve[Investment Approval]
  Brief[IT Implementation Brief] --> Provision[Platform Provisioning]
  Approve --> Provision
  Provision --> Build[Build & Configure]
  Build --> Launch[Pilot Launch]
```

## Conclusion
Two outputs ready for leadership and engineering: the executive one‑pager and the implementation brief. These secure funding and guide delivery from pilot to production.
