# Quality, Observability, and Reliability

## Introduction: the cost of untrustworthy data
Reliability is the new security. If data is wrong or late, AI and decisions fail. Establish SLOs/SLIs and observability so the promises in Data Contracts are measurable and enforceable. Artifact: Lineage + Observability Checklist.

## Part 1: defining reliability with SLOs and SLIs
- SLI: raw metric (e.g., freshness latency Bronze→Gold)
- SLO: target for the SLI over time (e.g., 99.5% within 60 minutes over 30 days)
- SLA: consequence/error budget

```mermaid
flowchart TD
  A[Business Requirement: Reduce Unplanned Downtime] --> B[Data Product Owner]
  B --> C[Data Contract]
  C -- Sets Target --> D[SLO: 99.5% Data Completeness]
  D -- Requires Measurement --> E[SLI: % NULLs in Key Column]
  E --> F[Platform Monitoring System]
  F -- Failure Alert --> B
```

SLOs convert business need into measurable commitments; the platform measures SLIs and alerts on breach.

SLO management loop
```mermaid
flowchart LR
  Define[Define SLOs] --> Instrument[Instrument SLIs]
  Instrument --> Monitor[Monitor Dashboards]
  Monitor --> Alert[Alert on Breach]
  Alert --> Triage[Root Cause via Logs/Lineage]
  Triage --> Fix[Fix Pipeline/Config]
  Fix --> Review[Review Error Budget]
  Review --> Define
```

## Part 2: the core three SLIs
- Freshness (timeliness): delta between event_timestamp and processing_timestamp; example target 99.9% < 5 minutes for PdM.
- Completeness (presence/volume): records received vs expected; % non‑NULL in key fields; example ≥99.5% wells daily and ≥99% non‑NULL production_volume.
- Accuracy (semantic/constraint): % values within valid ranges (e.g., 500–1,500 PSI); target ≥98%.

## Part 3: full data observability and lineage
Observability explains why failures happen using Metrics, Logs, and Traces (lineage).

```mermaid
flowchart TD
  A[Data Product] --> B(Metrics)
  A --> C(Logs)
  A --> D(Traces/Lineage)

  B -- SLIs/SLOs --> E[Data Quality Dashboard]
  C -- Error Stack --> F[Debug Pipeline Failure]
  D -- End‑to‑End Flow --> G[Impact Analysis]

  style A fill:#FFD700,stroke:#333
  style E fill:#ccf,stroke:#333
  style G fill:#ffc,stroke:#333
```

- Metrics: what is wrong (freshness/completeness/accuracy trends)
- Logs: where in code it failed
- Traces/Lineage: who is impacted; supports governance questions (e.g., NDPA masking at Silver) and safe deprecations

## Activity: apply the checklist
1) Choose the most critical SLI for your pilot.
2) Set an SLO target.
3) Identify the lineage you must see when the SLO breaches (affected models/dashboards).

## Conclusion & transition
You’ve established measurable reliability and deep diagnosis. Next: the platform blueprint and reference implementation plan—who builds the tooling (lineage, serverless compute, CI/CD) and how to deliver it in phases.
