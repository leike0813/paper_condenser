## Purpose

Define the SQLite single-source-of-truth runtime, gate discipline, render-only runtime views, and DB-backed final outputs.
## Requirements
### Requirement: SQLite is the only runtime source of truth

The package MUST persist runtime state in a single SQLite database under the artifact root.

#### Scenario: A runtime workspace is initialized

- **WHEN** runtime bootstrap succeeds
- **THEN** `.paper-condenser-tmp/<document-slug>/paper-condenser.db` exists
- **AND** the DB is treated as the only runtime source of truth
- **AND** Markdown views and final outputs are rendered from DB state rather than treated as editable truth

### Requirement: Runtime progression is gate-driven

The package MUST use a single gate entry to determine the only allowed next action.

#### Scenario: A runtime workspace is resumed

- **WHEN** `gate_runtime.py` is run against an existing `artifact-root`
- **THEN** it returns `workflow_stage`
- **AND** it returns `next_action`
- **AND** it returns blockers and pending confirmations when progression is not allowed

#### Scenario: Style profiling remains inside Stage 3

- **WHEN** Stage 3 basics and content selection are complete
- **AND** `style_profile.status` is not yet `complete`
- **THEN** gate remains at `stage_3_target_settings`
- **AND** gate returns `persist_style_profile`
- **AND** it MUST NOT advance to `stage_4_condensation_plan`

#### Scenario: The runtime enters final drafting

- **WHEN** Stage 4 planning is complete
- **THEN** gate may return `prepare_section_drafting`, `persist_section_draft`, `approve_section_draft`, `persist_output_target`, or `render_final_output_bundle`
- **AND** it MUST NOT allow a one-shot final drafting bypass

### Requirement: Gate discipline blocks premature drafting

The runtime gate MUST keep Stage 5 planning and Stage 6 drafting as separate gated phases.

#### Scenario: Stage 5 has not fully completed

- **WHEN** the condensation plan or section rewrite plan is still waiting for approval
- **THEN** gate returns the corresponding confirm action
- **AND** it MUST NOT advance to Stage 6 drafting actions

### Requirement: Runtime views are render-only

The package MUST render human-readable Markdown views from the DB and MUST NOT treat them as runtime truth. The numbered runtime views MUST be ordered to match the workflow reading order from Stage 1 through Stage 6.

#### Scenario: A stage write succeeds

- **WHEN** `stage_runtime.py` persists stage data
- **THEN** the runtime view files are re-rendered from the database through the external template layer
- **AND** the Agent is expected to treat them as read-only
- **AND** the numbered Markdown view filenames MUST follow the workflow-aligned order:
  - `01-agent-resume.md`
  - `02-manuscript-profile.md`
  - `03-supporting-elements-inventory.md`
  - `04-scope-segments.md`
  - `05-semantic-source-units.md`
  - `06-target-settings.md`
  - `07-content-selection-board.md`
  - `08-style-profile.md`
  - `09-condensation-plan.md`
  - `10-section-rewrite-plan.md`
  - `11-section-drafting-board.md`

#### Scenario: Section drafting state changes

- **WHEN** section drafting, approval, or output-target persistence succeeds
- **THEN** the workflow-aligned drafting-board view and section-review views are re-rendered from the database
- **AND** the Agent is expected to treat them as read-only

### Requirement: Runtime rendering does not silently degrade

The package MUST fail loudly if a required runtime-view template is missing or broken.

#### Scenario: A required runtime-view template is unavailable

- **WHEN** gate or a stage write triggers view rendering
- **AND** a required template file is missing or invalid
- **THEN** the command exits non-zero
- **AND** the runtime does not fall back to inline Python string rendering

### Requirement: Final outputs are rendered from DB state

The package MUST keep final draft and rewrite report as output files, but they MUST be rendered from DB-backed content.

#### Scenario: Final drafting completes

- **WHEN** final drafting reaches bundle rendering successfully
- **THEN** `.paper-condenser-tmp/<document-slug>/final-draft.tex` exists
- **AND** `.paper-condenser-tmp/<document-slug>/rewrite-report.md` exists
- **AND** neither file is treated as runtime truth

### Requirement: Final outputs are rendered by assembly from DB-backed approved drafts

The runtime MUST treat final bundle rendering as an assembly step over DB-backed approved drafts.

#### Scenario: Final bundle rendering completes

- **WHEN** `render_final_output_bundle` succeeds
- **THEN** the DB-backed final outputs are rendered from approved section drafts
- **AND** the runtime copies any referenced images into the output directory
- **AND** the runtime rewrites image paths in the final LaTeX output

### Requirement: Gate returns a minimal payload example for the next action

The gate runtime MUST return a machine-readable minimal payload example together with `next_action`.

#### Scenario: The next action requires payload

- **WHEN** `gate_runtime.py` returns a payload-bearing `next_action`
- **THEN** the result includes `next_action_payload_example`
- **AND** that field contains a minimal JSON object that can be used as the starting shape for the next stage write

#### Scenario: The next action does not require payload

- **WHEN** `gate_runtime.py` returns a no-payload `next_action`
- **THEN** `next_action_payload_example` is `null`

### Requirement: Language Context Is Confirmed Before Stage 2 Analysis Continues

The runtime MUST confirm `working_language` and an initial `target_language` before Stage 2 analysis proceeds.

#### Scenario: Stage 2 blocks on language context

- **WHEN** intake and supporting-elements inventory are complete
- **AND** language context has not been confirmed
- **THEN** gate returns `confirm_language_context` as the only allowed next action

### Requirement: Runtime Templates Use Workspace Copies

The runtime MUST render read-only Markdown views from workspace template copies after language context is confirmed.

#### Scenario: Prebuilt template languages

- **WHEN** `working_language` is `zh` or `en`
- **THEN** Stage 2 materializes the matching prebuilt template set into the workspace

#### Scenario: Non-prebuilt working language

- **WHEN** `working_language` is not `zh` or `en`
- **THEN** gate returns `persist_runtime_template_translation`
- **AND** Stage 2 cannot continue until translated workspace templates are written

### Requirement: Final Bundle Consumes Translated Sections

The final bundle renderer MUST assemble translated sections, not working-language drafts.

#### Scenario: Translation gate before final render

- **WHEN** all section drafts are approved and output target is confirmed
- **AND** translated sections are missing or stale
- **THEN** gate returns `persist_translated_sections`
- **AND** `render_final_output_bundle` remains blocked

