# Deal Structure Models v3.0

## Auto-populated from DEAL CONTEXT

## SBA 7(a) MODEL
🌐 Search for current rate before every model.

| Input | Value |
|-------|-------|
| Purchase Price | [from valuation or context] |
| Down Payment (10%) | [calculated] |
| SBA Loan Amount | [calculated] |
| Term | 10 years |
| Interest Rate | 🌐 [current Prime + 2.75%] |
| Monthly Payment | [calculated] |
| Annual Debt Service | [calculated] |
| Year 1 SDE | [from context] |
| Post-DS Cash Flow | [calculated] |
| Cash-on-Cash Return | [calculated] |
| DSCR | [calculated] — must be ≥1.25x |

## SBA ELIGIBILITY CHECK
Auto-check against DEAL CONTEXT:
- [ ] Profitable 3+ years → [from context: years in business]
- [ ] DSCR > 1.25x → [calculated]
- [ ] Buyer equity injection ≥ 10%
- [ ] Total project < $5M
- [ ] Seller note on full standby

## SELLER NET PROCEEDS COMPARISON

| Scenario | Gross | Fee | Taxes | Net |
|----------|-------|-----|-------|-----|
| All Cash | $X | ($X) | ($X) | $X |
| SBA + Note | $X | ($X) | ($X) | $X + PV$X |
| Cash + Earnout | $X | ($X) | ($X) | $X + up to $X |

## BUYER AFFORDABILITY MATRIX

| Price | Down | Monthly DS | SDE Needed | DSCR |
|-------|------|-----------|-----------|------|
| [range of prices around asking] | | | | |

## EARNOUT FRAMEWORK
Use when: concentration risk, seller price > buyer value, growth claims

| Structure | Trigger | Period | Max |
|-----------|---------|--------|-----|
| Revenue retention | >90% TTM | 12–18 mo | $X |
| Growth milestone | Revenue hits $X | 24 mo | $X |
| Customer retention | Named accounts | 12 mo | $X |
