## ADDED Requirements

### Requirement: Staged Condensation Workflow

The skill MUST execute paper condensation as a staged workflow rather than a one-shot writing task.

#### Scenario: User provides a manuscript
- **WHEN** the skill receives a manuscript file, excerpt, or report section
- **THEN** it begins with manuscript understanding instead of drafting the target paper
- **AND** it progresses through analysis, decision capture, and planning before any final rewrite

### Requirement: Mandatory User-Owned Decisions

The skill MUST explicitly ask the user to confirm decisions that belong to the user.

#### Scenario: Required settings are missing
- **WHEN** target language, article form, target journal type, target body length, or emphasis choices are not yet confirmed
- **THEN** the skill asks the user for those decisions
- **AND** it does not invent the answers on the user's behalf

### Requirement: Four Persistent Working Artifacts

The skill MUST maintain exactly four core working artifacts for the first executable version.

#### Scenario: Artifact set is initialized
- **WHEN** the skill begins a new condensation task
- **THEN** it creates or updates these artifacts under a task-local artifact directory:
- **AND** `manuscript-profile.json` stores source facts and extractive judgments
- **AND** `target-settings.json` stores confirmed target constraints
- **AND** `style-profile.md` stores style diagnosis and recommendations
- **AND** `condensation-plan.md` stores the approved reduction strategy

### Requirement: Mixed Artifact Formats

The skill MUST use JSON for structured facts and Markdown for interpretive planning artifacts.

#### Scenario: Artifact formats are reviewed
- **WHEN** the first executable workflow is implemented
- **THEN** `manuscript-profile.json` and `target-settings.json` are JSON artifacts
- **AND** `style-profile.md` and `condensation-plan.md` are Markdown artifacts

### Requirement: Drafting Gate

The skill MUST block final drafting until prerequisite artifacts exist and the user has approved the plan.

#### Scenario: User requests drafting too early
- **WHEN** the user asks for the final condensed paper before the target settings or condensation plan are confirmed
- **THEN** the skill refuses to draft the final paper
- **AND** it continues the missing analysis, questioning, or planning steps

#### Scenario: Plan is fully locked
- **WHEN** all four artifacts exist and `condensation-plan.md` records explicit user approval
- **THEN** the skill may enter the final drafting stage

### Requirement: Read-Only Handling of Source Material

The skill MUST treat the source manuscript as read-only input.

#### Scenario: Source material is processed
- **WHEN** the skill reads the original manuscript or report section
- **THEN** it extracts information into artifacts instead of editing the original file
- **AND** it never rewrites the source manuscript in place

### Requirement: Package And Development References Stay Separate

The skill MUST distinguish package-internal references from repository-root development references.

#### Scenario: Reference usage is reviewed
- **WHEN** the skill loads its own guidance material
- **THEN** it treats files inside `paper-condenser/references/` as package references
- **AND** it does not rely on repository-root `references/` as runtime package assets
