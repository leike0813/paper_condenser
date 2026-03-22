## 1. OpenSpec Artifacts

- [x] 1.1 Write `proposal.md` and define the new capability `stage1-intake-bootstrap`
- [x] 1.2 Write `specs/stage1-intake-bootstrap/spec.md` for intake entrypoint, supported file types, deterministic fields, and JSON output
- [x] 1.3 Write `design.md` with intake-layer storage and no-semantic-inference decisions

## 2. Script Implementation

- [x] 2.1 Add `paper-condenser/scripts/stage1_intake.py`
- [x] 2.2 Read `manuscript-profile.json`, validate supported source types, and load source text
- [x] 2.3 Write `content_preview`, `source_stats`, and `intake_status` back to `manuscript-profile.json`
- [x] 2.4 Return JSON with `artifact_root`, `updated_fields`, and `source_stats`

## 3. Protocol And Skill Updates

- [x] 3.1 Update `paper-condenser/assets/artifact-templates/manuscript-profile.json` with default intake-layer fields
- [x] 3.2 Update `paper-condenser/references/artifact-protocol.md` to document intake-layer fields in `manuscript-profile.json`
- [x] 3.3 Update `paper-condenser/SKILL.md` so file-path flows run `stage1_intake.py` before semantic Stage 1 analysis

## 4. Validation

- [x] 4.1 Run `openspec validate bootstrap-stage1-intake`
- [x] 4.2 Bootstrap a fresh artifact root from a Markdown source and run `stage1_intake.py`
- [x] 4.3 Verify `manuscript-profile.json` contains preview, source stats, and intake status
- [x] 4.4 Run `stage1_intake.py` against an unsupported source type and verify non-zero exit
- [x] 4.5 Run the external skill `quick_validate.py` check against `paper-condenser/`
- [x] 4.6 Run `mypy paper-condenser/scripts/stage1_intake.py paper-condenser/scripts/bootstrap_runtime.py paper-condenser/scripts/init_artifacts.py`
