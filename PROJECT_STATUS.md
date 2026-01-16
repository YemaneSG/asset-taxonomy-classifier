# Asset Taxonomy Classifier – Project Status

## Objective
Reduce manual asset taxonomy classification by:
- checking existing enterprise mappings first
- routing only unmapped parts for AI + SME review

---

## Current Focus
**DB Check #2 – EPIC hierarchy lookup**

Reason:
This check determines whether a part already exists before classification,
preventing unnecessary ML and SME effort.

---

## Completed
- Project repo and environment setup
- Streamlit MVP scaffold
- Dataset identified and scoped
- Phase 1 target defined (TOOLNAME)

---

## In Progress
- EPIC hierarchy API access validation
- PN + Description submission flow

---

## Blocked / Risks
- EPIC hierarchy API approval pending

Mitigation:
- Designing lookup logic and response handling
- Building UI flow independent of final API response

---

## Next Milestones
1. Validate DB#2 lookup end-to-end
2. Return “Mapped / Unmapped” result to user
3. Persist lookup outcomes
4. Enable downstream classification only for unmapped parts
