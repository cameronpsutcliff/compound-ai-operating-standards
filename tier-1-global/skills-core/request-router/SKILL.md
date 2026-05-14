# Skill: request-router
# Compound AI Operating Standards v2.2.0
# Source: cameronsutcliff.com/compound-ai | License: Apache 2.0

## What this skill does

Routes any incoming request to the right skill. Load at session start.
Once active, scan every request for trigger patterns before responding.

This skill has two modes:

1. **Routing table** (existing). Pattern matches → invoke skill silently.
2. **Panel offer triggers** (new in v2.2.0). Humility-signal matches →
   ask the operator if they want a panel, do NOT auto-invoke.

The second mode is what makes the kit responsive to operator humility:
when the operator signals uncertainty, the agent offers wider input
rather than deciding solo.

## Load at session start

Add to your session-start: load `_skills-index.md`, then load this file.

---

## Routing table (matches invoke a skill)

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
| "set up a panel", "convene a panel", "have agents review each other", "multi-agent review", "panel review", "second opinion on this draft", "independent review", "third opinion" | `agent-panel-review`              |
| "plan this with the panel", "set up a planning panel", "have agents propose plans", "converge on a plan", "split this work across agents", "who should own what", "compare independent plans" | `agent-panel-planning`            |

## How to apply a routed skill

1. Identify the matching row.
2. State: "Applying [skill-name] to this request."
3. Load the SKILL.md from the matching tier and follow it exactly.

Cognitive mode skills and capability skills live in `tier-2-capabilities/skills/`. Infrastructure skills live in `tier-1-global/skills-core/` and are usually loaded already.

---

## Panel offer triggers (matches OFFER a panel, do NOT auto-invoke)

These trigger patterns signal operator humility. When matched, the
correct behavior is to OFFER the panel, not invoke one. The operator
opts in (or declines) before the panel runs.

| If the request contains... (operator humility signals)                                              | Offer this skill                  |
|-----------------------------------------------------------------------------------------------------|-----------------------------------|
| "I'm not sure", "I'm uncertain how to", "what's the right approach", "what's the best way to"      | `agent-panel-planning`            |
| "your thoughts", "what do you think", "want a second opinion", "what am I missing"                  | `agent-panel-planning`            |
| "high-stakes", "irreversible", "can't walk this back", "before I commit", "this feels risky"        | `agent-panel-planning`            |
| "I have a draft plan but want to test it", "test my framing", "is my plan right"                    | `agent-panel-planning`            |
| "I've drafted this, is it any good", "review this before I ship", "is this ready"                   | `agent-panel-review`              |

### Offer response template

When a panel-offer trigger matches, respond before doing anything else
with something like:

> "This sounds like a [high-uncertainty decision / high-stakes
> deliverable / planning question]. Want me to set up a panel? Two or
> three agents could each [propose an approach independently / produce
> a sealed first-pass review], then converge. I can sketch the panel
> composition if useful, or you can name the agents.
>
> If you'd rather think alone first, just say so and I'll proceed solo."

### When NOT to offer

Some humility signals do not warrant a panel offer:

- The question is small and reversible at low cost — just answer
- The operator has already declined a panel offer in this session for
  the same topic — do not re-offer
- The operator has explicitly said "let me think alone" — respect it
- The matched phrase is incidental ("I'm not sure I follow your last
  message" is not a planning panel signal)

If you are unsure whether to offer, lean toward offering. A declined
offer takes one line of operator response. A skipped offer that should
have happened costs much more.

### Why this mode exists

Standard agent behavior is reactive: the operator asks, the agent
answers. The panel-offer pattern adds a proactive layer: when the
operator signals uncertainty, the agent surfaces the panel option
before deciding solo. This is operator humility (asking for wider
input) wired into the kit as a default behavior, not as a manual
gesture.

---

## Compound requests

Some requests need more than one skill. Apply in sequence:

- **Analysis requests:** `parallel-lens-synthesis`, then `consequence-simulation`
- **Decision requests:** `consequence-simulation`, then `simulation-to-action-bridge`
- **Adversarial review of a plan:** `pressure-test`, then `cross-domain-translation` for audience framing
- **Hard decision under uncertainty:** `parallel-lens-synthesis`, then `nod-protocol` on the synthesis, then `simulation-to-action-bridge`
- **High-stakes deliverable, start to finish:** `agent-panel-planning` to converge on the plan, then `agent-panel-review` on the drafts that emerge, with `nod-protocol` on any contested decision
- **Full strategic cycle:** `parallel-lens-synthesis`, `consequence-simulation`, `simulation-to-action-bridge`

## Passthrough

No pattern match: respond directly. Not every request needs a routed skill.
Routing overhead is only worth it when the task has real analytical complexity.

## Source references

- `_skills-index.md` -- complete skill registry, both infrastructure and capabilities
- `tier-1-global/AGENT.md` -- tier-level operating rules
- `AGENT.md` (root) -- model routing table (use synthesis-tier model for any routed skill)
- `tier-1-global/skills-core/agent-panel-planning/reference/when-to-convene.md` -- the threshold guide for panel-offer responses
