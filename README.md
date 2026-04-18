# M&A Analyst Agent v3.2

**Lower Middle Market · Sell-Side · Production-Grade**

An AI deal execution engine for sell-side M&A brokers in the lower middle market ($1M–$5M EBITDA). Replaces 15–25 hours of analyst work per deal.

---

## Table of Contents

1.  [What This Does](#1-what-this-does)
2.  [Quick Start](#2-quick-start)
3.  [Commands](#3-commands)
4.  [Deal Onboarding](#4-deal-onboarding)
5.  [Multi-Deal Management](#5-multi-deal-management)
6.  [Unstructured Intake](#6-unstructured-intake)
7.  [Deal Memory & Consistency](#7-deal-memory--consistency)
8.  [Investment Thesis & Strategy](#8-investment-thesis--strategy)
9.  [Quality Assurance](#9-quality-assurance)
10. [Auto-Propagation](#10-auto-propagation)
11. [Deal Lifecycle](#11-deal-lifecycle)
12. [File Index](#12-file-index)
13. [Setup Checklist](#13-setup-checklist)
14. [API Integration](#14-api-integration)
15. [Maintenance](#15-maintenance)
16. [Limitations](#16-limitations)
17. [Customization](#17-customization)
18. [Version History](#18-version-history)

---

## 1. What This Does

### Capabilities

| Capability | Description |
|-----------|-------------|
| **Valuation** | SDE/EBITDA multiples with live market comps, scenario analysis (bear/base/bull) |
| **Investment Thesis** | Buyer-facing narrative: headline, 3 reasons to buy, why now, fear neutralizers |
| **Deal Strategy** | Market clearing price, buyer ranking, deal killers, process plan, negotiation leverage |
| **CIM Generation** | Full 8-section Confidential Information Memorandum with live industry data |
| **Teaser Creation** | Anonymous 1-page buyer-facing teaser |
| **Buyer Targeting** | Persona matching, live acquirer research, outreach emails, follow-up sequences |
| **Risk Analysis** | Auto-detected flags with severity ratings and mitigation narratives |
| **Quality of Earnings** | EBITDA bridge, NWC analysis, revenue cuts, pro forma P&L |
| **Deal Structuring** | SBA modeling, seller notes, earnouts, buyer affordability matrix |
| **LOI Evaluation** | Offer comparison, deal certainty scoring, red flag identification |
| **Seller Readiness** | Pre-market checklist with gap identification and timeline |
| **Deal Screening** | Should you take this engagement? Fee economics and marketability |
| **QA System** | 5-level consistency and quality checks across all outputs |

### Key Features

| Feature | What It Means |
|---------|--------------|
| `/start` onboarding | Agent asks every question — you just answer |
| Unstructured intake | Paste notes, emails, bullets — agent parses automatically |
| Multi-deal pipeline | Manage all active deals in one conversation with `/deals` dashboard |
| Deal Memory | Single source of truth — numbers never contradict across outputs |
| Investment thesis | Every deal gets a compelling buyer narrative, not just analysis |
| Deal strategy | Agent advises on pricing, buyer ranking, deal killers, negotiation |
| Live web research | Searches for current multiples, market data, active buyers |
| Auto-propagation | Update one field, all affected outputs get flagged |
| QA system | 5-level check catches number errors, narrative contradictions, and weak claims |
| Source citations | Every market data point is cited or flagged as an embedded benchmark |

---

## 2. Quick Start

**Time to set up: 10 minutes. No code required.**

| Step | Action |
|------|--------|
| 1 | Go to [claude.ai](https://claude.ai) → **Projects** → **Create Project** → Name it `M&A Analyst Agent` |
| 2 | Copy contents of `system_prompt.md` → Paste into **Custom Instructions** |
| 3 | Upload all `.md` files from the [File Index](#12-file-index) to **Project Knowledge** |
| 4 | Enable **web search** in Claude settings |
| 5 | Open a conversation and type `/new [deal name]` |

Then either type `/start` for guided onboarding, or paste everything you know about the deal. The agent takes over from there.

---

## 3. Commands

### Deal Management

| Command | What It Does |
|---------|-------------|
| `/new [name]` | Create a new deal and make it active |
| `/deals` | Show pipeline dashboard of all active deals |
| `/deals all` | Include archived deals in dashboard |
| `/deal [name]` | Switch active deal (fuzzy matching supported) |
| `/archive [name]` | Archive a deal with reason (closed / dead / paused) |
| `/rename [old] [new]` | Rename a deal |
| `/compare [a] [b]` | Side-by-side comparison of two deals |

### Onboarding

| Command | What It Does |
|---------|-------------|
| `/start` | Launch guided 7-phase questionnaire |
| *(paste info)* | Agent parses unstructured text automatically |

### Analysis

| Command | What It Does |
|---------|-------------|
| `/valuation` | Full valuation with live comps + bear/base/bull scenarios |
| `/cim` | Complete CIM with live industry data |
| `/teaser` | Anonymous 1-page teaser |
| `/buyers` | Buyer list + outreach emails with live acquirer research |
| `/risks` | Risk report with auto-detected flags |
| `/qoe` | Quality of Earnings analysis |
| `/structure` | SBA model + deal structure scenarios |
| `/all` | Generate all of the above |

### Strategy

| Command | What It Does |
|---------|-------------|
| `/strategy` | Full deal strategy: clearing price, buyer ranking, deal killers, process plan, negotiation leverage |
| `/thesis` | Generate or regenerate the investment thesis |
| `/timeline` | Show deal event history |

### Evaluation

| Command | What It Does |
|---------|-------------|
| `/loi [terms]` | Evaluate one or more LOIs against deal context |
| `/readiness` | Seller readiness assessment |
| `/screening` | Should we take this engagement? |

### Quality

| Command | What It Does |
|---------|-------------|
| `/check` | Quick consistency check — numbers match across all outputs? |
| `/qa` | Full 5-level quality assurance (numbers, narrative, logic, completeness, anti-BS) |

### Context

| Command | What It Does |
|---------|-------------|
| `/status` | Show deal context summary + which outputs have been generated |
| `/update [field] [value]` | Update a field — flags all affected outputs |
| `/gaps` | Show all missing or incomplete fields |
| `/export` | Export deal context as JSON |

### Examples

```
/new Charlotte Roofing              → Creates new deal, prompts for info
/start                              → Launches guided onboarding
/valuation                          → Bear/base/bull with live comps
/strategy                           → Clearing price + buyer ranking + deal killers
/thesis                             → Investment thesis with fear neutralizers
/update revenue_ttm 4500000         → Updates context, flags affected outputs
/deal summit                        → Switches to "Project Summit"
/deals                              → Shows full pipeline dashboard
/loi All cash $3.2M, 45-day DD     → Evaluates LOI against deal context
/compare ABC Metro                  → Side-by-side deal comparison
/qa                                 → Full quality check before sending to buyers
/check                              → Quick number consistency verification
```

---

## 4. Deal Onboarding

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
| Generates investment thesis | All phases | Headline + 3 reasons + why now + fear neutralizers |
| Matches buyer persona | Phases 2+4+5+6 | Primary + secondary buyer type |
| Checks SBA feasibility | Phases 2+3+6 | DSCR calculation |
| Identifies data gaps | All phases | Missing items flagged by priority |

---

## 5. Multi-Deal Management

Brokers run 5–15 deals at once. This agent manages the full pipeline.

### Dashboard (`/deals`)

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📊 DEAL DASHBOARD
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

  #  Deal Name          Industry    Revenue   SDE     Stage         Data
  ─  ─────────          ────────    ───────   ───     ─────         ────
→ 1  ABC Roofing        Roofing     $4.2M     $850K   CONTEXT DONE  92%
  2  Project Summit     HVAC        $6.1M     $1.4M   IN MARKET     100%
  3  Metro HVAC         HVAC        $2.8M     —       INTAKE        40%
  4  Lakeside Plumbing  Plumbing    $3.5M     $620K   LOI STAGE     100%

→ = Active Deal | Archived: 2 (type /deals all)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
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

When you switch, the agent shows a brief summary of the deal and its current stage.

### Comparing Deals

```
/compare ABC Metro
```

Produces a side-by-side table: financials, valuation, risk rating, data completeness, and key differences between two deals.

---

## 6. Unstructured Intake

You don't have to use the guided questionnaire. Just paste whatever you have.

### Example: Quick Dump

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
2. Organize it into the standard deal context
3. Show you what it captured
4. Tell you exactly what's missing, grouped by priority
5. Ask: fill in gaps now, or work with what you have?

### Example: Partial Info + Question

```
/new Quick Screen

HVAC company, $3M revenue, owner wants $5M for it. Is that realistic?
```

The agent creates the deal, notes the gaps, and gives you a directional answer immediately — flagging every assumption.

### What the Parser Catches

| Data Type | Examples It Recognizes |
|-----------|----------------------|
| Revenue | "$4.2M revenue", "top line is 4.2", "does about 4 mil" |
| SDE/EBITDA | "$850K SDE", "cash flow of 850", "earns about 850" |
| Employees | "22 employees", "team of 22", "22 people" |
| Years | "18 years", "since 2006", "been around 18 years" |
| Location | "Charlotte NC", "in North Carolina", "Charlotte area" |
| Owner info | "owner is 62", "does all the sales", "wants to retire" |
| Customers | "top 3 are 40%", "biggest customer is 20%", "no contracts" |
| Deal terms | "SBA eligible", "wants all cash", "open to seller note" |
| Risks | "messy books", "owner dependent", "lease is up" |
| Growth | "could expand to commercial", "hasn't done marketing" |

---

## 7. Deal Memory & Consistency

### The Problem This Solves

In M&A, if the CIM says EBITDA is $700K but the valuation uses $710K, the deal loses credibility. The Deal Memory Layer prevents this.

### How It Works

After onboarding (guided or unstructured), the agent builds a **Deal Memory** — a single source of truth for every number, fact, and narrative in the deal. Every output reads from Deal Memory. Nothing contradicts it.

### Consistency Rules

| Rule | What It Means |
|------|--------------|
| **One Number, One Source** | Every financial figure in every output matches Deal Memory exactly |
| **SDE/EBITDA Lock** | Once calculated, the same SDE and EBITDA appear in valuation, CIM, teaser, buyer emails, SBA model, LOI evaluation |
| **Adjustment Consistency** | Add-backs appear identically in QoE, CIM, and valuation — same description, same dollar amount |
| **Risk Consistency** | If a risk is in Deal Memory, it appears in the risk report AND the CIM AND buyer targeting |
| **Growth Consistency** | Growth levers described the same way in CIM, teaser, thesis, and valuation |
| **Narrative Consistency** | Investment thesis headline and core story reflected in every buyer-facing document |

### Consistency Commands

| Command | What It Does |
|---------|-------------|
| `/check` | Quick pass: do all numbers match across generated outputs? |
| `/qa` | Full 5-level check (see [Quality Assurance](#9-quality-assurance)) |

---

## 8. Investment Thesis & Strategy

### Investment Thesis (`/thesis`)

Every deal gets a buyer-facing narrative — not just analysis. The thesis answers three questions buyers ask in the first 30 seconds:

| Question | Thesis Component |
|----------|-----------------|
| Why should I buy THIS business? | **Headline** — one sentence that makes a buyer lean in |
| What am I really getting? | **Three Reasons to Buy** — specific, evidence-backed, memorable |
| Why should I buy it NOW? | **Why Now** — seller motivation + market timing + business momentum |

The thesis also pre-builds **Buyer Fear Neutralizers** — for every risk in Deal Memory, a proactive narrative that addresses what buyers will worry about before they bring it up.

### Thesis Consistency

The investment thesis drives all marketing materials:

| Document | How Thesis Appears |
|----------|-------------------|
| CIM Executive Summary | Headline as opening line, three reasons as investment highlights |
| Teaser | Headline adapted for anonymous format, three reasons as key highlights |
| Buyer Outreach Email | Headline as subject line hook, top reason in body |
| CIM Buyer Rationale | Full thesis with supporting evidence |
| Valuation Summary | Three reasons referenced as key value drivers |

### Deal Strategy (`/strategy`)

Goes beyond analysis to strategic advice:

| Strategy Component | What It Answers |
|-------------------|----------------|
| **Market Clearing Price** | What will a buyer ACTUALLY pay? (not just what multiples say) |
| **Buyer Ranking** | Who is most likely to close? Scored by affordability, fit, capability, certainty, willingness to pay |
| **Top 3 Deal Killers** | What will kill this deal + prevention plan for each |
| **Process Strategy** | How to run the sell-side process: broad vs. targeted vs. curated |
| **Negotiation Leverage Map** | Seller leverage vs. buyer leverage, with response scripts |

---

## 9. Quality Assurance

### The QA System (`/qa`)

Before anything goes to a buyer, the agent runs a 5-level quality check:

| Level | What It Checks | Catches |
|-------|---------------|---------|
| **1. Numbers** | Every financial figure matches Deal Memory across all outputs | CIM says $710K but valuation says $700K |
| **2. Narrative** | Thesis, risks, growth levers consistent across all documents | CIM tells one story, teaser tells another |
| **3. Logic** | Margins reasonable, growth claims match data, no contradictions | "Strong management team" but no #2 exists |
| **4. Completeness** | All required CIM sections present, all data cited | Missing industry overview, unsourced claims |
| **5. Anti-BS** | Every claim has evidence in Deal Memory | "Diversified customer base" but top 3 = 50% |

### QA Output

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
✅ QA CHECK — ABC Roofing
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

NUMBERS:     ✅ All consistent (12/12 passed)
NARRATIVE:   ✅ All consistent (8/8 passed)
LOGIC:       ⚠️ 1 flag (add-backs at 38% of net income)
COMPLETE:    ✅ All sections present
ANTI-BS:     ⚠️ 1 weak claim (rephrase "diversified")

OVERALL: PASS WITH 2 WARNINGS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

### When QA Runs Automatically

| Trigger | Levels Run |
|---------|-----------|
| Any financial output | Level 1 (numbers) |
| CIM, teaser, buyer emails | Levels 1 + 2 (numbers + narrative) |
| Valuation, QoE, deal structure | Levels 1 + 3 (numbers + logic) |
| Full CIM or `/all` | All 5 levels |

---

## 10. Auto-Propagation

When you update any field with `/update`, the agent tracks what's affected:

| Field Changed | Outputs Affected |
|--------------|-----------------|
| Revenue | SDE margin, valuation, CIM financials, teaser, SBA model, buyer returns |
| Add-backs | SDE, EBITDA, valuation, QoE, CIM financials, thesis |
| Customer concentration | Risk flags, multiple adjustment, valuation, risk narratives, buyer targeting, LOI evaluation |
| Owner role | Risk flags, multiple adjustment, CIM ops section, buyer targeting, transition plan, thesis fear neutralizers |
| Asking price | Deal structure, SBA feasibility, buyer affordability, teaser, strategy clearing price |

After flagging affected outputs, the agent asks: *"Want me to regenerate any of these now?"*

---

## 11. Deal Lifecycle

```
/new [name]
    │
    ▼
  INTAKE ─────────── /start or paste info
    │
    ▼
  CONTEXT COMPLETE ── all critical fields filled
    │                  (auto: thesis + risk flags generated)
    ├── /screening ─── Should we take this?
    ├── /readiness ─── Is seller ready?
    │
    ▼
  VALUED ──────────── /valuation + /strategy
    │
    ▼
  MARKETING ─────────  /cim + /teaser
    │
    ▼
  OUTREACH ────────── /buyers
    │
    ▼
  IOI REVIEW ──────── IOIs received
    │
    ▼
  LOI STAGE ─────────  /loi
    │
    ▼
  DILIGENCE ─────────  /update stage DILIGENCE
    │
    ▼
  CLOSING ────────── /update stage CLOSING
    │
    ▼
  ARCHIVED ────────── /archive (closed / dead / paused)
```

Stages transition automatically based on commands run. Override anytime with `/update stage [STAGE NAME]`. View history with `/timeline`.

At each stage transition, the agent suggests what to do next.

---

## 12. File Index

### System Configuration

| # | File | Purpose | Upload To |
|---|------|---------|-----------|
| 1 | `system_prompt.md` | Master instructions, commands, behavioral rules | Custom Instructions |

### Core System

| # | File | Purpose | Upload To |
|---|------|---------|-----------|
| 2 | `onboarding_flow.md` | Guided questionnaire + unstructured intake parsing | Project Knowledge |
| 3 | `multi_deal_management.md` | Deal registry, dashboard, switching, comparison | Project Knowledge |
| 4 | `deal_memory.md` | Single source of truth + consistency rules | Project Knowledge |
| 5 | `deal_lifecycle_engine.md` | Stage tracking, transitions, stage-appropriate behavior | Project Knowledge |

### Intelligence Layer

| # | File | Purpose | Upload To |
|---|------|---------|-----------|
| 6 | `web_research_protocol.md` | Search triggers, query library, source hierarchy | Project Knowledge |
| 7 | `source_citation_rules.md` | Citation format, anti-hallucination rules | Project Knowledge |
| 8 | `investment_thesis.md` | Thesis generation: headline, reasons, why now, fear neutralizers | Project Knowledge |
| 9 | `deal_strategy.md` | Clearing price, buyer ranking, deal killers, process, negotiation | Project Knowledge |
| 10 | `qa_checklist.md` | 5-level quality assurance system | Project Knowledge |

### Deal Analysis

| # | File | Purpose | Upload To |
|---|------|---------|-----------|
| 11 | `valuation_logic.md` | Multiples, adjustments, revenue quality scoring, scenarios | Project Knowledge |
| 12 | `qoe_framework.md` | EBITDA bridge, working capital, revenue cuts, pro forma | Project Knowledge |
| 13 | `deal_structure.md` | SBA modeling, seller notes, earnouts, affordability | Project Knowledge |
| 14 | `risk_framework.md` | Auto-detection rules, severity ratings, mitigation narratives | Project Knowledge |

### Marketing & Outreach

| # | File | Purpose | Upload To |
|---|------|---------|-----------|
| 15 | `cim_template.md` | Full CIM structure with thesis integration | Project Knowledge |
| 16 | `teaser_template.md` | Anonymous teaser structure | Project Knowledge |
| 17 | `buyer_targeting.md` | Buyer personas, outreach templates, follow-up sequences | Project Knowledge |

### Deal Execution

| # | File | Purpose | Upload To |
|---|------|---------|-----------|
| 18 | `loi_evaluation.md` | LOI comparison matrix, deal certainty scoring, red flags | Project Knowledge |
| 19 | `seller_prep.md` | Pre-market readiness checklist | Project Knowledge |
| 20 | `deal_screening.md` | Engagement screening, fee economics, walk-away triggers | Project Knowledge |
| 21 | `engagement_guidance.md` | Broker fee structures, engagement terms | Project Knowledge |

### Schemas (API Only)

| # | File | Purpose | Use |
|---|------|---------|-----|
| 22 | `input_schema.json` | Structured deal intake format | Local reference |
| 23 | `output_schema.json` | Structured output parsing format | Local reference |

**Total: 21 knowledge files · 1 system prompt · 2 schemas · ~35,000 tokens**

---

## Deployment

### Option A: Claude Code Skill

For developers using Claude Code (CLI/IDE).

**Directory structure:**
```
~/.claude/skills/ma-analyst-agent/
├── SKILL.md
├── core/
│   ├── onboarding_flow.md
│   ├── multi_deal_management.md
│   ├── deal_memory.md
│   └── deal_lifecycle_engine.md
├── intelligence/
│   ├── web_research_protocol.md
│   ├── source_citation_rules.md
│   ├── investment_thesis.md
│   ├── deal_strategy.md
│   └── qa_checklist.md
├── analysis/
│   ├── valuation_logic.md
│   ├── qoe_framework.md
│   ├── deal_structure.md
│   └── risk_framework.md
├── marketing/
│   ├── cim_template.md
│   ├── teaser_template.md
│   └── buyer_targeting.md
├── execution/
│   ├── loi_evaluation.md
│   ├── seller_prep.md
│   ├── deal_screening.md
│   └── engagement_guidance.md
└── schemas/
    ├── input_schema.json
    └── output_schema.json
```

**Setup:**
```bash
mkdir -p ~/.claude/skills/ma-analyst-agent/{core,intelligence,analysis,marketing,execution,schemas}
# Copy all files into their respective directories
# SKILL.md goes in the root of ma-analyst-agent/
```

Claude Code will auto-discover the skill and activate it when 
M&A-related topics are discussed or any `/command` is used.

### Option B: Claude.ai Project

For brokers using Claude in the browser. No code required.

1. Go to claude.ai → Projects → Create Project
2. Paste `SKILL.md` content (below the YAML) into Custom Instructions
3. Upload all 20 `.md` files to Project Knowledge (flat, no folders)
4. Enable web search
5. Type `/new [deal name]`

### Option C: Anthropic API

For developers building custom applications.

```python
# See API Integration section below
```



---

## 13. Setup Checklist

```
CUSTOM INSTRUCTIONS
  □  system_prompt.md

PROJECT KNOWLEDGE — Core System
  □  onboarding_flow.md
  □  multi_deal_management.md
  □  deal_memory.md
  □  deal_lifecycle_engine.md

PROJECT KNOWLEDGE — Intelligence Layer
  □  web_research_protocol.md
  □  source_citation_rules.md
  □  investment_thesis.md
  □  deal_strategy.md
  □  qa_checklist.md

PROJECT KNOWLEDGE — Deal Analysis
  □  valuation_logic.md
  □  qoe_framework.md
  □  deal_structure.md
  □  risk_framework.md

PROJECT KNOWLEDGE — Marketing & Outreach
  □  cim_template.md
  □  teaser_template.md
  □  buyer_targeting.md

PROJECT KNOWLEDGE — Deal Execution
  □  loi_evaluation.md
  □  seller_prep.md
  □  deal_screening.md
  □  engagement_guidance.md

SETTINGS
  □  Web Search → ENABLED
```

### First Use

```
  □  Type /new [deal name]
  □  Paste deal info OR type /start
  □  Agent parses → organizes → asks for gaps
  □  Run /screening — should we take this deal?
  □  Run /readiness — is the seller ready?
  □  Run /valuation — what's it worth?
  □  Run /strategy — how do we run this deal?
  □  Run /all — generate everything
  □  Run /qa — verify everything before sending
  □  Add more deals with /new
  □  View pipeline with /deals
```

---

## 14. API Integration

For developers building this into a custom application.

```python
import anthropic
import os

class MAAAgent:
    def __init__(self):
        self.client = anthropic.Anthropic()
        self.system = self._build_system()
        self.messages = []

    def _build_system(self):
        files = [
            "system_prompt.md", "onboarding_flow.md",
            "multi_deal_management.md", "deal_memory.md",
            "deal_lifecycle_engine.md",
            "web_research_protocol.md", "source_citation_rules.md",
            "investment_thesis.md", "deal_strategy.md",
            "qa_checklist.md",
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
print(agent.chat("/strategy"))
print(agent.chat("/qa"))
print(agent.chat("/deals"))
```

> ⚠️ **Code Status:** This is reference architecture, not production code. Before deployment, add error handling, rate limiting, streaming, token management, caching, and tests. Estimated dev time to production: 20–40 hours.

---

## 15. Maintenance

| Task | Frequency | Source |
|------|-----------|--------|
| Update embedded multiples | Quarterly | BizBuySell Insight Report, IBBA Market Pulse |
| Verify SBA rate assumptions | Monthly | sba.gov |
| Review risk framework | Semi-annually | Recent deal experience |
| Optimize outreach templates | After every 50 sends | Response rate data |
| Full system review | Annually | All files against current market |

**How to update embedded data:**
1. Download latest BizBuySell Insight Report (free, quarterly)
2. Open `valuation_logic.md`
3. Update the SDE and EBITDA multiple tables
4. Add: `⚠️ Last reviewed: [DATE] by [NAME]`
5. Re-upload to Project Knowledge

---

## 16. Limitations

| Limitation | Impact | Workaround |
|-----------|--------|------------|
| **Paywalled data** | Can't access PitchBook, Capital IQ, GF Data | Recommends manual lookup; uses embedded fallbacks |
| **Web search reliability** | LMM multiples found ~30–40% of the time | Embedded benchmarks used as fallback, clearly flagged |
| **Content, not design** | CIM is structured text, not a formatted PDF | Format in Canva, Google Docs, or Word before sending |
| **US-focused** | Multiples, SBA rules, structures assume US | Modify knowledge files for international deals |
| **Not legal/financial advice** | Analytical tool only | Always verify with CPA and attorney |
| **$1M–$5M EBITDA** | Embedded multiples tuned for this range | Adjust `valuation_logic.md` for other ranges |

---

## 17. Customization

| What to Customize | Which File to Edit |
|-------------------|--------------------|
| Multiple ranges for your industry | `valuation_logic.md` |
| Industry-specific risk factors | `risk_framework.md` |
| Outreach email voice and tone | `buyer_targeting.md` |
| CIM section structure | `cim_template.md` |
| Investment thesis style | `investment_thesis.md` |
| Deal strategy frameworks | `deal_strategy.md` |
| QA check thresholds | `qa_checklist.md` |
| Onboarding questions | `onboarding_flow.md` |
| Fee structures | `engagement_guidance.md` |
| SBA criteria | `deal_structure.md` |

**To improve the agent over time:**
1. Test on a real deal (anonymize sensitive data)
2. Note where outputs miss the mark
3. Edit the relevant `.md` file
4. Re-upload to Project Knowledge
5. Repeat

---

## 18. Version History

| Version | Changes |
|---------|---------|
| **v3.2** (Current) | Deal Memory layer, investment thesis generator, deal strategy engine, 5-level QA system, deal lifecycle engine, cross-output consistency enforcement |
| v3.1 | Multi-deal management, unstructured intake, deal dashboard, fuzzy deal switching |
| v3.0 | Interactive `/start` onboarding, auto-propagation, command system |
| v2.1 | QoE framework, deal structuring, LOI evaluation, seller prep, deal screening |
| v2.0 | Live web research, source citations, anti-hallucination rules |
| v1.0 | Core valuation, CIM/teaser templates, buyer targeting, risk framework |
