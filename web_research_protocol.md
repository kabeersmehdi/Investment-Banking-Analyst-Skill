# Web Research Protocol — M&A Analyst Agent

## PURPOSE
This document defines how the agent conducts live web research,
validates sources, and integrates external data into deal outputs.

---

## RESEARCH PRIORITY HIERARCHY


## REALISTIC SEARCH SUCCESS RATES

| Data Type | Expected Success | Notes |
|-----------|-----------------|-------|
| General industry market size | 85% | Statista, IBISWorld usually available |
| Industry CAGR | 75% | Multiple free sources |
| LMM transaction multiples | 30-40% | Most primary data is paywalled |
| Specific comp transactions | 20-30% | Public deals only |
| Active acquirer names | 50-60% | Press releases, Axial, LinkedIn |
| SBA interest rates | 95% | Publicly available |
| Industry-specific risks | 70% | Trade publications, news |

## WHEN WEB SEARCH FAILS (It Will — Often)

The agent should:
1. State clearly: "Live search did not return reliable 
   multiple data for this industry."
2. Fall back to embedded benchmarks WITH the staleness warning
3. Recommend specific actions:
   - "Pull the latest BizBuySell Insight Report manually"
   - "Check IBBA Market Pulse (member login required)"
   - "Contact 2-3 brokers who recently closed similar deals"
   - "Request a DealStats (BVR) report for this NAICS code"
4. NEVER present a blog post citation as equivalent to 
   primary transaction data







### Tier 1: Preferred Sources (Highest Trust)
These sources are authoritative for LMM M&A data:

| Source | URL | Best For |
|--------|-----|---------|
| Axial | axial.net | LMM deal flow, multiples, buyer trends |
| BizBuySell Insight Report | bizbuysell.com/research | Sold business data, multiples by industry |
| IBBA Market Pulse | ibba.org | Broker survey data, deal terms |
| Pepperdine Private Capital | bschool.pepperdine.edu | Cost of capital, multiples by size |
| GF Data | gfdata.com | PE transaction multiples ($10M–$250M EV) |
| PitchBook (if accessible) | pitchbook.com | Comp transactions, buyer activity |
| Capital IQ (if accessible) | capitaliq.com | Comp transactions, financials |
| Dun & Bradstreet | dnb.com | Industry benchmarks |
| IBISWorld | ibisworld.com | Industry size, CAGR, trends |
| NAICS Association | naics.com | Industry classification + stats |

### Tier 2: Secondary Sources (Moderate Trust)
| Source | URL | Best For |
|--------|-----|---------|
| Axial Forum / Blog | axial.net/forum | Buyer trends, deal narratives |
| Divestopedia | divestopedia.com | Valuation education, multiples |
| DealRoom | dealroom.net | Deal activity, market trends |
| Mergr | mergr.com | Acquirer research |
| The Business Brokerage Press | bbpinc.com | Broker tools |
| Industry trade publications | varies | Sector-specific news |
| SEC EDGAR | sec.gov/edgar | Public company filings (for comps) |

### Tier 3: General Reference (Use with Caution)
| Source | URL | Notes |
|--------|-----|-------|
| Statista | statista.com | Market size data — cite with caveat |
| Grand View Research | grandviewresearch.com | CAGR data — verify independently |
| McKinsey / Bain reports | varies | Strategic trends — not deal-specific |
| News articles | varies | Good for "why now" narrative only |

---

## SEARCH QUERY LIBRARY

### Valuation Queries
"[INDUSTRY] M&A multiples 2024 2025 lower middle market"
"[INDUSTRY] EBITDA multiples sell-side 2024"
"[INDUSTRY] SDE multiple small business acquisition"
"[INDUSTRY] business sold price revenue multiple"
"BizBuySell [INDUSTRY] median sale price multiple"
"IBBA market pulse [INDUSTRY] 2024"
"Axial [INDUSTRY] deal activity multiples"

text


### Industry Overview Queries
"[INDUSTRY] market size 2024 2025 CAGR"
"[INDUSTRY] industry outlook 2025"
"[INDUSTRY] industry trends consolidation"
"[INDUSTRY] fragmented market private equity interest"
"IBISWorld [INDUSTRY] industry report"

text


