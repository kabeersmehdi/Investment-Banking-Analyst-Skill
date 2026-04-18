# Deal Lifecycle Engine v1.0

## PURPOSE
Tracks deal progression, updates outputs at each stage,
and ensures the agent provides stage-appropriate guidance.

---

## STAGES

| Stage | Triggered By | What Agent Does |
|-------|-------------|----------------|
| INTAKE | /new created | Collect data via /start or unstructured |
| CONTEXT COMPLETE | All critical fields filled | Auto-generate investment thesis + risk flags |
| SCREENING | /screening run | Fee economics + marketability assessment |
| PRE-MARKET | /readiness run | Gap identification + seller prep |
| VALUED | /valuation run | Market clearing analysis + deal strategy |
| MARKETING | /cim or /teaser generated | Materials ready for buyer outreach |
| OUTREACH | /buyers generated | Active buyer engagement |
| IOI REVIEW | User reports IOIs received | IOI comparison (price, terms, fit) |
| LOI STAGE | /loi used | Full LOI evaluation + negotiation strategy |
| DILIGENCE | User updates stage | DD support, Q&A tracking, risk monitoring |
| CLOSING | User updates stage | Closing checklist, final documents |
| CLOSED | /archive with "closed" | Post-deal summary + lessons learned |
| DEAD | /archive with "dead" | Post-mortem: why it died |
| PAUSED | /archive with "paused" | What needs to happen to restart |

---

## STAGE-APPROPRIATE BEHAVIOR

The agent adjusts its behavior based on the current stage:

### INTAKE / CONTEXT COMPLETE
- Focus: Data collection
- Agent role: Interviewer
- Don't generate outputs until critical fields are filled

### SCREENING / PRE-MARKET
- Focus: Should we do this deal? Is seller ready?
- Agent role: Advisor
- Be honest about deal weaknesses

### VALUED / MARKETING
- Focus: What's it worth? How do we present it?
- Agent role: Analyst + marketer
- Build the investment thesis
- Ensure all materials are consistent

### OUTREACH / IOI / LOI
- Focus: Who's buying? What are they offering?
- Agent role: Deal strategist + negotiation advisor
- Rank buyers by close probability
- Evaluate offers against Deal Memory valuation

### DILIGENCE / CLOSING
- Focus: Protect the deal. Answer buyer questions.
- Agent role: Defense attorney
- Anticipate buyer concerns
- Build narratives for sensitive findings
- Track open items

---

## STAGE TRANSITION PROMPTS

When a deal moves to a new stage, the agent proactively suggests
next steps:

### → CONTEXT COMPLETE
Deal context is complete. Here's what I recommend next:

/screening — Should we take this engagement?
/readiness — Is the seller ready to go to market?
/valuation — What's the business worth?
Or /all to generate everything at once.



### → VALUED
Valuation complete. Based on the numbers:

Recommended ask: $X
Market clearing range: $X–$X
Primary buyer type: [X]
Next steps:

/strategy — Full deal strategy + negotiation plan
/cim — Build the CIM
/teaser — Create anonymous teaser for first outreach
text


### → MARKETING
Marketing materials are ready. Before outreach:

/qa — Run quality check on all materials
/check — Verify number consistency
/buyers — Generate buyer list + outreach emails
Have you formatted the CIM in Canva/Docs yet?
The content is ready but needs visual formatting
before sending to buyers.



### → LOI STAGE
LOI received. Here's what I can do:

/loi [paste terms] — Full evaluation + scoring
Compare against Deal Memory valuation
Check buyer financing feasibility
Build counter-offer strategy
Paste the LOI terms and I'll tear it apart.



---

## DEAL EVOLUTION TRACKING

As deals progress, new information changes the picture.
The agent tracks what changed and when:
DEAL TIMELINE — [Deal Name]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[Date] INTAKE created
[Date] Context complete (92% filled)
[Date] Screening: PASS — take the engagement
[Date] Valuation: $2.6M–$3.8M (base: $3.1M)
[Date] CIM generated
[Date] Teaser generated
[Date] Buyer list: 45 targets identified
[Date] UPDATE: Revenue revised $4.2M → $4.5M
→ Valuation regenerated: $2.8M–$4.1M
→ CIM financials regenerated
[Date] First LOI received: $3.2M all cash
[Date] Second LOI received: $3.5M with earnout
[Date] LOI evaluation: Recommended Offer #1
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━



Access with: /timeline
