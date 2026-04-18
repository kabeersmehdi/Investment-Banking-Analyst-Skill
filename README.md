# Investment-Banking-Analyst-Skill

---

---
## M&A ANALYST AGENT v2.1
## Lower Middle Market | Sell-Side | Production-Grade


## What This Is

A complete AI analyst skill set for **sell-side M&A brokers** operating
in the **lower middle market ($1M–$5M EBITDA)**.

This is not a generic finance chatbot. It is a purpose-built system
that replicates the work of a top-tier investment banking analyst —
specifically tuned for:

- Founder-owned businesses
- Messy or incomplete financials (QuickBooks, tax returns, SDE-based)
- SBA-financed deal flow
- Owner-operator transition risk
- Real deal execution under time pressure

It searches the web in real time, cites every source, and produces
deal-ready outputs that brokers can hand directly to buyers, lenders,
and sellers.

---

## What's Included (v2.1 — Complete File List)

### Core System Files

| # | File | Purpose | Priority |
|---|------|---------|----------|
| 1 | `system_prompt.md` | Master agent instructions + behavioral rules | 🔴 Required |
| 2 | `web_research_protocol.md` | Live search rules, source hierarchy, query library | 🔴 Required |
| 3 | `source_citation_rules.md` | Citation standards, anti-hallucination rules | 🔴 Required |

### Deal Analysis & Valuation

| # | File | Purpose | Priority |
|---|------|---------|----------|
| 4 | `valuation_logic.md` | Multiple frameworks, adjustment factors, revenue quality scoring, scenario analysis | 🔴 Required |
| 5 | `qoe_framework.md` | Quality of Earnings analysis — revenue/expense normalization, pro forma P&L, working capital, cash-to-accrual | 🔴 Required |
| 6 | `deal_structure.md` | SBA modeling, seller notes, earnouts, asset vs. stock, DSCR calculations | 🔴 Required |
| 7 | `risk_framework.md` | Risk identification, severity ratings, narrative scripts, data room structure | 🔴 Required |

### Marketing & Outreach

| # | File | Purpose | Priority |
|---|------|---------|----------|
| 8 | `cim_template.md` | Full CIM generation — 8-section template with live industry data integration | 🔴 Required |
| 9 | `teaser_template.md` | Anonymous 1-page teaser template | 🔴 Required |
| 10 | `buyer_targeting.md` | 4 buyer personas, outreach templates, follow-up sequences, live buyer research | 🔴 Required |

### Deal Execution

| # | File | Purpose | Priority |
|---|------|---------|----------|
| 11 | `loi_evaluation.md` | LOI comparison matrix, deal certainty scoring, red flag identification | 🟡 High |
| 12 | `seller_prep.md` | Pre-market readiness checklist — financials, legal, operational, owner readiness | 🟡 High |
| 13 | `engagement_guidance.md` | Broker fee structures, engagement terms, minimum fees | 🟢 Optional |

### Schemas (For API / Structured Integrations)

| # | File | Purpose | Priority |
|---|------|---------|----------|
| 14 | `input_schema.json` | Structured deal intake format | 🟡 API Only |
| 15 | `output_schema.json` | Structured output parsing format | 🟡 API Only |

---

---

## Deployment Guide

### Option A: Claude.ai Projects (Recommended — No Code)

**This is the fastest way to get running. Takes 10 minutes.**

