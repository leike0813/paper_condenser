## Overview

This change closes a workflow gap: figures, tables, citations, and bibliography structure must no longer be treated as incidental details of final drafting. The package should treat them as supporting elements with their own deterministic inventory phase, user-visible target preferences, explicit planning decisions, and final-draft obligations.

## Key Decisions

### Reuse Existing Truth Sources

- Do not add a fifth intermediate artifact.
- Persist deterministic supporting-elements facts in `manuscript-profile.json`.
- Persist user preferences in `target-settings.json`.
- Persist migration decisions in `condensation-plan.md`.
- Persist style-related guidance for captions/citation prose in `style-profile.md`.

### Distributed Flow Instead Of New Stage Number

- Keep the current five-stage workflow.
- Stage 1 gains deterministic extraction and semantic scoping of supporting elements.
- Stage 4 gains figure/table/reference planning and approval.
- Stage 5 gains explicit migration and review rules for approved supporting elements.

### Deterministic Helper Scope

- Add a single helper script for Stage 1 inventory extraction.
- The script only extracts facts from single-file `.tex` sources:
  - figure environments
  - table environments
  - citation commands and citekeys
  - bibliography resource declarations and `thebibliography` entries
- The script must not decide whether an element should be kept, rewritten, merged, or omitted.

### Reference Model

- Formal first-version reference handling is `BibTeX / citekey` first.
- The workflow should preserve citekeys and bibliography structure where possible.
- The skill may still support `thebibliography` detection in Stage 1 inventory, but that mode is descriptive input truth rather than the preferred target workflow.

## Resulting Data Model

### manuscript-profile.json

Add a supporting-elements inventory block and a deterministic completion marker:

- `supporting_elements_status`
- `supporting_elements.figures`
- `supporting_elements.tables`
- `supporting_elements.citations`
- `supporting_elements.bibliography`

These fields store facts only.

### target-settings.json

Add two user-facing preference fields:

- `figure_table_preference`
- `reference_handling_preference`

They are part of the Stage 2 confirmation bundle and must be covered in readback.

### condensation-plan.md

Add two new planning sections:

- `## Figure / Table Plan`
- `## Reference Plan`

They are part of the Stage 4 approval gate.
