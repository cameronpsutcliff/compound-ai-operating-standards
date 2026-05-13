# Skill: request-router
# Compound AI Operating Standards
# Source: cameronsutcliff.com/compound-ai | License: Apache 2.0

## What this skill does

Routes any incoming request to the right cognitive mode skill. Load at session start.
Once active, scan every request for trigger patterns before responding.

This is the entry point to all six cognitive mode skills. It tells you WHAT to think
WITH, not what to think ABOUT.

## Load at session start

Add to your session-start: load `_skills-index.md`, then load this file.

## Routing table

| If the request contains...                                                                         | Apply this skill                  |
|----------------------------------------------------------------------------------------------------|-----------------------------------|
| "multiple perspectives", "what would X say", "steelman", "red-team", "debate", "ensemble"         | `parallel-lens-synthesis`         |
| "what could go wrong", "premortem", "stress test", "simulate outcomes", "second-order effects"     | `consequence-simulation`          |
| "explain to [audience]", "translate for", "rewrite for", "make this accessible", "exec summary"   | `cross-domain-translation`        |
| "pattern across", "common thread", "root cause", "what connects these", "why does this keep"      | `convergence-detection`           |
| "devil's advocate", "base rate", "am I being objective", "weight the evidence", "calibrated"      | `detached-judgment`               |
| "what should we do", "make this actionable", "next steps", "who owns", "OODA", "turn into a plan" | `simulation-to-action-bridge`     |

## How to apply a routed skill

1. Identify the matching row.
2. State: "Applying [skill-name] to this request."
3. Load `skills/[skill-name]/SKILL.md` and follow it exactly.

## Compound requests

Some requests need more than one cognitive mode. Apply in sequence:

- **Analysis requests**: parallel-lens-synthesis, then consequence-simulation
- **Decision requests**: consequence-simulation, then simulation-to-action-bridge
- **Full strategic cycle**: parallel-lens-synthesis, consequence-simulation, simulation-to-action-bridge

## Passthrough

No pattern match: respond directly. Not every request needs a cognitive mode.
Routing overhead is only worth it when the task has real analytical complexity.

## Source references

- `_skills-index.md` — complete skill registry, both infrastructure and cognitive modes
- `AGENT.md` — model routing table (use synthesis-tier model for any routed skill)
- Field Guide Chapter 17: Model Routing by Cognitive Load
- Field Guide Chapter 19: Multi-Agent Coordination