#### Step 1: Create a Project
1. Go to [claude.ai](https://claude.ai)
2. Click **Projects** in the left sidebar
3. Click **Create Project**
4. Name it: `M&A Analyst Agent`

#### Step 2: Set Custom Instructions
1. Open `system_prompt.md`
2. Copy the entire contents
3. Paste into the **Custom Instructions** field in Project Settings

#### Step 3: Upload Knowledge Files
Upload ALL of the following files to **Project Knowledge**:
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
✅ engagement_guidance.md (optional)

text


#### Step 4: Enable Web Search
1. In Claude settings, ensure **web search** is enabled
2. The agent will automatically search when needed

#### Step 5: Start Using It
Open a new conversation in the project and paste your deal data.

---

### Option B: Anthropic API Integration

For developers building this into a custom application.

#### Prerequisites
```bash
pip install anthropic
Basic Implementation
Python

import anthropic
import json
import os

class MAAAnalystAgent:
    """
    Lower Middle Market M&A Analyst Agent
    Requires: Anthropic API key with web search enabled
    """

    def __init__(self):
        self.client = anthropic.Anthropic()
        self.system_prompt = self._build_system_prompt()

    def _load_file(self, filename: str) -> str:
        """Load a knowledge file from the agent directory."""
        filepath = os.path.join("ma-analyst-agent-v2", filename)
        with open(filepath, "r") as f:
            return f.read()

    def _build_system_prompt(self) -> str:
        """Combine all knowledge files into a single system prompt."""
        files = [
            "system_prompt.md",
            "web_research_protocol.md",
            "source_citation_rules.md",
            "valuation_logic.md",
            "qoe_framework.md",
            "deal_structure.md",
            "risk_framework.md",
            "cim_template.md",
            "teaser_template.md",
            "buyer_targeting.md",
            "loi_evaluation.md",
            "seller_prep.md",
        ]

        sections = []
        for f in files:
            try:
                content = self._load_file(f)
                sections.append(f"# === {f} ===\n\n{content}")
            except FileNotFoundError:
                print(f"Warning: {f} not found, skipping.")

        return "\n\n---\n\n".join(sections)

    def analyze_deal(self, deal_input: dict, request: str) -> str:
        """
        Analyze a deal and generate requested outputs.

        Args:
            deal_input: Dict matching input_schema.json
            request: What outputs to generate
                     (e.g., "valuation + CIM + buyer list")

        Returns:
            Formatted analysis with sources
        """
        user_message = f"""
New deal for analysis.

## RESEARCH INSTRUCTIONS
1. Execute all relevant web searches before analysis
2. Search for: industry multiples, market size, active buyers,
   recent transactions, current risks, SBA rates
3. Cite all sources inline and in source blocks
4. Flag any embedded benchmarks clearly
5. Append master source log

## DEAL DATA
{json.dumps(deal_input, indent=2)}

## REQUESTED OUTPUTS
{request}
"""

        message = self.client.messages.create(
            model="claude-sonnet-4-20250514",
            max_tokens=16000,
            system=self.system_prompt,
            messages=[
                {"role": "user", "content": user_message}
            ]
        )

        return message.content[0].text

    def evaluate_loi(self, deal_context: dict, loi_data: list) -> str:
        """Evaluate one or more LOIs against each other."""
        user_message = f"""
Evaluate the following LOI(s) for this deal.

## DEAL CONTEXT
{json.dumps(deal_context, indent=2)}

## LOI(S) RECEIVED
{json.dumps(loi_data, indent=2)}

## REQUESTED OUTPUT
1. Offer comparison matrix (if multiple LOIs)
2. Deal certainty scoring for each offer
3. Red flag identification
4. Recommended negotiation strategy
5. Recommended selection with rationale
"""

        message = self.client.messages.create(
            model="claude-sonnet-4-20250514",
            max_tokens=8000,
            system=self.system_prompt,
            messages=[
                {"role": "user", "content": user_message}
            ]
        )

        return message.content[0].text

    def generate_cim(self, deal_input: dict) -> str:
        """Generate a full CIM with live market data."""
        return self.analyze_deal(
            deal_input,
            """Generate a FULL Confidential Information Memorandum:
1. Executive Summary
2. Industry Overview (MUST include live market data)
3. Business Overview
4. Financial Performance (with QoE-style normalization)
5. Growth Opportunities (supported by market data)
6. Risk Factors & Mitigation
7. Buyer Rationale (with return analysis for SBA + PE buyer)
8. Transaction Overview
9. Master Source Log"""
        )

    def generate_valuation(self, deal_input: dict) -> str:
        """Generate valuation with live comps."""
        return self.analyze_deal(
            deal_input,
            """Generate a comprehensive valuation:
1. Financial normalization (QoE-style)
2. Revenue quality scoring
3. Live comparable transaction search
4. SDE multiple analysis
5. EBITDA multiple analysis
6. Adjustment factor application
7. Scenario analysis (bear / base / bull)
8. Recommended asking price
9. SBA buyer return model
10. Deal structure recommendation
11. Confidence level assessment
12. Master source log"""
        )

    def generate_buyer_list(self, deal_input: dict) -> str:
        """Generate buyer list with live acquirer research."""
        return self.analyze_deal(
            deal_input,
            """Generate buyer targeting strategy:
1. Search for active acquirers in this industry (LIVE)
2. Search for recent M&A transactions (LIVE)
3. Identify primary + secondary buyer personas
4. Build tiered buyer list (Tier 1 / 2 / 3)
5. Write outreach email for each buyer type
6. Create follow-up sequence
7. Recommend outreach volume + channel strategy
8. Cite sources for all buyer activity data"""
        )

    def check_seller_readiness(self, deal_input: dict) -> str:
        """Run seller readiness assessment."""
        return self.analyze_deal(
            deal_input,
            """Run a pre-market seller readiness assessment:
1. Financial readiness check
2. Legal / structural readiness check
3. Operational readiness check
4. Owner readiness check
5. Marketing readiness check
6. Gap identification (what's missing before going to market)
7. Recommended timeline to market-ready
8. Priority action items for seller"""
        )


# ─── USAGE EXAMPLE ──────────────────────────────────────────

if __name__ == "__main__":

    agent = MAAAnalystAgent()

    deal = {
        "company_name": "ABC Roofing LLC",
        "industry": "Roofing Services",
        "sub_industry": "Residential + Commercial Roofing",
        "naics_code": "238160",
        "location": {
            "state": "North Carolina",
            "metro": "Charlotte",
            "service_area": "Charlotte metro + surrounding counties"
        },
        "business_model": "Project-Based",
        "years_in_business": 18,
        "employees": {
            "full_time": 22,
            "part_time": 4,
            "contractors": 8
        },
        "financials": {
            "revenue_ttm": 4200000,
            "revenue_year_1": 3800000,
            "revenue_year_2": 3500000,
            "gross_profit_ttm": 1680000,
            "sde_ttm": 850000,
            "ebitda_ttm": 700000,
            "net_income_ttm": 320000,
            "owner_salary": 225000,
            "market_rate_salary": 120000,
            "capex_annual": 85000,
            "working_capital": 180000,
            "total_debt": 150000,
            "cash_on_hand": 95000
        },
        "add_backs": [
            {
                "description": "Owner salary above market rate",
                "amount": 105000,
                "recurring": False,
                "documentation_available": True
            },
            {
                "description": "Personal vehicle expenses (2 trucks)",
                "amount": 18000,
                "recurring": False,
                "documentation_available": True
            },
            {
                "description": "Owner cell phone + home internet",
                "amount": 4200,
                "recurring": False,
                "documentation_available": True
            },
            {
                "description": "Owner health insurance (family plan)",
                "amount": 24000,
                "recurring": False,
                "documentation_available": True
            },
            {
                "description": "One-time equipment repair (storm damage)",
                "amount": 35000,
                "recurring": False,
                "documentation_available": True
            }
        ],
        "revenue_quality": {
            "recurring_pct": 15,
            "project_based_pct": 70,
            "contracted_pct": 15,
            "avg_contract_length_months": 6
        },
        "customer_concentration": {
            "top_customer_pct": 18,
            "top_3_pct": 40,
            "top_10_pct": 65,
            "total_active_customers": 85,
            "avg_customer_tenure_years": 4.5,
            "contracts_in_place": False
        },
        "real_estate": {
            "owned": False,
            "lease_remaining_months": 28,
            "renewal_options": True,
            "estimated_value": None
        },
        "owner": {
            "involvement": "Owner-Operator",
            "hours_per_week": 55,
            "primary_role": "Sales + estimating + customer relationships",
            "willing_to_stay": True,
            "transition_months": 12,
            "reason_for_sale": "Retirement — owner is 62"
        },
        "management_team": {
            "depth": "Thin",
            "key_roles_filled": [
                "Operations Manager",
                "Office Manager / Bookkeeper"
            ],
            "retention_risk": "Medium"
        },
        "deal_parameters": {
            "asking_price": None,
            "structure_preference": "SBA Eligible",
            "seller_note_max_pct": 15,
            "target_close_months": 9,
            "sba_eligible": True
        },
        "research_requests": {
            "fetch_industry_multiples": True,
            "fetch_market_size": True,
            "fetch_active_buyers": True,
            "fetch_recent_transactions": True,
            "fetch_industry_risks": True,
            "fetch_sba_rates": True
        },
        "known_risks": [
            "Owner is primary sales and estimating resource",
            "No formal contracts with customers",
            "Revenue is project-based, limited recurring"
        ],
        "growth_opportunities": [
            "Commercial roofing — currently 15% of revenue, could grow to 40%",
            "Insurance restoration work — high margin, untapped",
            "Geographic expansion to Raleigh-Durham market",
            "Maintenance contracts for existing customers"
        ],
        "notes": "Owner built this business from scratch. Well-known in the \
Charlotte market. Has a great reputation but has never had a salesperson — \
all relationships run through him. Operations Manager is strong and could \
potentially step into a GM role with support. Owner's wife does the \
bookkeeping part-time and would not stay post-close."
    }

    # Generate full valuation
    print("=" * 60)
    print("GENERATING VALUATION...")
    print("=" * 60)
    valuation = agent.generate_valuation(deal)
    print(valuation)

    # Generate buyer list
    print("\n" + "=" * 60)
    print("GENERATING BUYER LIST...")
    print("=" * 60)
    buyers = agent.generate_buyer_list(deal)
    print(buyers)

    # Check seller readiness
    print("\n" + "=" * 60)
    print("CHECKING SELLER READINESS...")
    print("=" * 60)
    readiness = agent.check_seller_readiness(deal)
    print(readiness)
Advanced: With External Search API
If using Claude API without built-in web search, integrate a
search provider:

Python

import requests

class WebSearchProvider:
    """
    Pluggable web search for the M&A Agent.
    Supports: Brave Search, Tavily, SerpAPI, Perplexity
    """

    def __init__(self, provider: str, api_key: str):
        self.provider = provider
        self.api_key = api_key

    def search(self, query: str, num_results: int = 5) -> list:
        """Execute a web search and return structured results."""

        if self.provider == "brave":
            return self._brave_search(query, num_results)
        elif self.provider == "tavily":
            return self._tavily_search(query, num_results)
        elif self.provider == "serpapi":
            return self._serp_search(query, num_results)
        else:
            raise ValueError(f"Unsupported provider: {self.provider}")

    def _brave_search(self, query: str, num_results: int) -> list:
        headers = {
            "Accept": "application/json",
            "X-Subscription-Token": self.api_key
        }
        params = {"q": query, "count": num_results}
        resp = requests.get(
            "https://api.search.brave.com/res/v1/web/search",
            headers=headers, params=params
        )
        results = resp.json().get("web", {}).get("results", [])
        return [
            {
                "title": r.get("title"),
                "url": r.get("url"),
                "snippet": r.get("description"),
                "age": r.get("age", "Unknown")
            }
            for r in results
        ]

    def _tavily_search(self, query: str, num_results: int) -> list:
        resp = requests.post(
            "https://api.tavily.com/search",
            json={
                "api_key": self.api_key,
                "query": query,
                "search_depth": "advanced",
                "max_results": num_results,
                "include_raw_content": False
            }
        )
        results = resp.json().get("results", [])
        return [
            {
                "title": r.get("title"),
                "url": r.get("url"),
                "snippet": r.get("content"),
                "age": "Recent"
            }
            for r in results
        ]

    def _serp_search(self, query: str, num_results: int) -> list:
        params = {
            "api_key": self.api_key,
            "q": query,
            "num": num_results
        }
        resp = requests.get(
            "https://serpapi.com/search", params=params
        )
        results = resp.json().get("organic_results", [])
        return [
            {
                "title": r.get("title"),
                "url": r.get("link"),
                "snippet": r.get("snippet"),
                "age": r.get("date", "Unknown")
            }
            for r in results
        ]


class EnhancedMAAAgent(MAAAnalystAgent):
    """
    Extended agent with external web search pre-processing.
    Injects live search results into the prompt context.
    """

    def __init__(self, search_provider: str, search_api_key: str):
        super().__init__()
        self.search = WebSearchProvider(search_provider, search_api_key)

    def _research_deal(self, deal: dict) -> str:
        """Pre-fetch live data and format as research context."""
        industry = deal.get("industry", "")
        queries = [
            f"{industry} M&A multiples 2024 2025 lower middle market",
            f"{industry} market size CAGR United States 2025",
            f"who is acquiring {industry} companies 2024 2025",
            f"{industry} EBITDA margins small business benchmark",
            f"{industry} industry trends consolidation 2025",
            "current SBA 7a interest rate 2025"
        ]

        research_results = []
        for q in queries:
            try:
                results = self.search.search(q, num_results=3)
                research_results.append({
                    "query": q,
                    "results": results
                })
            except Exception as e:
                research_results.append({
                    "query": q,
                    "results": [],
                    "error": str(e)
                })

        return json.dumps(research_results, indent=2)

    def analyze_deal(self, deal_input: dict, request: str) -> str:
        """Override to inject pre-fetched research."""
        research = self._research_deal(deal_input)

        user_message = f"""
New deal for analysis.

## PRE-FETCHED RESEARCH DATA
The following web search results have been retrieved for you.
Use these as primary sources. Cite the URLs provided.
If the data is insufficient, note what additional searches
you would recommend.

{research}

## DEAL DATA
{json.dumps(deal_input, indent=2)}

## REQUESTED OUTPUTS
{request}
"""

        message = self.client.messages.create(
            model="claude-sonnet-4-20250514",
            max_tokens=16000,
            system=self.system_prompt,
            messages=[
                {"role": "user", "content": user_message}
            ]
        )

        return message.content[0].text


# ─── USAGE WITH EXTERNAL SEARCH ─────────────────────────────

if __name__ == "__main__":

    agent = EnhancedMAAAgent(
        search_provider="tavily",
        search_api_key=os.environ["TAVILY_API_KEY"]
    )

    # Same deal input as above...
    result = agent.generate_valuation(deal)
    print(result)
Option C: n8n / Make / Zapier (No-Code Automation)
For brokers who want to automate deal intake via forms.

Workflow Architecture
text

┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│ Google Form  │────▶│ n8n / Make   │────▶│ Claude API   │
│ (Deal Input) │     │ (Orchestrator)│     │ (M&A Agent)  │
└──────────────┘     └──────┬───────┘     └──────┬───────┘
                            │                     │
                            ▼                     ▼
                     ┌──────────────┐     ┌──────────────┐
                     │ Web Search   │     │ Google Docs   │
                     │ (Tavily API) │     │ (CIM Output)  │
                     └──────────────┘     └──────────────┘
                                                 │
                                                 ▼
                                          ┌──────────────┐
                                          │ Email to      │
                                          │ Broker        │
                                          └──────────────┘
Setup Steps
Create a Google Form matching input_schema.json fields
Connect form to n8n/Make
n8n workflow:
a. Receive form submission
b. Run web searches via Tavily API
c. Format deal input + research as Claude prompt
d. Send to Claude API with system prompt
e. Parse output
f. Write CIM to Google Doc
g. Email link to broker
Total build time: ~4 hours
Option D: Cursor / Windsurf (Dev IDE)
Save system_prompt.md as .cursorrules in project root
Place all other .md files in a /knowledge directory
Reference knowledge files in your prompts as needed
Use with a web search plugin for live data
Complete Workflow Guide
Phase 1: Seller Onboarding
text

USER PROMPT:
"I just signed a new seller. Here's what I know about the business.
Run the seller readiness checklist and tell me what's missing
before we go to market."

[Paste deal data]
Agent will:

Run through seller_prep.md checklist
Identify gaps in financials, legal, operational readiness
Produce a prioritized action plan with timeline
Flag deal-breakers that must be resolved before marketing
Phase 2: Valuation
text

USER PROMPT:
"Generate a full valuation for this deal. Search for current
industry multiples. Model SBA buyer and PE buyer scenarios.
Show me the recommended asking price."

[Paste deal data]
Agent will:

Search web for live industry multiples
Normalize financials (QoE-style)
Score revenue quality
Apply adjustment factors
Run bear / base / bull scenarios
Model SBA buyer returns (DSCR check)
Recommend asking price with confidence level
Cite all sources
Phase 3: Marketing Materials
text

USER PROMPT:
"Generate the full CIM and a 1-page teaser. Use 'Project Summit'
as the codename. Research the roofing industry for the industry
overview section."
Agent will:

Search for industry market size, CAGR, trends
Generate 8-section CIM with live data
Generate anonymized teaser
Cite all market data sources
Append master source log
Phase 4: Buyer Outreach
text

USER PROMPT:
"Build me a buyer list for this deal. Search for who's actively
acquiring roofing companies. Write outreach emails for each
buyer type."
Agent will:

Search for active acquirers in roofing
Search for recent roofing M&A transactions
Identify Tier 1/2/3 buyers with sources
Write customized outreach emails (4 templates)
Create follow-up sequence
Phase 5: LOI Evaluation
text

USER PROMPT:
"I received 3 LOIs. Evaluate them and tell me which one to take."

LOI 1: $3.2M all cash, 45-day diligence, SBA pre-approved
LOI 2: $3.5M with $500K earnout, 60-day diligence, no financing letter
LOI 3: $3.0M, 10% seller note, 30-day diligence, experienced buyer
Agent will:

Build offer comparison matrix
Score deal certainty for each LOI
Identify red flags
Recommend which offer to accept with rationale
Suggest negotiation strategy
Phase 6: Due Diligence Support
text

USER PROMPT:
"We're in diligence with Buyer 1. They sent this Q&A list.
Help me draft responses. Flag anything that could be a problem."

[Paste buyer questions]
Agent will:

Draft responses to each question
Flag questions that expose risks
Suggest narrative framing for sensitive topics
Recommend data room documents to share
Prompt Library (Copy & Paste)
Quick Valuation
text

Give me a quick valuation range for this business:
- Industry: [X]
- Revenue: $[X]M
- SDE: $[X]M
- Location: [State]
- Owner role: [Active/Absentee]
Search for current multiples. Give me bear/base/bull.
Full CIM
text

Generate a complete CIM for this deal. Codename: Project [X].
Research the industry. Include return analysis for an SBA buyer.
Cite all sources. Append master source log.
[Paste full deal data]
Teaser Only
text

Write a 1-page anonymous teaser. No company name.
Industry: [X] | State: [X] | Revenue: $[X]M | SDE: $[X]M
Include a live market data point about the industry.
Risk Report
text

Generate a risk analysis for this deal. Search for
industry-specific risks. Rate each risk Low/Medium/High.
Write mitigation narratives for every Medium+ risk.
[Paste deal data]
Buyer List
text

Who is buying [INDUSTRY] companies right now? Search for:
- Recent acquisitions (last 12 months)
- PE firms active in this space
- Strategic acquirers
Build me a tiered buyer list with outreach angles.
SBA Feasibility Check
text

Can an SBA buyer afford this deal?
Purchase price: $[X]M
SDE: $[X]M
Model: 10% down, 10-year SBA 7(a)
Search for current SBA rate. Calculate DSCR.
Tell me if this passes SBA underwriting.
LOI Review
text

Review this LOI and score it:
- Deal certainty (1-10)
- Red flags
- Negotiation leverage points
- Recommended counter-terms
[Paste LOI terms]
Market Timing Narrative
text

Build me a "why sell now" narrative for a [INDUSTRY] business.
Search for:
- Industry M&A activity trends
- Multiple expansion/compression
- Macro tailwinds
- Competitive dynamics
Cite everything.
Comp Transaction Search
text

Find me comparable transactions for:
- Industry: [X]
- Revenue range: $[X]M-$[X]M
- EBITDA range: $[X]M-$[X]M
- Last 24 months
List: target, acquirer, deal value, implied multiple, source.
Deal Structure Advice
text

Best deal structure for this situation:
- Asking price: $[X]M
- SDE: $[X]M
- Buyer type: [Individual/Search Fund/PE]
- Seller wants: [Max cash / Flexible / Quick close]
Model: all-cash vs. SBA vs. seller note scenarios.
Calculate buyer returns for each.
Quality Assurance Checklist
Before Sending Valuation to Client
text

□ Live industry multiples sourced (not just embedded)
□ SDE and EBITDA both calculated
□ Revenue quality scored
□ All add-backs documented with justification
□ Bear/base/bull scenarios complete
□ Asking price within defensible range
□ SBA feasibility checked (if applicable)
□ Confidence level assigned
□ All sources cited with URLs
□ No fabricated data points
Before Sending CIM to Buyers
text

□ Industry overview uses live market data
□ Financial tables are accurate (double-check math)
□ Add-backs are defensible (would a CPA agree?)
□ Growth opportunities are specific and credible
□ Risks are disclosed honestly with mitigation
□ Return analysis uses current SBA rate
□ No confidential info in wrong sections
□ Teaser has NO identifying information
□ Master source log is complete
□ Legal disclaimer is included
Before Acting on LOI Evaluation
text

□ All offers compared on equal terms
□ Deal certainty scored objectively
□ Financing risk assessed for each buyer
□ Red flags identified
□ Broker has verified buyer financials independently
□ Seller has been briefed on tradeoffs
Context Budget
Component	Estimated Tokens
system_prompt.md	~2,500
web_research_protocol.md	~2,000
source_citation_rules.md	~1,200
valuation_logic.md	~2,800
qoe_framework.md	~1,500
deal_structure.md	~1,800
risk_framework.md	~2,500
cim_template.md	~3,000
teaser_template.md	~800
buyer_targeting.md	~3,200
loi_evaluation.md	~1,200
seller_prep.md	~1,000
engagement_guidance.md	~500
TOTAL	~24,000
This fits comfortably within Claude's context window (200K tokens),
leaving ~176K tokens for deal data, web search results, and
multi-turn conversation.

Recommended Tech Stack
For Solo Brokers (No-Code)
Tool	Purpose	Cost
Claude Pro	Agent runtime	$20/mo
Google Docs	CIM formatting	Free
BizBuySell	Listing + buyer leads	~$60/mo
Canva	CIM design polish	Free–$13/mo
For Brokerage Teams (Low-Code)
Tool	Purpose	Cost
Claude Pro / Team	Agent runtime	$20–30/mo/user
n8n (self-hosted)	Workflow automation	Free
Tavily API	Web search	$0.01/search
Google Workspace	Docs + Forms	$7/mo/user
Notion	Deal pipeline tracking	Free–$10/mo
For Tech-Forward Firms (Full Build)
Tool	Purpose	Cost
Anthropic API	Agent runtime	Usage-based
Brave / Tavily API	Web search	Usage-based
PostgreSQL	Deal database	Free–hosted
Next.js / React	Frontend	Free
Vercel	Hosting	Free–$20/mo
Stripe	Client billing	2.9% + $0.30
Known Limitations
Platform Limitations
⚠️ Paywalled sources: Cannot access PitchBook, Capital IQ,
GF Data, or IBISWorld directly. Will flag when premium data
would improve accuracy and suggest free alternatives.

⚠️ Web search variability: Search result quality depends
on Claude's built-in search or your external search API.
Niche industries may have limited online data.

⚠️ No CRM integration: Deal pipeline tracking must be done
externally (Notion, Airtable, DealCloud, etc.).

⚠️ No document generation: Outputs are text/markdown.
CIM formatting for client delivery requires Google Docs,
Word, or Canva.

Analytical Limitations
⚠️ Not a CPA or attorney: Financial normalization and legal
observations are directional, not professional opinions.
Always have a CPA validate QoE and an attorney review
deal documents.

⚠️ Embedded multiples may lag: If live search fails, embedded
benchmark ranges may not reflect current market conditions.
Always verify before client-facing use.

⚠️ No predictive modeling: The agent cannot predict future
market conditions, interest rates, or buyer sentiment.
Scenario analysis is illustrative, not predictive.

Scope Limitations
⚠️ Optimized for $1M–$5M EBITDA: Businesses below $500K
SDE or above $10M EBITDA may need adjusted frameworks.

⚠️ US-focused: Valuation multiples, SBA rules, and deal
structures assume US-based transactions. International
deals require significant modification.

⚠️ Sell-side focused: This agent is built for brokers
representing sellers. Buy-side analysis (due diligence
for buyers) requires a different configuration.

Changelog
v2.1 (Current)
Added: qoe_framework.md — Quality of Earnings analysis
Added: deal_structure.md — SBA, seller note, earnout modeling
Added: loi_evaluation.md — LOI comparison and scoring
Added: seller_prep.md — Pre-market readiness checklist
Added: engagement_guidance.md — Broker fee structures
Added: Revenue quality scoring to valuation_logic.md
Added: Enhanced API implementation with external search
Added: No-code automation guide (n8n/Make)
Added: Complete prompt library
v2.0
Added: Live web research capability
Added: web_research_protocol.md — Search rules + source hierarchy
Added: source_citation_rules.md — Citation standards
Added: Industry overview section to CIM (live-data required)
Added: Live buyer research to targeting
Added: Master source log on all outputs
Added: Research quality scoring
Added: Anti-hallucination rules
v1.0
Initial release
Core valuation (SDE + EBITDA multiples)
CIM + teaser templates
Buyer targeting (4 personas)
Risk framework
Financial normalization
License & Disclaimer
This agent configuration is provided as-is for professional use
by licensed business brokers and M&A advisors.

This tool does not provide legal, tax, or financial advice.
All outputs are analytical aids. The broker/advisor remains solely
responsible for:

Accuracy of data provided to clients and buyers
Compliance with state and federal brokerage regulations
Fiduciary duties to seller clients
Representations made in marketing materials
Deal structure advice (consult transaction attorney)
Tax implications (consult CPA / tax advisor)
Always verify agent outputs against independent professional
analysis before use in live transactions.

Support & Feedback
This is an open configuration. To improve it:

Test it on a real deal (anonymize sensitive data)
Note where outputs need refinement
Adjust the relevant .md file
Re-upload to your Claude Project
Common refinements:

Adjust embedded multiples for your specific industry focus
Add industry-specific risk factors
Customize outreach templates to your firm's voice
Add your firm's branding to CIM/teaser templates
Tune the self-critique loop strictness
Quick Start (30 Seconds)
Go to claude.ai → Projects → New Project
Paste system_prompt.md into Custom Instructions
Upload all .md files to Project Knowledge
Enable web search
Type:
text

I have a new deal. Here's what I know:

Industry: HVAC
Location: Texas
Revenue: $3.5M
SDE: $750K
Owner is 60, wants to retire, runs all sales.
17 years in business, 15 employees.

Give me: valuation range, top risks, and a 1-page teaser.
Search for current HVAC multiples.
You're live.

text


---

**That's the complete README.** Copy the entire markdown block above into your `README.md` file. It covers setup, deployment (4 options), full workflow, prompt library, API c
