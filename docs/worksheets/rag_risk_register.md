# RAG Risk Register — Procurement (EPICFORGE)

## How to use
1) Copy this register per application; align risks with your policy corpus and retriever.
2) Keep mitigations actionable; assign clear owners.
3) Review metrics weekly; trigger incident steps on threshold.

Identify risks, mitigations, owners, and evaluation metrics for Retrieval‑Augmented Generation in RFQ and policy assistance.

## 1. Context
- Product / Application: Vendor portal assistant & policy explainer
- Owner: Platform Team (RAG framework) + DPO (procurement)
- Model / Retriever: Local LLM + hybrid search (policy/T&Cs/SOW templates)

## 2. Risks
| ID | Risk | Impact (H/M/L) | Likelihood (H/M/L) | Mitigation | Owner |
|----|------|-----------------|--------------------|------------|-------|
| R1 | Hallucinated compliance advice in RFQ | High | Medium | Output grounding with citations; refuse if low confidence | Platform |
| R2 | Use of outdated policy/T&Cs | High | Medium | Freshness filter (≤ 6 months); deprecate old docs | DPO |
| R3 | Leakage of vendor PII in answers | High | Low | PII detection/redaction policy; ABAC enforced | Platform |
| R4 | Toxic/biased language to vendors | Medium | Low | Safety filter; inclusive language checker | Platform |

(Add rows as needed)

## 3. Evaluation rubric
- Correctness: % grounded answers citing current docs
- Relevance: % answers using the correct policy domain
- Safety: % outputs passing toxicity/PII checks
- Completeness: % answers covering all requested RFQ steps

## 4. Incident response
- Alerting thresholds: >1% unsafe or ungrounded outputs/day
- Rollback plan: disable generation; retrieval‑only fallback
- Communication plan: notify DPO and legal; vendor comms template

