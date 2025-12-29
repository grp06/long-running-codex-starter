---
name: project-breakdown
description: Extract and summarize the core functionality that needs to be built from a PRD.
license: MIT
compatibility: "OpenCode / Agent Skills. Works with any PRD format."
metadata:
  short-description: Summarize functionality to build
  category: planning
  artifact: functionality-summary
  output: repo-files
  audience: engineering
---

# Project Breakdown

## Purpose
Read a PRD and break it down into logical phases, extracting the functionality that needs to be built for each phase. Each phase summary will be used by agents to create detailed execution plans.

## Inputs
- PRD path (default `prd/PRD.md`)

## Outputs
- `.agent/phases/` directory with phase-specific functionality files
- `.agent/phases/phase-01.md`, `.agent/phases/phase-02.md`, etc. - functionality summary for each phase

## Rules
- Keep it simple and focused on functionality only
- No implementation details or technical decisions
- No timelines or effort estimates
- Just list the features/capabilities that need to exist for each phase

## Workflow
1. Read the PRD
2. Break down into logical phases based on dependencies and complexity
3. Extract user-facing features and functionality for each phase
4. Summarize each phase's functionality in simple, clear language
5. Write to `.agent/phases/phase-01.md`, `.agent/phases/phase-02.md`, etc.
