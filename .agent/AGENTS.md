# Agent Workflow

**All agent-generated files must be saved in the project's `.agent/` folder.**

## Developer Flow

1. **Initial Input**: I write/dictate my thoughts and ideas into `.agent/scribbles/somefile.md`

2. **Kickoff**: I tell you to start the development process

3. **PRD Creation**: You generate a Product Requirements Document using `.codex/skills/writing-prds/SKILL.md` and save it as `.agent/prd/PRD.md`

4. **Project Breakdown**: You break the PRD into development phases using `.codex/skills/project-breakdown/SKILL.md`, creating `.agent/phases/phase-01.md`, etc.

5. **ExecPlan Creation**: For each phase, you create a detailed execution plan using `.agent/execplans/PLANS.md`, saving as `.agent/execplans/phase-1-execplan.md`, etc.

6. **Test-First Development**: Before implementing any execplan, write failing tests that will pass after implementation

7. **Implementation**: Execute each execplan carefully, ensuring tests pass. Make commits at reasonable checkpoints when functionality is working and tested.

## Memory System

You will state across long-running development cycles using two memory mechanisms:

### Current State (`.agent/CURRENT.md`)
**Keep this file constantly updated** - it serves as the agent's working memory:

- **Active phase + execplan path**: Current phase number and execplan file being worked on
- **Last known failing tests summary**: Current test failures and their status
- **Next 1-3 concrete actions**: Specific, actionable next steps
- **Temporary constraints**: Any "do not refactor X until Y passes" type rules

**Update CURRENT.md before/after every major action.**

### Development Journal (`.agent/journal/YYYY-MM-DD-HH-MM-SS.md`)
**Individual timestamped entries** - the agent's persistent memory:

- **What changed, why**: Record all modifications and reasoning
- **What was observed**: Test output snippets, error messages, unexpected behavior
- **Links to commits**: Reference any git commits made

**Create a new timestamped journal file after every significant event. Make commits at reasonable checkpoints and always link them in journal entries.**

## Testing Requirements

- Use pytest for all tests
- Write tests BEFORE implementation (TDD approach)
- Tests must fail initially, then pass after implementation
- Tests should be comprehensive but focused on the functionality being built

## Commit Strategy

- **Make commits at reasonable checkpoints** when functionality is working and tested
- **Atomic commits**: Each commit should represent a single, complete piece of functionality
- **Meaningful commit messages**: Include what was implemented and why
- **Link commits in journal entries**: Always reference commit hashes in the development journal
- **Before major changes**: Commit current working state as a checkpoint
- **After completing functionality**: Commit when tests pass and feature works end-to-end

## ExecPlans

Use ExecPlans for complex features or significant refactors. ExecPlans follow the process described in `.agent/PLANS.md` and provide a structured approach from design to implementation. **All execplans must be saved in `.agent/execplans/phase-1-execplan.md`, `.agent/execplans/phase-2-execplan.md`, etc.**


# IMPORTANT: You should fully understand the project before starting. After starting, you must follow through completely without stopping. Maintain the memory system (CURRENT.md and journal files) throughout the entire process. 