# Investment-Banking-Analyst-Skill

# M&A Analyst Agent v2.0 — Setup Guide
## With Live Web Research & Source Citation

---

## What's New in v2.0
- ✅ Live web search before every valuation
- ✅ Automatic source citation on all market data
- ✅ Industry-specific comp data fetched in real time
- ✅ Active buyer research sourced live
- ✅ Embedded benchmark fallback with clear flagging
- ✅ Research quality scoring on every output
- ✅ Master source log appended to all major outputs

---

## File Index

| File | Purpose |
|------|---------|
| `system_prompt.md` | Upload as Claude system prompt |
| `web_research_protocol.md` | Research rules + source hierarchy |
| `source_citation_rules.md` | Citation standards + anti-hallucination rules |
| `valuation_logic.md` | Valuation methodology + multiples |
| `cim_template.md` | Full CIM generation template |
| `teaser_template.md` | Anonymous 1-page teaser |
| `buyer_targeting.md` | Buyer personas + outreach logic |
| `risk_framework.md` | Risk identification + narratives |
| `input_schema.json` | Deal intake structure |
| `output_schema.json` | Output parsing structure |

---

## Deployment Options

### Option A: Claude.ai Projects (Recommended — No Code)
1. Create a new **Project** in Claude.ai
2. Upload ALL `.md` files to **Project Knowledge**
3. Paste contents of `system_prompt.md` into **Custom Instructions**
4. Enable web search in Claude settings
5. Start a conversation — paste deal inputs in JSON or plain text

> ✅ Claude will automatically search the web when needed and
> cite sources in every output.

---

### Option B: API with Web Search Tool

```python
import anthropic

# Load all reference documents
def load_doc(filename):
    with open(filename, "r") as f:
        return f.read()

docs = {
    "system": load_doc("system_prompt.md"),
    "research": load_doc("web_research_protocol.md"),
    "citations": load_doc("source_citation_rules.md"),
    "valuation": load_doc("valuation_logic.md"),
    "cim": load_doc("cim_template.md"),
    "teaser": load_doc("teaser_template.md"),
    "buyers": load_doc("buyer_targeting.md"),
    "risks": load_doc("risk_framework.md"),
}

# Combine all docs into full system prompt
full_system = docs["system"] + "\n\n---\n\n" + \
    "\n\n---\n\n".join([
        docs["research"],
        docs["citations"],
        docs["valuation"],
        docs["cim"],
        docs["teaser"],
        docs["buyers"],
        docs["risks"]
    ])

client = anthropic.Anthropic()

# Deal input
deal_input = {
    "company_name": "ABC Roofing",
    "industry": "Roofing Services",
    "sub_industry": "Residential + Commercial Roofing",
    "location": {"state": "North Carolina", "metro": "Charlotte"},
    "financials": {
        "revenue_ttm": 4200000,
        "sde_ttm": 850000,
        "ebitda_ttm": 700000
    },
    "add_backs": [
        {"description": "Owner salary above market", 
         "amount": 75000, "recurring": False},
        {"description": "Personal vehicle expenses", 
         "amount": 18000, "recurring": False}
    ],
    "customer_concentration": {
        "top_3_pct": 40,
        "contracts_in_place": False
    },
    "owner": {
        "involvement": "Owner-Operator",
        "primary_role": "Sales",
        "reason_for_sale": "Retirement"
    },
    "research_requests": {
        "fetch_industry_multiples": True,
        "fetch_market_size": True,
        "fetch_active_buyers": True,
        "fetch_recent_transactions": True,
        "fetch_industry_risks": True,
        "fetch_sba_rates": True
    },
    "notes": "Owner heavily involved in sales. Wants to retire in 18 months."
}

import json

message = client.messages.create(
    model="claude-opus-4-5",
    max_tokens=8096,
    system=full_system,
    messages=[
        {
            "role": "user",
            "content": f"""
New deal for analysis. Please:
1. Execute all relevant web searches (industry multiples, market 
   size, active buyers, recent transactions, current risks)
2. Generate: valuation summary, risk analysis, 1-page teaser
3. Cite all sources inline and in source blocks
4. Flag any embedded benchmarks clearly
5. Append master source log at the end

Deal Data:
{json.dumps(deal_input, indent=2)}
"""
        }
    ]
)

print(message.content[0].text)
```

