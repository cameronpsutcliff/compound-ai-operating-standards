# Skill: agent-panel-review
# Compound AI Operating Standards
# Source: cameronsutcliff.com/compound-ai | License: Apache 2.0

## What this skill does

Convenes a panel of agents to review a high-stakes deliverable using
**independent-first-pass, structured-critique, no-ego convergence**. The
panel is not a roundtable. Agents do not see each other's drafts during
the first pass. Cross-contamination is what kills convergence; sealing
the first pass is what makes the convergence honest.

This is a Tier 1 infrastructure skill because it sits above any specific
deliverable. The panel can be used on a plan, a document, a code change,
a decision, or a release.

## When to convene

Load `reference/when-to-convene.md`. In short: high-stakes deliverables,
multi-perspective work, irreversible decisions. NOT for daily code or
single-answer questions.

## Triggers

"set up a panel", "convene a panel", "have agents review each other",
"multi-agent review", "panel review", "second opinion", "independent
review", "third opinion", "let's get critiques from a few agents"

## The protocol in six stages

| Stage | What happens | The hard rule |
|---|---|---|
| **1. Frame** | Operator writes one prompt. Same prompt for every panelist. | One prompt, no variants. |
| **2. Independent first pass** | Each agent produces a full first attempt with no visibility into the others. | No agent reads another's draft. No shared scratchpad. No peeking. |
| **3. Cross-critique** | Each agent reads the others' outputs and produces a structured critique. | Critique is for the work, not the agent. Template enforced. |
| **4. Self-revise** | Each agent revises its own output in light of critiques. | No re-arguing. Adopt or write one line of dissent. |
| **5. Converge** | Operator picks the merge architecture from the three revisions. | Merge takes the strongest layer from each. Not an average. |
| **6. Loop or ship** | If gaps remain, loop 3-5. If clean, ship. | Loop-1 converge means you did not need a panel. Loop-4 still arguing means scope is too big. |

Load `reference/protocol.md` for the full procedure.

## Role assignment

Roles are functions, not identities. Any agent can hold any role. Common
panel shapes are in `reference/roles.md`. Default shape for documents:
voice / substance / architecture. Default shape for code: builder /
critic / integrator. Default shape for analysis: researcher / skeptic /
synthesizer.

## Critique format

The critique template lives in `reference/critique-format.md`. The
template is what prevents critique from becoming negging. Every critique
covers four cells: strongest claim, weakest claim, shared blind spot,
one thing worth stealing.

## Which agents excel at what

`reference/agent-strengths.md` covers known model strengths. The skill
works with any combination, including three sessions of the same agent
in three different roles.

## The merge (Stage 5) framework

Stage 5 is the only stage where the operator's judgment is the deciding
factor, not the panel's. Without a framework, the operator's bias
reasserts: the layer that matches their instinct gets called "strongest"
silently. Load `reference/merge-framework.md` for the per-dimension
scoring procedure, operator-bias check (two questions before locking a
dimension), and the honest-test for a healthy merge.

## Loop-4 recovery

A panel that has not converged by Loop 4 needs diagnostic, not another
loop. Load `reference/loop-4-recovery.md` for the five common causes
(too-broad question, hidden assumption, wrong composition, scope creep,
fatigue), recovery moves per cause, and the "ship the imperfect" rule
that protects against sunk-cost panic.

## Worked example

`reference/worked-example.md` shows the full six-stage protocol on a
synthetic deliverable. The example is the method, not a real artifact.
See the Field Guide chapter "Agent Panel Review" for the narrative
walkthrough.

## Pair with

- `nod-protocol` — when the panel disagrees and the disagreement needs
  gated opposite-construction
- `pressure-test` — when one agent's critique role uses CEO/scope lenses
- `quality-gate` — applied to the merged deliverable before ship

## The discipline that makes this work

**Stage 2 must be sealed.** Once an agent has seen another agent's
draft, its independent signal is destroyed for that loop. Cross-
contamination is what produces convergence theater instead of
convergence.

If the seal breaks (operator accidentally pastes one agent's output
into another's prompt), restart the loop. The lost time is cheaper than
the lost signal.
