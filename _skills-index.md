# Skills Index
# Compound AI Operating Standards v2.0.0
# Source: cameronsutcliff.com/compound-ai | License: Apache 2.0

Load this file at session start. It is the complete capability registry. Eighteen skills total, organized by tier.

---

## Tier 1 — Session Infrastructure (7 skills)

These run the session. Load at session start; the `request-router` then handles dispatch.

| Skill | Trigger | Pointer | Status |
|---|---|---|---|
| **request-router** | Load at session start. Auto-routes any request to the right skill. | `tier-1-global/skills-core/request-router/SKILL.md` | active |
| context-loader | "load context", "what should I read", "start session" | `tier-1-global/skills-core/context-loader/SKILL.md` | active |
| token-economist | "token audit", "optimize context", "reduce cost" | `tier-1-global/skills-core/token-economist/SKILL.md` | active |
| engagement-bootstrap | "new project", "bootstrap this", "set up the project" | `tier-1-global/skills-core/engagement-bootstrap/SKILL.md` | active |
| quality-gate | "quality check", "validate this output", "is this ready" | `tier-1-global/skills-core/quality-gate/SKILL.md` | active |
| pattern-promoter | "promote this pattern", "save this lesson", "make this reusable" | `tier-1-global/skills-core/pattern-promoter/SKILL.md` | active |
| provenance-check | "verify origin", "check provenance", "is this the official version" | `tier-1-global/skills-core/provenance-check/SKILL.md` | active |

---

## Tier 2 — Cognitive Modes (6 skills)

Change HOW you reason. The router auto-selects based on request patterns.

| Skill | When the router fires it | Pointer | Status |
|---|---|---|---|
| **parallel-lens-synthesis** | "multiple perspectives", "steelman", "red-team", "debate this" | `tier-2-capabilities/skills/parallel-lens-synthesis/SKILL.md` | active |
| **consequence-simulation** | "what could go wrong", "premortem", "stress test", "simulate" | `tier-2-capabilities/skills/consequence-simulation/SKILL.md` | active |
| **cross-domain-translation** | "explain to [audience]", "translate for", "make accessible" | `tier-2-capabilities/skills/cross-domain-translation/SKILL.md` | active |
| **convergence-detection** | "common thread", "root cause", "what connects these" | `tier-2-capabilities/skills/convergence-detection/SKILL.md` | active |
| **detached-judgment** | "devil's advocate", "base rate", "am I being objective" | `tier-2-capabilities/skills/detached-judgment/SKILL.md` | active |
| **simulation-to-action-bridge** | "what should we do", "next steps", "OODA", "make this actionable" | `tier-2-capabilities/skills/simulation-to-action-bridge/SKILL.md` | active |

---

## Tier 2 — Analytical Capabilities (5 skills)

The workhorses. Load when the task calls for them.

| Skill | When to use | Pointer | Status |
|---|---|---|---|
| **ultra-think** | Complex decisions; multi-angle analysis; "think deeply about" | `tier-2-capabilities/skills/ultra-think/SKILL.md` | active |
| **pressure-test** | Adversarial review with CEO lenses + GSTACK scope modes. "Pressure test this", "critique this", "rip this apart" | `tier-2-capabilities/skills/pressure-test/SKILL.md` | active |
| **code-audit** | Dependency audit, dead code, coverage gaps, security review | `tier-2-capabilities/skills/code-audit/SKILL.md` | active |
| **autoresearch** | Structured research on a topic with cited sources | `tier-2-capabilities/skills/autoresearch/SKILL.md` | active |
| **skill-creator** | Build new skills that follow this kit's conventions | `tier-2-capabilities/skills/skill-creator/SKILL.md` | active |

---

## Tier 2 — Domain Capabilities (2 skills)

| Skill | When to use | Pointer | Status |
|---|---|---|---|
| **viz** | Chart selection, dashboard design, viz critique. Grounded in Few (Perceptual Edge) and Kriebel (Makeover Monday). | `tier-2-capabilities/skills/viz/SKILL.md` | active |
| **stakeholder-mapping** | Map stakeholders for an initiative. Influence-interest grid + engagement strategy. | `tier-2-capabilities/skills/stakeholder-mapping/SKILL.md` | active |

---

## Pointer Skill Rule

Every `SKILL.md` stays under 80 lines. Deep references live in `skills/<name>/reference/` and load on demand. Skills are tools, not documentation.
