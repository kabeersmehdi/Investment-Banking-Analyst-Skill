# Deal Screening v3.0

## Triggered by: /screening
## Should we take this engagement?

### Marketability Test (Must Pass ALL)
Auto-check from DEAL CONTEXT:

| Test | Threshold | This Deal | Pass? |
|------|-----------|-----------|-------|
| SDE | > $250K | [from context] | ✅/❌ |
| Profitable | 2+ of last 3 years | [from context] | ✅/❌ |
| No active litigation | None | [from context] | ✅/❌ |
| Owner price realistic | Within 20% of market | [from valuation] | ✅/❌ |
| Lease transferable | Yes | [from context] | ✅/❌ |
| Owner cooperative | Willing to engage | [from context] | ✅/❌ |

### Fee Economics
| Metric | Value |
|--------|-------|
| Estimated sale price | [from valuation base case] |
| Fee rate | [from engagement_guidance or broker input] |
| Expected fee | [calculated] |
| Est. time to close | [from context] |
| Est. broker hours | [calculated: ~100-200 hrs] |
| Effective hourly rate | [calculated] |
| Minimum fee threshold | [broker input] |
| **WORTH TAKING?** | **YES / NO / MARGINAL** |

### Walk-Away Triggers
🚨 Auto-flag if any present in DEAL CONTEXT:
- Owner refuses to provide financials
- Price expectation > 2x realistic range
- EBITDA declining AND owner won't flex on price
- Active lawsuit with uncertain outcome
- Previously listed with 2+ brokers, didn't sell

### RECOMMENDATION
Based on screening: TAKE / PASS / TAKE WITH CONDITIONS
If conditions: list what must change before signing engagement.
