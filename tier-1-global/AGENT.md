# Tier 1: Global

The universal layer. Everything in this folder applies to every project, every session, every downstream consumer.

## What this tier owns

- **`conventions/`** — style guide, em-dash policy, voice rules, skill-author guide, token-efficiency rules, provenance conventions
- **`context/`** — `tier0.md` (always-load), `tier1-current.md` (live working context), `tier1-subsystem/` (per-domain slices)
- **`checklists/`** — session-start, session-closeout, era transitions (Demo → Ramp-up → Durable), pattern promotion, model routing
- **`skills-core/`** — 7 session infrastructure skills: request-router, context-loader, token-economist, engagement-bootstrap, quality-gate, pattern-promoter, provenance-check
- **`design-system/`** — Abyssal design tokens (CSS variables, base styles) for use in Tier 3 shells

## Rules at this tier

1. **Universal only.** If a file here is domain-specific (consulting, dev, finance), it belongs in Tier 2 or 3.
2. **Conventions are canonical.** Lower tiers reference; they do not duplicate.
3. **Skills here are pointer skills.** Each `SKILL.md` is under 80 lines and dispatches to deeper references on demand.
4. **The design system is the source of truth for styling.** Shells inherit; they do not redefine tokens.

## Load order at session start

1. `conventions/style-guide.md` — voice and formatting rules
2. `context/tier0.md` — project name, phase, primary constraint
3. `checklists/session-start.md` — the session bootstrap routine
4. `skills-core/request-router/SKILL.md` — activates routing for the session

## Escalate up / drill down

- **Up:** parent `../AGENT.md` (root operating contract)
- **Down:** `../tier-2-capabilities/AGENT.md` for capability skills, `../tier-3-shells/AGENT.md` for project scaffolds