### Buyer Research Queries
"who is acquiring [INDUSTRY] companies 2024 2025"
"[INDUSTRY] PE acquisitions lower middle market 2024"
"[INDUSTRY] strategic acquirers M&A activity"
"[INDUSTRY] roll-up strategy private equity"
"search fund acquisitions [INDUSTRY]"
"[INDUSTRY] add-on acquisitions platform"

text


### Comparable Transaction Queries
"[INDUSTRY] acquisition announced 2024 2025"
"[INDUSTRY] company sold transaction value"
"[INDUSTRY] M&A deal [STATE/REGION] 2024"
"[COMPANY SIZE/REVENUE] [INDUSTRY] acquisition"

text


### Risk & Regulatory Queries
"[INDUSTRY] regulatory changes 2024 2025"
"[INDUSTRY] labor market trends workforce"
"[INDUSTRY] supply chain risks"
"[INDUSTRY] litigation trends"

text


---

## DATA EXTRACTION RULES

### For Multiple Data Points
When extracting multiples from a source:
1. Record the exact range stated (e.g., "4.5x–6.2x EBITDA")
2. Record the time period referenced
3. Record the deal size range (if specified)
4. Note any caveats (geography, business quality, etc.)
5. Flag if the multiple is median, mean, or range

### For Market Size / CAGR
1. Record the base year and projected year
2. Record the methodology (top-down vs. bottom-up)
3. Note whether it's global, US-only, or regional
4. Cross-reference with a second source if possible

### For Comparable Transactions
1. Record: target name (if public), acquirer, date, deal value
2. Calculate implied multiple if revenue/EBITDA is available
3. Note if it's a strategic vs. financial buyer
4. Flag if deal is outside LMM range (EV > $50M)

---

## CONFLICT RESOLUTION

If two sources report conflicting multiples:
1. Report both ranges with their respective sources
2. Explain likely reason for discrepancy (deal size, time period, quality)
3. Default to the more conservative range for the base case
4. Use the higher range for the bull case

Example output:
> Valuation Note: Sources report a range of multiples for this sector.
> BizBuySell reports 2.8x–3.5x SDE (median: 3.1x) for small HVAC
> businesses [Source 1]. Axial reports 4.5x–6.0x EBITDA for
> institutional-quality LMM HVAC platforms [Source 2]. The discrepancy
> reflects deal size and buyer type differences. This analysis applies
> 3.0x–4.5x SDE for an individual/SBA buyer scenario and
> 5.0x–6.5x EBITDA for an institutional buyer scenario.

---

## FRESHNESS STANDARDS

| Data Type | Maximum Age |
|-----------|-------------|
| Transaction multiples | 18 months |
| Market size / CAGR | 24 months |
| Industry trends | 12 months |
| Buyer acquisition activity | 6 months |
| Regulatory / legal news | 6 months |
| Comparable transactions | 36 months |

If data exceeds freshness threshold:
> ⚠️ [STALE DATA FLAG] — This source is [X] months old. Multiples
> may not reflect current market conditions. Recommend verification
> before client presentation.

---

## CITATION FORMATTING STANDARDS

### Inline Citation
> HVAC businesses in the $1M–$3M EBITDA range traded at 4.5x–6.0x
> EBITDA in 2024. 🌐 [Axial, "HVAC M&A Trends 2024",
> https://axial.net/hvac-trends-2024, accessed June 2025]

### End-of-Section Source Block
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📚 SOURCES — [Section Name]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[1] Axial | "HVAC M&A Trends 2024" | https://axial.net/...
| Accessed: June 2025 | Data: EBITDA multiple range 4.5x–6.0x

[2] BizBuySell Insight Report Q4 2024 | https://bizbuysell.com/...
| Accessed: June 2025 | Data: Median sale price/cash flow = 3.1x

[3] IBISWorld HVAC Industry Report 2025 | https://ibisworld.com/...
| Accessed: June 2025 | Data: Market size $XX B, CAGR X.X%
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

text


---

## FAILED SEARCH HANDLING

If a web search returns no usable results:
⚠️ [RESEARCH NOTE]
Live web search for [QUERY] returned no actionable results.

Fallback applied: Embedded benchmark data from agent training.
This data reflects historical LMM transaction patterns and
may not reflect current market conditions.

📊 Embedded Benchmark: [INDUSTRY] EBITDA multiples: X.Xx–X.Xx
[Source: Agent training data — verify before client use]

Recommended action: Cross-reference with BizBuySell Insight Report,
IBBA Market Pulse, or Axial before presenting to client.
