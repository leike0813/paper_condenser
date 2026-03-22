## 1. OpenSpec Artifacts

- [x] 1.1 Write `proposal.md` and define the new capability `artifact-template-bootstrap`
- [x] 1.2 Write `specs/artifact-template-bootstrap/spec.md` for template coverage, naming parity, minimal content, and documentation linkage
- [x] 1.3 Write `design.md` with the template directory choice and minimal-template decisions

## 2. Template Assets

- [x] 2.1 Add `paper-condenser/assets/artifact-templates/manuscript-profile.json`
- [x] 2.2 Add `paper-condenser/assets/artifact-templates/target-settings.json`
- [x] 2.3 Add `paper-condenser/assets/artifact-templates/style-profile.md`
- [x] 2.4 Add `paper-condenser/assets/artifact-templates/condensation-plan.md`

## 3. Documentation

- [x] 3.1 Update `paper-condenser/SKILL.md` to point to `assets/artifact-templates/` as initialization templates
- [x] 3.2 Update `paper-condenser/references/artifact-protocol.md` to explain the relation between package templates and runtime artifact copies

## 4. Validation

- [x] 4.1 Run `openspec validate bootstrap-artifact-templates`
- [x] 4.2 Run the external skill `quick_validate.py` check against `paper-condenser/`
- [x] 4.3 Verify that template file names, fields, headings, and default approval state match the protocol
