# Skill: request-router
# Compound AI Operating Standards v2.3.0
# Source: cameronsutcliff.com/compound-ai | License: Apache 2.0

## What this skill does

Routes any incoming request to the right skill. Load at session start.
Once active, scan every request for trigger patterns before responding.

This skill has three modes:

1. **Routing table** (existing). Pattern matches invoke a skill silently.
2. **Panel Offer fast-path** (refined in v2.3.0). Explicit panel phrases
   auto-invoke. No ambiguity.
3. **Panel Offer judgment** (refined in v2.3.0). Borderline requests get
   evaluated against five criteria. Match means OFFER, not auto-invoke.
   Operator decides.

The judgment mode is what keeps the kit from spamming "want a panel?" on
every "what do you think?" message. Normal user-agent collaboration stays
solo unless the request actually signals council-tier intent.

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
| "pressure test", "critique this", "rip this apart", "tear this apart", "is this ambitious enough" | `pressure-test`                   |
| "code audit", "dead code", "dependency check", "security review", "test coverage"                  | `code-audit`                      |
| "research this", "find sources", "structured research", "investigate"                              | `autoresearch`                    |
| "build a skill", "create a skill", "new skill for", "extend the kit"                               | `skill-creator`                   |

### Domain capabilities (Tier 2)

| If the request contains...                                                                         | Apply this skill                  |
|----------------------------------------------------------------------------------------------------|-----------------------------------|
| "viz", "what chart", "dashboard design", "chart critique", "data viz", "data visualization"        | `viz`                             |
| "stakeholder map", "influence interest", "stakeholder analysis", "engagement strategy"             | `stakeholder-mapping`             |

### Session infrastructure (Tier 1) -- explicit panel invocation (fast-path)

| If the request contains...                                                                         | Apply this skill                  |
|----------------------------------------------------------------------------------------------------|-----------------------------------|
| "convene a panel", "set up a panel", "let's run a panel", "panel review on this", "multi-agent review", "panel this" | `agent-panel-review`              |
| "convene a planning panel", "set up a planning panel", "plan this with the panel", "split this work across agents", "have agents propose plans" | `agent-panel-planning`            |

These are unambiguous: the operator named a panel. Auto-invoke without offering.

## How to apply a routed skill

1. Identify the matching row.
2. State: "Applying [skill-name] to this request."
3. Load the SKILL.md from the matching tier and follow it exactly.

---

## Panel Offer judgment (criteria, not phrase list)

The fast-path above catches explicit panel invocations. The judgment mode
catches the harder case: when the operator is signaling council-tier intent
without using the word "panel."

Before responding to any request, scan against these five criteria. **Match
on at least ONE means OFFER the panel.** No match means just answer.

### The five criteria

1. **Explicit invitation to another model or agent.** The operator gestures
   toward an agent OTHER than the one they're talking to. Examples: "I want
   another model's read on this," "what would [other agent] say," "second
   opinion from a different model," "let's get [Codex/Gemini/Kiro] in on this."

2. **Stuck-state signal: their own reasoning is looping.** The operator
   describes being unable to decide. Examples: "I keep going back and
   forth," "I've changed my mind three times," "I can't decide between X
   and Y," "I keep talking myself out of it."

3. **High-stakes, hard-to-reverse decision with explicit "don't want to
   decide alone" framing.** Not just "this is important," but explicit
   signaling that the operator does not want to commit solo. Examples:
   "this is too important to decide alone," "I don't want to commit without
   more eyes on it," "this is irreversible and I'm not confident."

4. **Explicit panel or council words.** Even outside the fast-path phrasings.
   Examples: "I want a council on this," "let's get a few agents together,"
   "I want this run through the panel pattern."

5. **Complete draft plan + explicit desire for alternative framings.** The
   operator has a plan they wrote, and they explicitly want it tested
   against other plans. Examples: "I drafted this plan, want to test it
   against alternatives," "I have a framing but want to see other framings."

### What does NOT trigger an offer (treat as normal collaboration)

The most important part of this section. Without it, the kit spams panel
offers on routine collaborative dialogue.

| Operator says... | Treat as... |
|---|---|
| "what do you think?", "your thoughts?", "your take?" | Normal collab. Just answer. |
| "is this any good?", "any feedback?" | Normal collab. Just answer. |
| "I'm not sure how to approach this" | Engage deeper solo. T2, not T3. |
| "help me think through this", "walk me through it" | Engage deeper solo. T2. |
| "I'm stuck on this" | Engage deeper solo. T2, unless paired with criterion 2 above. |
| "tear this apart", "rip this apart" | Invoke `pressure-test`, not a panel. |
| "is this important?" or "is this risky?" | Ask back, do not assume T3. |

The distinction is whether the operator is gesturing toward OTHER agents
or just asking THIS agent to engage. Asking this agent more deeply is solo
collaboration. Asking for OTHER agents' input is council-tier.

---

## The offer response template

When a Panel Offer judgment criterion matches, respond with the template
BEFORE doing anything else. The operator opts in or declines.

```
This sounds like [reason matching the triggered criterion].
Want me to set up a panel? [Two or three] agents would each
[propose an approach / produce a sealed first-pass review]
independently, then we'd converge. I can sketch the panel
composition or you can name the agents.

If you'd rather think alone first, just say so and I'll proceed solo.
```

### The soft-offer pattern (for borderline cases)

When the operator's signal is borderline (matches a criterion weakly, or
sits between T2 and T3), do NOT derail with a full panel offer question.
Instead:

1. Answer the question as posed.
2. End with one sentence mentioning the panel as available.

Example response shape:

> [Full answer to the operator's question.]
>
> If you want another model's perspective specifically, I can set up a
> panel with [Codex / Kiro / Gemini] -- we'd each propose independently
> then converge. Up to you.

The operator can ignore it (continue the conversation) or take it ("yes,
set up the panel"). No friction either way. The soft-offer keeps the kit
responsive without being naggy.

---

## When NOT to offer (even on a criterion match)

Some criterion matches do not warrant an offer:

- The question is small and reversible at low cost. Just answer.
- The operator has already declined a panel offer in this session for the
  same topic. Do not re-offer.
- The operator has explicitly said "let me think alone." Respect it.
- The matched phrase is incidental. "I'm not sure I follow your last
  message" is not a planning panel signal even though it matches criterion 2.

If you are unsure whether to offer, lean toward the **soft-offer pattern**
(answer + one-sentence panel mention at the end). A declined soft-offer
takes zero operator response (they just continue). A skipped offer that
should have happened costs much more.

---

## Why judgment, not pattern matching

Substring matching is brittle. "I keep going in circles" and "I've been
spinning on this all day" are the same intent in different lexemes. A
phrase list rots; criteria document the judgment.

The agent reading this file IS the classifier. There is no external hook.
The discipline is: before responding, scan the request against the five
criteria above. Match means offer (or soft-offer if borderline). No match
means just answer. The criteria do the routing; the agent does the
judgment.

This is operator humility wired into the kit as a default behavior, not
as a phrase-list-driven feature.

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

No pattern match AND no Panel Offer criterion match: respond directly.
Most requests fall here. Not every request needs a routed skill or a panel
offer. Routing overhead is only worth it when the task has real analytical
complexity; panel offers are only worth it when the operator is signaling
council-tier intent.

## Source references

- `_skills-index.md` -- complete skill registry
- `tier-1-global/AGENT.md` -- tier-level operating rules
- `AGENT.md` (root) -- model routing table
- `tier-1-global/skills-core/agent-panel-planning/reference/when-to-convene.md` -- the threshold guide for panel-offer responses
