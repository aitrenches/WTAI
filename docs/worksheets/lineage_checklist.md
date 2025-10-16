# Lineage & Observability Checklist

Use this to ensure end‑to‑end traceability and reliable operations.

## Scope
- Data product:
- Owner (DPO):
- Period covered:

## Lineage
- [ ] Upstream sources listed and linked
- [ ] Transformations documented (jobs/notebooks)
- [ ] Downstream consumers/models enumerated
- [ ] Impact analysis view available

## Observability
- Metrics (SLIs)
  - [ ] Freshness instrumented and visible
  - [ ] Completeness instrumented and visible
  - [ ] Accuracy/constraints monitored
- Logs
  - [ ] Error logs centralized and searchable
- Traces
  - [ ] Job execution traces connected to lineage graph

## Governance & compliance
- [ ] PII masking/tokenization verified at Silver
- [ ] Purpose limitation enforced (ABAC rules)
- [ ] Retention policy active (Bronze lifecycle)

## Incident response
- [ ] Alerts configured with runbooks
- [ ] Ownership/RACI documented
- [ ] Post‑incident review process defined

