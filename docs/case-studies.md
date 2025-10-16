# Cross-Industry Case Studies

These case studies provide concrete examples that we will analyze throughout the masterclass. They are designed for a mixed audience, from executives to engineers, with a primary focus on Oil & Gas but with direct parallels to Telecommunications and Renewable Energy in Nigeria.

**Learning Objective (Analyze):** Deconstruct each use case into its constituent data products, contracts, SLOs, and governance controls to understand its impact on KPIs and the underlying platform.

---

### Case Study 1: Oil & Gas Upstream Predictive Maintenance

- **Problem**: Unplanned downtime from equipment failure and financial penalties from gas flaring.
- **Data Products**:
    - **Sensor Telemetry Product**: Real-time data from wellheads and facilities.
    - **Maintenance Work Order Product**: Historical and current maintenance logs.
    - **Emissions Reporting Product**: Flaring volume and environmental data.
- **Key Controls**: Attribute-Based Access Control (ABAC) on specific wells; strict PII segregation in personnel logs; end-to-end data lineage for auditing emissions reports.
- **Target KPIs**: Increase equipment uptime by **+2-4%**, reduce OPEX by **-5-8%**, and reduce flaring volumes by **-10-20%**.
- **Architecture**: A streaming ingestion path feeding a medallion lakehouse architecture, with a feature store for ML models and a RAG implementation for accessing standard operating procedures (SOPs).

---

### Case Study 2: Telecommunications Churn Prediction

- **Problem**: High customer churn rates in competitive prepaid mobile segments.
- **Data Products**:
    - **User Intent Signals Product**: Real-time usage patterns.
    - **Offer Catalog Product**: Available retention offers.
    - **Customer 360 Product**: A holistic customer view with embedded privacy controls.
- **Key Controls**: Policy-to-control mapping for marketing consent; API throttling to manage system load; detailed audit trails for all offers made.
- **Target KPIs**: Reduce monthly churn by **-2-5 percentage points**; increase Average Revenue Per User (ARPU) by **+3-6%** through targeted upsells.
- **Architecture**: Streaming feature engineering for low-latency scoring and an explainability layer to guide call center agents.

---

### Case Study 3: Nigerian Renewable Energy Asset Performance

- **Problem**: Failures and service delays for distributed solar inverters as adoption grows.
- **Data Products**:
    - **Asset Telemetry Product**: Performance data from solar assets.
    - **Service Ticketing Product**: Customer issue and event logs.
    - **Parts Inventory Product**: Availability of replacement parts.
- **Key Controls**: Customer consent management for data usage; localized language support for field operations using the N-ATLAS model.
- **Target KPIs**: Reduce Mean Time To Repair (MTTR) by **-20-35%**; increase total energy yield by **+3-7%**.
- **Architecture**: Edge buffering for intermittent connectivity, a centralized lakehouse for analytics, and a multilingual RAG system for field technician manuals.