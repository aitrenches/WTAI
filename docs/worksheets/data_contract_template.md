# Data Contract — RFQ Master Product (Procurement/EPICFORGE)

## How to use
1) Keep this as the human‑readable summary; point your machine‑readable spec here.
2) Fill SLOs/SLIs precisely; link to dashboards and lineage.
3) Store in version control; changes go through approval gate.

## Product & ownership
- Product name & version: rfq_master v1.0
- Domain / Business unit: Procurement (Sourcing)
- Data Product Owner (DPO): Head of Strategic Sourcing
- Contact: sourcing-office@example.com

## Purpose & consumers
- Approved purposes: Sourcing, Reporting, Spend Analytics (no ad‑hoc export of PII)
- Consumer applications/teams: Bid Normalizer, Spend Analytics, Finance Reporting, Audit

## Schema & semantics
- Tables/fields (excerpt)
  - rfq_header: id(string, pk), category(string), region(string NG|…), open_date(timestamp), due_date(timestamp), owner(string tokenized)
  - rfq_line: rfq_id(string fk), item_code(string), qty(decimal >=0), uom(string), target_price(currency)
  - attachments: rfq_id(string fk), url(string), type(enum: sow|tcs)
- Semantics
  - due_date: vendor submission cutoff (WAT); late submissions rejected
  - uom: per corporate catalog; item_code must exist in catalog

## Quality & reliability
- Freshness SLO: bid window updates reflected within < 60 seconds
- Completeness SLO: ≥ 99% of required fields present (header + lines)
- Accuracy SLO: ≥ 99.5% pass business rules (currency/tax/qty constraints)
- SLIs & instrumentation: freshness_latency_s; required_field_completeness_pct; rule_pass_rate

## Security & compliance
- PII fields: vendor_contact_name/email (tokenized at Silver); access to detokenization restricted and audited
- Access policy (ABAC): role ∈ {ProcurementManager, Auditor}; region ∈ {NG, …}; purpose ∈ {Sourcing, Reporting}
- Retention policy: Bronze 18 months; Silver 24 months; Gold 36 months
- DPIA link: not required for v1.0; re‑evaluate for v1.1 if additional identifiers added

## Versioning & lifecycle
- Versioning scheme: semantic (vMAJOR.MINOR)
- Deprecation policy: v1 supported 12 months after v2 release; change log published
- Change approval: DPO approval + platform control check (CI policy gate)

## Evidence & monitoring
- Lineage link: lineage/proc/rfq_master
- Quality dashboard: dashboards/proc/rfq_master_quality
- Audit/reporting: audit/proc/access_logs (purpose enforcement)

