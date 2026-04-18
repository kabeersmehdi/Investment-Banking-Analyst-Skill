# M&A ANALYST AGENT v3.0
# Interactive Onboarding + Auto-Propagation
# Lower Middle Market | Sell-Side | Production-Grade
# ══════════════════════════════════════════════════════

## What This Is

An AI analyst for sell-side M&A brokers in the lower middle market
($1M–$5M EBITDA). It replaces 15–25 hours of analyst work per deal.

**What's new in v3.0:**
- `/start` command launches interactive onboarding
- Agent asks every question it needs — you just answer
- All outputs auto-populate from your answers
- Update any field with `/update` — affected outputs flagged
- Risk flags auto-detected from your answers
- SBA feasibility auto-checked
- No more copying data between files

---

## How It Works

### Step 1: Type `/start`
The agent walks you through 7 phases of questions:

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

### Step 2: Confirm Your Data
After all phases, the agent shows a full DEAL CONTEXT SUMMARY.
You confirm or correct anything.

### Step 3: Run Any Command
Every command auto-populates from your answers:

| Command | What It Does |
|---------|-------------|
| `/valuation` | Full valuation with live comps + scenarios |
| `/cim` | Complete CIM with live industry data |
| `/teaser` | Anonymous 1-page teaser |
| `/buyers` | Buyer list + outreach emails |
| `/risks` | Risk report with auto-detected flags |
| `/qoe` | Quality of Earnings analysis |
| `/structure` | SBA model + deal structure scenarios |
| `/loi` | Evaluate LOI(s) received |
| `/readiness` | Seller readiness assessment |
| `/screening` | Should we take this engagement? |
| `/status` | Show current deal context + outputs generated |
| `/update` | Change a data point — flags affected outputs |
| `/export` | Export deal context as JSON |
| `/all` | Generate everything |

### Step 4: Iterate
Change anything with `/update [field] [value]`.
The agent tells you which outputs need regeneration.

---

## Quick Start (10 Minutes)

### Claude.ai Projects (Recommended)

1. **Create Project**
   - Go to claude.ai → Projects → Create Project
   - Name: `M&A Analyst Agent`

2. **Set Custom Instructions**
   - Copy entire contents of `system_prompt.md`
   - Paste into Custom Instructions

3. **Upload Knowledge Files** (all of these):
   ```
   ✅ onboarding_flow.md
   ✅ web_research_protocol.md
   ✅ source_citation_rules.md
   ✅ valuation_logic.md
   ✅ qoe_framework.md
   ✅ deal_structure.md
   ✅ risk_framework.md
   ✅ cim_template.md
   ✅ teaser_template.md
   ✅ buyer_targeting.md
   ✅ loi_evaluation.md
   ✅ seller_prep.md
   ✅ deal_screening.md
   ✅ engagement_guidance.md
   ```

4. **Enable Web Search** in Claude settings

5. **Start a conversation and type:** `/start`

That's it. The agent takes over from there.

---

## File Index

| # | File | Purpose | Load |
|---|------|---------|------|
| 1 | `system_prompt.md` | Master instructions + commands | Custom Instructions |
| 2 | `onboarding_flow.md` | /start questionnaire + auto-propagation | Knowledge |
| 3 | `web_research_protocol.md` | Search rules + source hierarchy | Knowledge |
| 4 | `source_citation_rules.md` | Citation standards | Knowledge |
| 5 | `valuation_logic.md` | Multiples + adjustments + revenue scoring | Knowledge |
| 6 | `qoe_framework.md` | EBITDA bridge + NWC + revenue cuts | Knowledge |
| 7 | `deal_structure.md` | SBA + seller note + earnout models | Knowledge |
| 8 | `risk_framework.md` | Auto-detection rules + narratives | Knowledge |
| 9 | `cim_template.md` | CIM section structure | Knowledge |
| 10 | `teaser_template.md` | Anonymous teaser structure | Knowledge |
| 11 | `buyer_targeting.md` | Persona matching + outreach | Knowledge |
| 12 | `loi_evaluation.md` | LOI comparison + scoring | Knowledge |
| 13 | `seller_prep.md` | Readiness checklist | Knowledge |
| 14 | `deal_screening.md` | Engagement screening | Knowledge |
| 15 | `engagement_guidance.md` | Fee structures | Knowledge |
| 16 | `input_schema.json` | Deal context structure (API) | Reference |
| 17 | `output_schema.json` | Output structure (API) | Reference |

---

## Command Reference

### Core Commands

```
/start              Launch deal onboarding (REQUIRED FIRST)
/valuation          Generate valuation with live comps
/cim                Generate full CIM
/teaser             Generate anonymous teaser
/buyers             Generate buyer list + outreach
/risks              Generate risk report
/qoe                Generate Quality of Earnings analysis
/structure          Generate deal structure models
/all                Generate all of the above
```

### Deal Management Commands

```
/status             Show deal context summary + outputs generated
/update [field] [v] Update a field (e.g., /update revenue_ttm 4500000)
/export             Export deal context as JSON
```

### Evaluation Commands

```
/loi [terms]        Evaluate one or more LOIs
/readiness          Run seller readiness check
/screening          Should we take this engagement?
```

### Examples

```
/start
→ Begins the 7-phase onboarding questionnaire

/valuation
→ Generates bear/base/bull valuation with live comps

/update owner_hours_per_week 35
→ Updates context, flags risk changes

/loi All cash $3.2M, 45-day diligence, SBA pre-approved
→ Evaluates LOI against deal context

/buyers
→ Searches web for active acquirers, builds tiered list

/status
→ Shows what data you've provided and what's been generated
```

