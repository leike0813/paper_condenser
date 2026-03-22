## Why

The package currently treats Stage 5 as complete once `final-draft.tex` exists, but that leaves no persisted trace of how the final condensed manuscript was produced, which source regions support each final section, or where the user should look when revising the result. For a manuscript-condensation workflow, the final draft alone is not enough: users also need an explicit rewrite report that records the key Stage 1-4 decisions and maps the final manuscript back to the original source at a usable level of detail.

## What Changes

- Add a mandatory Stage 5 companion output: `rewrite-report.md`.
- Define a mixed-granularity traceability contract: section-level mapping for all final sections, plus finer notes for key paragraphs, key figures, key tables, and key references.
- Make Stage 5 incomplete unless both `final-draft.tex` and `rewrite-report.md` are persisted.
- Add a dedicated Stage 5 rewrite-report playbook and document the report structure in the artifact protocol.
- Update the Stage 5 playbook so report generation happens after drafting and before final delivery.

## Capabilities

### New Capabilities

- `rewrite-report-output-clarification`: Define a persisted Markdown rewrite report that summarizes the transformation process and maps the final draft back to the original manuscript.

### Modified Capabilities

- `stage5-playbook-clarification`: Extend Stage 5 so rewrite-report generation is part of the mandatory output and completion gate.
- `supporting-elements-flow-clarification`: Require the rewrite report to cover key figures, tables, citations, and bibliography decisions where they materially affect the final draft.

## Impact

- Affects the core skill contract in `paper-condenser/SKILL.md`.
- Affects Stage 5 workflow documentation and the artifact protocol.
- Adds a new Stage 5 reference document for rewrite-report generation.
- Does not add new helper scripts or new intermediate state truth sources.
