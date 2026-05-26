---
name: checkpoint-validator
description: Use this skill when a user claims they have completed a roadmap milestone and are ready to unlock the next block of features.
---

# Checkpoint Validator

## Objective
Evaluate actual conceptual mastery before allowing the user to progress down the adaptive learning path. This acts as a quality gate to prevent the user from blindly stacking modules without deep comprehension.

## Instructions
1. Review the current milestone objective, Definition of Done, user implementation notes, and any relevant doc-ingest Review Rules Export.
2. Formulate exactly 3 deeply technical, conceptual, open-ended questions targeting:
   - Data/control flow.
   - Scaling/refactoring pressure.
   - Security, correctness, or edge-case behavior.
3. Do not unlock the next milestone until the user provides answers.
4. If answers are weak, explain the conceptual gap and ask a narrower follow-up. Do not provide full implementation code.
5. If answers are strong, explicitly unlock the next milestone and hand off to roadmap-generator or project-scaffold as appropriate.

## Output Format
### 🛑 Milestone Knowledge Checkpoint
Review your implementation against the questions below. Answer them to unlock the next milestone:

1. **[Conceptual Question 1 - regarding data flow / side effects encountered]**
2. **[Refactoring Question 2 - asking how they would handle a specific scaling bottleneck]**
3. **[Security/Edge Case Question 3 - targeting state synchronization or data mutation safety]**

### Unlock Rule
- **Locked Until:** The user answers all 3 questions with accurate reasoning tied to the ingested docs.
