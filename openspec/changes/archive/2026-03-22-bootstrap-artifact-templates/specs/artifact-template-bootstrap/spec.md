## ADDED Requirements

### Requirement: Package-Owned Artifact Template Set

The package MUST include a built-in template set for the four defined workflow artifacts.

#### Scenario: Template assets are inspected
- **WHEN** the package assets are reviewed
- **THEN** `paper-condenser/assets/artifact-templates/` exists
- **AND** it contains templates for `manuscript-profile.json`, `target-settings.json`, `style-profile.md`, and `condensation-plan.md`

### Requirement: Runtime File Name Parity

Each template file MUST use the same file name as its runtime artifact counterpart.

#### Scenario: Templates are copied into a task artifact directory
- **WHEN** an agent initializes `artifacts/<document-slug>/`
- **THEN** it can copy each template without renaming
- **AND** the resulting runtime file names match the workflow contract exactly

### Requirement: Minimal Valid Template Content

Templates MUST be minimal initialization skeletons rather than rich examples.

#### Scenario: JSON templates are reviewed
- **WHEN** `manuscript-profile.json` and `target-settings.json` templates are opened
- **THEN** they contain the minimum protocol fields
- **AND** their values are safe empty values or minimal placeholders

#### Scenario: Markdown templates are reviewed
- **WHEN** `style-profile.md` and `condensation-plan.md` templates are opened
- **THEN** they contain the agreed section headers
- **AND** they use brief placeholder guidance instead of scenario-specific example content

### Requirement: Unapproved Plan By Default

The condensation plan template MUST start in an unapproved state.

#### Scenario: Plan template is initialized
- **WHEN** `condensation-plan.md` is copied from the package template set
- **THEN** its `Approval` section indicates that the plan is not yet approved

### Requirement: Documentation Links To Templates

The package documentation MUST state where artifact templates are stored and what they are for.

#### Scenario: Skill documentation is read
- **WHEN** another agent reads the skill documentation
- **THEN** it can identify `paper-condenser/assets/artifact-templates/` as the source of initialization templates
- **AND** it understands that those templates are copied into `artifacts/<document-slug>/` as starting points rather than treated as live task state
