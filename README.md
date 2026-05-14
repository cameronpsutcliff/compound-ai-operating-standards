# Compound AI Operating Standards -- Starter Kit v2.2.0

A drop-in operating layer that turns any agent (Claude, Codex, Cursor, Aider, Continue) into a compounding work surface. Ships with a tiered directory structure, 21 ready-to-load skills, four project shells, and a complete field guide explaining why the kit is shaped this way.

**New in v2.2.0:** `agent-panel-planning` (Tier 1) for upstream plan convergence with independent plans, element-level voting, cross-suggestions for other agents, and strength-matched task assignment. Router gained a Panel Offer Triggers section: operator-humility signals ("I'm not sure", "high-stakes", "test my framing") prompt the agent to OFFER a panel rather than auto-invoke one. Field guide split into Chapter 31 (Planning) + Chapter 32 (Review).

**Carried from v2.1.0:** `agent-panel-review` (Tier 1) for sealed multi-agent review on drafts. `nod-protocol` (Tier 2 cognitive) for five-gate opposite-construction. Operationalized `reference/protocol.md` for all 6 cognitive modes.

**Canonical site:** [cameronsutcliff.com/compound-ai](https://cameronsutcliff.com/compound-ai)
**Source repo:** [github.com/cameronpsutcliff/compound-ai-operating-standards](https://github.com/cameronpsutcliff/compound-ai-operating-standards)
**Field guide (rendered):** [cameronsutcliff.com/compound-ai/field-guide](https://cameronsutcliff.com/compound-ai/field-guide)

---

## What ships

```
compound-ai-operating-standards/
├── README.md                     ← you are here
├── AGENT.md                      ← root operating contract (every agent reads this)
├── CLAUDE.md                     ← 3-line pointer to AGENT.md
├── _tiers.md                     ← inheritance model (Tier 1 / 2 / 3)
├── _skills-index.md              ← complete skill registry, 18 skills
├── _map.md                       ← navigation map
│
├── tier-1-global/                ← universal: everything inherits this
│   ├── conventions/                style-guide, token-efficiency, skill-author rules
│   ├── context/                    tier0 always-load, tier1-current working context
│   ├── checklists/                 session-start, era transitions, model-routing
│   └── skills-core/                request-router + 6 session infrastructure skills
│
├── tier-2-capabilities/          ← workhorse skills: load when the task calls for them
│   ├── skills/                     13 skills (6 cognitive modes + 5 analytical + 2 domain)
│   └── templates/                  lineage-record, quality-gates, token-budget
│
├── tier-3-shells/                ← project scaffolds: pick one per deliverable
│   ├── slide-shell/                presentation deck (keyboard nav, speaker notes, fullscreen)
│   ├── scroll-shell/               data-storytelling page (scroll animations, sliders, charts)
│   ├── mission-control/            dashboard (grid layout, RAG status, sparklines, role filter)
│   └── course-shell/               sequential lessons (gating, quizzes, progress tracking)
│
├── code/                         reference implementations (cache_key.py, schema_validator.py, etc.)
├── scripts/                      build-manifest, verify-integrity, verify-origin
├── hooks/                        git hooks (pre-commit/no-em-dashes, post-session/append-state)
└── docs/                         FIELD-GUIDE.md and publication docs
```

## What you get

**21 skills** organized by tier, every one a pointer file under 80 lines that dispatches to richer reference material on demand:

| Tier | Count | Skills |
|---|---|---|
| **1 -- Session infrastructure** | 9 | request-router, context-loader, token-economist, engagement-bootstrap, quality-gate, pattern-promoter, provenance-check, agent-panel-planning, agent-panel-review |
| **2 -- Cognitive modes** | 7 | parallel-lens-synthesis, consequence-simulation, cross-domain-translation, convergence-detection, detached-judgment, simulation-to-action-bridge, nod-protocol |
| **2 -- Analytical capabilities** | 5 | ultra-think, pressure-test, code-audit, autoresearch, skill-creator |
| **2 -- Domain capabilities** | 2 | viz, stakeholder-mapping |

**4 shells** for the most common deliverable types: open `index.html` in a browser, edit content, deploy as static HTML.

**A complete framework** (the field guide) explaining why the kit is structured this way, what each pattern does, and when not to use AI at all.

## Install

### Option A: Drop into an existing project

```bash
# Clone next to your project
git clone https://github.com/cameronpsutcliff/compound-ai-operating-standards.git .compound-ai

# Hand the kit to your agent
echo "Read .compound-ai/AGENT.md and follow the session-start checklist." | claude
```

The agent reads `AGENT.md`, walks the tier structure, and is operational in under a minute.

### Option B: Use the agent-facing handoff

For any agent (Claude Code, Codex, Cursor, Aider, Continue.dev), paste this prompt:

```
You are about to work with the Compound AI Operating Standards kit
at <path-to-kit>. Read these files in order:

  1. AGENT.md (root operating contract)
  2. _tiers.md (the inheritance model)
  3. _skills-index.md (full skill registry)
  4. tier-1-global/checklists/session-start.md (the bootstrap routine)
  5. tier-1-global/skills-core/request-router/SKILL.md

After loading, you have access to 18 skills. The request-router will
auto-dispatch based on what I ask. For deliverables, pick a shell from
tier-3-shells/.

Confirm you've loaded the kit by stating which skills are available
and which shell you'd recommend for [my project type].
```

### Option C: Use as a reference

If you don't want to install anything, the field guide explains the patterns and you can adopt them piecemeal. See [cameronsutcliff.com/compound-ai/field-guide](https://cameronsutcliff.com/compound-ai/field-guide).

## How it works

1. **You ask an agent for something.** "Pressure-test this plan", "what chart for this data", "map stakeholders for this initiative".
2. **The request-router matches your language to a skill** (see `tier-1-global/skills-core/request-router/SKILL.md` for the routing table).
3. **The skill loads, runs, and returns a structured output.** Every skill ships with an output template, so results are consistent.
4. **For deliverables, you pick a shell from `tier-3-shells/`** and fill in the content. The interactivity, navigation, theming, and progress tracking are already wired.

The compounding part: every session that runs through this kit reinforces the same patterns. Outputs accumulate in `STATE.md` and `session-log.md`. Patterns that prove themselves get promoted via `pattern-promoter`. The system gets cheaper and more reliable the longer it runs.

## What this kit is NOT

- **Not a prompt library.** The skills are reasoning scaffolds, not pre-written prompts.
- **Not vendor-specific.** Works with any agent that reads `AGENT.md` (or `CLAUDE.md`, which routes to AGENT.md).
- **Not a framework that requires buy-in.** Pick the tiers and skills you need; ignore the rest.
- **Not a replacement for thinking.** The skills change *how* you reason; they don't replace the work of reasoning.

## Versioning

This is **v2.2.0**. Minor version bump from v2.1.0 to add `agent-panel-planning` (Tier 1), the upstream planning sibling of `agent-panel-review`. Router gained Panel Offer Triggers. Field guide split Chapter 31 into Planning (Ch 31) and Review (Ch 32); "Before and After" is now Ch 33. The v2.0.0 line is the major-version anchor: directory structure changed (tier-based hierarchy replaces flat layout) and the skill count grew from 6 to 18; v2.1.0 took it to 20; v2.2.0 takes it to 21.

See `releases/` for full version history.

## License

- **Documentation:** CC BY 4.0
- **Code:** Apache 2.0
- **Origin:** Compound AI Operating Standards by Cameron Sutcliff

Cite the canonical source when you fork or extend: `https://cameronsutcliff.com/compound-ai`

## Provenance verification

Every release includes a manifest with SHA256 checksums. To verify your local copy matches the canonical release:

```bash
./scripts/verify-origin.py --online
```

Returns `VERIFIED` if the local manifest matches the canonical website manifest.

## Getting help

- **Field guide questions:** read [cameronsutcliff.com/compound-ai/field-guide](https://cameronsutcliff.com/compound-ai/field-guide)
- **Bug reports / requests:** open an issue on [GitHub](https://github.com/cameronpsutcliff/compound-ai-operating-standards/issues)
- **Pattern contributions:** PR welcome. Every promoted pattern needs a Field Guide reference and a working skill or shell.

---

*Compound AI Operating Standards: operating layer for AI work that accumulates instead of evaporates.*
