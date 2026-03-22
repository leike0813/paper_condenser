## MODIFIED Requirements

### Requirement: Formal Input Contract Uses A Single `.tex` Manuscript File

The package MUST define its formal source input as a single UTF-8 `.tex` manuscript file path.

#### Scenario: The main skill contract is inspected
- **WHEN** the formal input contract is reviewed
- **THEN** it describes a single `.tex` manuscript file path as the supported formal source input
- **AND** it does not describe Markdown or plain-text files as the formal production input path
