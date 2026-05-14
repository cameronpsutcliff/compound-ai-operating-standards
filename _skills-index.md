# Skills Index
# Compound AI Operating Standards v2.2.0
# Source: cameronsutcliff.com/compound-ai | License: Apache 2.0

Load this file at session start. It is the complete capability registry. Twenty-one skills total, organized by tier.

---

## Tier 1 -- Session Infrastructure (9 skills)

These run the session. Load at session start; the `request-router` then handles dispatch.

| Skill | Trigger | Pointer | Status |
|---|---|---|---|
| **request-router** | Load at session start. Auto-routes any request to the right skill; offers panels on operator-humility signals. | `tier-1-global/skills-core/request-router/SKILL.md` | active |
| context-loader | "load context", "what should I read", "start session" | `tier-1-global/skills-core/context-loader/SKILL.md` | active |
| token-economist | "token audit", "optimize context", "reduce cost" | `tier-1-global/skills-core/token-economist/SKILL.md` | active |
| engagement-bootstrap | "new project", "bootstrap this", "set up the project" | `tier-1-global/skills-core/engagement-bootstrap/SKILL.md` | active |
| quality-gate | "quality check", "validate this output", "is this ready" | `tier-1-global/skills-core/quality-gate/SKILL.md` | active |
| pattern-promoter | "promote this pattern", "save this lesson", "make this reusable" | `tier-1-global/skills-core/pattern-promoter/SKILL.md` | active |
| provenance-check | "verify origin", "check provenance", "is this the official version" | `tier-1-global/skills-core/provenance-check/SKILL.md` | active |
| **agent-panel-planning** | "plan this with the panel", "converge on a plan", "split this work across agents", "who should own what". Independent plans, cross-suggestions, voting, strength-matched task split. | `tier-1-global/skills-core/agent-panel-planning/SKILL.md` | active |
| **agent-panel-review** | "set up a panel", "convene a panel", "multi-agent review", "second opinion". Independent-first-pass, structured-critique, no-ego convergence. | `tier-1-global/skills-core/agent-panel-review/SKILL.md` | active |

---

## Tier 2 -- Cognitive Modes (7 skills)

Change HOW you reason. The router auto-selects based on request patterns. New in v2.1.0: each cognitive mode ships a `reference/protocol.md` that operationalizes the skill end-to-end. The seventh skill, `nod-protocol`, fills the adversarial reasoning gap identified during the v2.0.0 review.

| Skill | When the router fires it | Pointer | Status |
|---|---|---|---|
| **parallel-lens-synthesis** | "multiple perspectives", "steelman", "red-team", "debate this" | `tier-2-capabilities/skills/parallel-lens-synthesis/SKILL.md` | active |
| **consequence-simulation** | "what could go wrong", "premortem", "stress test", "simulate" | `tier-2-capabilities/skills/consequence-simulation/SKILL.md` | active |
| **cross-domain-translation** | "explain to [audience]", "translate for", "make accessible" | `tier-2-capabilities/skills/cross-domain-translation/SKILL.md` | active |
| **convergence-detection** | "common thread", "root cause", "what connects these" | `tier-2-capabilities/skills/convergence-detection/SKILL.md` | active |
| **detached-judgment** | "devil's advocate", "base rate", "am I being objective" | `tier-2-capabilities/skills/detached-judgment/SKILL.md` | active |
| **simulation-to-action-bridge** | "what should we do", "next steps", "OODA", "make this actionable" | `tier-2-capabilities/skills/simulation-to-action-bridge/SKILL.md` | active |
| **nod-protocol** | "play devil's advocate", "argue the opposite", "construct the opposite case", "NOD this". Five-gate opposite-construction with signing test. | `tier-2-capabilities/skills/nod-protocol/SKILL.md` | active |

---

## Tier 2 -- Analytical Capabilities (5 skills)

The workhorses. Load when the task calls for them.

| Skill | When to use | Pointer | Status |
|---|---|---|---|
| **ultra-think** | Complex decisions; multi-angle analysis; "think deeply about" | `tier-2-capabilities/skills/ultra-think/SKILL.md` | active |
| **pressure-test** | Adversarial review with CEO lenses + GSTACK scope modes. "Pressure test this", "critique this", "rip this apart" | `tier-2-capabilities/skills/pressure-test/SKILL.md` | active |
| **code-audit** | Dependency audit, dead code, coverage gaps, security review | `tier-2-capabilities/skills/code-audit/SKILL.md` | active |
| **autoresearch** | Structured research on a topic with cited sources | `tier-2-capabilities/skills/autoresearch/SKILL.md` | active |
| **skill-creator** | Build new skills that follow this kit's conventions | `tier-2-capabilities/skills/skill-creator/SKILL.md` | active |

---

## Tier 2 -- Domain Capabilities (2 skills)

| Skill | When to use | Pointer | Status |
|---|---|---|---|
| **viz** | Chart selection, dashboard design, viz critique. Grounded in Few (Perceptual Edge) and Kriebel (Makeover Monday). | `tier-2-capabilities/skills/viz/SKILL.md` | active |
| **stakeholder-mapping** | Map stakeholders for an initiative. Influence-interest grid + engagement strategy. | `tier-2-capabilities/skills/stakeholder-mapping/SKILL.md` | active |

---

## v2.2.0 changes

- **Added `agent-panel-planning`** (Tier 1). Independent-plans panel protocol with element-level voting, concession-with-attribution + path-forward-for-others, reconvene, ratification, and strength-matched task split. Pairs upstream of `agent-panel-review`.
- **Router gained Panel Offer Triggers section.** New behavior: when operator humility signals fire ("I'm not sure", "high-stakes", "want a second opinion", "test my framing"), the agent OFFERS a panel and the operator opts in. Distinct from the existing routing table which silently invokes.
- **Field guide:** Chapter 31 split into Ch 31 (Planning) + Ch 32 (Review). Original Ch 31 content is now Ch 32; "Before and After" is now Ch 33.

## v2.1.0 changes

- **Added `agent-panel-review`** (Tier 1). Independent-first-pass panel protocol with sealed Stage 2 and four-cell critique format.
- **Added `nod-protocol`** (Tier 2 cognitive). Five-gate opposite-construction with signing test. Fills the adversarial reasoning gap.
- **Operationalized all 6 existing cognitive modes** with `reference/protocol.md` files (step procedure, output template, worked example, anti-patterns).
- **Router updated** with new triggers for both new skills and a new compound-request entry for high-stakes deliverables.

---

## Pointer Skill Rule

Every `SKILL.md` stays under 80 lines. Deep references live in `skills/<name>/reference/` and load on demand. Skills are tools, not documentation.
