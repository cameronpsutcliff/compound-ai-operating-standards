# Skill: request-router
# Compound AI Operating Standards v2.1.0
# Source: cameronsutcliff.com/compound-ai | License: Apache 2.0

## What this skill does

Routes any incoming request to the right skill. Load at session start.
Once active, scan every request for trigger patterns before responding.

## Load at session start

Add to your session-start: load `_skills-index.md`, then load this file.

## Routing table

### Cognitive modes (Tier 2)

| If the request contains...                                                                         | Apply this skill                  |
|----------------------------------------------------------------------------------------------------|-----------------------------------|
| "multiple perspectives", "what would X say", "steelman", "red-team", "debate", "ensemble"         | `parallel-lens-synthesis`         |
| "what could go wrong", "premortem", "stress test", "simulate outcomes", "second-order effects"     | `consequence-simulation`          |
| "explain to [audience]", "translate for", "rewrite for", "make this accessible", "exec summary"   | `cross-domain-translation`        |
| "pattern across", "common thread", "root cause", "what connects these", "why does this keep"      | `convergence-detection`           |
| "devil's advocate", "base rate", "am I being objective", "weight the evidence", "calibrated"      | `detached-judgment`               |
| "what should we do", "make this actionable", "next steps", "who owns", "OODA", "turn into a plan" | `simulation-to-action-bridge`     |
| "play devil's advocate", "argue the opposite", "construct the opposite case", "NOD this", "steelman the other side", "what would the opposite say" | `nod-protocol`                    |

### Analytical capabilities (Tier 2)

| If the request contains...                                                                         | Apply this skill                  |
|----------------------------------------------------------------------------------------------------|-----------------------------------|
| "think deeply", "multi-angle", "ultra think", high-stakes architecture decision                   | `ultra-think`                     |
| "pressure test", "critique this", "rip this apart", "is this ambitious enough", "rethink this plan" | `pressure-test`                 |
| "code audit", "dead code", "dependency check", "security review", "test coverage"                  | `code-audit`                      |
| "research this", "find sources", "structured research", "investigate"                              | `autoresearch`                    |
| "build a skill", "create a skill", "new skill for", "extend the kit"                               | `skill-creator`                   |

### Domain capabilities (Tier 2)

| If the request contains...                                                                         | Apply this skill                  |
|----------------------------------------------------------------------------------------------------|-----------------------------------|
| "viz", "what chart", "dashboard design", "chart critique", "data viz", "data visualization"        | `viz`                             |
| "stakeholder map", "influence interest", "stakeholder analysis", "engagement strategy"             | `stakeholder-mapping`             |

### Session infrastructure (Tier 1)

| If the request contains...                                                                         | Apply this skill                  |
|----------------------------------------------------------------------------------------------------|-----------------------------------|
| "set up a panel", "convene a panel", "have agents review each other", "multi-agent review", "panel review", "second opinion", "independent review", "third opinion" | `agent-panel-review`              |

## How to apply a routed skill

1. Identify the matching row.
2. State: "Applying [skill-name] to this request."
3. Load the SKILL.md from the matching tier and follow it exactly.

Cognitive mode skills and capability skills live in `tier-2-capabilities/skills/`. Infrastructure skills live in `tier-1-global/skills-core/` and are usually loaded already.

## Compound requests

Some requests need more than one skill. Apply in sequence:

- **Analysis requests:** `parallel-lens-synthesis`, then `consequence-simulation`
- **Decision requests:** `consequence-simulation`, then `simulation-to-action-bridge`
- **Adversarial review of a plan:** `pressure-test`, then `cross-domain-translation` for audience framing
- **Hard decision under uncertainty:** `parallel-lens-synthesis`, then `nod-protocol` on the synthesis, then `simulation-to-action-bridge`
- **High-stakes deliverable:** `agent-panel-review` (drives the whole loop), with `nod-protocol` invoked on disagreements
- **Full strategic cycle:** `parallel-lens-synthesis`, `consequence-simulation`, `simulation-to-action-bridge`

## Passthrough

No pattern match: respond directly. Not every request needs a routed skill.
Routing overhead is only worth it when the task has real analytical complexity.

## Source references

- `_skills-index.md` -- complete skill registry, both infrastructure and capabilities
- `tier-1-global/AGENT.md` -- tier-level operating rules
- `AGENT.md` (root) -- model routing table (use synthesis-tier model for any routed skill)
