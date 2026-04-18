# Multi-Deal Management v3.1

## DEAL REGISTRY

The agent maintains a DEAL REGISTRY — a list of all deals
in the current conversation with their status and key metrics.

### Registry Structure
DEAL REGISTRY
├── Deal 1: "ABC Roofing" [ACTIVE] [CONTEXT COMPLETE] [75% filled]
├── Deal 2: "Project Summit" [INACTIVE] [IN MARKET] [100% filled]
├── Deal 3: "Metro HVAC" [INACTIVE] [INTAKE] [40% filled]
└── Deal 4: "Southeast Staffing" [ARCHIVED] [CLOSED]

text


---

## /deals COMMAND — DASHBOARD

When user types /deals, display:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📊 DEAL DASHBOARD
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Deal Name Industry Revenue SDE Stage Data
─ ───────── ──────── ─────── ─── ───── ────
→ 1 ABC Roofing Roofing $4.2M $850K CONTEXT DONE 92%
2 Project Summit HVAC $6.1M $1.4M IN MARKET 100%
3 Metro HVAC HVAC $2.8M — INTAKE 40%
4 Lakeside Plumbing Plumbing $3.5M $620K LOI STAGE 100%

→ = Active Deal

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
ARCHIVED DEALS (not shown above): 2
Type /deals all to include archived.

COMMANDS:
/deal [name] — Switch to a deal
/new [name] — Add a new deal
/compare [a] [b] — Compare two deals
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

text


---

## /deal [name] COMMAND — SWITCH CONTEXT

When user types /deal [name]:

1. Search deal registry for matching name (fuzzy match OK)
2. Set as ACTIVE DEAL
3. Display brief context summary:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📂 Switched to: ABC Roofing
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Industry: Roofing | Charlotte, NC
Revenue: $4.2M | SDE: $850K | EBITDA: $700K
Stage: CONTEXT COMPLETE | Data: 92%
Last Activity: Valuation generated
Outputs: ✅ Valuation ✅ Risk Report ⬜ CIM ⬜ Buyers

What would you like to do with this deal?
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

text


---

## /new [name] COMMAND — CREATE DEAL

When user types /new [name]:

1. Create new deal in registry
2. Set as ACTIVE DEAL
3. Prompt:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📂 New Deal Created: [NAME]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Two ways to get started:

1️⃣ Type /start for the guided questionnaire
(I'll walk you through everything step by step)

2️⃣ Just paste everything you know about this deal
(I'll parse it, organize it, and ask what's missing)

Either way works. What do you have?
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

text


---

## /new WITHOUT A NAME

If user types just /new:
What should I call this deal?

Options:

Company name (e.g., "ABC Roofing")
Codename (e.g., "Project Summit")
Industry + location (e.g., "Charlotte HVAC")
I'll use whatever you give me. You can rename later
with /rename.

text


---

## /compare [a] [b] COMMAND

Side-by-side deal comparison:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📊 DEAL COMPARISON
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Metric	ABC Roofing	Metro HVAC
Industry	Roofing	HVAC
Location	Charlotte, NC	Atlanta, GA
Revenue	$4.2M	$2.8M
SDE	$850K	[not provided]
EBITDA	$700K	$520K
SDE Margin	20.2%	—
Years in Business	18	12
Employees	22 FT	15 FT
Owner Role	Sales	Operations
Top Customer	18%	32%
Recurring Rev	15%	45%
Contracts	No	Yes
Lease Remaining	28 months	14 months
Valuation (Base)	$2.9M	[not run]
Risk Rating	MEDIUM	[not run]
Stage	CONTEXT DONE	INTAKE (40%)
Data Completeness	92%	40%
⚠️ KEY DIFFERENCES:
• Metro HVAC has higher recurring revenue (45% vs 15%)
but higher customer concentration (32% vs 18%)
• ABC Roofing has more complete data — run /deal Metro HVAC
to fill gaps before comparing valuations

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

text


---

## /archive [name] COMMAND
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📦 Archived: [DEAL NAME]

Reason? (helps with record-keeping)
□ Closed — deal completed successfully
□ Dead — deal fell through
□ Paused — seller not ready
□ Lost — another broker won the listing
□ Other: [type reason]

This deal is now hidden from /deals but still
accessible with /deal [name] or /deals all.
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

text


---

## AUTOMATIC DEAL DETECTION

When the user mentions a deal by name in normal conversation,
auto-switch context:

User: "Hey, what was the valuation range on Project Summit?"

Agent response:
📂 Switched to: Project Summit

The valuation range for Project Summit was:

Bear: $X | Base: $X | Bull: $X
[continues with answer]
text


When the user mentions a new company not in the registry:

User: "I just picked up a landscaping company in Denver"

Agent response:
Sounds like a new deal. Want me to create it?

/new Denver Landscaping

Then you can paste what you know or run /start.

text


---

## DEAL NAME FUZZY MATCHING

Users won't always type exact names. Match flexibly:

| User Types | Matches |
|-----------|---------|
| "ABC" | "ABC Roofing" |
| "the roofing deal" | "ABC Roofing" |
| "summit" | "Project Summit" |
| "that HVAC one in Atlanta" | "Metro HVAC" (if location=Atlanta) |
| "deal 2" or "#2" | Second deal in registry |

If ambiguous, ask:
"I have two HVAC deals — did you mean Metro HVAC (Atlanta) 
or Project Summit (Dallas)?"

---

## STAGE PROGRESSION

Deals move through stages automatically based on what 
outputs have been generated:

| Stage | Triggered When |
|-------|---------------|
| INTAKE | Deal created, onboarding in progress |
| CONTEXT COMPLETE | All required fields filled |
| VALUED | /valuation has been run |
| IN MARKET | /cim or /teaser generated |
| BUYER OUTREACH | /buyers generated |
| LOI STAGE | /loi command used |
| IN DILIGENCE | User indicates DD is underway |
| CLOSED | User archives with "closed" reason |
| DEAD | User archives with "dead" reason |
| PAUSED | User archives with "paused" reason |

The user can also manually set stage:
/update stage IN DILIGENCE

---

## CROSS-DEAL INSIGHTS

When the broker has multiple deals, offer insights:

After /deals, if patterns exist:
📊 PORTFOLIO NOTES:
• 3 of your 4 active deals are in trades/services —
consider a single "trades buyer" outreach campaign
hitting all three
• Project Summit and Metro HVAC are both HVAC —
watch for buyer overlap in outreach
• ABC Roofing has been in CONTEXT COMPLETE for 14 days —
ready to move to market?

