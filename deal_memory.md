# Deal Memory Layer v1.0

## PURPOSE
This is the SINGLE SOURCE OF TRUTH for every deal.
Every output — valuation, CIM, teaser, buyer list, risk report,
QoE, deal structure — MUST read from and stay consistent with
the Deal Memory.

No output may contradict the Deal Memory. If the agent detects
a contradiction, it must stop and resolve it before proceeding.

---

## DEAL MEMORY STRUCTURE

When /start completes or unstructured intake is parsed, the
agent builds the following locked data object. This object
is THE authority for all downstream outputs.

### CORE FACTS (Immutable Unless /update Used)
DEAL_MEMORY: {

identity: {
name: "",
codename: "",
industry: "",
sub_industry: "",
naics: "",
location_state: "",
location_metro: "",
years_in_business: 0,
business_model: "",
description: ""
},

financials: {
revenue: {
ttm: 0,
year_1: 0,
year_2: 0,
yoy_growth_pct: 0
},
gross_profit: {
ttm: 0,
margin_pct: 0
},
net_income_reported: 0,
add_backs: [
{ item: "", amount: 0, documented: false }
],
total_add_backs: 0,
owner_comp: {
current_total: 0,
market_replacement: 0,
excess_above_market: 0
},
sde: {
ttm: 0,
margin_pct: 0,
calculation: "net_income + total_add_backs"
},
ebitda: {
ttm: 0,
margin_pct: 0,
calculation: "sde - market_replacement_salary"
},
working_capital: 0,
capex_annual: 0,
debt: 0,
cash: 0,
accounting_basis: "",
financial_records: ""
},

customers: {
total_active: 0,
top_1_pct: 0,
top_3_pct: 0,
top_10_pct: 0,
contracts_in_place: false,
avg_tenure_years: 0,
recurring_pct: 0,
repeat_no_contract_pct: 0,
project_based_pct: 0,
revenue_quality_score: 0
},

operations: {
owner_role: "",
owner_hours: 0,
reason_for_sale: "",
transition_months: 0,
family_in_business: "",
ft_employees: 0,
has_number_2: false,
key_roles: [],
facility: "",
lease_remaining_months: 0
},

deal: {
asking_price: 0,
structure_preference: "",
sba_eligible: false,
seller_note_max_pct: 0,
target_close_months: 0,
assets_included: [],
assets_excluded: []
},

valuation: {
multiple_range: { low: 0, mid: 0, high: 0 },
multiple_source: "",
ev_range: { bear: 0, base: 0, bull: 0 },
recommended_ask: 0,
adjustments_applied: [],
confidence: ""
},

risks: [
{ risk: "", severity: "", source_field: "", narrative: "" }
],

growth: [
{ lever: "", description: "", evidence: "" }
],

investment_thesis: {
headline: "",
three_reasons_to_buy: [],
why_now: "",
buyer_fear_neutralizers: []
}
}



---

## CONSISTENCY RULES

### Rule 1: One Number, One Source
Every financial figure in any output MUST match the Deal Memory exactly.
If the CIM says revenue is $4.2M, the teaser says $4.2M, the valuation
uses $4.2M, and the buyer email says $4.2M.

### Rule 2: SDE/EBITDA Lock
Once SDE and EBITDA are calculated in Deal Memory, they cannot be
presented differently in any output. The EXACT same number appears
everywhere.

Specifically:
- Valuation: uses Deal Memory SDE/EBITDA
- CIM financial tables: uses Deal Memory SDE/EBITDA
- CIM executive summary: uses Deal Memory SDE/EBITDA
- Teaser: uses Deal Memory SDE/EBITDA (or rounded range)
- Buyer emails: uses Deal Memory SDE/EBITDA
- SBA model: uses Deal Memory SDE/EBITDA
- LOI evaluation: compares against Deal Memory SDE/EBITDA

### Rule 3: Adjustment Consistency
If an add-back is listed in Deal Memory, it must appear identically in:
- QoE EBITDA bridge
- CIM add-back schedule
- Valuation normalization section
Same description. Same dollar amount.

### Rule 4: Risk Consistency
If a risk is flagged in Deal Memory, it must appear in:
- Risk report
- CIM risk section
- Buyer targeting (as concern to address)
- LOI evaluation (as negotiation factor)

A risk cannot appear in the CIM but be absent from the risk report,
or vice versa.

### Rule 5: Growth Consistency
Growth opportunities listed in Deal Memory must appear identically in:
- CIM growth section
- Buyer rationale section
- Investment thesis
- Teaser (abbreviated)

### Rule 6: Narrative Consistency
The investment thesis headline and core narrative must be reflected in:
- CIM executive summary (first paragraph)
- Teaser opportunity description
- Buyer outreach email hook
- Buyer rationale section

The SAME story is told across all documents, adapted for format
but never contradicting.

---

## UPDATE PROTOCOL

When /update is used:
1. Update the specific field in Deal Memory
2. Show: "DEAL MEMORY UPDATED: [field] [old] → [new]"
3. Recalculate any dependent fields:
   - If add-back changes → recalculate SDE → recalculate EBITDA
   - If revenue changes → recalculate margins
   - If customer data changes → recalculate revenue quality score
   - If owner data changes → re-evaluate risk flags
4. List ALL outputs that now contain stale data
5. Ask: "Want me to regenerate [affected outputs]?"

---

## CONSISTENCY CHECK COMMAND

### /check

When user types /check, the agent:
1. Reviews all generated outputs against Deal Memory
2. Flags any inconsistency found:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🔍 CONSISTENCY CHECK — [Deal Name]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

✅ Revenue: Consistent across all outputs ($4.2M)
✅ SDE: Consistent across all outputs ($850K)
⚠️ EBITDA: CIM shows $710K but valuation uses $700K
→ Deal Memory says: $700K
→ FIX: Regenerate CIM financial section
✅ Add-backs: Consistent (5 items, $186.2K total)
✅ Risks: All 4 flagged risks appear in risk report AND CIM
✅ Growth: All 4 levers consistent across CIM and teaser
⚠️ Asking price: Teaser shows $3.5M but valuation
recommends $3.2M
→ Which is correct? /update asking_price to resolve

RESULT: 2 inconsistencies found. Fix before sending to buyers.
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━


---

## PRE-OUTPUT CHECK

Before generating ANY output, the agent silently runs:
1. Are all referenced numbers from Deal Memory?
2. Does the narrative match the investment thesis?
3. Are risks acknowledged consistently?
4. Are growth levers described the same way?

If any check fails, fix it before presenting the output.
Do NOT present inconsistent outputs to the user.
