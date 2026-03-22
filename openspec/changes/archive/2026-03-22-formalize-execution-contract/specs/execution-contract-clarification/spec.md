## ADDED Requirements

### Requirement: Explicit Script Responsibility Contract

The skill MUST explicitly define which work belongs to scripts.

#### Scenario: Script contract is reviewed
- **WHEN** another agent reads the skill instructions
- **THEN** it can identify which tasks are mandatory script responsibilities
- **AND** those tasks are limited to deterministic, repetitive, and verifiable work

### Requirement: Explicit LLM Responsibility Contract

The skill MUST explicitly define which work belongs to the LLM.

#### Scenario: LLM contract is reviewed
- **WHEN** another agent reads the skill instructions
- **THEN** it can identify which tasks require semantic understanding, user interaction, judgment, and writing strategy
- **AND** those tasks are reserved to the LLM rather than delegated to scripts

### Requirement: Forbidden Delegation Rules

The skill MUST explicitly forbid delegating semantic judgment work to scripts.

#### Scenario: Delegation boundary is reviewed
- **WHEN** another agent reads the execution contract
- **THEN** it sees that scripts must not decide topic, novelty, structural importance, condensation priorities, or final writing strategy

### Requirement: Mandatory File-Path Entry Sequence

The skill MUST define a mandatory execution sequence for file-path inputs.

#### Scenario: File-path input enters the workflow
- **WHEN** the user provides a manuscript file path
- **THEN** the skill first runs `bootstrap_runtime.py`
- **AND** then runs `stage1_intake.py`
- **AND** only after those steps may the LLM begin Stage 1 semantic analysis

### Requirement: Mandatory Artifact Recovery Sequence

The skill MUST define how to recover when an artifact root exists but is incomplete.

#### Scenario: Artifact root exists but files are incomplete
- **WHEN** a later run detects a known artifact root with missing runtime files
- **THEN** the skill runs `init_artifacts.py`
- **AND** it does not assume the artifact state from memory alone

### Requirement: Stage Recipes With Gates

The skill MUST document each stage as a gated recipe.

#### Scenario: Stage execution contract is reviewed
- **WHEN** another agent reads the staged workflow
- **THEN** each stage defines preconditions, required script calls, LLM tasks, outputs, and do-not-advance conditions
- **AND** later stages are blocked until earlier gates are satisfied
