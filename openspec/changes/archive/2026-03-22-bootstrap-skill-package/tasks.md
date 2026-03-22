## 1. OpenSpec Artifacts

- [x] 1.1 Write `proposal.md` for the bootstrap change and declare the new capability `skill-package-bootstrap`
- [x] 1.2 Write `specs/skill-package-bootstrap/spec.md` with requirements for package root, metadata, reserved directories, invocation name, and repository reference boundaries
- [x] 1.3 Write `design.md` with the selected package-root, metadata, and placeholder-directory decisions

## 2. Skill Package Skeleton

- [x] 2.1 Create `paper-condenser/SKILL.md` with minimal valid frontmatter and the sections `Overview`, `Hard Constraints`, `Workflow`, and `Resources`
- [x] 2.2 Create `paper-condenser/agents/openai.yaml` with the agreed interface metadata
- [x] 2.3 Preserve `paper-condenser/references/`, `paper-condenser/scripts/`, and `paper-condenser/assets/` with placeholder files

## 3. Validation

- [x] 3.1 Run `openspec validate bootstrap-skill-package`
- [x] 3.2 Run the external skill `quick_validate.py` check against `paper-condenser/`
- [x] 3.3 Confirm the package metadata uses `paper-condenser` consistently and that the repository-root `references/` directory remains untouched
