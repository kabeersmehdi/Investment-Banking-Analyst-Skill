# M&A Analyst Agent v3.1

**Lower Middle Market | Sell-Side | Production-Grade**

An AI analyst for sell-side M&A brokers in the lower middle market ($1M–$5M EBITDA).
Replaces 15–25 hours of analyst work per deal.

---

## Table of Contents

1. [Overview](#overview)
2. [Quick Start](#quick-start)
3. [Commands](#commands)
4. [Deal Onboarding](#deal-onboarding)
5. [Multi-Deal Management](#multi-deal-management)
6. [Unstructured Intake](#unstructured-intake)
7. [Auto-Propagation](#auto-propagation)
8. [Deal Lifecycle](#deal-lifecycle)
9. [File Index](#file-index)
10. [Setup Checklist](#setup-checklist)
11. [API Integration](#api-integration)
12. [Maintenance](#maintenance)
13. [Limitations](#limitations)
14. [Customization & Support](#customization--support)

---

## Overview

### What It Does

| Capability | Description |
|-----------|-------------|
| **Valuation** | SDE/EBITDA multiples with live market comps, scenario analysis |
| **CIM Generation** | Full 8-section CIM with live industry data |
| **Teaser Creation** | Anonymous 1-page buyer-facing teaser |
| **Buyer Targeting** | Persona matching, live acquirer research, outreach emails |
| **Risk Analysis** | Auto-detected flags with severity ratings and narratives |
| **Quality of Earnings** | EBITDA bridge, NWC analysis, revenue cuts |
| **Deal Structuring** | SBA modeling, seller notes, earnouts, buyer affordability |
| **LOI Evaluation** | Offer comparison, deal certainty scoring, red flags |
| **Seller Readiness** | Pre-market checklist with gap identification |
| **Deal Screening** | Should you take this engagement? Fee economics check |

### Key Features

- **`/start`** — Interactive onboarding asks every question for you
- **Paste anything** — Dump unstructured notes and the agent parses them
- **Multi-deal** — Manage your entire pipeline in one conversation
- **Live research** — Searches the web for current multiples, buyers, and trends
- **Auto-propagation** — Update one field, all affected outputs get flagged
- **Source citations** — Every market data point is cited or flagged as embedded

---

## Quick Start

**Time to set up: 10 minutes. No code required.**

### Step 1: Create Project
Go to [claude.ai](https://claude.ai) → Projects → Create Project → Name it `M&A Analyst Agent`

### Step 2: Set Custom Instructions
Copy the entire contents of `system_prompt.md` → Paste into **Custom Instructions**

### Step 3: Upload Knowledge Files
Upload all `.md` files listed in the [File Index](#file-index) to **Project Knowledge**

### Step 4: Enable Web Search
Turn on web search in Claude settings

### Step 5: Start
Open a new conversation and type:

```
/new ABC Roofing
```

Then either type `/start` for guided onboarding, or paste everything you know about the deal.

---

## Commands

DEAL MANAGEMENT
  /new [name]           Create new deal
  /deals                Pipeline dashboard
  /deals all            Include archived
  /deal [name]          Switch active deal
  /archive [name]       Archive deal
  /rename [old] [new]   Rename deal
  /compare [a] [b]      Compare two deals

ONBOARDING
  /start                Guided 7-phase questionnaire
  (or just paste info)  Agent parses automatically

ANALYSIS
  /valuation            Valuation with live comps
  /cim                  Full CIM
  /teaser               Anonymous teaser
  /buyers               Buyer list + outreach
  /risks                Risk report
  /qoe                  Quality of Earnings
  /structure            Deal structure models
  /all                  Generate everything

STRATEGY (NEW)
  /strategy             Full deal strategy
  /thesis               Investment thesis
  /timeline             Deal event history

EVALUATION
  /loi [terms]          Evaluate LOI(s)
  /readiness            Seller readiness check
  /screening            Engagement screening

QUALITY (NEW)
  /check                Quick consistency check
  /qa                   Full 5-level QA

CONTEXT
  /status               Deal summary + outputs
  /update [field] [val] Update field
  /gaps                 Show missing fields
  /export               Export as JSON

### Examples

```
/new Charlotte Roofing              → Creates new deal
/start                              → Guided onboarding
/valuation                          → Bear/base/bull with live comps
/update revenue_ttm 4500000         → Updates context, flags changes
/deal summit                        → Switches to "Project Summit"
/deals                              → Shows full pipeline dashboard
/loi All cash $3.2M, 45-day DD     → Evaluates LOI against context
/compare ABC Metro                  → Side-by-side deal comparison
```

---

## Deal Onboarding

### Guided Path (`/start`)

The agent walks you through 7 phases, asking 3–5 questions at a time:

| Phase | What It Asks | Time |
|-------|-------------|------|
| 1. Company Basics | Name, industry, location, description | 2 min |
| 2. Financials | 3yr revenue, profit, SDE/EBITDA | 3 min |
| 3. Add-Backs | Owner comp, personal expenses, one-time items | 3 min |
| 4. Customers | Concentration, contracts, revenue type | 2 min |
| 5. Operations | Owner role, team, facility, transition | 3 min |
| 6. Deal Parameters | Price, structure, timeline, assets | 2 min |
| 7. Broker Notes | Risks, strengths, growth, ideal buyer | 2 min |

**Total: ~15 minutes for complete deal intake.**

After each phase, the agent confirms your answers. After all 7 phases, you get a full Deal Context Summary to review before proceeding.

### What Happens Automatically After Onboarding

| Action | Trigger | Output |
|--------|---------|--------|
| Calculates SDE | Phase 3 answers | Net Income + all add-backs |
| Calculates EBITDA | Phase 3 answers | SDE minus market-rate salary |
| Scores revenue quality | Phase 4 answers | 1–10 score → multiple impact |
| Detects risks | All phases | Auto-flagged ⚠️ list |
| Matches buyer persona | Phases 2+4+5+6 | Primary + secondary buyer type |
| Checks SBA feasibility | Phases 2+3+6 | DSCR calculation |
| Identifies data gaps | All phases | Missing items flagged |

---

## Multi-Deal Management

Brokers run multiple deals at once. This agent handles that.

### Dashboard (`/deals`)

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📊 DEAL DASHBOARD
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

  #  Deal Name          Industry    Revenue   SDE     Stage         Data
  ─  ─────────          ────────    ───────   ───     ─────         ────
→ 1  ABC Roofing        Roofing     $4.2M     $850K   CONTEXT DONE  92%
  2  Project Summit     HVAC        $6.1M     $1.4M   IN MARKET     100%
  3  Metro HVAC         HVAC        $2.8M     —       INTAKE        40%
  4  Lakeside Plumbing  Plumbing    $3.5M     $620K   LOI STAGE     100%

→ = Active Deal | Archived: 2 (type /deals all)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

### Switching Deals

The agent uses fuzzy matching — you don't need exact names:

| You Type | Matches |
|----------|---------|
| `/deal ABC` | ABC Roofing |
| `/deal summit` | Project Summit |
| `/deal 2` | Second deal in registry |
| `"what about the roofing deal?"` | ABC Roofing (auto-detected) |
| `"that HVAC one in Atlanta"` | Metro HVAC |

When you switch, the agent shows a brief summary of the deal you're now working on.

### Comparing Deals

```
/compare ABC Metro
```

Produces a side-by-side table comparing financials, valuation, risk rating, data completeness, and key differences.

---

## Unstructured Intake

You don't have to use the guided questionnaire. Just paste whatever you have.

### How It Works

```
/new Charlotte Roofing

Just signed this one — roofing company in Charlotte NC,
been around 18 years, owner is 62 and wants to retire.
Revenue is about $4.2M, SDE around $850K. He has 22
employees but does all the sales himself. Top 3 customers
are 40% of revenue, no contracts. Wants an SBA-eligible
deal. Wife does the books part-time but won't stay.
```

**The agent will:**
1. Parse every data point from your text
2. Organize it into the standard deal context format
3. Show you what it captured
4. Tell you exactly what's missing, grouped by priority
5. Ask: fill in gaps now, or work with what you have?

### What the Parser Catches

| Data Type | Examples It Recognizes |
|-----------|----------------------|
| Revenue | "$4.2M revenue", "top line is 4.2", "does about 4 mil" |
| SDE/EBITDA | "$850K SDE", "cash flow of 850", "earns about 850" |
| Employees | "22 employees", "team of 22", "22 people" |
| Years | "18 years", "since 2006", "been around 18 years" |
| Location | "Charlotte NC", "in North Carolina", "Charlotte area" |
| Owner age | "owner is 62", "he's 62" |
| Owner role | "does all the sales", "runs everything" |
| Motivation | "wants to retire", "burned out", "health" |
| Concentration | "top 3 are 40%", "biggest customer is 20%" |
| Contracts | "no contracts", "MSAs in place", "handshake deals" |
| Structure | "SBA eligible", "wants all cash", "open to seller note" |
| Risks | "messy books", "owner dependent", "lease is up" |
| Growth | "could expand to commercial", "hasn't done marketing" |

### Partial Info Works Too

```
/new Quick Screen

HVAC company, $3M revenue, owner wants $5M for it. Is that realistic?
```

The agent creates the deal, notes the data gaps, and still gives you a directional answer using what it has — flagging every assumption.

---

## Auto-Propagation

When you update any field with `/update`, the agent tells you which outputs are affected:

| Field Changed | Outputs Affected |
|--------------|-----------------|
| Revenue | SDE margin, valuation, CIM financials, teaser, SBA model, buyer returns |
| Customer concentration | Risk flags, multiple adjustment, valuation, risk narratives, buyer targeting, LOI evaluation |
| Owner role | Risk flags, multiple adjustment, CIM ops section, buyer targeting, transition plan |
| Add-backs | SDE, EBITDA, valuation, QoE, CIM financials |
| Asking price | Deal structure, SBA feasibility, buyer affordability, teaser |

After flagging affected outputs, the agent asks: *"Want me to regenerate any of these now?"*

---

## Deal Lifecycle

```
/new [name]
    │
    ▼
  INTAKE ─── /start or paste info
    │
    ▼
  CONTEXT COMPLETE ─── all critical fields filled
    │
    ├── /screening ─── Should we take this?
    ├── /readiness ─── Is seller ready?
    │
    ▼
  VALUED ─── /valuation
    │
    ▼
  IN MARKET ─── /cim  /teaser
    │
    ▼
  BUYER OUTREACH ─── /buyers
    │
    ▼
  LOI STAGE ─── /loi
    │
    ▼
  IN DILIGENCE ─── (manual update)
    │
    ▼
  ARCHIVED ─── /archive (closed / dead / paused)
```

Stage transitions happen automatically based on commands run. Override anytime with `/update stage [STAGE NAME]`.

---

## File Index

### System Configuration

| # | File | Purpose | Upload To |
|---|------|---------|-----------|
| 1 | `system_prompt.md` | Master instructions, commands, behavioral rules | Custom Instructions |

### Core Logic

| # | File | Purpose | Upload To |
|---|------|---------|-----------|
| 2 | `onboarding_flow.md` | Guided questionnaire + unstructured intake parsing | Project Knowledge |
| 3 | `multi_deal_management.md` | Deal registry, dashboard, switching, comparison | Project Knowledge |
| 4 | `web_research_protocol.md` | Search triggers, query library, source hierarchy | Project Knowledge |
| 5 | `source_citation_rules.md` | Citation format, anti-hallucination rules | Project Knowledge |

### Deal Analysis

| # | File | Purpose | Upload To |
|---|------|---------|-----------|
| 6 | `valuation_logic.md` | Multiples, adjustments, revenue quality scoring | Project Knowledge |
| 7 | `qoe_framework.md` | EBITDA bridge, working capital, revenue cuts | Project Knowledge |
| 8 | `deal_structure.md` | SBA modeling, seller notes, earnouts | Project Knowledge |
| 9 | `risk_framework.md` | Auto-detection rules, severity ratings, narratives | Project Knowledge |

### Marketing & Outreach

| # | File | Purpose | Upload To |
|---|------|---------|-----------|
| 10 | `cim_template.md` | Full CIM section structure | Project Knowledge |
| 11 | `teaser_template.md` | Anonymous teaser structure | Project Knowledge |
| 12 | `buyer_targeting.md` | Buyer personas, outreach templates, follow-up sequences | Project Knowledge |

### Deal Execution

| # | File | Purpose | Upload To |
|---|------|---------|-----------|
| 13 | `loi_evaluation.md` | LOI comparison matrix, deal certainty scoring | Project Knowledge |
| 14 | `seller_prep.md` | Pre-market readiness checklist | Project Knowledge |
| 15 | `deal_screening.md` | Engagement screening, fee economics | Project Knowledge |
| 16 | `engagement_guidance.md` | Broker fee structures, engagement terms | Project Knowledge |

### Schemas (API Only)

| # | File | Purpose | Upload To |
|---|------|---------|-----------|
| 17 | `input_schema.json` | Structured deal intake format | Local reference |
| 18 | `output_schema.json` | Structured output parsing format | Local reference |

**Total: 16 knowledge files + 1 system prompt + 2 schemas = 19 files**
**Estimated context: ~28,000 tokens**

---

CLAUDE PROJECT SETUP — v3.2
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

CUSTOM INSTRUCTIONS:
  □ system_prompt.md (updated with new commands)

PROJECT KNOWLEDGE:
  
  Core System:
  □ onboarding_flow.md
  □ multi_deal_management.md
  □ deal_memory.md                  ← NEW
  □ deal_lifecycle_engine.md        ← NEW

  Intelligence Layer:
  □ web_research_protocol.md
  □ source_citation_rules.md
  □ investment_thesis.md            ← NEW
  □ deal_strategy.md                ← NEW
  □ qa_checklist.md                 ← NEW

  Deal Analysis:
  □ valuation_logic.md (updated — trimmed DCF)
  □ qoe_framework.md
  □ deal_structure.md
  □ risk_framework.md

  Marketing & Outreach:
  □ cim_template.md (updated — thesis integration)
  □ teaser_template.md
  □ buyer_targeting.md

  Deal Execution:
  □ loi_evaluation.md
  □ seller_prep.md
  □ deal_screening.md
  □ engagement_guidance.md

SETTINGS:
  □ Web Search → ENABLED

TOTAL: 20 knowledge files + 1 system prompt = 21 files
ESTIMATED CONTEXT: ~35,000 tokens
---
----


### First Use

```
  □ Type /new [deal name]
  □ Paste deal info OR type /start
  □ Agent parses → organizes → asks for gaps
  □ Run /screening (should we take this deal?)
  □ Run /readiness (is the seller ready?)
  □ Run /valuation (what's it worth?)
  □ Run /all (generate everything)
  □ Add more deals with /new
  □ View pipeline with /deals
```

---

## API Integration

For developers building this into a custom application.

### Basic Implementation

```python
import anthropic
import json
import os

class MAAAgent:
    def __init__(self):
        self.client = anthropic.Anthropic()
        self.system = self._build_system()
        self.messages = []

    def _build_system(self):
        files = [
            "system_prompt.md", "onboarding_flow.md",
            "multi_deal_management.md",
            "web_research_protocol.md", "source_citation_rules.md",
            "valuation_logic.md", "qoe_framework.md",
            "deal_structure.md", "risk_framework.md",
            "cim_template.md", "teaser_template.md",
            "buyer_targeting.md", "loi_evaluation.md",
            "seller_prep.md", "deal_screening.md",
            "engagement_guidance.md"
        ]
        sections = []
        for f in files:
            path = os.path.join("agent", f)
            if os.path.exists(path):
                with open(path) as fh:
                    sections.append(fh.read())
        return "\n\n---\n\n".join(sections)

    def chat(self, user_message: str) -> str:
        self.messages.append({"role": "user", "content": user_message})
        response = self.client.messages.create(
            model="claude-sonnet-4-20250514",
            max_tokens=16000,
            system=self.system,
            messages=self.messages
        )
        reply = response.content[0].text
        self.messages.append({"role": "assistant", "content": reply})
        return reply


# Usage
agent = MAAAgent()
print(agent.chat("/new ABC Roofing"))
print(agent.chat("Roofing company in Charlotte NC, $4.2M revenue, $850K SDE..."))
print(agent.chat("/valuation"))
print(agent.chat("/deals"))
```

### Code Status

> ⚠️ This is reference architecture, not production code.
> Before deployment, add: error handling, rate limiting,
> streaming, token management, caching, and tests.
> Estimated dev time to production: 20–40 hours.

---

## Maintenance

| Task | Frequency | Source |
|------|-----------|--------|
| Update embedded multiples | Quarterly | BizBuySell Insight Report, IBBA Market Pulse |
| Verify SBA rate assumptions | Monthly | sba.gov |
| Review risk framework | Semi-annually | Recent deal experience |
| Optimize outreach templates | After every 50 sends | Response rate data |
| Full system review | Annually | All files against current market |

### How to Update Embedded Data

1. Download latest BizBuySell Insight Report (free, quarterly)
2. Open `valuation_logic.md`
3. Update the SDE and EBITDA multiple tables
4. Add date stamp: `⚠️ Last reviewed: [DATE] by [NAME]`
5. Re-upload to Project Knowledge

---

## Limitations

| Limitation | Impact | Workaround |
|-----------|--------|------------|
| **Paywalled data sources** | Live search won't access PitchBook, Capital IQ, GF Data | Agent recommends manual lookup; uses embedded fallbacks |
| **Web search reliability** | LMM transaction multiples found ~30-40% of the time | Embedded benchmarks used as fallback, clearly flagged |
| **Content, not design** | CIM output is structured text, not a formatted PDF | Format in Canva, Google Docs, or Word before sending to buyers |
| **US-focused** | Multiples, SBA rules, deal structures assume US transactions | Modify for international deals |
| **Not legal/financial advice** | Analytical tool only | Always verify with CPA and attorney |
| **$1M–$5M EBITDA optimized** | Embedded multiples tuned for this range | Adjust `valuation_logic.md` for deals outside this range |

---

## Customization & Support

### Common Refinements

| What to Customize | Which File to Edit |
|-------------------|--------------------|
| Multiple ranges for your industry focus | `valuation_logic.md` |
| Industry-specific risk factors | `risk_framework.md` |
| Outreach email voice and tone | `buyer_targeting.md` |
| CIM section structure or emphasis | `cim_template.md` |
| Onboarding questions | `onboarding_flow.md` |
| Fee structures | `engagement_guidance.md` |
| SBA eligibility criteria | `deal_structure.md` |

### Improving the Agent Over Time

1. Test on a real deal (anonymize sensitive data)
2. Note where outputs miss the mark
3. Edit the relevant `.md` file
4. Re-upload to Project Knowledge
5. Repeat

### Version History

| Version | Date | Changes |
|---------|------|---------|
| v3.1 | Current | Multi-deal management, unstructured intake, deal dashboard |
| v3.0 | — | Interactive onboarding, auto-propagation, command system |
| v2.1 | — | QoE framework, deal structuring, LOI evaluation, seller prep |
| v2.0 | — | Live web research, source citations, anti-hallucination rules |
| v1.0 | — | Core valuation, CIM/teaser templates, buyer targeting, risk framework |