---

## What the Agent Does Automatically

After `/start` completes, the agent:

| Action | Trigger | Output |
|--------|---------|--------|
| Calculates SDE | Phase 3 answers | SDE = Net Income + all add-backs |
| Calculates EBITDA | Phase 3 answers | EBITDA = SDE - market-rate salary |
| Scores revenue quality | Phase 4 answers | 1-10 score → multiple impact |
| Detects risks | All phases | Auto-flagged ⚠️ list |
| Matches buyer persona | Phases 2+4+5+6 | Primary + secondary buyer type |
| Checks SBA feasibility | Phases 2+3+6 | DSCR calculation |
| Identifies data gaps | All phases | Missing items flagged |

---

## Auto-Propagation: How Updates Flow

When you change a data point, the agent tracks what's affected:

```
┌─────────────────┐
│ Revenue changes  │
├─────────────────┤
│ Affects:        │
│ → SDE margin    │
│ → Valuation     │
│ → CIM financials│
│ → Teaser        │
│ → SBA model     │
│ → Buyer returns │
└─────────────────┘

┌─────────────────┐
│ Customer conc.  │
│ changes         │
├─────────────────┤
│ Affects:        │
│ → Risk flags    │
│ → Multiple adj. │
│ → Valuation     │
│ → Risk narratives│
│ → Buyer targeting│
│ → LOI evaluation│
└─────────────────┘

┌─────────────────┐
│ Owner role      │
│ changes         │
├─────────────────┤
│ Affects:        │
│ → Risk flags    │
│ → Multiple adj. │
│ → CIM ops section│
│ → Buyer targeting│
│ → Transition plan│
└─────────────────┘
```

---

## API Integration

### Basic Setup

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
        self.messages.append({
            "role": "user",
            "content": user_message
        })
        response = self.client.messages.create(
            model="claude-sonnet-4-20250514",
            max_tokens=16000,
            system=self.system,
            messages=self.messages
        )
        assistant_msg = response.content[0].text
        self.messages.append({
            "role": "assistant",
            "content": assistant_msg
        })
        return assistant_msg

# Usage
agent = MAAAgent()

# Start onboarding
print(agent.chat("/start"))

# Answer Phase 1
print(agent.chat("""
Company: ABC Roofing LLC
Does residential and commercial roofing in Charlotte NC area.
Industry: Roofing Services
Location: Charlotte, North Carolina
18 years in business
Mostly B2B (commercial) and B2C (residential)
"""))

# Continue answering phases...
# Agent tracks all context and auto-populates outputs

# Generate valuation after onboarding
print(agent.chat("/valuation"))

# Update a field
print(agent.chat("/update revenue_ttm 4500000"))

# Check status
print(agent.chat("/status"))
```

---

## Maintenance Schedule

| Task | Frequency | How |
|------|-----------|-----|
| Update embedded multiples | Quarterly | Edit valuation_logic.md with latest BizBuySell/IBBA data |
| Check SBA rate assumptions | Monthly | Verify against sba.gov |
| Review risk framework | Semi-annually | Add risks from recent deal experience |
| Update outreach templates | After 50 sends | Optimize based on response rates |
| Full system review | Annually | Review all files against current market |

---

## Limitations

⚠️ **Web search won't always find LMM multiples.** Most
transaction data is paywalled. Agent uses embedded fallbacks
and recommends manual verification.

⚠️ **Outputs are content, not formatted documents.** CIM needs
formatting in Canva/Docs/Word before sending to buyers.

⚠️ **Not legal or financial advice.** Always verify with CPA
and attorney before acting on outputs.

⚠️ **US-focused.** Multiples, SBA rules, deal structures assume
US transactions.

⚠️ **Optimized for $1M-$5M EBITDA.** Adjust embedded multiples
for deals outside this range.

---

## Setup Checklist

```
CLAUDE PROJECT SETUP
□ system_prompt.md          → Custom Instructions
□ onboarding_flow.md        → Project Knowledge
□ web_research_protocol.md  → Project Knowledge
□ source_citation_rules.md  → Project Knowledge
□ valuation_logic.md        → Project Knowledge
□ qoe_framework.md          → Project Knowledge
□ deal_structure.md         → Project Knowledge
□ risk_framework.md         → Project Knowledge
□ cim_template.md           → Project Knowledge
□ teaser_template.md        → Project Knowledge
□ buyer_targeting.md        → Project Knowledge
□ loi_evaluation.md         → Project Knowledge
□ seller_prep.md            → Project Knowledge
□ deal_screening.md         → Project Knowledge
□ engagement_guidance.md    → Project Knowledge
□ Web Search               → ENABLED

FIRST USE
□ Type /start
□ Answer all 7 phases
□ Confirm deal context
□ Run /screening (should we take this?)
□ Run /readiness (is seller ready?)
□ Run /valuation (what's it worth?)
□ Run /all (generate everything)
```

---

## Support

This is an open skill configuration. To improve it:
1. Test on a real deal (anonymize data)
2. Note where outputs miss the mark
3. Edit the relevant .md file
4. Re-upload to Claude Project

The most common refinements:
- Adjust embedded multiples for your industry focus
- Add industry-specific risk factors from your experience
- Customize email templates to your firm's voice
- Add your firm's branding references to CIM template
