# Valuation Logic — LMM M&A Analyst Agent v2.0

## LIVE DATA FIRST POLICY
Before applying any embedded multiple, the agent MUST attempt to
retrieve live transaction data for the specific industry and deal size.
Embedded ranges are fallbacks only.

---

## PRIMARY METHOD: Comparable Transaction Multiples

### Step 1: Search for Live Comps
Execute the following searches:
1. "[INDUSTRY] M&A multiples 2024 2025 lower middle market"
2. "BizBuySell [INDUSTRY] median sale price multiple"
3. "IBBA market pulse [INDUSTRY] [YEAR]"
4. "Axial [INDUSTRY] deal data multiples"

### Step 2: Extract Multiple Range
From live sources, identify:
- Low end (bear market / distressed deals)
- Median (typical market transaction)
- High end (premium / competitive process)

### Step 3: Apply Adjustment Factors
Adjust base multiple up or down based on deal-specific factors
(see adjustment table below).

### Step 4: Apply to Normalized Financials
Enterprise Value = Normalized SDE or EBITDA × Adjusted Multiple

---

## EMBEDDED MULTIPLE RANGES (FALLBACK ONLY)
📊 Use only when live data is unavailable. Flag as embedded.

### SDE Multiple Framework

## EMBEDDED MULTIPLE RANGES — LAST UPDATED: [DATE]
⚠️ WARNING: These ranges are fallback estimates.
ALWAYS search for live data first.
These benchmarks should be manually updated quarterly
by the broker using the latest:
- BizBuySell Insight Report (free, quarterly)
- IBBA Market Pulse Survey (member access)
- Axial deal data (if available)

LAST MANUAL REVIEW: [DATE]
REVIEWED BY: [BROKER NAME]
NEXT REVIEW DUE: [DATE + 90 DAYS]

📊 [EMBEDDED BENCHMARK — Source: Agent training data, historical LMM
transaction patterns. Verify with BizBuySell Insight Report or IBBA
Market Pulse before presenting to clients.]

### EBITDA Multiple Framework
Use when: EBITDA > $2M, buyer likely PE / family office / strategic

| EBITDA Range | Bear    | Base    | Bull    |
|--------------|---------|---------|---------|
| $1M–$2M      | 3.8x    | 4.8x    | 5.5x    |
| $2M–$3M      | 4.5x    | 5.5x    | 6.5x    |
| $3M–$5M      | 5.0x    | 6.0x    | 7.0x    |
| $5M+         | 6.0x    | 7.5x    | 9.0x+   |

📊 [EMBEDDED BENCHMARK — Same caveat as above]

---

## INDUSTRY-SPECIFIC MULTIPLE NOTES
The agent will search for the following before each valuation:

| Industry Bucket | Search Query | Typical Range (Embedded) |
|----------------|-------------|--------------------------|
| HVAC / Plumbing | "HVAC M&A multiples 2025" | 4.0x–7.0x EBITDA |
| Roofing / Exterior | "roofing company M&A multiples" | 3.5x–6.0x EBITDA |
| Landscaping | "landscaping M&A multiples LMM" | 3.0x–5.5x EBITDA |
| Healthcare / Home Health | "home health M&A multiples" | 5.0x–8.0x EBITDA |
| Technology / SaaS | "SaaS M&A multiples SMB" | 2.0x–5.0x Revenue |
| Distribution | "distribution company M&A multiples" | 4.0x–6.5x EBITDA |
| Manufacturing | "manufacturing M&A multiples LMM" | 4.5x–7.0x EBITDA |
| Business Services | "business services M&A multiples" | 4.5x–7.5x EBITDA |
| Staffing | "staffing company M&A multiples" | 3.0x–6.0x EBITDA |
| Food & Beverage | "F&B company M&A multiples" | 3.0x–6.0x EBITDA |

📊 All ranges above are embedded benchmarks. Live search supersedes.

---

## MULTIPLE ADJUSTMENT FACTORS

### Upward Adjustments (+ 0.25x to + 1.5x per factor)

| Factor | Typical Adjustment |
|--------|-------------------|
| Recurring revenue > 70% | +0.50x to +1.00x |
| Contracts in place > 12 months | +0.25x to +0.75x |
| Management team in place | +0.50x to +1.00x |
| Revenue growing 15%+ YoY | +0.50x to +1.00x |
| EBITDA margin > 20% | +0.25x to +0.75x |
| Proprietary IP / brand / process | +0.25x to +1.50x |
| Roll-up platform potential | +0.50x to +1.50x |
| Clean / audited financials | +0.25x to +0.50x |
| Long-term customer contracts | +0.50x to +1.00x |
| Geographic expansion ready | +0.25x to +0.50x |

