# Skill: request-router
# Compound AI Operating Standards v2.3.2
# Source: cameronsutcliff.com/compound-ai | License: Apache 2.0

## What this skill does

Routes any incoming request to the right skill. Load at session start.
Once active, scan every request for trigger patterns before responding.

Three modes:

1. **Routing table** -- explicit pattern matches auto-invoke a skill.
2. **Panel Offer fast-path** -- explicit panel phrasings auto-invoke a panel skill.
3. **Panel Offer judgment** -- borderline requests evaluated against five criteria; match means OFFER, operator decides.

The judgment mode is what keeps the kit from spamming "want a panel?" on every "what do you think?" message. Rationale lives in `reference/router-rationale.md`.

## Routing table

### Cognitive modes (Tier 2)

| If the request contains... | Apply this skill |
|---|---|
| "multiple perspectives", "what would X say", "steelman", "red-team", "debate", "ensemble" | `parallel-lens-synthesis` |
| "what could go wrong", "premortem", "stress test", "simulate outcomes", "second-order effects" | `consequence-simulation` |
| "explain to [audience]", "translate for", "rewrite for", "make this accessible", "exec summary" | `cross-domain-translation` |
| "pattern across", "common thread", "root cause", "what connects these", "why does this keep" | `convergence-detection` |
| "devil's advocate", "base rate", "am I being objective", "weight the evidence", "calibrated" | `detached-judgment` |
| "what should we do", "make this actionable", "next steps", "who owns", "OODA", "turn into a plan" | `simulation-to-action-bridge` |
| "play devil's advocate", "argue the opposite", "construct the opposite case", "NOD this" | `nod-protocol` |

### Analytical capabilities (Tier 2)

| If the request contains... | Apply this skill |
|---|---|
| "think deeply", "multi-angle", "ultra think" | `ultra-think` |
| "pressure test", "critique this", "rip this apart", "tear this apart" | `pressure-test` |
| "code audit", "dead code", "dependency check", "security review", "test coverage" | `code-audit` |
| "research this", "find sources", "structured research", "investigate" | `autoresearch` |
| "build a skill", "create a skill", "new skill for", "extend the kit" | `skill-creator` |

### Domain capabilities (Tier 2)

| If the request contains... | Apply this skill |
|---|---|
| "viz", "what chart", "dashboard design", "chart critique", "data viz" | `viz` |
| "stakeholder map", "influence interest", "stakeholder analysis" | `stakeholder-mapping` |

### Session infrastructure (Tier 1) -- explicit invocation

| If the request contains... | Apply this skill |
|---|---|
| "convene a panel", "set up a panel", "panel review on this", "multi-agent review", "panel this" | `agent-panel-review` |
| "convene a planning panel", "plan this with the panel", "split this work across agents", "have agents propose plans" | `agent-panel-planning` |
| "ship gate", "release captain", "is this ready to ship", "pre-release check", "verify the release" | `release-captain` |

## How to apply a routed skill

1. Identify the matching row.
2. State: "Applying [skill-name] to this request."
3. Load the SKILL.md from the matching tier and follow it exactly.

## Panel Offer judgment (five criteria)

Before responding, scan against these. Match on at least ONE means OFFER the panel (do not auto-invoke).

1. **Explicit invitation to another model or agent.** "I want another model's read", "what would [other agent] say."
2. **Stuck-state signal.** "I keep going back and forth", "I've changed my mind three times."
3. **High-stakes + don't-decide-alone framing.** "Too important to decide alone", "irreversible and I'm not confident."
4. **Explicit panel or council words** outside the fast-path. "I want a council on this", "run this through the panel pattern."
5. **Complete draft plan + desire for alternative framings.** "I drafted this, want to test against alternatives."

For each criterion: detailed examples, full offer template, soft-offer pattern, and when NOT to offer live in `reference/panel-offer-threshold.md`.

### What does NOT trigger an offer

Quick reference. Full table in `reference/panel-offer-threshold.md`.

- "what do you think?", "your thoughts?" -- normal collab
- "I'm not sure how to approach this" -- engage deeper solo
- "tear this apart" -- invoke `pressure-test`, not a panel
- "what could go wrong" -- invoke `consequence-simulation`

The distinction: gesturing toward OTHER agents vs asking THIS agent to engage. Solo collaboration stays solo.

## Compound requests

Some requests need a skill chain (analysis + decision + action). Recipes in `reference/compound-requests.md`.

## Passthrough

No routing-table match and no Panel Offer criterion match: respond directly. Most requests fall here. Routing overhead and panel offers are only worth it when the task has real analytical complexity or council-tier intent.

## Reference files

- `reference/compound-requests.md` -- skill chain recipes
- `reference/panel-offer-threshold.md` -- expanded criteria, offer template, soft-offer pattern
- `reference/router-rationale.md` -- why three modes, why judgment beats phrase-list
