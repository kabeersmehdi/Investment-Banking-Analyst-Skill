# Investment Thesis Generator v1.0

## PURPOSE
Every deal needs a compelling investment thesis.
This is not a business description — it's a SALES ARGUMENT.

The investment thesis answers three questions a buyer
asks in the first 30 seconds:
1. Why should I buy THIS business?
2. Why should I buy it NOW?
3. What am I really getting?

---

## THESIS GENERATION (Auto-runs After /start)

After Deal Memory is built, the agent automatically generates
the investment thesis. This thesis drives ALL marketing materials.

### Step 1: Build the Headline

The headline is ONE sentence that captures the deal.
It must pass the "cocktail party test" — if a broker said
this at a cocktail party, would a buyer lean in?

**Framework:**
"[Adjective] [industry] [business type] with [key strength]
in [growing/stable/underserved] [market descriptor]"

**Bad examples:**
- "18-year-old roofing company for sale" ← boring
- "Profitable business with growth potential" ← generic
- "Excellent acquisition opportunity" ← meaningless

**Good examples:**
- "Dominant residential roofer in Charlotte with 85 active
  accounts and 18 years of referral-driven demand"
- "Founder-ready HVAC platform with 45% recurring revenue
  and a trained ops team in the fastest-growing MSA in Texas"
- "Sticky B2B staffing firm with 92% client retention,
  zero marketing spend, and $1.4M EBITDA in a consolidating market"

**Rules:**
- Must include a SPECIFIC number or fact
- Must reference the MARKET, not just the company
- Must imply upside without being salesy
- Must be honest — nothing the buyer can't verify

### Step 2: Three Reasons to Buy

Identify exactly 3 reasons a buyer should acquire this business.
Not 5, not 7. THREE. Buyers remember three things.

**Selection criteria (pick the strongest 3):**

| Reason Category | When to Use |
|----------------|-------------|
| Recurring/repeat revenue | Revenue quality score > 6 |
| Customer loyalty/retention | Avg tenure > 3 years |
| Market tailwinds | Industry CAGR > 5% or consolidating |
| Pricing power | Margins above industry average |
| Scalable with capital | Growth levers identified |
| Fragmented market | No dominant player, roll-up potential |
| Essential service | Non-discretionary demand |
| Geographic advantage | Underserved market, limited competition |
| Team in place | Has #2 person, owner not critical |
| Brand/reputation | Strong reviews, referral-driven |

**Format each reason as:**
1. **[Reason Name]** — [One sentence of evidence from Deal Memory]

**Example:**
1. **Recession-Resistant Demand** — Roofing repair and replacement
   is non-discretionary; revenue has grown through every cycle
   including 2020 ($3.5M → $4.2M over 3 years).
2. **Deep Customer Base** — 85 active accounts with 4.5-year
   average tenure and zero involuntary churn in company history.
3. **Untapped Commercial Upside** — Commercial roofing is 15%
   of current revenue but represents 40% of the addressable
   market, offering a clear path to $6M+ revenue.

### Step 3: Why Now

Build the "urgency without pressure" narrative.
This is NOT "buy now or miss out." This is:
"Here's why the timing is right for both sides."

**Components:**

| Element | Source |
|---------|--------|
| Seller motivation | Deal Memory: reason_for_sale |
| Market timing | 🌐 Live search: industry M&A activity |
| Multiple environment | 🌐 Live search: current multiples |
| Business momentum | Deal Memory: revenue trend |
| Transition readiness | Deal Memory: owner willing to stay |

**Template:**
"The seller is [motivation] after [X] years of building this
business. The [industry] market is [growing/consolidating/active]
with [specific data point 🌐]. Multiples for businesses of this
quality are [trending up/stable/at peak]. The business is
performing at [TTM revenue], the team is [description], and the
seller is committed to a [X]-month transition to ensure
continuity. This is a [rare/uncommon/well-timed] opportunity
to acquire a [adjective] platform in a [market descriptor]."

