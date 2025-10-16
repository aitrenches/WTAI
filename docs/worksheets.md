# Worksheets and Templates

Use directly in workshops; keep vendor-agnostic. Export to Teams or your preferred tool.

Templates
- KPI tree template (use-case -> KPI -> measure -> baseline -> target)
- Value hypothesis canvas (assumptions, risks, leading indicators)
- Data product canvas (purpose, owner, consumers, SLOs, versioning)
- Data contract template (schema, semantics, freshness, quality thresholds, PII)
- RAG risk register (risks, mitigations, evaluation metrics, fallback)
- ROI calculator (benefits, costs, risk-adjusted value)
- Lineage/observability checklist (SLIs, alerts, incident runbook)

Data product lifecycle
```mermaid
flowchart TB
  Ideate --> Define --> Build --> Validate --> Operate --> Improve
  Define -->|Contract| Build
  Operate -->|SLO reports| Improve
```

Governance workflow
```mermaid
flowchart LR
  Policy --> Controls --> Implementation --> Evidence --> Audit
  Implementation --> Monitoring
  Monitoring --> Evidence
```

Downloadable stubs (to be added)
- data_product_canvas.md
- data_contract_template.md
- rag_risk_register.md
- roi_calculator.xlsx
- lineage_checklist.md
