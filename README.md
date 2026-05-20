# Compound AI Operating Standards: Starter Kit v2.6.0

A drop-in operating layer that helps any capable agent (Claude, Codex, Cursor,
Aider, Continue) work with durable routing, token discipline, goal loops,
validation, provenance, and memory. The kit is vendor-neutral: Claude Code
`/goal` is supported as an adapter, but the portable behavior is the Compound
AI goal contract.

**New in v2.6.0:** the durable behavioral overlay. `goal-runner` turns
substantial work into an objective, completion condition, validation plan,
context budget, stop conditions, and memory update. `trigger-indexer` maintains
the machine-readable trigger registry used by `request-router`. Adoption now
commits behaviors, not just kit awareness: route before complex replies, use
goal contracts for verifiable multi-step work, budget context, validate the
rendered/user-visible contract, slow-lane blocked items, and write useful
memory.

**Carried from v2.5.0:** `adoption-captain` safely layers the kit into an
existing project, preserves host rules, applies additively under `.compound-ai/`,
validates with the host project's own commands, and updates project instruction
surfaces with marker-bounded sections.

**Canonical site:** [cameronsutcliff.com/compound-ai](https://cameronsutcliff.com/compound-ai)
**Source repo:** [github.com/cameronpsutcliff/compound-ai-operating-standards](https://github.com/cameronpsutcliff/compound-ai-operating-standards)
**Field guide:** [cameronsutcliff.com/compound-ai/field-guide](https://cameronsutcliff.com/compound-ai/field-guide)

---

## What ships

```
compound-ai-operating-standards/
├── AGENT.md                      root operating contract
├── ADOPT.md                      existing-project adoption entry point
├── HANDOFF.md                    new-project / fresh-agent handoff
├── _skills-index.md              human skill registry, 27 skills
├── tier-1-global/
│   ├── conventions/
│   │   └── trigger-registry.yaml machine-readable routing registry
│   ├── checklists/               session start, closeout, model routing
│   └── skills-core/              13 infrastructure skills
├── tier-2-capabilities/          14 cognitive, analytical, domain skills
├── tier-3-shells/                slide, scroll, mission-control, course
├── code/                         reference implementations
├── scripts/                      build-manifest, verify-integrity, verify-origin
└── docs/                         FIELD-GUIDE.md and publication docs
```

## What you get

**27 skills** organized by tier, each `SKILL.md` kept under 100 lines with a
target of 80:

| Tier | Count | Skills |
|---|---:|---|
| Tier 1: session infrastructure | 13 | request-router, goal-runner, trigger-indexer, context-loader, token-economist, engagement-bootstrap, quality-gate, pattern-promoter, provenance-check, agent-panel-planning, agent-panel-review, release-captain, adoption-captain |
| Tier 2: cognitive modes | 7 | parallel-lens-synthesis, consequence-simulation, cross-domain-translation, convergence-detection, detached-judgment, simulation-to-action-bridge, nod-protocol |
| Tier 2: analytical capabilities | 5 | ultra-think, pressure-test, code-audit, autoresearch, skill-creator |
| Tier 2: domain capabilities | 2 | viz, stakeholder-mapping |

**4 shells** for deliverables: slide, scroll, mission-control, and course.

## Install

### Option A: Adopt into an existing project

```bash
git clone https://github.com/cameronpsutcliff/compound-ai-operating-standards.git .compound-ai
```

Then hand the agent `ADOPT.md`, not just `AGENT.md`:

```text
Read .compound-ai/ADOPT.md and run adoption-captain. Preserve this project's
existing rules, propose an additive plan before edits, and install the durable
behavioral overlay only after approval.
```

### Option B: Bootstrap a new project

Use `HANDOFF.md` and `engagement-bootstrap`.

### Option C: Use as reference

Read the field guide and adopt the patterns piecemeal.

## How it works

1. The agent loads `AGENT.md`, `_skills-index.md`, `request-router`, and
   `trigger-registry.yaml`.
2. The router maps requests to the smallest useful skill chain.
3. Substantial work routes through `goal-runner`: objective, completion
   condition, validation, context budget, stop conditions, memory update.
4. The agent validates the user-visible contract before declaring done.
5. Durable lessons move into state, logs, instructions, or reusable patterns.

## Claude Code `/goal`

Claude Code v2.1.139+ supports `/goal`, which keeps Claude working across turns
until a completion condition is met. Compound AI supports it as an adapter:
write the goal contract first, then pass the completion condition to `/goal`.
Other agents use the same contract manually through `goal-runner`.

## What this kit is not

- Not a prompt library.
- Not vendor-specific.
- Not a replacement for the host project's own rules.
- Not a demand to load the full field guide at startup.

## Versioning

This is **v2.6.0**. It adds the durable behavioral overlay (`goal-runner`,
`trigger-indexer`, `trigger-registry.yaml`) and updates adoption memory so
future sessions inherit behavior, not just references. v2.5.0 added
`adoption-captain`; v2.4.0 added `release-captain`; v2.3.x hardened package
discipline and panel review.

See `releases/` for full version history.

## License

- **Documentation:** CC BY 4.0
- **Code:** Apache 2.0
- **Origin:** Compound AI Operating Standards by Cameron Sutcliff

Cite the canonical source when you fork or extend:
`https://cameronsutcliff.com/compound-ai`

## Provenance verification

```bash
./scripts/verify-origin.py --online
```

Returns `VERIFIED` if the local manifest matches the canonical website manifest.
