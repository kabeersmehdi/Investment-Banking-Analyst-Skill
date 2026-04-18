# ONBOARDING FLOW v3.1 — Guided + Unstructured

## TWO INTAKE PATHS

### Path A: Guided Onboarding (/start)
The 7-phase questionnaire (unchanged from v3.0).
Used when broker wants to be walked through it.

### Path B: Unstructured Dump (Paste Info)
User pastes deal info in any format. Agent parses it.
Used when broker already has the info and just wants
to get moving.

### Path C: Hybrid
User pastes some info, agent parses it, then asks
remaining questions from the guided flow — but ONLY
the questions whose answers weren't found in the dump.

---

## PATH B: UNSTRUCTURED INTAKE PROTOCOL

### Trigger
Any of these trigger unstructured intake:
- User pastes a paragraph of deal info after /new [name]
- User says "here's what I know about this deal"
- User forwards an email or notes about a business
- User provides partial info without using /start
- User says "I have a new deal" and describes it

### Parsing Engine

#### Financial Data Extraction
Look for patterns:
- "$X.XM revenue" or "revenue of X" or "top line is X"
- "$XK SDE" or "seller's discretionary earnings" or "cash flow"
- "EBITDA of X" or "earnings of X"
- "profit of X" or "net income X" or "makes X a year"
- "X employees" or "X people" or "team of X"
- "X years" or "been around since XXXX" or "founded in XXXX"
- Any dollar amounts — try to map to the right field

#### Owner Data Extraction
Look for:
- Age mentions ("owner is 62")
- Role descriptions ("runs sales", "does estimating")
- Motivation ("wants to retire", "health issues", "burned out")
- Transition ("willing to stay X months")
- Family ("wife does the books", "son works there")
- Hours ("works 60 hours", "part-time", "absentee")

#### Customer Data Extraction
Look for:
- Concentration ("top customer is 20%", "biggest client is X%")
- Count ("85 customers", "about 100 accounts")
- Contracts ("no contracts", "MSAs in place")
- Recurring ("mostly project work", "X% recurring")

#### Risk Data Extraction
Look for negative indicators:
- "owner does all the sales"
- "no contracts"
- "concentrated"
- "declining"
- "messy books" or "tax returns only"
- "lease is up soon"
- Any phrase suggesting concern

#### Growth Data Extraction
Look for:
- "could expand into X"
- "hasn't done any marketing"
- "commercial side is untapped"
- "only serves [geography]"

### Parsing Output Format

After parsing, display:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📋 DEAL INTAKE — PARSED FROM YOUR INPUT
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

COMPANY BASICS
Name: [extracted or "Not provided"]
Industry: [extracted or "Not identified"]
Location: [extracted or "Not provided"]
Years in Business: [extracted or "Unknown"]
Business Model: [extracted or "Unknown"]

FINANCIALS
Revenue (TTM): [extracted or "Not provided"]
SDE: [extracted or "Not provided"]
EBITDA: [extracted or "Not provided"]
Net Income: [extracted or "Not provided"]

OWNER
Role: [extracted or "Unknown"]
Hours/Week: [extracted or "Unknown"]
Reason for Sale: [extracted or "Unknown"]
Transition: [extracted or "Unknown"]

CUSTOMERS
Concentration: [extracted or "Unknown"]
Contracts: [extracted or "Unknown"]
Revenue Type: [extracted or "Unknown"]

TEAM
Employees: [extracted or "Unknown"]
Has #2: [extracted or "Unknown"]

DEAL PARAMETERS
Asking Price: [extracted or "TBD"]
Structure: [extracted or "Unknown"]
Timeline: [extracted or "Unknown"]

RISKS IDENTIFIED
⚠️ [any risks detected from language]

GROWTH OPPORTUNITIES
✅ [any growth levers detected]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

text


Then immediately show gaps:
MISSING INFORMATION

🔴 CRITICAL — Need these for valuation:
• [field]: [why it matters]
• [field]: [why it matters]

🟡 IMPORTANT — Need these for CIM/risk report:
• [field]

🟢 NICE TO HAVE:
• [field]

Want to fill these in now? Or I can work with what
I have and flag assumptions.
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

text


---

## FIELD REQUIREMENT TIERS

### 🔴 CRITICAL (Cannot produce valuation without)
- Industry
- Revenue (TTM) — at least one year
- SDE or EBITDA or Net Income (need at least one to calculate)
- Owner compensation (to calculate SDE if not provided)

### 🟡 IMPORTANT (Needed for full CIM + risk)
- Location
- Years in business
- Employee count
- Owner role and hours
- Customer concentration (top 1 and top 3 %)
- Revenue type (recurring vs project)
- Contracts in place (yes/no)
- Facility status (owned/leased)
- Reason for sale
- Add-backs (itemized with amounts)

### 🟢 NICE TO HAVE (Improves quality)
- Prior year revenue (2-3 years)
- Gross profit / gross margin
- Specific add-back documentation
- Average customer tenure
- Seasonality description
- Key roles on team
- Growth opportunities (specific)
- Known risks (itemized)
- Deal structure preference
- Target timeline

---

## PHASE 1-7 GUIDED QUESTIONS (UNCHANGED)

[Same as v3.0 — Phase 1 through Phase 7]
[Only asked if /start is used OR to fill gaps after 
unstructured intake]

---

## SMART GAP-FILLING

When asking for missing data after unstructured intake,
DON'T re-ask as a formal questionnaire. Instead, ask
conversationally:

INSTEAD OF:
"Phase 2, Question 4: What is your TTM Gross Profit?"

DO THIS:
"I've got the revenue at $4.2M and SDE at $850K. 
Quick ones I'm missing:
- What's the gross profit or gross margin? 
  (Even a rough % works)
- How much does the owner pay himself total 
  (salary + distributions + benefits)?
- Any debt on the books?"

Group 3-5 related questions. Don't overwhelm.

---

## CONTEXT COMPLETION TRACKING

Track completion % for each deal:

| Section | Fields | Filled | % |
|---------|--------|--------|---|
| Company Basics | 6 | 5 | 83% |
| Financials | 12 | 8 | 67% |
| Add-Backs | variable | 4 items | ✓ |
| Customers | 10 | 6 | 60% |
| Operations | 14 | 10 | 71% |
| Deal Parameters | 9 | 5 | 56% |
| Broker Notes | 7 | 3 | 43% |
| **OVERALL** | | | **64%** |

Show this in /status and /deals dashboard.
