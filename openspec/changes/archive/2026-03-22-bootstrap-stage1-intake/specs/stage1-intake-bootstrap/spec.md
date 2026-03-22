## ADDED Requirements

### Requirement: Formal Stage 1 Intake Script

The package MUST provide a deterministic Stage 1 intake script.

#### Scenario: Stage 1 intake entrypoint is inspected
- **WHEN** the package scripts are reviewed
- **THEN** `paper-condenser/scripts/stage1_intake.py` exists
- **AND** it is the formal deterministic intake entrypoint for Stage 1

### Requirement: Artifact-Root-Based Interface

The intake script MUST operate on an existing artifact root.

#### Scenario: Caller runs intake
- **WHEN** the caller executes the intake script
- **THEN** it passes `--artifact-root <path>`
- **AND** the script reads `manuscript-profile.json` from that artifact directory

### Requirement: Limited Supported Source Types

The first intake version MUST only support Markdown and plain-text files.

#### Scenario: Supported source file is referenced
- **WHEN** `manuscript-profile.json` declares `single_file:md` or `single_file:txt`
- **THEN** the script reads the source text and continues intake

#### Scenario: Unsupported source file is referenced
- **WHEN** `manuscript-profile.json` declares any other `source_type`
- **THEN** the script exits with a non-zero code
- **AND** it does not write partial intake data

### Requirement: Deterministic Intake Fields

The intake script MUST write deterministic, non-semantic intake fields into `manuscript-profile.json`.

#### Scenario: Intake succeeds
- **WHEN** the script completes successfully
- **THEN** `manuscript-profile.json` includes `content_preview`
- **AND** it includes `source_stats`
- **AND** it includes `intake_status`

### Requirement: Deterministic Source Statistics

The intake script MUST compute deterministic source statistics from the source text and file metadata.

#### Scenario: Source statistics are written
- **WHEN** intake succeeds
- **THEN** `source_stats` includes `char_count`
- **AND** it includes `line_count`
- **AND** it includes `file_size_bytes`

### Requirement: No Semantic Inference During Intake

The intake script MUST NOT infer semantic manuscript fields.

#### Scenario: Intake writes back to manuscript profile
- **WHEN** the script updates `manuscript-profile.json`
- **THEN** it does not generate `topic`
- **AND** it does not generate `main_work`
- **AND** it does not generate `novelty`
- **AND** it does not generate `section_outline`

### Requirement: Structured JSON Output

The intake script MUST return machine-consumable JSON on stdout.

#### Scenario: Intake succeeds
- **WHEN** the script exits successfully
- **THEN** stdout contains JSON
- **AND** the JSON includes `artifact_root`, `updated_fields`, and `source_stats`
