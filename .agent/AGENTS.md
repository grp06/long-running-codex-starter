# Agent Workflow

## Developer Flow

1. **Initial Input**: I write/dictate my thoughts and ideas into `.agent/scribbles/somefile.md`

2. **Kickoff**: I tell you to start the development process

3. **PRD Creation**: You generate a Product Requirements Document using `.codex/skills/writing-prds/SKILL.md`

4. **Project Breakdown**: You break the PRD into development phases using `.codex/skills/project-breakdown/SKILL.md`

5. **ExecPlan Creation**: For each phase, you create a detailed execution plan using `.agent/execplans/PLANS.md`

6. **Test-First Development**: Before implementing any execplan, write failing tests that will pass after implementation

7. **Implementation**: Execute each execplan carefully, ensuring tests pass

## Testing Requirements

- Use pytest for all tests
- Write tests BEFORE implementation (TDD approach)
- Tests must fail initially, then pass after implementation
- Tests should be comprehensive but focused on the functionality being built

## ExecPlans

Use ExecPlans for complex features or significant refactors. ExecPlans follow the process described in `.agent/PLANS.md` and provide a structured approach from design to implementation. Execplans you create should be placed in .agent/execplans/phase-1-execplan.md, .agent/execplans/phase-2-execplan.md, etc...


# IMPORTANT: You should fully understand the project before starting. After starting, you must follow through completely without stopping. 