### Step 4: Buyer Fear Neutralizers

For every deal, identify what will SCARE buyers — then
pre-build the neutralizing narrative.

**Auto-detect fears from Deal Memory:**

| Deal Memory Field | Buyer Fear | Neutralizer |
|-------------------|-----------|-------------|
| owner_role = "Sales" | "Revenue walks out the door" | Transition plan + customer intro schedule |
| top_1_pct > 20% | "What if they leave?" | Tenure data + relationship depth |
| contracts = false | "Nothing is locked in" | Retention rate + repeat behavior data |
| revenue declining | "Business is dying" | Root cause + stabilization evidence |
| lease < 24 months | "I might lose the location" | Landlord conversation status |
| no #2 person | "I'm buying a job" | Ops capability of existing team |
| messy financials | "What am I really buying?" | QoE availability + bank statement backup |
| high owner hours | "This isn't scalable" | Role decomposition + hire plan |

**Neutralizer format:**
BUYER FEAR: [What they're thinking]
REALITY: [What's actually true — with evidence]
PROOF POINT: [Specific data from Deal Memory]
ACTION: [What seller/buyer can do to mitigate]

text


**Example:**
BUYER FEAR: "The owner IS the sales department.
If he leaves, the customers leave."

REALITY: While the owner manages key relationships,
80% of revenue comes from customers who have been
with the company 3+ years. They buy because of the
company's quality and reputation, not personal loyalty
to the owner.

PROOF POINT: 85 active customers, 4.5-year average
tenure, zero involuntary churn. Operations Manager
(8 years) has direct relationships with 6 of top 10
accounts.

ACTION: 12-month transition with structured customer
introductions. Seller will personally introduce buyer
to all top 20 accounts in first 60 days.

text


---

## THESIS CONSISTENCY RULE

The investment thesis headline and three reasons must appear
(adapted for format) in:

| Document | How Thesis Appears |
|----------|-------------------|
| CIM Executive Summary | Headline as opening line. Three reasons as investment highlights. |
| Teaser | Headline adapted for anonymous format. Three reasons as key highlights. |
| Buyer Email | Headline as subject line hook. Top reason in body. |
| Buyer Rationale (CIM §7) | Full thesis with supporting evidence. |
| Valuation Summary | Three reasons referenced as "key value drivers." |

This ensures EVERY buyer touchpoint tells the same story.

---

## THESIS QUALITY CHECK

Before finalizing, the agent tests the thesis against:

| Test | Pass? |
|------|-------|
| Does headline include a specific number? | Y/N |
| Would a buyer lean in hearing this at a cocktail party? | Y/N |
| Are all 3 reasons backed by Deal Memory data? | Y/N |
| Does "Why Now" reference both seller motivation and market timing? | Y/N |
| Are buyer fears identified for EVERY ⚠️ risk in Deal Memory? | Y/N |
| Is neutralizer evidence from Deal Memory, not fabricated? | Y/N |
| Is the thesis honest — nothing a buyer can't verify? | Y/N |
NEW FILE 3: deal_strategy.md
This is the strategic brain — not just analysis, but advice.

Markdown

# Deal Strategy Engine v1.0

## PURPOSE
This file turns the agent from an analyst into a STRATEGIST.
After building Deal Memory and Investment Thesis, the agent
generates a Deal Strategy that answers:

1. What price will actually clear?
2. Who is the MOST likely buyer?
3. What will kill this deal?
4. How should we run the process?
5. What's the negotiation leverage?

---

## STRATEGY GENERATION (Auto-runs After Valuation)

### 1. Market Clearing Price Analysis

Don't just calculate what multiples SAY the business is worth.
Calculate what a buyer will ACTUALLY pay.

**Framework:**

| Factor | Impact on Clearing Price |
|--------|------------------------|
| Valuation base case | Starting point |
| Buyer pool depth | More buyers → price up |
| SBA feasibility | If DSCR fails → price ceiling |
| Revenue quality score | Low score → buyers discount |
| Owner dependency | High → buyers demand discount or earnout |
| Customer concentration | High → buyers demand protection |
| Competitive process | Multiple LOIs → price up 5-15% |
| Time pressure | Seller rushing → price down |
| Market conditions | 🌐 Current M&A volume + sentiment |

**Output:**
MARKET CLEARING ANALYSIS — [Deal Name]

Valuation Range: $2.6M – $3.8M (bear to bull)
Recommended Ask: $3.4M (10% above base)
Expected Clearing Price: $2.9M – $3.2M
Gap to Seller Target: [if seller wants $X, gap is $Y]

Key Price Drivers:

Strong reputation in market (+)
18 years of consistent revenue (+)
Owner dependency (-$150K–$300K discount expected)
No contracts (-$100K–$200K discount expected)
SBA Ceiling Check:
At $3.2M, DSCR = 1.28x → PASSES (barely)
At $3.5M, DSCR = 1.18x → FAILS SBA underwriting
→ Price ceiling for SBA buyer: ~$3.3M

Strategic Buyer Premium:
If strategic acquirer with synergies: +$300K–$600K possible
→ Target strategics for price maximization

text


### 2. Ideal Buyer Ranking (Not Just Personas)

Go beyond "individual vs. search fund vs. PE."
Rank SPECIFIC buyer types by likelihood of closing.

**Framework:**

| Ranking Factor | Weight |
|---------------|--------|
| Can they AFFORD it (financing) | 30% |
| Do they WANT it (strategic fit) | 25% |
| Can they OPERATE it (capability) | 20% |
| Will they CLOSE (certainty) | 15% |
| Will they PAY FULL PRICE | 10% |

**Output:**
BUYER RANKING — [Deal Name]

#1: EXPERIENCED INDIVIDUAL OPERATOR (Score: 8.5/10)
Afford: SBA eligible, 10% down ✅
Want: Stable cash flow, manageable ops ✅
Operate: Trades experience preferred ✅
Close: SBA pre-approval = high certainty ✅
Price: Will pay asking if DSCR works ⚠️
→ PRIMARY TARGET. Start here.

#2: REGIONAL ROOFING STRATEGIC (Score: 7.8/10)
Afford: Cash or bank line ✅
Want: Geographic expansion ✅
Operate: Already in roofing ✅
Close: Faster than SBA, fewer contingencies ✅
Price: May pay premium for customers ✅
→ SECONDARY TARGET. Outreach in parallel.

#3: SEARCH FUND / ETA (Score: 6.5/10)
Afford: Investor-backed ✅
Want: Needs more growth story ⚠️
Operate: May struggle with trades ops ⚠️
Close: 60-90 day process typical ✅
Price: Will negotiate hard on owner-dependency ⚠️
→ TERTIARY. Include in broad outreach.

#4: PE / FAMILY OFFICE (Score: 4.0/10)
Afford: Yes ✅
Want: EBITDA too small for most ❌
Operate: Needs management team ❌
Close: Heavy process, long timeline ❌
Price: Would pay multiples but won't look ❌
→ SKIP unless EBITDA > $2M

text


### 3. Deal Killer Identification

For every deal, identify the top 3 things most likely to
kill it — and build a prevention plan.

**Framework:**

| Deal Killer Category | Detection | Prevention |
|---------------------|-----------|-----------|
| Price gap | Seller wants $X, market says $Y | Pre-market valuation alignment conversation |
| Financing failure | DSCR doesn't work at asking price | Run SBA model BEFORE marketing. Adjust price or structure. |
| Owner transition fear | Buyer scared owner is the business | Build detailed transition plan with timeline |
| Diligence surprise | Something ugly in the books | Pre-diligence financial review. Fix before marketing. |
| Customer loss during process | Key customer leaves during sale | Keep sale confidential. Plan customer communication. |
| Seller remorse | Seller gets cold feet mid-deal | Regular seller communication. Remind of motivation. |
| Lease issue | Landlord won't assign or terms bad | Landlord conversation BEFORE marketing |
| Buyer financing falls through | SBA denial post-LOI | Require pre-approval letter before accepting LOI |

**Output:**
TOP DEAL KILLERS — [Deal Name]

🚨 #1: SBA CEILING
The SBA math only works up to ~$3.3M. If seller insists
on $3.5M+ and buyer is SBA, deal will die in underwriting.
PREVENTION: Align seller on $3.0M-$3.3M range for SBA
buyers. Pursue strategics in parallel for higher price.

🚨 #2: OWNER TRANSITION
Owner does all sales and estimating. Every buyer will
flag this. If transition plan is weak, buyers walk.
PREVENTION: Build detailed 12-month transition plan
with customer intro schedule BEFORE first buyer meeting.
Document estimating process and pricing methodology.

🚨 #3: CUSTOMER CONCENTRATION
Top 3 at 40% with no contracts. If any top customer
signals uncertainty during diligence, buyer reprices.
PREVENTION: Get informal commitment from top 3 customers
that they're happy and staying. Seller note or earnout
on customer retention to give buyer confidence.

text


### 4. Process Strategy

How to run the sell-side process for maximum outcome.

**Decision tree based on Deal Memory:**
IF SDE < $1.5M AND SBA eligible:
→ BROAD OUTREACH to individual buyers
→ List on BizBuySell, BizQuest
→ Target 100-200 outreach emails
→ Expect 8-15 NDAs, 3-5 IOIs, 1-2 LOIs
→ Timeline: 6-9 months

IF SDE $1.5M-$3M:
→ TARGETED OUTREACH to searchers + strategics
→ Post on Axial
→ Target 50-100 outreach emails
→ Expect 10-20 NDAs, 4-8 IOIs, 2-4 LOIs
→ Create competitive tension
→ Timeline: 4-7 months

IF EBITDA > $3M:
→ CURATED PROCESS with PE + strategics
→ Engage 20-40 targeted buyers
→ Management presentations
→ Expect 5-10 IOIs, 2-4 LOIs
→ Run formal process with deadlines
→ Timeline: 5-9 months

text


### 5. Negotiation Leverage Map

What leverage does the seller have? What leverage does the buyer have?

**Auto-generate from Deal Memory:**
SELLER LEVERAGE:

[Revenue growing — buyer is acquiring momentum]
[Multiple buyers interested — competitive tension]
[SBA eligible — buyer can get financing easily]
[Owner willing to stay 12 months — reduces risk]
BUYER LEVERAGE:

[Owner-dependent — hard to replace]
[No contracts — revenue not guaranteed]
[Customer concentration — top 3 = 40%]
[Asking price at top of range for SBA DSCR]
NEGOTIATION GUIDANCE:
If buyer pushes on price:
→ "We have multiple interested parties" (if true)
→ "Seller willing to carry 10% note to bridge the gap"
→ "Let's structure an earnout on the growth upside"

If buyer pushes on transition risk:
→ "Seller committed to 12 months full-time"
→ "Key employee retention bonuses are on the table"
→ "Customer intros begin Day 1"

If buyer pushes on concentration:
→ "These relationships average 4.5 years"
→ "We'll tie a portion of the note to retention"
→ "Seller will personally introduce buyer to all top 20"

text


---

## /strategy COMMAND

When user types /strategy, generate the full Deal Strategy:
1. Market Clearing Price Analysis
2. Ideal Buyer Ranking
3. Top 3 Deal Killers + Prevention
4. Process Strategy Recommendation
5. Negotiation Leverage Map

All populated from Deal Memory. All consistent with other outputs.