### Downward Adjustments (- 0.25x to - 1.5x per factor)

| Factor | Typical Adjustment |
|--------|-------------------|
| Single customer > 25% revenue | -0.50x to -1.00x |
| Owner = primary salesperson | -0.50x to -1.00x |
| Revenue declining YoY | -0.50x to -1.50x |
| EBITDA margin < 10% | -0.25x to -0.75x |
| Tax returns only (no P&L) | -0.25x to -0.75x |
| Cyclical / seasonal revenue | -0.25x to -0.50x |
| High customer concentration (top 3 > 60%) | -0.75x to -1.50x |
| Lease < 18 months remaining | -0.25x to -0.50x |
| Owner working > 60 hrs/week | -0.50x to -1.00x |
| Commodity market / no moat | -0.50x to -1.00x |

---

## SCENARIO ANALYSIS FRAMEWORK

| Scenario | Multiple Used | Assumption |
|----------|--------------|------------|
| Bear Case | Low end minus adjustments | Discount for risks, no synergy |
| Base Case | Midpoint with adjustments | Standard market, typical buyer |
| Bull Case | High end plus synergy | Strategic buyer, competitive process |

---

## SECONDARY METHOD: Simplified DCF

Use only when:
- Contracted, predictable cash flows (visibility > 3 years)
- Institutional buyer likely
- Cross-validation of comp-based valuation needed

### DCF Inputs
- FCF = EBITDA – Maintenance CapEx – Working Capital Changes
- Discount Rate: 20%–30% for LMM (illiquidity premium)
- Terminal Multiple: 3x–5x terminal year EBITDA
- Projection Period: 3–5 years

### DCF Note
Always cross-reference DCF output against comp multiples.
If DCF implies materially higher value, explain the delta.
If DCF implies materially lower value, flag for client.

---

## ASKING PRICE STRATEGY

1. Set asking price at bull case or 10%–15% above base case
2. Leave 5%–15% negotiation room
3. Never set below base case
4. Check SBA loan ceiling ($5M max for 7(a))
5. Flag if asking price requires aggressive assumptions
6. Consider deal structure impact on effective price

---


## REVENUE QUALITY SCORING

| Revenue Type | Quality Score | Multiple Impact |
|-------------|--------------|-----------------|
| Contracted recurring (auto-renew) | 10/10 | +1.0x to +1.5x |
| Subscription / retainer | 9/10 | +0.75x to +1.25x |
| Repeat non-contracted (same customers, no contract) | 7/10 | +0.25x to +0.50x |
| Repeat project-based (same customers, RFP each time) | 5/10 | Baseline |
| New project-based (always hunting) | 3/10 | -0.25x to -0.50x |
| One-time / transactional | 2/10 | -0.50x to -1.00x |

### Blended Revenue Quality Score
Calculate: (Revenue Type A % × Score) + (Revenue Type B % × Score) = Weighted Score

Example:
- 40% contracted recurring (10) + 35% repeat non-contracted (7) + 25% project (5)
- Weighted Score = (0.40 × 10) + (0.35 × 7) + (0.25 × 5) = 7.7 / 10

| Weighted Score | Valuation Zone |
|---------------|---------------|
| 8.0–10.0 | Premium — top of multiple range |
| 6.0–7.9 | Standard — mid-range multiple |
| 4.0–5.9 | Discounted — low end of range |
| <4.0 | Significant discount — lifestyle risk |



## MULTI-SERVICE / HYBRID BUSINESSES

When a business spans multiple service lines:

### Step 1: Revenue-Weight the Multiple
| Service Line | % Revenue | Industry Multiple | Weighted |
|-------------|----------|-------------------|----------|
| Roofing | 60% | 3.5x SDE | 2.10x |
| Siding | 25% | 3.0x SDE | 0.75x |
| Gutters | 15% | 2.5x SDE | 0.375x |
| **Blended Multiple** | **100%** | | **3.225x** |

### Step 2: Search for Multiples for Each Line
Execute separate web searches for each major service line
(any line >15% of revenue).

### Step 3: Adjust for Diversification
Multi-service businesses get a +0.25x to +0.50x premium
for revenue diversification (less risk of single-service
demand shock).






## VALUATION RED FLAGS

⚠️ Revenue declining 2+ consecutive years
⚠️ EBITDA margin compression > 200bps
⚠️ Single customer > 25% of revenue
⚠️ Owner = primary salesperson, no succession plan
⚠️ Add-backs exceed 30% of reported net income
⚠️ No P&L — tax returns only
⚠️ Deferred maintenance or capex need
⚠️ Lease expiring within 18 months of close
⚠️ Pending litigation or regulatory issues
⚠️ Revenue heavily seasonal (>50% in one quarter)
