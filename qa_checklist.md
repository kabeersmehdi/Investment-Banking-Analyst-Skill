# QA & Consistency Checklist v1.0

## PURPOSE
Before ANY output is shown to the user as "final," the agent
runs this checklist internally. If any check fails, the agent
fixes it before presenting.

---

## /qa COMMAND

User can also manually trigger this check.

---

## LEVEL 1: NUMBER CONSISTENCY

Run on: Every output

| Check | How | Fix |
|-------|-----|-----|
| Revenue matches Deal Memory across all outputs | Compare every instance | Replace with Deal Memory value |
| SDE matches Deal Memory across all outputs | Compare every instance | Replace with Deal Memory value |
| EBITDA matches Deal Memory across all outputs | Compare every instance | Replace with Deal Memory value |
| Add-backs total matches across QoE, CIM, valuation | Sum and compare | Recalculate from Deal Memory |
| Asking price consistent across teaser, CIM, structure | Compare | Use Deal Memory value |
| Employee count consistent | Compare | Use Deal Memory value |
| Years in business consistent | Compare | Use Deal Memory value |
| Revenue growth % calculated correctly | Verify math | Recalculate |
| Margins calculated correctly | Revenue ÷ metric | Recalculate |
| SBA payment calculated correctly | Verify amortization | Recalculate |
| DSCR calculated correctly | SDE ÷ annual debt service | Recalculate |

---

## LEVEL 2: NARRATIVE CONSISTENCY

Run on: CIM, teaser, buyer emails, valuation

| Check | Pass? |
|-------|-------|
| Investment thesis headline used in CIM exec summary | Y/N |
| Same 3 reasons to buy in CIM AND teaser AND emails | Y/N |
| "Why now" narrative consistent across CIM and teaser | Y/N |
| Risks in CIM match risks in risk report | Y/N |
| Growth opportunities in CIM match Deal Memory | Y/N |
| Buyer rationale references the same value drivers as valuation | Y/N |
| Teaser contains NO identifying information | Y/N |
| All documents tell the SAME story about the business | Y/N |

---

## LEVEL 3: LOGICAL CHECKS

Run on: Valuation, QoE, deal structure

| Check | Flag If |
|-------|---------|
| SDE margin reasonable for industry | Outside ±30% of benchmark |
| EBITDA margin reasonable for industry | Outside ±30% of benchmark |
| Revenue growth claim matches actual data | Growth % ≠ calculated |
| Add-backs > 40% of reported net income | ⚠️ Aggressive add-backs |
| Asking price > bull case valuation | ⚠️ Overpriced |
| Asking price < bear case valuation | ⚠️ Underpriced |
| DSCR < 1.25x at asking price | ⚠️ SBA won't underwrite |
| Revenue declining but growth opportunities cited | ⚠️ Contradiction |
| Owner called "not critical" but works 50+ hrs | ⚠️ Contradiction |
| "Strong management team" but no #2 exists | ⚠️ Contradiction |
| "Recurring revenue" but recurring_pct < 20% | ⚠️ Misleading |
| "Diversified customer base" but top 3 > 50% | ⚠️ Misleading |
| "Minimal transition risk" but owner does all sales | ⚠️ Misleading |

---

## LEVEL 4: COMPLETENESS CHECK

Run on: CIM, full output packages

| Section | Present? | Quality? |
|---------|---------|---------|
| Executive Summary | Y/N | Strong hook? Specific numbers? |
| Industry Overview | Y/N | Live data sourced? |
| Business Overview | Y/N | Customer + ops detail? |
| Financial Performance | Y/N | 3-year trend? Add-back table? |
| Growth Opportunities | Y/N | Specific + credible? |
| Risk Factors | Y/N | Honest + mitigation? |
| Buyer Rationale | Y/N | Return analysis included? |
| Transaction Overview | Y/N | Structure + assets + timeline? |
| Source Citations | Y/N | All market claims sourced? |

---

## LEVEL 5: ANTI-BULLSHIT CHECK

This is the "would a smart buyer see through this?" check.

| Claim Made | Evidence in Deal Memory | Verdict |
|-----------|----------------------|---------|
| [claim 1] | [data or lack thereof] | Supported / Weak / Unsupported |
| [claim 2] | [data] | Supported / Weak / Unsupported |

Any "Unsupported" → remove or rephrase the claim.
Any "Weak" → add a caveat or soften the language.

---

## QA OUTPUT FORMAT
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
✅ QA CHECK — [Deal Name]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

NUMBERS: ✅ All consistent (12/12 checks passed)
NARRATIVE: ✅ All consistent (8/8 checks passed)
LOGIC: ⚠️ 1 flag (add-backs = 38% of net income —
close to aggressive threshold)
COMPLETE: ✅ All sections present
ANTI-BS: ⚠️ 1 weak claim ("diversified customer base"
but top 3 = 40% — recommend rephrasing to
"growing customer base with concentration
being actively addressed")

OVERALL: PASS WITH 2 WARNINGS
Action items:

Consider softening add-back language in CIM
Rephrase customer diversification claim
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━



---

## AUTO-RUN RULES

The agent runs QA checks automatically:
- LEVEL 1 (numbers): Before EVERY output
- LEVEL 2 (narrative): Before CIM, teaser, buyer emails
- LEVEL 3 (logic): Before valuation, QoE, deal structure
- LEVEL 4 (completeness): Before CIM and /all
- LEVEL 5 (anti-BS): Before CIM and buyer-facing materials

The user can also run /qa manually at any time.
The user can run /check for a quick consistency-only check.
