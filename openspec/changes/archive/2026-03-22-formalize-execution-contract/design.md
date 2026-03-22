## Context

The package currently has enough implementation pieces to run a real workflow, but the normative contract among those pieces is still underspecified. The next risk is not missing code; it is inconsistent execution, where different agents use different mental models for when to invoke scripts, when to ask the user, and when to move forward.

## Goals / Non-Goals

**Goals:**
- Turn the current workflow description into a strong execution contract
- Clarify script-only work, LLM-only work, and forbidden delegation
- Make stage progression depend on explicit gates rather than inferred intent
- Keep the public script interfaces unchanged

**Non-Goals:**
- Introduce a full state machine
- Refactor or redesign the existing scripts
- Add new artifacts or new runtime scripts
- Move detailed policy out of `SKILL.md`

## Decisions

- Put the main contract directly into `SKILL.md` so it is always in the primary load path.
- Keep `stage-workflow.md` as a detailed recipe companion rather than the source of hard rules.
- Use a stage recipe format with five fixed parts for every stage:
  - `Preconditions`
  - `Required Script Calls`
  - `LLM Tasks`
  - `Outputs`
  - `Do Not Advance Until`
- Define three explicit contract sections in `SKILL.md`:
  - `Script Responsibilities`
  - `LLM Responsibilities`
  - `Forbidden Delegation`
- Keep script interfaces unchanged and allow only wording-level alignment if needed.

## Risks / Trade-offs

Putting more contract material directly into `SKILL.md` increases its size, but it also ensures the hard rules are visible in the first-read path. That trade-off is acceptable because the problem being solved is execution drift, not lack of auxiliary detail.
