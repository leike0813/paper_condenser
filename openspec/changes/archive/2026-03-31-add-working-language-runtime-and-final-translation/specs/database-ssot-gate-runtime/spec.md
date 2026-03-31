## ADDED Requirements

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
