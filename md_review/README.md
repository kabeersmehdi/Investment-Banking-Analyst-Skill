## Purpose

A credibility-first review tool for analyst deliverables (CIMs, pitch books, financial summaries, models, valuation exhibits) that behaves like an MD at a lower-middle-market M&A advisory firm (e.g., Stony Hill):

- Prioritize the issues that will kill buyer/seller confidence  
- Think adversarially  
- Enforce one source of truth  
- Produce a short, ranked punch list (“8 must-fix items”) rather than a long nitpick list  

---

## Design Principles

- ✅ **Prioritization over volume**  
  Critical / High / Medium / Low, with exact locations and actionable fixes  

- 🧠 **Adversarial buyer lens**  
  Flags valuation/comps/DCF inconsistencies, missing EV bridge, unsupported claims, inconsistent narratives  

- 📏 **One source of truth**  
  Canonical metrics + canonical number formatting + terminology registry  

- 🧼 **Clarity & professionalism**  
  No draft comments, consistent formatting, explicit assumptions/definitions  

- 🔒 **Confidentiality Safe Mode (default)**  
  No client names, no non-public financials, no data-room text; scrubbed audit logging  

---

## What It Checks (The “MD Lens”)

### ✅ Tier 1 — Must-Have (Highest Leverage)

- **Grammar & terminology**  
  Typos, awkward phrasing, passive voice, inconsistent terms (“Seller” vs “Vendor”)

- **Number consistency**  
  Canonical format ($X.Xm or $X,XXX,XXX), consistent rounding, same metric matches across slides/tables/models, table sums add up  

- **Date consistency**  
  FY / projection period / transaction date consistent across narrative, tables, model tabs  

- **Formatting & client-readiness**  
  Fonts/colors, slide structure, no internal comments/draft notes  

---

### 📊 Tier 2 — IB / M&A-Specific (Credibility Killers)

- **Valuation sanity**  
  DCF assumptions coherent (growth vs discount rate, terminal multiple vs comps)  
  Comps multiples within reasonable sector band  
  EV bridge present and correct (EV ↔ Equity Value, net debt, options/minority interest if applicable)

- **CIM / pitch structure**  
  Required sections present and ordered:  
  Company Overview, Financial Summary, Projections + Assumptions, Growth Plan, Transaction Overview, Appendix  

- **Narrative ↔ numbers alignment**  
  Growth claims supported by CAGR/margins  
  Risks paired with mitigations  
  No contradictions between story and model  

- **Financial cross-check**  
  P&L → BS → CF flow integrity (net income, depreciation, working capital, retained earnings)

---

### 🏢 Tier 3 — Stony Hill / Sell-Side Specific

- **Seller narrative consistency**  
  “Why sell” is specific and credible  
  Value creation plan is concrete and supportable  

- **Valuation range discipline**  
  Asking range aligns with multiple + financial profile  
  QoE adjustments documented and defensible  

- **Professional polish**  
  Consistent appendix definitions  
  Explicit sources for each key figure  

---

## Output: MD-Style Punch List

The default report is a **ranked punch list**, not a full checklist.

Each issue includes:

- **Severity**: Critical / High / Medium / Low  
- **Issue + location**: Exact slide, table, model tab, cell, or page  
- **Why it matters**: Buyer/seller attack surface  
- **Recommended fix**: Precise, defensible change  
- **Owner**: Analyst / Associate / MD (suggested)  

---

### Example Output

| Rank | Severity | Issue | Location | Why it kills credibility | Recommended fix | Owner |
|------|----------|-------|----------|--------------------------|------------------|--------|
| 1 | Critical | EBITDA inconsistent ($5.0m vs $5m) | Slide 4 vs Slide 7 | Buyer will challenge numbers immediately | Canonicalize to $5.0m everywhere | Analyst |
| 2 | Critical | Missing EV bridge | Valuation page | Buyer will demand it in diligence | Add explicit EV ↔ Equity bridge | Analyst |
| 3 | High | Table total $12.4m vs sum $12.35m | Financial summary table | Signals sloppy diligence | Reconcile or state rounding policy | Analyst |

---

## Configuration (Make It Your Firm Standard)

### `config/rules.yaml` (Core Guardrails)

- Canonical number format: `$X.Xm` (one decimal) or `$X,XXX,XXX` (whole dollars) — choose one  
- Rounding policy: headline figures vs line items; tolerance for sum drift  
- Terminology registry: canonical terms (e.g., EBITDA, Net Debt, Enterprise Value)  
- Required CIM sections: enforce exact section names/order  
- Tolerance rules: acceptable variance (e.g., ±$0.1m or ±0.5%)  

---

### `config/industry_ranges.yaml` (Non-Sensitive)

- Sector-based EBITDA multiple bands  
  - Example: software 8.5x–12.0x  
  - Example: industrials 6.0x–9.0x  

Used for valuation sanity checks. Must remain generic, non-sensitive, and auditable.

---

### `config/confidentiality.yaml` (Safe Mode Defaults)

- `safe_mode: true` (default)  
- Redaction rules (client names, emails, confidential labels)  
- Audit policy:
  - No raw client text stored  
  - Retain hashes / check counts only  

---

## Bottom Line

This tool answers one question:

**“If this goes to a buyer tomorrow, what breaks?”**

Fix those issues first. Everything else is secondary.
