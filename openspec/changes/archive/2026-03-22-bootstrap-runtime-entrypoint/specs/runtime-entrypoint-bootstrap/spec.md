## ADDED Requirements

### Requirement: Formal Runtime Bootstrap Script

The package MUST provide a formal runtime bootstrap script for file-path manuscript inputs.

#### Scenario: Runtime entrypoint is inspected
- **WHEN** the package scripts are reviewed
- **THEN** `paper-condenser/scripts/bootstrap_runtime.py` exists
- **AND** it is the first-stage runtime entrypoint for file-path inputs

### Requirement: Explicit Source Path Interface

The runtime bootstrap script MUST accept a manuscript file path explicitly.

#### Scenario: Caller bootstraps from a source file
- **WHEN** the caller runs the runtime bootstrap script
- **THEN** it passes `--source-path <path>`
- **AND** the script validates that the source path exists and is a file

### Requirement: Deterministic Slug And Artifact Root

The script MUST derive a deterministic slug from the source file name and use it to select the artifact root.

#### Scenario: Source file name is valid
- **WHEN** the caller passes a source file path
- **THEN** the script derives a hyphen-case `document-slug` from the file name
- **AND** it targets `artifacts/<document-slug>/`

#### Scenario: Target artifact root already exists
- **WHEN** `artifacts/<document-slug>/` already exists
- **THEN** the script exits with a non-zero code
- **AND** it does not auto-rename the slug or overwrite the existing directory

### Requirement: Runtime Bootstrap Reuses Template Initialization

The runtime bootstrap MUST initialize the workspace through the existing artifact initialization logic.

#### Scenario: Fresh runtime bootstrap succeeds
- **WHEN** the target artifact root does not yet exist
- **THEN** the script initializes the four artifact files from package templates
- **AND** it does not duplicate template-copy logic separately from the formal initialization workflow

### Requirement: Deterministic Manuscript Metadata Seeding

The runtime bootstrap script MUST seed `manuscript-profile.json` with deterministic source metadata only.

#### Scenario: Bootstrap completes
- **WHEN** the script initializes a runtime artifact workspace
- **THEN** it writes `source_id`, `source_path`, `source_type`, `scope`, and `status` into `manuscript-profile.json`
- **AND** it does not infer semantic fields such as `topic`, `main_work`, or `section_outline`

### Requirement: Structured JSON Output

The runtime bootstrap script MUST return machine-consumable JSON on stdout.

#### Scenario: Bootstrap succeeds
- **WHEN** the script exits successfully
- **THEN** stdout contains JSON
- **AND** the JSON includes `document_slug`, `artifact_root`, and `created_files`
