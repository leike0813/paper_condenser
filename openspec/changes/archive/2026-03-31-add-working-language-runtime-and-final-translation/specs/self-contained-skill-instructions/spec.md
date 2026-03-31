## MODIFIED Requirements

### Requirement: SKILL.md Explains Language Context And Final Translation

`SKILL.md` MUST explain that:

- Stage 2 confirms `working_language`
- runtime text artifacts and section drafts use `working_language`
- Stage 3 finalizes `target_language`
- final drafting includes an explicit translation step before assembly-only rendering

#### Scenario: Agent reads only SKILL.md

- **WHEN** an agent reads `SKILL.md` without opening playbooks
- **THEN** it can understand the working-vs-target language split
- **AND** it can see that final assembly does not perform freeform rewriting
