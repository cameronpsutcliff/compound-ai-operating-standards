# Skill: stakeholder-mapping
# Compound AI Operating Standards v2.0.0
# Source: cameronsutcliff.com/compound-ai | License: Apache 2.0

## What this skill does

Map stakeholders for any initiative. Identify each person's influence and
interest, classify them on the influence-interest grid, and produce an
engagement strategy per quadrant. Standard PMI / PMBOK stakeholder
management pattern, adapted for AI-assisted prep work.

## Triggers

"stakeholder map", "stakeholder mapping", "influence interest grid",
"who do we need to manage", "stakeholder analysis", "engagement strategy",
"power interest matrix", "who has influence over this"

## How to apply

### 1. Collect

Gather stakeholder information from available sources:
- Names and titles mentioned in meetings or documents
- Org chart data if available
- LinkedIn profile context (see "Data sources" below for an optional upstream)
- Meeting notes that reveal relationship dynamics
- Who introduced whom, who defers to whom, who pushes back

### 2. Map relationships

For each stakeholder, document:
- **Name and title**
- **Reports to** (direct manager)
- **Key responsibility** (what they own or care about)
- **Influence level** (High / Medium / Low — based on org position and observed behavior)
- **Interest level** (High / Medium / Low — how engaged they are with the initiative)
- **Communication preference** (data-heavy, executive summary, visual, verbal)
- **What they need from the initiative** (specific outcome they're tracking)

### 3. Influence-interest grid

Place each stakeholder in one of four quadrants:

|  | High Interest | Low Interest |
|---|---|---|
| **High Influence** | **MANAGE CLOSELY** — regular engagement, tailored updates, involve in decisions | **KEEP SATISFIED** — executive summaries, do not overwhelm, surface only key decisions |
| **Low Influence** | **KEEP INFORMED** — include in updates, invite to demos, potential champions | **MONITOR** — light touch, loop in when relevant to their area |

### 4. "What does their boss care about" framework

For each stakeholder in the MANAGE CLOSELY or KEEP SATISFIED quadrants:
- Who do they report to?
- What does their boss care about?
- How does this initiative make this person's boss's priorities look addressed?
- What language and metrics would resonate at the next level up?

This ensures every deliverable is framed for the person you're talking to AND for the person they need to impress.

### 5. Engagement strategy

For each stakeholder in MANAGE CLOSELY and KEEP SATISFIED, generate:
- **Recommended cadence** (weekly, bi-weekly, as-needed)
- **Communication format** (email, meeting, dashboard, deck)
- **Key messages** (what to emphasize in every interaction with this person)
- **Relationship risks** (anything that could erode trust)

### 6. Output

Structured markdown with:
- Stakeholder table (name, title, influence, interest, reports-to)
- Influence-interest grid visualization
- Per-person engagement strategy cards for MANAGE CLOSELY and KEEP SATISFIED quadrants
- "What does their boss care about" summary for the top 3-5 stakeholders

## Pair with

- `cross-domain-translation` — to re-encode the same message for different stakeholders without losing fidelity
- `pressure-test` — to stress-test the engagement strategy before committing to a cadence

## Data sources (optional upstream)

For LinkedIn-based organizational mapping, [linkedin-osint-toolkit](https://github.com/michaelelizarov/linkedin-osint-toolkit) (MIT, by Michael Elizarov) provides employee scraping, role classification, and org-chart generation. The toolkit output (org chart JSON) slots directly into the "Collect" step above. Credit the original repo if you use it; this skill does not bundle the code.

## Source references

- Influence-interest grid: PMI / PMBOK standard stakeholder management
- Engagement quadrants (Manage Closely / Keep Satisfied / Keep Informed / Monitor): Mendelow's matrix
- "What does their boss care about" reframe: practitioner adaptation
