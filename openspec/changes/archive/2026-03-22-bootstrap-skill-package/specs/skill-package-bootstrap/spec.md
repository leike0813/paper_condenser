## ADDED Requirements

### Requirement: Publishable Skill Package Root

The repository MUST contain a recognizable Skill package root at `paper-condenser/`.

#### Scenario: Package root is inspected
- **WHEN** an agent or tool inspects the repository for the deliverable Skill package
- **THEN** it finds a dedicated package root at `paper-condenser/`
- **AND** the repository root remains a development workspace rather than the package root

### Requirement: Required Skill Metadata Files

The Skill package MUST include valid package metadata files required for discovery and invocation.

#### Scenario: Skill metadata is validated
- **WHEN** the package is validated as an Open Agent Skill
- **THEN** `paper-condenser/SKILL.md` exists with valid frontmatter
- **AND** `paper-condenser/agents/openai.yaml` exists with interface metadata

### Requirement: Reserved Internal Resource Layout

The Skill package MUST reserve internal directories for future references, scripts, and assets.

#### Scenario: Package resources are prepared for later iterations
- **WHEN** a maintainer inspects the package contents
- **THEN** `paper-condenser/references/`, `paper-condenser/scripts/`, and `paper-condenser/assets/` exist
- **AND** the directories are preserved even before real contents are added

### Requirement: Stable Public Invocation Name

The Skill package MUST expose the public invocation identifier `$paper-condenser` consistently across its metadata.

#### Scenario: Invocation metadata is compared
- **WHEN** the package metadata is reviewed
- **THEN** the skill name in `paper-condenser/SKILL.md` is `paper-condenser`
- **AND** `paper-condenser/agents/openai.yaml` includes a default prompt that explicitly references `$paper-condenser`

### Requirement: Repository References Stay Outside The Package

This initialization MUST NOT treat the repository-root `references/` directory as package-internal resources.

#### Scenario: Initialization scope is checked
- **WHEN** the bootstrap change is reviewed
- **THEN** the repository-root `references/` directory remains outside `paper-condenser/`
- **AND** no existing reference document is moved, deleted, or rewritten as part of package initialization
