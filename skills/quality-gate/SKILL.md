# Skill: quality-gate
# Compound AI Operating Standards
# Source: cameronsutcliff.com/compound-ai | License: Apache 2.0

## What this skill does
Checks whether a generated artifact meets the quality bar before it ships.

## Triggers
"quality check", "validate output", "ship check", "is this ready", "so what test"

## What it checks
1. Schema: does the output conform to the declared output schema?
2. Richness: is the narrative content above the richness floor (not a thin generation)?
3. Lineage: does the output have provenance edges pointing at source evidence?
4. So What: can the output be explained in terms of why it matters to a decision?
5. Grounding: are specific claims traceable to source evidence (no hallucinated specifics)?

## Quality gate checklist
- [ ] Output passes schema validation (no missing required fields, correct types)
- [ ] Narrative sections are above richness floor (not below 50% of historical max)
- [ ] At least one lineage edge recorded (derived_from source evidence)
- [ ] "So What" is explicit: output explains why it matters, not just what happened
- [ ] No ungrounded specifics (every named entity, number, or claim has a source)

## Failure actions
- Schema failure: retry once with error injected into prompt
- Richness failure: preserve prior version, log to quality ledger
- Lineage missing: log warning, do not block (lineage is best-effort)
- So What missing: flag for human review before surfacing to end consumer
- Grounding failure: reject output, do not surface

## Source references
- `code/schema_validator.py` -- schema validation implementation
- `code/pipeline_runs.sql` -- quality ledger table
- Field Guide Chapter 21: Schema Validation at LLM Boundaries
- Field Guide Chapter 24: The Quality Immune System
- Field Guide Chapter 25: The "So What" Test
