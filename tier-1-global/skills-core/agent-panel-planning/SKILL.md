# Skill: agent-panel-planning
# Compound AI Operating Standards
# Source: cameronsutcliff.com/compound-ai | License: Apache 2.0

## What this skill does

Converges a panel of agents on a plan for a high-stakes deliverable, then
splits the work based on demonstrated strength. Pairs with `agent-panel-review`:
**planning** produces the plan and the role assignment; **review** runs the
sealed critique on the deliverable that emerges.

This is a Tier 1 infrastructure skill. It sits above any specific deliverable.
Use it when the question is "what should we build and who is best at each
piece," not "is what we built any good."

## When to convene a planning panel

Convene when at least one is true:
- The plan itself is what needs to be right (not just the execution)
- Multiple agents have genuinely different framings of the problem
- The work will be divided across agents and you need strength-matched routing
- An operator wants to test their own framing against independent reframings

Do NOT convene when:
- The plan is obvious and only execution matters (skip to `agent-panel-review`)
- One agent has already framed the problem well and you just want pressure-testing
  (use `pressure-test` or `nod-protocol` instead)
- Time pressure exceeds the value of a multi-pass convergence

## Triggers

"plan this with the panel", "set up a planning panel", "have agents propose
plans", "converge on a plan", "split this work across agents", "who should
own what", "compare independent plans"

## The protocol in six stages

| Stage | What happens | The hard rule |
|---|---|---|
| 1. Frame | Operator writes one prompt. Same prompt to every panelist. | One prompt, no variants. Each panelist must frame the WHOLE problem, not a slice. |
| 2. Independent plans (sealed) | Each agent produces a complete proposed plan with no visibility into the others. | Sealed. If the seal breaks, restart that panelist's plan. |
| 3. Cross-feedback | Each agent reads the others' plans and produces structured cross-feedback with element-level votes. | Vote on specific decision points, not on whole plans. Reasoning required per vote. |
| 4. Concession + private revise + cross-suggestions | Each agent (a) names what it concedes and to which other agent, (b) revises its own plan, (c) proposes paths forward for the OTHER agents. Sealed. | The cross-suggestions move is the load-bearing one. Each agent must propose how the others should adjust, not just adjust itself. |
| 5. Reconvene | Each agent reads the revised plans AND the cross-suggestions from the others. No seal. | This is where convergence happens. Adopt accepted suggestions; flag rejected ones. |
| 6. Voting + ratification + task split | Operator surfaces decision points. Agents vote with one-line reasoning. Operator locks the plan and the task assignment based on demonstrated strength in this round. | Task assignment is by demonstrated dominance, not preset role labels. |

Load `reference/protocol.md` for the full stage-by-stage procedure.

## Cross-feedback format

Stage 3 uses a structured template: per-plan critique with strongest claim,
weakest claim, shared blind spot, one thing worth stealing, plus a votes block
on specific decision points the operator surfaces.

Load `reference/cross-feedback-template.md`.

## Concession discipline

Stage 4 is where the panel earns its cost. Each agent must:
1. Name concessions explicitly (concede X to Y agent on Z dimension)
2. Revise its own plan to absorb the conceded points
3. Propose specific path-forward adjustments for each OTHER agent

Load `reference/concession-discipline.md`.

## Strength-matched task split

Stage 6's task assignment is not preset. Each task gets one owner based on
which agent demonstrated dominant capability on that dimension in this round.
This is the antidote to council theater (where agents agree but no one is
actually accountable for the work).

Load `reference/task-assignment.md`.

## Execution discipline (after ratification)

Once the plan is ratified, the agents execute. During execution, when an agent
hits a decision point not covered by ratification, the discipline is to escalate
to the operator with the panel's prior context, not to decide solo. This is
operator-in-the-loop voting on request, not autonomous drift.

Load `reference/escalation-discipline.md`.

## Pair with

- `agent-panel-review` — runs sealed critique on the deliverable the planning panel produced
- `nod-protocol` — when a Stage 3 vote splits the panel; run NOD on the contested decision
- `pressure-test` — on the ratified plan before execution begins, especially Stages 5-6 worth pressure-testing

## Worked example

`reference/worked-example.md` shows the protocol applied to a synthetic
deliverable. Shows what each stage produces. Does not pull the curtain back
on any real artifact.

## What this is NOT

Not a roundtable. Not a real-time debate. Not consensus-by-discussion. Each
move is staged; the discipline is the staging. Skip a stage and the panel
produces averaging, not convergence.
