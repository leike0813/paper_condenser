# Design

## Overview

This change moves `paper-condenser` to a database-first runtime architecture.

- SQLite becomes the only runtime source of truth.
- `gate_runtime.py` becomes the single read-only checkpoint and rendering entry.
- `stage_runtime.py` becomes the single write entry for all formal stage actions.
- Human-readable Markdown files become rendered views rather than editable artifacts.

## Core Decisions

### 1. Single DB SSOT

The runtime database is fixed at:

`<artifact-root>/paper-condenser.db`

All stage state, confirmations, analysis results, target settings, style data, condensation planning, and final outputs are persisted to SQLite before any rendered view is considered authoritative.

### 2. Strict gate-driven progression

The runtime uses a fixed state machine:

- `stage_0_bootstrap`
- `stage_1_intake_and_inventory`
- `stage_2_manuscript_analysis`
- `stage_3_target_settings`
- `stage_4_style_profile`
- `stage_5_condensation_plan`
- `stage_6_final_drafting`
- `stage_7_completed`

Only the gate may determine `next_action`.

### 3. Read-only rendered views

The previous runtime files are replaced with rendered Markdown views:

- `01-agent-resume.md`
- `02-manuscript-profile.md`
- `03-target-settings.md`
- `04-style-profile.md`
- `05-condensation-plan.md`
- `06-supporting-elements-inventory.md`

They are written by the runtime renderer after DB writes and must not be edited directly.

### 4. Final outputs remain files, but not truth

`final-draft.tex` and `rewrite-report.md` stay as final deliverables, but they are rendered from DB-backed content. They are no longer considered runtime truth.

### 5. Wrapper handling

Legacy scripts are no longer the primary interface. Where feasible they may proxy into the new runtime. Where no coherent proxy exists, they may become deprecated shims with explicit failure messages.

## Data Model Strategy

The database uses fixed logical tables:

- `runtime_workspace`
- `workflow_state`
- `manuscript_source`
- `manuscript_intake`
- `supporting_elements_inventory`
- `manuscript_analysis`
- `target_settings`
- `style_profile`
- `condensation_plan`
- `final_outputs`
- `pending_confirmations`
- `action_log`

The business tables store structured JSON payloads or explicit text columns, while `workflow_state` and `pending_confirmations` drive gate decisions.

## Rendering Strategy

`gate_runtime.py` re-renders all Markdown views after evaluating DB state. `stage_runtime.py` writes DB content, then invokes the same evaluation and rendering path so the workspace stays synchronized after each action.

## Non-Goals

- No attempt is made to keep the old file-first workflow as a first-class supported mode.
- No attempt is made to turn SQLite scripts into a substitute for LLM semantic work.
- No automatic compilation of LaTeX is introduced in this change.
