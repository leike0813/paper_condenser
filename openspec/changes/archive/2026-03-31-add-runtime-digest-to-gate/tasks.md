# Tasks

## 1. Runtime digest asset

- [x] Add `paper-condenser/assets/runtime/skill-runtime-digest.md`
- [x] Keep the digest shorter than `SKILL.md` and focused on runtime discipline

## 2. Gate output

- [x] Add a fixed digest loader in `runtime_core.py`
- [x] Return `runtime_digest` from both gate entry paths
- [x] Keep existing gate fields unchanged

## 3. Skill/docs

- [x] Update `SKILL.md` to document the new read order
- [x] Update `gate-and-stage-runtime.md` to describe `runtime_digest`

## 4. Validation

- [x] Run `openspec validate add-runtime-digest-to-gate`
- [x] Run `quick_validate.py paper-condenser`
- [x] Run `mypy` on `runtime_core.py` and `gate_runtime.py`
