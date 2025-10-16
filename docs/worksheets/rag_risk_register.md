# RAG Risk Register

Identify risks, mitigations, owners, and evaluation metrics for Retrieval‑Augmented Generation systems.

## 1. Context
- Product / Application:
- Owner:
- Model / Retriever:

## 2. Risks
| ID | Risk | Impact (H/M/L) | Likelihood (H/M/L) | Mitigation | Owner |
|----|------|-----------------|--------------------|------------|-------|
| R1 | Hallucinated statement |  High | Medium | Output grounding check with citations; thresholded refusal | Platform Team |
| R2 | Outdated document used |  Medium | Medium | Freshness filters; recency scoring; doc deprecation | DPO |
| R3 | Sensitive info leakage |  High | Low | PII detection/redaction; policy checks; ABAC | Platform Team |
| R4 | Toxic or unsafe output |  High | Low | Safety classifier; allowlist/denylist; HITL | Platform Team |

(Add rows as needed)

## 3. Evaluation rubric
- Correctness: % grounded answers
- Relevance: % answers citing top‑k relevant docs
- Safety: % outputs passing toxicity/leak tests
- Completeness: % answers covering all requested aspects

## 4. Incident response
- Alerting thresholds:
- Rollback plan:
- Communication plan:

