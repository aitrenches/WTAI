# Data Product Canvas — Procurement (EPICFORGE)

Use this canvas to define a data product aligned to KPIs and governance.

## How to use
1) Duplicate this file for your product; keep headings.
2) Fill every field; link to your KPI tree, contract, lineage and dashboards.
3) Validate SLOs with the Platform Team; finalize with the DPO.

## 1. Product summary
- Name: RFQ Master Product
- Version: v1.0
- Domain / Business unit: Procurement (Sourcing)
- Data Product Owner (DPO): Head of Strategic Sourcing
- Primary consumers: Category Managers, Finance (Spend Analytics), Legal (Contracting)

## 2. Value & KPI
- Problem statement: Manual, inconsistent RFQ creation and bid analysis slows cycle time and reduces vendor participation; missing analytics limits savings.
- KPI tree link (goal → driver → metric): Reduce Sourcing Cycle Time → Standardize RFQs → Time to Award; Increase Vendor Participation → Simplify Submissions → Response Rate; Improve Savings → Better Comparability → Negotiated Savings %
- 90‑day pilot goal (measurable): Cut RFQ cycle time by 30% and increase vendor response rate by 40% in one category (MRO spares).

## 3. Interfaces & contract
- Contract URL/path: contracts/proc/rfq_master_v1.0.yaml
- Purpose(s) allowed (e.g., Forecasting, BI Reporting): Sourcing, Reporting, Spend Analytics
- Schema overview (tables/fields): rfq_header(id, category, region, open_date, due_date), rfq_line(item_code, qty, uom), attachments(url, type)
- Semantics notes (business meaning for critical fields): due_date = vendor submission cutoff, uom per corporate catalog; attachments include SoW and T&Cs

## 4. Quality & reliability
- Freshness SLO: Bid window updates reflected within < 1 minute
- Completeness SLO: ≥ 99% of required fields present on RFQ and line items
- Accuracy/constraint SLO: Currency/Tax rules pass validation ≥ 99.5%
- SLIs to instrument: freshness_latency_s, required_field_completeness_pct, pricing_rule_pass_rate

## 5. Security & compliance
- PII present? (Y/N). If Y, masking/tokenization plan at Silver: Y; vendor contact info tokenized at Silver
- Access model (ABAC attributes: role, region, purpose): role ∈ {ProcurementManager, Auditor}; region ∈ {NG, …}; purpose ∈ {Sourcing, Reporting}
- DPIA required? (Y/N). Link to DPIA: N (no sensitive identifiers beyond contacts); reassess if IDs added

## 6. Lineage & observability
- Upstream sources: Vendor Portal submissions, ERP vendor master
- Downstream consumers/models: Bid Normalizer, Spend Analytics, Savings Dashboard
- Lineage visibility (tool/link): lineage/proc/rfq_master
- Alerting & incident runbook: Alerts on SLO breach; runbook PROC‑SLO‑RFQ‑001

## 7. Delivery plan
- Platform tooling needed (CI/CD, lineage, policy engine, cost showback): CI/CD templates; lineage; ABAC engine; cost showback tag: product=rfq_master
- Milestones (design, build, validate, launch): Design wk1‑2; Build wk3‑6; Validate wk7‑8; Launch wk9‑10
- Risks & mitigations: Vendor low adoption → simplify portal; Data inconsistencies → templates and field validation; Compliance → tokenization

