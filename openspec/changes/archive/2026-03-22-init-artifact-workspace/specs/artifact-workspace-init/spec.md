## ADDED Requirements

### Requirement: Formal Artifact Initialization Script

The package MUST provide a deterministic script that initializes a task-local artifact workspace.

#### Scenario: Initialization entrypoint is inspected
- **WHEN** the package scripts are reviewed
- **THEN** `paper-condenser/scripts/init_artifacts.py` exists
- **AND** it is the formal entrypoint for artifact workspace initialization

### Requirement: Explicit Artifact Root Interface

The initialization script MUST accept an explicit artifact root path rather than deriving it from source inputs.

#### Scenario: Caller initializes a workspace
- **WHEN** the caller runs the initialization script
- **THEN** it passes `--artifact-root <path>`
- **AND** the script uses that path as the target workspace directory

### Requirement: Template-Based Workspace Initialization

The script MUST initialize the workspace from the package-owned artifact templates.

#### Scenario: Target directory does not exist
- **WHEN** the caller provides a non-existent target artifact directory
- **THEN** the script creates the directory
- **AND** it copies the four template files from `paper-condenser/assets/artifact-templates/` into that directory

### Requirement: Fill Missing Files Without Overwriting

The script MUST preserve any artifact files that already exist.

#### Scenario: Target directory already contains some artifact files
- **WHEN** the initialization script runs against an existing artifact directory
- **THEN** it copies only missing template files
- **AND** it does not overwrite any existing files

### Requirement: Structured JSON Output

The script MUST return machine-consumable output on stdout.

#### Scenario: Initialization completes successfully
- **WHEN** the script exits with success
- **THEN** stdout contains JSON
- **AND** the JSON includes `artifact_root`, `created_files`, and `skipped_files`

### Requirement: Invalid Initialization Fails Fast

The script MUST fail with a non-zero exit code when initialization cannot be completed safely.

#### Scenario: Template set is incomplete or the target path is invalid
- **WHEN** a required template file is missing or the target path cannot be used as a directory
- **THEN** the script exits with a non-zero code
- **AND** it does not silently continue with partial initialization
