# Project Operating Contract
# Compound AI Operating Standards v2.4.0
# Source: cameronsutcliff.com/compound-ai | License: Apache 2.0 (code) / CC BY 4.0 (docs)

Canonical URL: `https://cameronsutcliff.com/compound-ai`

## What this kit is

A drop-in operating layer that turns any agent (Claude, Codex, Cursor, Aider, Continue) into a compounding work surface. Ships with a tiered directory structure, 22 ready-to-load skills, four project shells, the Abyssal design system, and a complete field guide explaining why the kit is shaped this way.

## What this kit is not

1. Not a prompt library. The skills are reasoning scaffolds, not prompts.
2. Not vendor-specific. It uses `AGENT.md` as the canonical contract; `CLAUDE.md` is a 3-line pointer.
3. Not a framework that requires buy-in. Pick the tiers you need and ignore the rest.

## Hard constraints

1. Never inline content into `AGENT.md` or `SKILL.md` files past 80 lines. Long content goes in a `reference/` subfolder, dispatched on demand.
2. Never duplicate Tier 1 content in Tier 2 or 3. Reference upstream.
3. Always use `AGENT.md` as the canonical operating contract. `CLAUDE.md` exists only as a pointer for Claude-specific tooling.
4. Always credit external canon (Stephen Few, Andy Kriebel, GSTACK by Garry Tan, etc.) in skill source references. Never inherit personal attributions from upstream sources.

## Tier model

Read `_tiers.md` for the inheritance rules. Quick summary:

- `tier-1-global/` -- universal: conventions, context, checklists, core skills, design system
- `tier-2-capabilities/` -- domain skills: viz, code-audit, pressure-test, cognitive modes, etc.
- `tier-3-shells/` -- project scaffolds: slide, scroll, mission-control, course

## Context map

| Question | Load |
|---|---|
| Current project state | `STATE.md` |
| Recent changes | `session-log.md` |
| Open items | `BACKLOG.md` |
| Tier model | `_tiers.md` |
| File map | `_map.md` |
| Skill registry | `_skills-index.md` |
| Always-load context | `tier-1-global/context/tier0.md` |
| Current working context | `tier-1-global/context/tier1-current.md` |

## Context tiers (loading depth, distinct from folder tiers)

**Tier 0:** Always load. Short operating contract + task.

**Tier 1:** Load for most project work. Current state + relevant subsystem slice.

**Tier 2:** Load on demand. Full specs, long logs, detailed design docs.

**Tier 3:** Do not load directly. Use search, database queries, or exact file lookup.

## Model routing

| Task type | Route |
|---|---|
| Classification, extraction, formatting | Small or local model |
| Mechanical edit | Fast coding model |
| Multi-file implementation | Strong coding model |
| Synthesis, analysis, strategy | Strong reasoning model |
| Status check | File read, script, or test command |
| Complex reasoning request | Route via `tier-1-global/skills-core/request-router/SKILL.md` |

## Skills

Twenty-two skills total, organized by tier. See `_skills-index.md` for the complete registry with triggers.

**Tier 1 -- session infrastructure (10 skills):**
request-router, context-loader, token-economist, engagement-bootstrap, quality-gate, pattern-promoter, provenance-check, agent-panel-planning, agent-panel-review, release-captain

**Tier 2 -- capabilities (12 skills):**
parallel-lens-synthesis, consequence-simulation, cross-domain-translation, convergence-detection, detached-judgment, simulation-to-action-bridge, nod-protocol, ultra-think, code-audit, autoresearch, skill-creator, pressure-test, viz, stakeholder-mapping

The `request-router` auto-dispatches based on request triggers. It also OFFERS panels (planning or review) when operator-humility signals fire. `release-captain` runs the ten-step ship gate on any release. Most users never have to think about which skill applies.

## Session lifecycle

**Start:**

1. Read this file.
2. Read `_tiers.md`.
3. Read `tier-1-global/context/tier0.md`.
4. Read `_skills-index.md` and load `tier-1-global/skills-core/request-router/SKILL.md`.
5. Read `STATE.md`.
6. Load relevant Tier 1 context only if needed.

**End:**

1. Update `STATE.md`.
2. Add an entry to `session-log.md`.
3. Update `BACKLOG.md` if needed.
4. Promote reusable patterns via `pattern-promoter`.

## Governance

Confirm before:

1. Destructive data operations.
2. Force pushes or history rewrites.
3. Billing changes.
4. External publishing.
5. Auth, permission, or secret changes.

For everything else, act within this contract.
