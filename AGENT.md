# Project Operating Contract
# Compound AI Operating Standards
# Source: cameronsutcliff.com/compound-ai | License: Apache 2.0

Canonical URL: `https://cameronsutcliff.com/compound-ai`

## What This Project Is

[One sentence describing what this project is and who it serves.]

## What This Project Is Not

1. Not [common wrong interpretation].
2. Not [adjacent project or false assumption].
3. Not [rejected architecture or workflow].

## Hard Constraints

1. Never [destructive or rejected operation].
2. Never [tool, vendor, or pattern this project has ruled out].
3. Always [package manager, runtime, or source-of-truth rule].
4. Always [quality, test, or release rule].

## Tech Stack

| Layer | Tool | Notes |
|---|---|---|
| Language | [fill] | [fill] |
| Package manager | [fill] | [fill] |
| Database or store | [fill] | [fill] |
| Test runner | [fill] | [fill] |
| Scheduler | [fill] | [fill] |
| AI runtimes | [fill] | [fill] |

## Context Map

| Question | Load |
|---|---|
| Current state | `STATE.md` |
| Recent changes | `session-log.md` |
| Open items | `BACKLOG.md` |
| Project overview | `Project.md` |
| File map | `_map.md` |
| Skill registry | `_skills-index.md` |
| Always-load context | `context/tier0.md` |
| Current working context | `context/tier1-current.md` |

## Context Tiers

**Tier 0:** Always load. The short operating contract and the task.

**Tier 1:** Load for most project work. Current state plus the relevant subsystem slice.

**Tier 2:** Load on demand. Full specs, long logs, detailed design docs, or large references.

**Tier 3:** Do not load directly. Use search, database queries, or exact file lookup.

## Model Routing

| Task type | Route |
|---|---|
| Classification, extraction, formatting | Small or local model |
| Mechanical edit | Fast coding model |
| Multi-file implementation | Strong coding model |
| Synthesis, analysis, strategy | Strong reasoning model |
| Status check | File read, script, or test command |
| Complex reasoning request | Load cognitive mode via `skills/request-router/SKILL.md` |

## Cognitive Modes

This kit ships with six cognitive mode skills that change HOW you reason.
Load `skills/request-router/SKILL.md` at session start to activate auto-routing.
Full registry and trigger phrases in `_skills-index.md`.

| Mode | What it does |
|---|---|
| parallel-lens-synthesis | Multiple independent reasoning threads, then synthesize |
| consequence-simulation | Premortem, second-order effects, failure modes before acting |
| cross-domain-translation | Re-encode for a different audience without losing fidelity |
| convergence-detection | Surface patterns and root causes across disparate inputs |
| detached-judgment | Evidence-only evaluation, calibrated confidence, no advocacy bias |
| simulation-to-action-bridge | Convert analysis to sequenced, ownable decisions |

## Session Lifecycle

**Start:**

1. Read this file.
2. Read `context/tier0.md`.
3. Read `_skills-index.md` and load `skills/request-router/SKILL.md`.
4. Read `STATE.md`.
5. Load relevant Tier 1 context only if needed.
6. Search before loading broad history.

**End:**

1. Update `STATE.md`.
2. Add an entry to `session-log.md`.
3. Update `BACKLOG.md` if needed.
4. Promote reusable patterns to the project knowledge layer.

## Governance

Confirm before:

1. Destructive data operations.
2. Force pushes or history rewrites.
3. Billing changes.
4. External publishing.
5. Auth, permission, or secret changes.

For everything else, act within this contract.
