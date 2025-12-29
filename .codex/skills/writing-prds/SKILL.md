---
name: writing-prds
description: Turn raw product notes or dictation into a concise PRD with clear requirements and acceptance criteria.
metadata:
  short-description: Draft a PRD from raw notes
  category: product
  artifact: prd
  output: repo-file
---

# PRD Writer

## Purpose
Create a concise PRD that translates raw product notes into stable requirements, acceptance criteria, and open questions.

## Inputs
- Source notes or dictation file path
- Optional existing PRD path to update

If any required input is missing or unclear, stop and ask for the exact path or details.

## Output
- `prd/PRD.md` by default, or the user-specified PRD path

## Rules
- No implementation or tests.
- Fail fast on missing inputs; return actionable errors.
- Keep scope explicit: goals, non-goals, constraints.
- Use stable requirement IDs:
  - FR-### for functional requirements
  - NFR-### for non-functional requirements
- Each requirement must have acceptance criteria.

## Workflow
1. Locate the source notes and any existing PRD.
2. Extract problem, users, goals, non-goals, constraints, risks, and success metrics.
3. Convert needs into FR/NFR with acceptance criteria.
4. Capture assumptions and open questions.
5. Validate coverage: every goal maps to FR/NFR; every FR/NFR has acceptance criteria; contradictions are flagged.

## PRD Structure
- Summary
- Users and use cases
- Goals and non-goals
- Requirements
  - Functional requirements (FR-### + acceptance criteria)
  - Non-functional requirements (NFR-### + acceptance criteria)
- Constraints and dependencies
- Risks and open questions
- Success metrics
