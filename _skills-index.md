# Skills Index
# Compound AI Operating Standards v2.5.0
# Source: cameronsutcliff.com/compound-ai | License: Apache 2.0

Load this file at session start. It is the complete capability registry. Twenty-three skills total, organized by tier.

---

## Tier 1 -- Session Infrastructure (11 skills)

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
| **release-captain** | "ship gate", "release captain", "is this ready to ship", "pre-release check", "verify the release". Ten-step ship gate including verify-integrity, verify-origin, manifest-version reconciliation, line-count budget, public-download HTTP checks, and screenshots. | `tier-1-global/skills-core/release-captain/SKILL.md` | active |
| **adoption-captain** | "adopt this kit", "install into my current repo", "optimize this existing agent", "use these techniques going forward", "do not break my stack". Eight-stage protocol for adopting the kit into an existing project: discover host context, preserve host rules, inventory kit, map skills, propose plan, apply additively, validate non-breakage, commit kit awareness to host agent's instruction surfaces. | `tier-1-global/skills-core/adoption-captain/SKILL.md` | active |

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

## v2.5.0 changes

- **Added `adoption-captain`** (Tier 1, session infrastructure). The inbound mirror of `release-captain`. Eight-stage protocol for adopting the kit into an existing project: discover host context (existing agent files, package files, test/build/lint commands, state logs); preserve host rules (Preserve / Add / Modify / Defer / Conflict map); inventory kit surface; map kit to stack (adopt now / adapt / defer / skip / conflict per skill); propose phased plan; apply additively under `.compound-ai/`; validate with host project's own tests; document and **commit kit awareness to host agent's instruction surfaces** (CLAUDE.md, AGENT.md, AGENTS.md, .cursorrules, etc.) via marker-bounded sections so future sessions inherit the kit without re-discovery. Ships with eight reference files including the load-bearing `memory-commit-protocol.md`. Tier 1 skill count: 10 → 11. Total skills: 22 → 23.
- **New top-level `ADOPT.md`**: entry point for adopting the kit into existing projects. Companion to `HANDOFF.md` which serves new-project bootstrap. Includes the drop-in prompt for adopting agents and the full description of the eight-stage protocol.
- **`HANDOFF.md` forks**: explicit "new project vs existing project" branch at the top. New projects continue with `HANDOFF.md` + `engagement-bootstrap`; existing projects route to `ADOPT.md` + `adoption-captain`.
- **Router updated**: new fast-path trigger row for `adoption-captain` ("adopt this kit", "install into my current repo", "do not break my stack", "migrate my agent instructions"). New "two-mode bootstrap distinction" section disambiguates new-project vs existing-project entry points.
- **Codex polish from v2.4.0 critique**: INSTALL.md version bumped (was stuck at v2.3.0); skill-count references updated throughout README/AGENT.md (was reporting 18 in places after the kit grew to 22, now 23); AGENT.md "Tier 2 = 12 skills" typo fixed (the list contains 14, broken into 7 cognitive + 5 analytical + 2 domain); "pointer skills under 80 lines" rewording to "under 100 lines, target 80" matches the actual budget enforced by release-captain Step 9.

## v2.4.0 changes

- **Added `release-captain`** (Tier 1, session infrastructure). The ten-step ship gate that would have caught every failure Codex flagged in v2.3.1. Steps: clean unzip, `verify-integrity.py`, `verify-origin.py --online`, manifest-version reconciliation, SHA256SUMS coverage, field guide badge match, releaseUrl resolves, all public downloads return 200, `SKILL.md` line-count budget, screenshots. Ships with `reference/checklist.md`, `reference/verification-protocol.md` (exact commands), `reference/output-template.md` (structured SHIP/BLOCK report), and `reference/origin.md` (credits Codex's v2.3.1 cross-feedback). Tier 1 skill count: 9 → 10. Total skills: 21 → 22.
- **Router updated**: new fast-path trigger row for `release-captain` ("ship gate", "release captain", "pre-release check"). New compound-request entry: "Pre-ship release verification" runs `release-captain` (with optional `agent-panel-review` upstream if the deliverable also warrants editorial review).

## v2.3.2 changes

- **Discipline pass after Codex's v2.3.1 critique.** SKILL.md files that drifted over 100 lines are pushed back under budget by relocating prose into `reference/` files. The router split into three reference files (`compound-requests.md`, `panel-offer-threshold.md`, `router-rationale.md`); `agent-panel-review`, `agent-panel-planning`, and `stakeholder-mapping` SKILL.md files trimmed; stakeholder-mapping's protocol moved to its own `reference/protocol.md`.
- **ZIP includes historical release notes**: v2.3.1's ZIP build dropped `releases/v2.1.0|v2.2.0|v2.3.0/RELEASE-NOTES.md`, breaking `verify-integrity.py` on clean extract. Fixed by changing the build to retain release-notes-only history.
- **Versioned manifests**: `compound-ai/manifest.json` is now the latest stable; each release has its own immutable `compound-ai/releases/<version>/manifest.json`. `verify-origin.py --online` works against either.
- **Scorecard rubric requires `Verification performed:` opening line**: prevents the scorecard from praising package design while the package fails on clean extract. Dimensions 4 and 5 cap at 75 if verification is skipped.
- **Website fixes**: field guide reader version badge and `releaseUrl` constant both pointed at v1.0.0; now bound to the current release. Field guide markdown SHA added to `SHA256SUMS`.

## v2.3.1 changes

- **`agent-panel-review` gains `scorecard-rubric.md`**: ten-dimension quantitative evaluation rubric with 0-100 scoring, evidence-cited notes, composite score, and dual grade (strategy vs artifact production). Heavier alternative to the four-cell template; use for high-stakes panels, standalone single-deliverable evaluation, or post-mortems. The ten dimensions are Thesis sharpness, Audience layering, Substance density, Portability/vendor-neutrality, Package design, Reference artifact/immediate utility, Audience signaling, Discipline, Originality, Critique-readiness.

## v2.3.0 changes

- **Refined `request-router`**: Panel Offer Triggers section replaced with a 5-criteria judgment + soft-offer pattern. Distinguishes T1 normal collab ("what do you think?") from T2 deeper solo collab ("help me think through this") from T3 council-warranted requests. Most humility signals now soft-offer (answer + one-sentence panel mention), not full-derail panel-offer prompts.
- **`agent-panel-review` gains `merge-framework.md`**: per-dimension scoring procedure for Stage 5 with operator-bias check (two questions before locking each dimension) to prevent the operator's instinct from masquerading as panel signal.
- **`agent-panel-review` gains `loop-4-recovery.md`**: five common causes of panel failure at loop 4 (too-broad question, hidden assumption, wrong composition, scope creep, fatigue) with recovery moves per cause and the "ship the imperfect" rule.
- **`agent-panel-planning/reference/when-to-convene.md` gains standing-vs-convened sub-section**: trade-off framing for permanent multi-agent operating structures vs per-deliverable convening. Adam Federman credited via citation in `_citations.md` registry.
- **New top-level `INSTALL.md`**: walks operators through the multi-agent question; pitches free-tier setups (Claude/GPT/Gemini free tiers, Aider+Ollama, same-model panels) for operators with only one agent.
- **New top-level `_citations.md`**: canonical attribution registry. Field guide reader resolves `[^key]` markers to superscript tooltips with Name + Contribution on hover.
- **Field guide foreword gains audience callout**: who this manual is for and who it is not for.

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
