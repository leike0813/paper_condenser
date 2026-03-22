## Context

The bootstrap change created a valid package skeleton, but the package still lacks operational instructions. To make `paper-condenser` usable by another agent, the workflow needs explicit stages, mandatory user checkpoints, and a stable artifact model that can carry state across a long condensation session.

## Goals / Non-Goals

**Goals:**
- Turn `paper-condenser/SKILL.md` into an executable protocol
- Define a stable first-version artifact set
- Keep the package concise by pushing detailed stage and artifact rules into package references
- Preserve the existing public invocation name and UI metadata

**Non-Goals:**
- Add helper scripts
- Copy or migrate repository-root reference documents
- Introduce additional UI metadata or package assets
- Expand the artifact model beyond the minimum four-file set

## Decisions

- Keep the public skill name `$paper-condenser` unchanged and leave `agents/openai.yaml` untouched.
- Rewrite `SKILL.md` in Chinese-first form, with English file names and field names where structure benefits from stability.
- Use a task-local artifact root `artifacts/<document-slug>/` for persistent state. The slug is derived from the source filename or a user-confirmed short identifier.
- Use exactly four artifacts:
  - `manuscript-profile.json` for source facts, outline abstraction, novelty, removable candidates, and open questions
  - `target-settings.json` for confirmed user constraints and must-keep or must-avoid rules
  - `style-profile.md` for writing-style observations, problems, and target-style guidance
  - `condensation-plan.md` for the target outline, priority map, length allocation, and approval record
- Keep stage details and artifact schema details in two package references so the main `SKILL.md` remains readable.

## Risks / Trade-offs

Using only four artifacts keeps the first executable version simple, but it compresses some detail that might later deserve separate artifacts such as outline extraction or session state. This is acceptable for v1 because the goal is to establish a stable core protocol before splitting the state model further.
