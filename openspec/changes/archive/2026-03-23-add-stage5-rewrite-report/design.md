## Overview

This change adds a mandatory companion output to Stage 5: a persisted Markdown rewrite report that explains the transformation from source manuscript to condensed LaTeX draft. The report is not a new intermediate artifact; it is a final-output companion, produced after drafting and before Stage 5 is considered complete.

## Key Decisions

### Markdown-Only Companion Output

- The report output is `rewrite-report.md`.
- It is written into the runtime workspace alongside `final-draft.tex`.
- No JSON mirror is added in v1; the primary audience is a human user continuing revision work.

### Mixed-Granularity Traceability

- Every final-draft section or subsection must receive a section-level source mapping.
- Additional fine-grained notes are required only for:
  - key paragraphs that concentrate major compression or restructuring
  - key figures and tables
  - key references or citation clusters
- This avoids turning the report into a noisy paragraph-by-paragraph dump.

### No New Script

- Report generation stays in the LLM domain.
- Existing helper scripts remain unchanged because the report is interpretive and explanatory rather than deterministic.

### Final Output Pair

- Stage 5 now produces two required outputs:
  - `final-draft.tex`
  - `rewrite-report.md`
- Stage 5 cannot complete if either file is missing.

## Report Structure

The report should use a stable Markdown structure:

- `## Run Summary`
- `## Stage Decisions`
- `## Final Draft Section Map`
- `## Key Paragraph And Element Notes`
- `## Unresolved Risks / Follow-up`

This structure is detailed enough for revision work, while staying readable.