---

### Option C: Cursor / Windsurf (Dev)
1. Add `system_prompt.md` as `.cursorrules`
2. Reference docs available in your workspace
3. Use with a web search plugin or Perplexity API

---

## Workflow Guide

### Step 1: Input
Provide deal data using `input_schema.json` as a template.
Can be JSON, plain English, or a mix.

### Step 2: Research Phase (Automatic)
Agent will search for:
- [ ] Industry transaction multiples (live)
- [ ] Market size + CAGR (live)
- [ ] Recent M&A transactions (live)
- [ ] Active buyers in the sector (live)
- [ ] Industry-specific risks (live)
- [ ] Current SBA rates (live)

### Step 3: Analysis Phase
- Financial normalization
- Valuation with live comps
- Risk identification (live + embedded)
- Buyer targeting with live buyer data

### Step 4: Output Generation
Choose what you need:
```
"Generate full CIM with sources"
"Give me valuation summary and risk analysis"
"Build buyer list with recent deal activity"
"Write teaser for individual buyer audience"
"Identify risks and write mitigation narratives"
"Run scenario analysis — bear/base/bull"
```

### Step 5: Quality Check
Ask the agent:
```
"Critique this output — what did we miss?"
"Which sources are oldest? Flag them."
"What will buyers push back on hardest?"
"Is the asking price defensible with live data?"
```

---

## Citation Verification Checklist

Before sending any output to a client:

```
□ All multiples have a live source OR are flagged [EMBEDDED]
□ Market size / CAGR figures have URLs
□ Buyer list has sourced, live activity data
□ No URL was invented or hallucinated
□ Master source log is complete
□ Research quality score is 7/10 or higher
□ Stale sources (>18 months) are flagged
□ Embedded benchmarks are clearly labeled
```

---

## Known Limitations

⚠️ **Web search quality** depends on Claude's tool access.
   In Claude Projects, web search is built-in.
   Via API, you may need to integrate a search tool
   (Brave Search API, Perplexity, Tavily, or SerpAPI).

⚠️ **Paywalled sources** (PitchBook, Capital IQ, GF Data)
   cannot be accessed directly. The agent will note when
   a premium source would be ideal and suggest alternatives.

⚠️ **Multiple data** is not always available for niche
   industries. Fallback to embedded benchmarks with clear
   flagging is automatic.

⚠️ **This is a deal support tool, not legal or financial
   advice.** Broker remains responsible for all
   representations made to buyers and sellers.

---

## Recommended External Data Subscriptions

For the best results, pair this agent with:

| Tool | Cost | Best For |
|------|------|---------|
| BizBuySell Insight Reports | Free | LMM sold business data |
| IBBA Market Pulse | Member | Broker survey data |
| Axial (membership) | Varies | Deal flow + buyer matching |
| GF Data | Subscription | PE transaction multiples |
| IBISWorld | Subscription | Industry reports |
| PitchBook | Enterprise | Full comp transaction data |

The agent will always attempt free/public sources first
and flag when a premium source would improve accuracy.
✅ Master Setup Checklist
text

CLAUDE PROJECT SETUP
□ system_prompt.md          → Custom Instructions
□ web_research_protocol.md  → Project Knowledge
□ source_citation_rules.md  → Project Knowledge
□ valuation_logic.md        → Project Knowledge
□ cim_template.md           → Project Knowledge
□ teaser_template.md        → Project Knowledge
□ buyer_targeting.md        → Project Knowledge
□ risk_framework.md         → Project Knowledge
□ Web Search                → ENABLED in Claude settings

API SETUP (if building)
□ input_schema.json         → Deal intake form
□ output_schema.json        → Output parser
□ Search tool integrated    → Brave / Tavily / Perplexity
□ All .md files injected    → System prompt

BEFORE EVERY CLIENT OUTPUT
□ Research quality score ≥ 7/10
□ All multiples sourced or flagged
□ No invented URLs
□ Master source log complete
□ Stale data flagged
Total context: ~18,000 tokens across all files.
Fits within Claude's context window.
For API use: inject all docs into system prompt for best results.
For Projects: upload all files to Knowledge, enable web search.
