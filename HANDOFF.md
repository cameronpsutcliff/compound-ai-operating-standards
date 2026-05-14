# Agent Handoff
# Compound AI Operating Standards v2.3.0
# Source: cameronsutcliff.com/compound-ai | License: Apache 2.0

This is the document you hand to a fresh agent (Claude, Codex, Cursor, Aider, Continue, or any other) to get it operational on this kit in under two minutes.

---

## Drop-in prompt

Copy everything between the rules and paste into a new agent session:

---

You are about to use the **Compound AI Operating Standards kit v2.3.0** at this path. The kit is a tiered operating layer with 21 skills and 4 project shells. Your job is to load it correctly, then help me work.

**Read these files in this exact order:**

1. `AGENT.md`: root operating contract (what this kit is, what it isn't, governance rules)
2. `_tiers.md`: the inheritance model (Tier 1 / 2 / 3)
3. `_skills-index.md`: complete skill registry with triggers
4. `tier-1-global/checklists/session-start.md`: the bootstrap routine
5. `tier-1-global/skills-core/request-router/SKILL.md`: the routing table that matches my requests to skills
6. `tier-1-global/context/tier0.md`: always-load context (project name, phase, primary constraint)

**After loading, confirm by stating:**

- The 9 Tier 1 infrastructure skills you have access to (request-router + 6 session skills + agent-panel-planning + agent-panel-review)
- The 12 Tier 2 capability skills you have access to (7 cognitive modes, 5 analytical, 2 domain)
- The router has TWO modes: the routing table (matches invoke a skill silently) and the Panel Offer Triggers section (humility signals OFFER a panel, do not auto-invoke). Acknowledge both.
- The 4 Tier 3 shells available (slide, scroll, mission-control, course)
- Which shell you'd recommend for the project at hand (if I've told you the project type. If not, ask.)

**Operating rules:**

1. Every request I make: first check the `request-router` routing table. If a skill matches, load it from the matching tier and follow its protocol.
2. Pointer skills are under 80 lines. They dispatch to `reference/` subfolders. Load those references only when the skill says to.
3. Compound requests (analysis + decision + action) trigger sequenced skills. See request-router's "Compound requests" section.
4. `AGENT.md` is the canonical operating contract. `CLAUDE.md` exists only as a 3-line pointer to AGENT.md, never read CLAUDE.md for content.
5. Update `STATE.md` and append to `session-log.md` at the end of every non-trivial session.
6. Confirm before destructive operations, force pushes, billing changes, external publishing, or auth/secret changes.

**Begin by reading the files in the order above. When done, report what you've loaded and ask me what I'm working on.**

---

## What the agent sees after running this

```
LOADED COMPOUND AI v2.3.0
═════════════════════════

Tier 1: Session infrastructure (9 skills):
  ✓ request-router (active, auto-routing + panel-offer mode enabled)
  ✓ context-loader
  ✓ token-economist
  ✓ engagement-bootstrap
  ✓ quality-gate
  ✓ pattern-promoter
  ✓ provenance-check
  ✓ agent-panel-planning
  ✓ agent-panel-review

Tier 2: Cognitive modes (7 skills):
  ✓ parallel-lens-synthesis
  ✓ consequence-simulation
  ✓ cross-domain-translation
  ✓ convergence-detection
  ✓ detached-judgment
  ✓ simulation-to-action-bridge
  ✓ nod-protocol

Tier 2: Analytical capabilities (5 skills):
  ✓ ultra-think
  ✓ pressure-test
  ✓ code-audit
  ✓ autoresearch
  ✓ skill-creator

Tier 2: Domain capabilities (2 skills):
  ✓ viz
  ✓ stakeholder-mapping

Tier 3: Shells (4):
  ✓ slide-shell (presentation deck)
  ✓ scroll-shell (data-storytelling page)
  ✓ mission-control (dashboard)
  ✓ course-shell (sequential lessons)

Routing: active. What are you working on?
```

If the agent's response doesn't look like the above, restart and check that the file paths are correct relative to the agent's working directory.

## Tested with

This handoff has been validated against:
- **Claude Code**: reads `CLAUDE.md` first (which routes to AGENT.md), then proceeds through the checklist
- **Claude API** (custom integrations): reads `AGENT.md` natively
- **Codex CLI**: reads `AGENT.md` natively (Codex's standard convention)
- **Cursor**: reads `AGENT.md` via its rules file mechanism
- **Aider**: reads `CONVENTIONS.md` natively; symlink `AGENT.md` to `CONVENTIONS.md` for Aider projects

If your agent reads a different file convention (e.g. `INSTRUCTIONS.md`, `.cursorrules`), create that as a symlink or 3-line pointer to `AGENT.md` and you're done.

## Custom project handoff

For a project that uses this kit, write a project-specific handoff that subclasses this one:

```markdown
# Project Handoff: [Project Name]

You are working on [project] which uses Compound AI Operating Standards v2.3.0.

Read these files in order:
1. AGENT.md (root)
2. Project.md (project-specific overview: what this is, who uses it, current state)
3. _tiers.md, _skills-index.md, session-start.md, request-router (per HANDOFF.md)
4. STATE.md (live state)

Project-specific context:
- Tech stack: [fill]
- Current phase: [Demo / Ramp-up / Durable]
- Primary constraint: [fill]
- Key skills for this project: [name 2-3 from the registry]

Begin by loading the files above, then ask me what's next.
```

This is the pattern used in `tier-1-global/checklists/new-project.md` for the `engagement-bootstrap` skill.

## Recovery

If the agent gets confused or drifts:

```
Reset to the Compound AI Operating Standards baseline:
- Re-read AGENT.md
- Re-load _skills-index.md and request-router
- Tell me what skills are active
```

This recovers the agent's state without requiring a full session restart.
