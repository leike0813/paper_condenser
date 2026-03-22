## ADDED Requirements

### Requirement: File-Path-Only Stage 1 Entry

The first supported version of the skill MUST treat file-path input as the only formal workflow entry for Stage 1.

#### Scenario: The Stage 1 entry contract is inspected
- **WHEN** the package instructions are reviewed
- **THEN** Stage 1 begins from a source file path
- **AND** the package no longer treats pasted body text, pasted fragments, or pure descriptions as formal first-class entry modes

### Requirement: Mandatory Deterministic Preparation Sequence

Stage 1 MUST define a mandatory deterministic preparation sequence before any semantic manuscript analysis begins.

#### Scenario: A new source file enters the workflow
- **WHEN** the agent receives a manuscript file path
- **THEN** it first runs `bootstrap_runtime.py --source-path <SOURCE_PATH>`
- **AND** it runs `init_artifacts.py --artifact-root <ARTIFACT_ROOT>` if the artifact workspace is incomplete
- **AND** it runs `stage1_intake.py --artifact-root <ARTIFACT_ROOT>` before semantic analysis

### Requirement: Stage 1 Playbook Substeps

The Stage 1 contract MUST define explicit substeps after deterministic preparation.

#### Scenario: The Stage 1 playbook is inspected
- **WHEN** the Stage 1 instructions are read
- **THEN** they define scope identification
- **AND** they define topic and research-question synthesis
- **AND** they define main-work and novelty extraction
- **AND** they define section-outline and removable-candidate identification
- **AND** they define open-question consolidation and gate checking

### Requirement: Manuscript Profile as Stage 1 Source of Truth

Stage 1 MUST write its usable understanding draft into `manuscript-profile.json`.

#### Scenario: Stage 1 completes successfully
- **WHEN** the agent finishes the Stage 1 playbook
- **THEN** `manuscript-profile.json` includes a usable `scope`
- **AND** it includes a usable `topic`
- **AND** it includes non-empty `main_work`
- **AND** it includes non-empty `novelty`
- **AND** it includes non-empty `section_outline`
- **AND** it includes non-empty `removable_candidates`
- **AND** it includes explicit `open_questions`
- **AND** `status` is updated to `analysis_complete`

### Requirement: Open Questions Must Be Persisted

Stage 1 MUST persist unresolved manuscript ambiguities instead of leaving them only in the live conversation.

#### Scenario: The agent cannot fully resolve a manuscript ambiguity
- **WHEN** Stage 1 still has unresolved but non-blocking questions
- **THEN** the questions are written into `manuscript-profile.json.open_questions`
- **AND** the workflow may still advance if the rest of the Stage 1 gate is satisfied

### Requirement: Stage 1 Question Boundary

Stage 1 MUST distinguish manuscript-understanding questions from later-stage target-setting questions.

#### Scenario: Stage 1 user interaction is needed
- **WHEN** the agent asks questions during Stage 1
- **THEN** the questions are limited to manuscript scope, document boundaries, source ambiguity, and understanding blockers
- **AND** the agent does not ask for target language, target form, target journal type, or target body length during Stage 1

### Requirement: Stage 1 Advancement Gate

The package MUST define a specific minimum gate for entering Stage 2.

#### Scenario: The workflow checks whether Stage 2 may begin
- **WHEN** Stage 1 is evaluated for completion
- **THEN** deterministic intake is already complete
- **AND** `scope`, `topic`, `main_work`, `novelty`, `section_outline`, `removable_candidates`, and `open_questions` are all present in usable draft form
- **AND** the workflow does not advance if manuscript understanding exists only in the agent's transient context
