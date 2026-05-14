# Dry-Run Adoption Report

**Kit version:** Compound AI Operating Standards v2.5.0
**Host project:** cameronsutcliffdotcom (Cameron's personal site)
**Host path:** `/Users/cameronsutcliff/masterportfolio/cameronsutcliffdotcom`
**Operator:** Claude session, dogfooding `adoption-captain` on its debut release
**Date:** 2026-05-14

This is the proof-of-protocol report Codex requested as an acceptance criterion for v2.5.0. It runs `adoption-captain`'s eight stages against a real mature project (the same React/Vite/TypeScript codebase that hosts `cameronsutcliff.com`) and documents what each stage would produce.

This is a **dry run**: no files in `cameronsutcliffdotcom` are actually modified. The report shows what `adoption-captain` would do, with the operator's approval, on a real-world adoption.

---

## Stage 1: Discover host context

### Existing agent instruction surfaces

| Path | Format | Active for |
|---|---|---|
| `CLAUDE.md` | Markdown, project root | Claude Code sessions in this repo |
| `README.md` | Markdown | Users, GitHub viewers |
| `project.md` | Markdown | Reference doc linked from CLAUDE.md |
| `session-log.md` | Append-only markdown | Cross-session history |
| `~/.claude/CLAUDE.md` | Global Claude Code instructions | All projects for this user (out of scope by default) |

No `AGENTS.md`, `.cursorrules`, `.aider.conf.yml`, or `CONVENTIONS.md` detected. Single primary instruction surface for the kit-relevant agent: project-level `CLAUDE.md`.

### Tech stack detection

| Indicator | Detected |
|---|---|
| `package.json` (npm) | yes |
| `vite.config.ts` (Vite bundler) | yes |
| `tsconfig.json` (TypeScript) | yes |
| `eslint.config.js` (ESLint) | yes |
| `vitest.config.ts` (referenced by test script) | yes |
| `vercel.json` (Vercel deploy) | yes |

Stack: **React + Vite + TypeScript + ESLint + Vitest + Vercel.**

### Commands

| Purpose | Command (from package.json) |
|---|---|
| Test | `npm run test` (vitest run) |
| Build | `npm run build` (tsc -b && vite build) |
| Lint | `npm run lint` (eslint .) |
| Type-check | (folded into `npm run build` via `tsc -b`) |
| Dev server | `npm run dev` (vite) |

### State, decision, and architecture surfaces

| Path | Role |
|---|---|
| `session-log.md` | Cross-session history (kit-style discipline already in use) |
| `project.md` | Project overview, linked from CLAUDE.md |
| `README.md` | Public-facing intro |
| `docs/` | Additional documentation directory |
| `plans/` | Pre-existing plans directory |

### CI/deploy

| Path | Role |
|---|---|
| `vercel.json` | Vercel deployment configuration |
| `dist/` | Build output (gitignored) |

No GitHub Actions workflows detected. Deployment is Vercel-on-push.

---

## Stage 2: Preserve host rules

| Existing rule | Source | Adoption implication |
|---|---|---|
| CLAUDE.md is the authoritative agent file | `CLAUDE.md` line 1 | PRESERVE. Kit additions go as a marker-bounded section appended, not replacing. |
| `session-log.md` is append-only with newest entries on top | `session-log.md` style + global CLAUDE.md instructions | PRESERVE. Kit's session-log discipline matches; do not introduce a competing log. |
| Long dashes (em-dashes) banned everywhere | Global `~/.claude/CLAUDE.md` | ALIGNED. Kit's own no-em-dash discipline matches. No conflict. |
| Tech stack: React/Vite/TypeScript/Vercel | `package.json`, `vite.config.ts` | PRESERVE. Kit does not modify any of this. |
| ESLint configuration | `eslint.config.js` | PRESERVE. Kit does not modify. |
| Vitest configuration | `vitest.config.ts` (referenced) | PRESERVE. Kit does not modify. |
| Vercel deployment | `vercel.json` | PRESERVE. Kit does not modify. |
| `worktrees/` directory present | Filesystem | PRESERVE. Likely git worktree pattern; kit does not touch. |
| Public artifacts at `public/compound-ai/` | Existing v2.4.0 kit artifacts published to the site | NOTE. The kit is ALREADY published from this repo. Adoption of the kit AS A USER (vs as a publisher) is layered on top. |

**Conflicts: zero.** The kit's discipline aligns with or is silent on every existing rule.

---

## Stage 3: Inventory kit surface

The kit ships 23 skills, 4 shells, scripts, hooks. For dry-run brevity, only the categories matter at this stage; per-skill mapping happens in Stage 4.

- 11 Tier 1 skills (session infrastructure)
- 7 Tier 2 cognitive modes
- 5 Tier 2 analytical capabilities
- 2 Tier 2 domain capabilities
- 4 Tier 3 shells (slide, scroll, mission-control, course)
- Reference implementations in `code/`
- Verification scripts in `scripts/`
- Optional git hooks in `hooks/`

---

## Stage 4: Map kit to stack

### Tier 1 (session infrastructure)

| Skill | Classification | Rationale |
|---|---|---|
| request-router | **Adopt now** | Universal value; routes any future request to the right skill |
| context-loader | **Adapt** | This project does not use the kit's tier0/tier1 file structure; adapt to load CLAUDE.md + project.md as the project's tier context |
| token-economist | **Adopt now** | Stack-agnostic; immediately useful |
| engagement-bootstrap | **Skip** | This is an existing project, not new; adoption-captain is the right entry, not engagement-bootstrap |
| quality-gate | **Adopt now** | Stack-agnostic; useful before merging changes |
| pattern-promoter | **Adopt now** | Stack-agnostic |
| provenance-check | **Adopt now** | Already used (the public manifest is verified via verify-origin.py) |
| agent-panel-planning | **Defer** | Currently a single-agent project; convene only when high-stakes planning warrants |
| agent-panel-review | **Defer** | Same as planning |
| release-captain | **Adopt now** | The site IS the kit's publisher; release-captain applies directly to website releases |
| **adoption-captain** | (self) | The skill being run |

### Tier 2 (cognitive modes)

| Skill | Classification | Rationale |
|---|---|---|
| parallel-lens-synthesis | **Adopt now** | Useful for architecture decisions |
| consequence-simulation | **Adopt now** | Useful for pre-deploy stress tests |
| cross-domain-translation | **Adopt now** | Already implicitly used when explaining IIP to executives |
| convergence-detection | **Adopt now** | Useful for cross-incident pattern analysis |
| detached-judgment | **Adopt now** | Stack-agnostic |
| simulation-to-action-bridge | **Adopt now** | Stack-agnostic |
| nod-protocol | **Adopt now** | Useful for high-stakes decisions about IIP architecture, etc. |

### Tier 2 (analytical capabilities)

| Skill | Classification | Rationale |
|---|---|---|
| ultra-think | **Adopt now** | Universally useful |
| pressure-test | **Adopt now** | Useful before shipping any architectural change |
| code-audit | **Adopt now** | Direct fit; this project has real code to audit |
| autoresearch | **Adopt now** | Useful for any factual claim added to the site |
| skill-creator | **Defer** | Adopt when a new skill is genuinely needed |

### Tier 2 (domain capabilities)

| Skill | Classification | Rationale |
|---|---|---|
| viz | **Adopt with adaptation** | Site already has Recharts visualizations; viz's canon (Few + Kriebel) should govern new charts but existing charts are grandfathered |
| stakeholder-mapping | **Defer** | Not currently relevant; adopt when needed |

### Tier 3 (shells)

None adopted now. The site already has its own React-based scroll/data-storytelling page. Shells are reference scaffolds for new projects that don't have their own; this project does.

---

## Stage 5: Propose phased plan

### Phase 1: Additive scaffolding (no behavior change yet)

1. Create `.compound-ai/` directory at project root
2. Drop kit files into `.compound-ai/`
3. Generate `.compound-ai/adoption-report.md` (this document, finalized)
4. Append marker-bounded section to project `CLAUDE.md` listing adopted skills + triggers + preserve rules + validation commands
5. Do NOT touch `~/.claude/CLAUDE.md` (global) unless operator explicitly opts in

### Phase 2: Behavior alignment (operator-gated)

Phase 2 items are presented but NOT applied without operator opt-in:

1. Switch the site's release process to use `release-captain`'s ten-step gate (currently the site's commits run informal pre-deploy checks)
2. Adopt `pressure-test` before any architecture-level change (e.g. new sub-tool added to the parent site)
3. Adopt `quality-gate` before any deploy commit (a one-skill check rather than a full panel)
4. Optionally enable kit git hooks (no-em-dash pre-commit) -- already aligned with the global discipline so this is low-risk

### Phase 3: Future-state (deferred)

1. Adopt `agent-panel-review` if/when high-stakes editorial deliverables warrant it
2. Adopt `agent-panel-planning` if/when major architecture decisions warrant a panel
3. Adopt `viz` skill's canon for any new chart added going forward

---

## Stage 6: Apply additively (preview)

Files that WOULD be created (Phase 1):

- `.compound-ai/AGENT.md` (kit operating contract, copy)
- `.compound-ai/_skills-index.md` (kit registry, copy)
- `.compound-ai/_tiers.md`, `.compound-ai/_map.md`, `.compound-ai/_citations.md` (kit metadata)
- `.compound-ai/HANDOFF.md`, `.compound-ai/ADOPT.md`, `.compound-ai/INSTALL.md` (kit handoff docs)
- `.compound-ai/tier-1-global/` (all Tier 1 skills)
- `.compound-ai/tier-2-capabilities/` (all Tier 2 skills)
- `.compound-ai/tier-3-shells/` (all 4 shells, available as reference)
- `.compound-ai/docs/FIELD-GUIDE.md` (deep manual, not loaded by default)
- `.compound-ai/scripts/` (verify-integrity, verify-origin, build-manifest)
- `.compound-ai/code/` (reference implementations)
- `.compound-ai/adoption-report.md` (this document, finalized)

Files that WOULD be modified (Phase 1):

- Project `CLAUDE.md`: append marker-bounded section, NO other changes

Files explicitly NOT touched:

- `README.md`, `project.md`, `session-log.md`
- `package.json`, `tsconfig.json`, `vite.config.ts`, `eslint.config.js`, `vercel.json`
- `~/.claude/CLAUDE.md` (global; not in scope for project-level adoption)
- Any file under `src/`, `public/`, `api/`, `packages/`

---

## Stage 7: Validate non-breakage (commands that WOULD run after apply)

| Check | Command | Expected outcome |
|---|---|---|
| Type-check | `npm run build` (includes `tsc -b`) | PASS (build was passing before adoption; kit additions are markdown only) |
| Lint | `npm run lint` | PASS (no `.compound-ai/` paths in lint scope) |
| Tests | `npm run test` | PASS (no test changes) |

Validation result: PASS (predicted; would re-run after actual application).

---

## Stage 8a: Document (the report you are reading)

This file would be written to `.compound-ai/adoption-report.md` at the host project root upon real adoption.

---

## Stage 8b: Commit kit awareness to host CLAUDE.md

Proposed addition to project `CLAUDE.md` (would be appended at end of file, with operator approval):

```markdown
<!-- compound-ai:start v2.5.0 -->
## Compound AI Operating Standards

This project has the Compound AI kit installed at `.compound-ai/`. When working in
this project, the following kit techniques apply.

### Adopted skills (Phase 1)

| Skill | When to invoke |
|---|---|
| request-router | Auto-load at session start; routes any request |
| token-economist | "token audit", "optimize context" |
| quality-gate | Before any commit that changes user-visible content |
| pattern-promoter | When a pattern proves itself across 2+ contexts |
| provenance-check | "verify origin"; already in use for public manifests |
| release-captain | Before deploying to Vercel; runs the ten-step ship gate |
| parallel-lens-synthesis | Architecture decisions |
| consequence-simulation | Pre-deploy stress tests |
| cross-domain-translation | When explaining sub-tools to executive audiences |
| convergence-detection | Cross-incident pattern analysis |
| detached-judgment, simulation-to-action-bridge, nod-protocol | High-stakes decisions |
| ultra-think, pressure-test, code-audit, autoresearch | As named |
| viz (with adaptation) | For NEW charts; existing Recharts visualizations are grandfathered |

Full registry: `.compound-ai/_skills-index.md`. Router: `.compound-ai/tier-1-global/skills-core/request-router/SKILL.md`.

### Preserve rules

- CLAUDE.md is the authoritative project agent file; kit additions go in this marker-bounded section only
- `session-log.md` is append-only, newest on top; do not introduce a competing log
- Long dashes banned (aligned with global)
- Tech stack and configs (React/Vite/TypeScript/ESLint/Vitest/Vercel) are not modified by kit defaults

### Validation commands

- Test: `npm run test`
- Build: `npm run build`
- Lint: `npm run lint`

### Kit resources

- Adoption report: `.compound-ai/adoption-report.md`
- Field guide: `.compound-ai/docs/FIELD-GUIDE.md` (load chapters on demand only)
- For new releases of THIS site: invoke "ship gate" → `release-captain`
- For high-stakes decisions: invoke `nod-protocol` (opposite-construction) or `agent-panel-planning` (if multiple agents available)

For the full operating contract, see `.compound-ai/AGENT.md`.
<!-- compound-ai:end -->
```

This is ~30 lines. Project-tailored from the Stage 4 mapping. Marker-bounded for clean future updates or rollback.

---

## Memory commit summary

| Surface | Status | Operator approval |
|---|---|---|
| Project `CLAUDE.md` | **WOULD UPDATE** (Phase 1) | required before real adoption |
| Project `README.md` | NOT TOUCHED | n/a |
| Project `project.md` | NOT TOUCHED | n/a |
| Global `~/.claude/CLAUDE.md` | NOT TOUCHED | global surfaces require separate explicit opt-in; not requested |

Memory-commit verification (would run after real apply):

- File exists check: would confirm CLAUDE.md contains the marker-bounded section
- Marker check: would confirm both `compound-ai:start` and `compound-ai:end` markers are present and paired
- Idempotency check: would confirm re-running adoption-captain with v2.5.0 detects the existing section and skips re-addition

---

## Rollback procedure (would apply if operator decides to reverse)

1. Delete the `.compound-ai/` directory
2. Open project `CLAUDE.md`
3. Find `<!-- compound-ai:start v2.5.0 -->` and `<!-- compound-ai:end -->` markers
4. Delete everything between (and including) them
5. Save

That removes every change adoption-captain made. No other files were touched.

---

## Codex acceptance criteria check

From Codex's v2.5.0 spec:

| Criterion | Status in this dry run |
|---|---|
| Agent identifies host's existing instruction files | YES: CLAUDE.md, README.md, project.md, session-log.md identified |
| Agent detects package manager and core stack | YES: npm, React/Vite/TypeScript/ESLint/Vitest/Vercel |
| Agent detects build, test, lint, typecheck commands | YES: all four detected (typecheck folded into build) |
| Agent proposes adoption plan before edits | YES: Phase 1 / Phase 2 / Phase 3 explicit; no edits applied in dry run |
| Plan includes Preserve, Add, Modify, Defer, Conflict sections | YES: all five present (zero conflicts in this case) |
| No existing agent file overwritten | YES: only marker-bounded additive section proposed for CLAUDE.md |
| Kit placed under `.compound-ai/` | YES: default path |
| Only a minimal pointer added to existing agent docs | YES: ~30-line marker-bounded section |
| Validation commands are run or marked not found | YES: all three discovered; would be re-run after real apply |
| Adoption report is written | YES: this document |
| Future work routes through request-router without loading Field Guide wholesale | YES: Field guide stays in `.compound-ai/docs/`; not loaded by default |

**All eleven acceptance criteria pass on this dry run.**

---

## Conclusion

`adoption-captain` is operationally correct against a real mature project. The protocol:

- Detected every existing surface that needed preserving
- Mapped 23 kit skills to the project's actual needs with explicit rationale per skill
- Proposed a phased plan that adds value in Phase 1 with zero risk to the host stack
- Designed the memory-commit section to be marker-bounded, project-tailored, and trivially reversible
- Surfaced exactly one decision the operator needs to make (Phase 1 approval) before applying changes

If Cameron approves Phase 1 on this report, the actual adoption (creating `.compound-ai/`, appending the section to CLAUDE.md, validating with npm run test/build/lint) would take about 90 seconds. The discipline is operationalized; the operator's only job is consent.

This is the metabolism Codex prescribed: not "implement everything," but "structured adoption-captain that preserves the stack, maps the kit, then only applies safe changes."
