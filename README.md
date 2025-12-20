# Asset Taxonomy Classifier (Human-in-the-Loop)

AI-assisted asset taxonomy classification system with SME-in-the-loop validation, built using Python, scikit-learn, Streamlit, and Azure-ready deployment patterns.

This project automates a traditionally manual enterprise workflow: users submit a **Part Number** and **Part Description**, the system **pre-classifies** the item into a taxonomy (starting with **TOOLNAME**), and subject matter experts (SMEs) **confirm or correct** the prediction. Confirmed labels can be fed back into training data to continuously improve accuracy.

---

## Why this exists

In large enterprise asset management workflows, taxonomy mapping is often:
- manual and time-consuming
- inconsistent across regions/sites
- dependent on limited SME bandwidth

This project reduces SME workload by providing **high-confidence suggestions** while keeping humans in control of the final label.

---

## MVP Scope (Phase 1)

✅ **Option A (current focus): Predict TOOLNAME first**

**Inputs**
- Part Number
- Part Description

**Target**
- TOOLNAME

Future phases expand to multi-level taxonomy prediction:
- Product Family
- Technology
- Brand
- Tool

---

## Architecture

### High-level flow
1. End user submits Part Number + Part Description
2. Model predicts TOOLNAME (with confidence + top suggestions)
3. SME confirms or corrects prediction
4. Final record stored for downstream workflow
5. (Optional) feedback used for periodic retraining

### Diagram (Mermaid)
```mermaid
flowchart TD
  U[End User] -->|Submits Part Number + Description| UI[Streamlit UI]
  UI --> API[Python Backend / Inference Logic]
  API --> M[ML Model: TF-IDF + Classifier]
  M --> P[Prediction: TOOLNAME + Confidence]
  P --> SME[SME Review UI]
  SME -->|Confirm / Correct| DB[(SQLite / Postgres)]
  DB -->|Optional feedback loop| T[Retraining Pipeline]
  T --> M
