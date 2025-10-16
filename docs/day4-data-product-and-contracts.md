# The Data Product Operating Model & Data Contracts

## Introduction: the scaling problem
Many data initiatives fail to scale not because of technology, but because of the operating model. Treating data as a byproduct managed by a central team doesn’t scale. Shift from project/service‑ticket mindset to product ownership. Key artifacts: Data Product Canvas and Data Contract Template.

## The old way: the centralized bottleneck
Central teams become backlogs; context is lost; ownership is unclear; quality suffers; pipelines are brittle.

```mermaid
graph TD
    subgraph Business_Domains[Business Domains]
        D1(Upstream Ops)
        D2(Refining)
        D3(Logistics)
    end
    subgraph Central_Data_Team[Central Data Team]
        P(Platform Engineers)
        E(Data Engineers)
        A(Analysts)
    end
    subgraph Data_Consumers[Data Consumers]
        C1(BI Reports)
        C2(AI Models)
        C3(Finance App)
    end

    D1 -- Ticket: Need well data --> E
    D2 -- Ticket: Refinery sensor data --> E
    D3 -- Ticket: Shipping data --> E

    E -- Backlog --> P
    E -- Data is ready --> A

    A --> C1
    A --> C2
    E --> C3

    style E fill:#ffcccc,stroke:#333
```

Problems
- Loss of context and domain nuance
- No clear ownership for correctness
- Low quality and reactive cleanup
- Fragile downstream dependencies

## A new paradigm: treating data as a product (DaaP{:abbr="Data‑as‑a‑Product"})
Decentralize ownership to domains; the central team becomes a platform enabling self‑service.

```mermaid
graph TD
    subgraph Domain_Upstream[Domain: Upstream Ops]
        Owner1(Product Owner)
        Team1(Engineers)
        DP1[Sensor Telemetry Product]
        Team1 --> DP1
        Owner1 --> DP1
    end
    subgraph Domain_Logistics[Domain: Logistics]
        Owner2(Product Owner)
        Team2(Engineers)
        DP2[Vessel Tracking Product]
        Team2 --> DP2
        Owner2 --> DP2
    end
    subgraph Consumers
        C1(Predictive Maintenance App)
        C2(Supply Chain Optimization Model)
    end

    DP1 -- Contract --> C1
    DP2 -- Contract --> C2
    DP1 -- Contract --> C2
```

Product includes data, code, infra, metadata, owner, version, and interface. Domains create; platform team provides tooling and guardrails.

## The API for data: data contracts
A data contract is a formal, machine‑readable agreement between producer and consumers. It defines expectations and becomes part of CI/CD.

Contract lifecycle
```mermaid
flowchart TB
  Draft[Draft Contract] --> Review[Domain Review]
  Review --> Approve[Governance Approval]
  Approve --> Enforce[CI/CD Enforcement]
  Enforce --> Observe[SLI/SLO Monitoring]
  Observe --> Version{Need Change?}
  Version -- Yes --> Deprecate[Deprecate v1, Publish v2]
  Version -- No --> Operate[Operate]
```

Contract components
- Schema: columns, types, constraints; versioning for changes
- Semantics: precise business meaning (e.g., prod_vol: daily crude volume, bbl at STP)
- Quality & reliability (SLOs/SLIs):
  - Freshness: updated daily by 06:00 AM WAT
  - Completeness: monthly data > 99.5% of active wells
  - Accuracy: percent of readings within valid ranges
- PII & security: fields with PII; masking/tokenization; access tiers
- Lifecycle & deprecation: support windows per version; deprecation policy

Enforcement: contract is code in the deployment pipeline; violating changes fail builds.

## Interactive: your first data product canvas
Choose a core dataset for your pilot (e.g., Sensor Telemetry Product or User Intent Signals). Fill the canvas: owner, consumers, purpose, 1–2 critical SLOs.

## Conclusion and transition
This operating model—decentralized ownership + data contracts + platform enablement—scales value without scaling chaos. Next: workforce and culture—roles, skills, and adoption mechanics to make the model stick.
