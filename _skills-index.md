# Skills Index
# Compound AI Operating Standards
# Source: cameronsutcliff.com/compound-ai | License: Apache 2.0

This file is the complete capability registry for any project using this kit.
Load it at session start. It tells you what this system can do and how to invoke it.

---

## Session Infrastructure Skills

These skills manage how the session runs — context, quality, cost, and provenance.

| Skill | Trigger | Pointer | Status |
|---|---|---|---|
| **request-router** | Load at session start. Routes any request to the right cognitive mode. | `skills/request-router/SKILL.md` | active |
| context-loader | "load context", "what should I read", "start session" | `skills/context-loader/SKILL.md` | active |
| token-economist | "token audit", "optimize context", "reduce cost", "why is this slow" | `skills/token-economist/SKILL.md` | active |
| engagement-bootstrap | "new project", "bootstrap this", "set up the project" | `skills/engagement-bootstrap/SKILL.md` | active |
| quality-gate | "quality check", "validate this output", "ship check", "is this ready" | `skills/quality-gate/SKILL.md` | active |
| pattern-promoter | "promote this pattern", "save this lesson", "make this reusable" | `skills/pattern-promoter/SKILL.md` | active |
| provenance-check | "verify origin", "check provenance", "is this the official version" | `skills/provenance-check/SKILL.md` | active |

---

## Cognitive Mode Skills

These six skills change HOW you reason — not just what you produce. The request-router
selects the right one automatically based on what the user is asking for.

| Skill | What it does | When the router fires it | Pointer |
|---|---|---|---|
| **parallel-lens-synthesis** | Run independent reasoning threads from multiple vantage points, then synthesize | "multiple perspectives", "steelman", "red-team", "debate this" | `skills/parallel-lens-synthesis/SKILL.md` |
| **consequence-simulation** | Simulate outcomes before committing — premortem, second-order effects, failure modes | "what could go wrong", "premortem", "stress test", "simulate" | `skills/consequence-simulation/SKILL.md` |
| **cross-domain-translation** | Re-encode an idea for a different audience or register without losing fidelity | "explain to [audience]", "translate for", "make accessible", "exec summary" | `skills/cross-domain-translation/SKILL.md` |
| **convergence-detection** | Surface recurring patterns or shared root causes across disparate inputs | "common thread", "root cause", "what connects these", "why does this keep happening" | `skills/convergence-detection/SKILL.md` |
| **detached-judgment** | Evaluate evidence on its own terms — calibrated confidence, no advocacy bias | "devil's advocate", "base rate", "am I being objective", "weight the evidence" | `skills/detached-judgment/SKILL.md` |
| **simulation-to-action-bridge** | Convert analysis into sequenced, ownable decisions with clear initiative assignment | "what should we do", "next steps", "who owns this", "OODA", "make this actionable" | `skills/simulation-to-action-bridge/SKILL.md` |

---

## Pointer Skill Rule

Every `SKILL.md` stays under 80 lines. Deep references stay in Field Guide chapters.
Skills are tools, not documentation. Load them, use them, move on.
