# Cross-Industry Case Studies

These case studies will be referenced across Day 4 and Day 5 to connect strategy, architecture, governance, compliance, and platform execution. Each example maps value to KPI trees, defines data products and contracts, specifies SLO/SLI reliability targets, and identifies controls under the federated governance model.

**Learning Objective (Analyze):** Deconstruct each use case into data products, contracts, SLOs, controls, and platform components; quantify KPI impact and outline a 90‑day pilot.

---

### Case Study 1: Oil & Gas Upstream Predictive Maintenance

- **Problem**: Unplanned downtime from equipment failure and financial penalties from gas flaring.
- **Data Products**:
    - **Sensor Telemetry Product**: Real-time data from wellheads and facilities.
    - **Maintenance Work Order Product**: Historical and current maintenance logs.
    - **Emissions Reporting Product**: Flaring volume and environmental data.
- **Key Controls**: Attribute-Based Access Control (ABAC) on specific wells; strict PII segregation in personnel logs; end-to-end data lineage for auditing emissions reports.
- **Target KPIs**: Increase equipment uptime by **+2-4%**, reduce OPEX by **-5-8%**, and reduce flaring volumes by **-10-20%**.
- **Architecture**: Streaming ingestion → Medallion Lakehouse (Bronze/Silver/Gold) → Feature Store for PdM → RAG for SOP retrieval. Governance plane: lineage, ABAC, quality SLIs.
- **Data Contract Highlights**: schema/versioning; freshness SLO 99.9% <5m; completeness SLO ≥99.5% wells/day; accuracy SLO ≥98% valid pressure range.
- **Governance/Compliance**: masking at Silver for personnel references; ABAC by asset/region; DPIA if model decisions affect worker scheduling.
- **90‑Day Pilot Target**: one compressor asset; alert precision ≥90%; false alarms −50%; ROI quantified against avoided downtime.

---

### Case Study 2: Procurement (EPICFORGE)

- **Current Pain Points**:
  - Manual, time‑consuming RFQ creation, vendor communications, and bid analysis → weeks of cycle time and errors
  - Slow vendor response rates due to complex submissions and low transparency
  - Inconsistent data and formats across vendors; difficult comparisons; risk of omissions
  - Lack of analytics on spend patterns, vendor performance, and optimization opportunities
- **EPICFORGE Solution**:
  - AI‑powered automation: intelligent RFQ generation, automated vendor matching, smart bid analysis (manual effort −60%)
  - Seamless vendor experience: portal with template‑based submissions (response rate +40%)
  - Standardized workflows: template‑driven processes ensure consistency and comparable bids
  - Comprehensive analytics: real‑time spend, vendor performance, and savings opportunities
- **Data Products**:
  - **RFQ Master Product**: structured RFQ with schema and semantics
  - **Vendor Profile/Product**: capabilities, certifications, performance history
  - **Bid Submission Product**: normalized line‑items and terms
  - **Spend Analytics Product**: aggregated transactions and savings realized
- **Data Contract Highlights**: schema and mandatory semantics; freshness SLO (bid window updates <1m); completeness SLO ≥99% required fields; accuracy rules for currency/tax calculations.
- **Architecture**: Event‑driven ingestion from portal → Silver normalization → Gold analytics; optional RAG for policy/T&Cs lookup; lineage for auditability.
- **Governance/Compliance**: ABAC by role (ProcurementManager, Auditor) and purpose (Sourcing vs Reporting); PII tokenization for vendor contacts at Silver; DPIA if processing sensitive identifiers.
- **KPIs**: cycle time −30–60%; vendor participation +40%; negotiated savings uplift; maverick spend −10–20%.
- **90‑Day Pilot Target**: one category (e.g., MRO spares) with 10 vendors; implement portal templates, normalization pipeline, and analytics dashboard; demonstrate cycle‑time reduction and savings.

---

### Case Study 3: Nigerian Renewable Energy Asset Performance

- **Problem**: Failures and service delays for distributed solar inverters as adoption grows.
- **Data Products**:
    - **Asset Telemetry Product**: Performance data from solar assets.
    - **Service Ticketing Product**: Customer issue and event logs.
    - **Parts Inventory Product**: Availability of replacement parts.
- **Key Controls**: Customer consent management for data usage; localized language support for field operations using the N-ATLAS model.
- **Target KPIs**: Reduce Mean Time To Repair (MTTR) by **-20-35%**; increase total energy yield by **+3-7%**.
- **Architecture**: Edge buffering for intermittent connectivity → central lakehouse; anomaly detection; multilingual RAG for manuals.
- **Data Contract Highlights**: telemetry schema; freshness SLO <5m; completeness SLO ≥99%; accuracy rules per device class.
- **Governance/Compliance**: consent management; localized language support with N‑ATLAS; ABAC by region/installer.
- **90‑Day Pilot Target**: 1,000 inverters; MTTR −20–35%; yield +3–7%; publish DPO‑owned contract and SLOs.