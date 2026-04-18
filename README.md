# Investment-Banking-Analyst-Skill

# 🧠 Lower Middle Market M&A Analyst Agent

A production-grade AI agent designed to replicate a top-tier investment banking analyst—specifically tailored for **sell-side M&A brokers operating in the $1M–$5M EBITDA range**.

This agent is optimized for **real-world deal execution**, not theoretical finance.

---

## 🚀 Overview

The M&A Analyst Agent assists brokers by:
- Valuing businesses with imperfect financials (SDE-focused)
- Creating buyer-ready marketing materials (CIMs, teasers)
- Supporting live deal execution and diligence
- Generating buyer lists and outreach strategies
- Producing actionable market and industry insights

It is built to function like a **high-performing IB analyst under real deal pressure**.

---

## 🎯 Target Use Case

- Sell-side M&A brokers
- Lower middle market deals ($1M–$5M EBITDA)
- Founder-owned businesses
- Messy or incomplete financials (QuickBooks, tax returns, SDE adjustments)

---

## 🧩 Core Capabilities

### 1. Financial Modeling & Valuation
- SDE normalization and add-backs
- EBITDA adjustments
- Comparable transaction analysis (primary method)
- Simplified DCF modeling
- Scenario and sensitivity analysis

**Outputs:**
- Valuation range
- Recommended asking price
- Key value drivers

---

### 2. CIM & Marketing Material Generation
- 1-page anonymous teaser
- Full Confidential Information Memorandum (CIM)

**Includes:**
- Executive summary
- Business overview
- Financial performance
- Growth opportunities
- Risk factors
- Buyer rationale

---

### 3. Deal Execution & Due Diligence
- Data room structuring
- Buyer Q&A tracking frameworks
- Financial risk identification

**Outputs:**
- Risk reports
- Red flags
- Narrative strategies to address concerns

---

### 4. Buyer Targeting & Outreach
- Buyer persona identification:
  - Individual buyers
  - Search funds
  - Strategics
  - Financial buyers

**Generates:**
- Target buyer lists
- Outreach messaging
- Follow-up sequences

---

### 5. Industry & Market Intelligence
- Market size & growth (CAGR)
- Industry trends
- Competitive dynamics

**Outputs:**
- Strategic positioning insights
- “Why now” sell narrative

---

### 6. Iteration & Quality Control
- Self-critique loops
- Assumption validation
- Output refinement (2–3 passes)

---

## ⚙️ How It Works

### Step 1: Input Data
User provides:
- Company overview
- Financials (revenue, SDE, EBITDA)
- Industry
- Location
- Notes on operations, customers, risks

---

### Step 2: Processing
The agent:
1. Normalizes financials
2. Applies valuation methodologies
3. Identifies risks and opportunities
4. Builds marketing materials
5. Suggests buyer strategy

---

### Step 3: Output
Structured outputs include:
- Valuation summary
- CIM
- Teaser
- Buyer list + outreach messaging
- Risk analysis

---

## 📥 Input Schema (Example)

```json
{
  "company_name": "ABC Roofing",
  "industry": "Roofing Services",
  "location": "North Carolina",
  "revenue": 4200000,
  "sde": 850000,
  "ebitda": 700000,
  "add_backs": [
    "Owner salary above market",
    "Personal vehicle expenses"
  ],
  "customer_concentration": "Top 3 customers = 40%",
  "notes": "Owner heavily involved in sales"
}
