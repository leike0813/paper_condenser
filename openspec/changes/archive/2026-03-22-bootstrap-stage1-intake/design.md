## Context

The runtime bootstrap now creates a task-local artifact workspace and seeds deterministic source metadata, but Stage 1 still jumps directly from initialization to semantic analysis. A lightweight, deterministic intake step is needed so the agent starts from a stable preview and basic source statistics instead of a blank semantic profile.

## Goals / Non-Goals

**Goals:**
- Add a deterministic Stage 1 intake script
- Keep the first intake version limited to Markdown and plain-text files
- Persist intake output in `manuscript-profile.json` without creating a new artifact
- Make intake an explicit step in the Stage 1 workflow

**Non-Goals:**
- Support PDF or directory-based sources
- Infer topic, outline, novelty, or other semantic content
- Add a fifth runtime artifact
- Replace runtime bootstrap or low-level artifact initialization

## Decisions

- The script path is fixed at `paper-condenser/scripts/stage1_intake.py`.
- The CLI takes one required argument: `--artifact-root`.
- The script reads source metadata from `manuscript-profile.json` instead of taking the source path again directly.
- Supported source types are limited to `single_file:md` and `single_file:txt`.
- Intake output is written back into `manuscript-profile.json` through three fields:
  - `content_preview`
  - `source_stats`
  - `intake_status`
- `content_preview` is a predictable truncated preview rather than a full source copy.
- `source_stats` contains only deterministic counts and file size information.

## Risks / Trade-offs

Keeping intake inside `manuscript-profile.json` avoids expanding the artifact model, but it means the profile now contains both semantic placeholders and deterministic intake metadata. That trade-off is acceptable for now because the added fields are stable, bounded, and clearly documented as intake-layer data.
