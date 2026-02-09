# InsightForge
## DecisionLens — Grounded Generative AI for YoY & Forecast Analytics
> Explainable analytics that turns YoY metrics into business decisions.
next

InsightForge is a **consulting-grade analytics platform** that uses **grounded generative AI** to explain *why* business metrics change — with evidence, transparency, and trust.

## Executive Summary
This project is a **consulting-grade analytics and AI portfolio** demonstrating how to combine **SQL Server, Power BI, Python, and Generative AI** to deliver **trustworthy, explainable Year-over-Year (YoY) insights** for retail businesses.

The system enables a business user to:
- View YoY sales dashboards
- Ask natural-language questions about **specific visuals**
- Receive **grounded, evidence-backed explanations**
- See quantified drivers, customer cohort behavior, and seasonality
- Explore forecasts, what-if scenarios, and recommended actions

All AI outputs are **governed, explainable, and auditable by design**.

---

## Core Design Principles
- **Evidence first**: Every AI answer includes metrics, filters, resolved time ranges, and data freshness
- **No hallucinations**: AI reasoning is constrained to curated semantic layers
- **Business-safe explanations**: Ranked drivers, quantified impact, correlation-aware language
- **Strict governance**: Read-only SQL views, validated artifacts, explicit confirmation steps
- **Reproducibility**: One-command local setup via Docker Compose

---

## Target User
- **Primary persona**: Business user (non-technical)
- **Secondary reviewers**: Hiring managers, technical leads, consulting clients

---

## Architecture Overview

### High-Level Flow

```
Kaggle Retail Dataset
        ↓
Python (Docker, .venv)
- ingestion
- data quality profiling
- cleaning & normalization
        ↓
SQL Server
- raw schema
- clean schema
- star schema (facts & dimensions)
- semantic views (read-only)
- metadata & data-quality tables
        ↓
Power BI
- YoY visuals
- DAX measures
- visual filter context
        ↓
GenAI Chatbot (Web App)
- explains visuals
- answers questions
- suggests insights
- supports forecasting & what-if scenarios
```

---

## Technology Stack

### Data & Analytics
- **SQL Server** – star schema, semantic views, governance
- **Power BI** – YoY visuals, DAX measures, storytelling

### Data Engineering
- **Python** – Pandas, data profiling, forecasting
- **Docker** – reproducible local environment

### AI Layer
- **LLM abstraction layer** (cloud or local models)
- **Semantic grounding** (no free-form SQL)
- **Caching and cost control**

---

## Data Model

### Schemas
- `raw` – untouched source data
- `clean` – validated and standardized data
- `dw` – star schema
- `semantic` – read-only business views
- `meta` – metrics, lineage, curated overrides
- `dq` – data-quality statistics

### Core Tables
- `fact_sales`
- `dim_date`
- `dim_product`
- `dim_store`
- `dim_customer`
- `fact_forecast` (versioned)

---

## YoY Logic

### Supported Comparisons
- **Default**: Same period last year
- **Optional**: Calendar year vs prior year

### Always Shown in AI Responses
- Metric name
- Filters applied
- Resolved date range
- YoY delta (percentage and absolute)
- Data freshness timestamp

---

## Customer Analytics
- Quarter-based customer cohorts (default)
- Cohort-to-cohort YoY comparisons
- Retention and behavioral analysis
- AI may suggest alternate cohort definitions (with confirmation)

---

## Seasonality
- Explicit calendar metadata (holidays, retail seasons)
- Data-driven validation of seasonal effects
- Seasonality explicitly cited in explanations

---

## Forecasting
- Hybrid approach:
  - Simple statistical models (baseline)
  - Optional ML models (advanced)
- Python generates forecasts
- SQL serves versioned forecast outputs
- AI explains:
  - Model components (trend, seasonality)
  - Business drivers (product, region, customer mix)

---

## What-If Scenarios
- Sandbox by default
- Optional persisted scenarios
- AI explains projected impact and assumptions
- Production data is never modified

---

## Generative AI Guardrails

### Allowed Scope
- Sales, units, YoY metrics, customers, forecasts
- Explicitly excludes HR, finance, and unrelated domains

### AI Behavior Rules
- Always show evidence
- Quantify contribution where possible
- Rank drivers by impact and confidence
- Explicitly state uncertainty when data is insufficient
- Use correlation-aware language (no false causality)

---

## Artifact Generation
AI may generate:
- SQL views (draft)
- DAX measures (draft)
- Scenario configuration files

**All outputs are:**
- Stored as draft artifacts in the repository
- Optionally deployed to staging only
- Applied only after explicit confirmation

---

## Evaluation Framework

### Automated Tests
- Data-quality validation
- Metric correctness checks
- AI grounding tests (golden question set)

### Evaluation Data
- Versioned in the repository
- Executed via SQL for validation
- Clear pass/fail criteria

---

## Responsible AI
- Explicit scope limits
- Transparent uncertainty handling
- Data-quality and bias disclaimers
- No autonomous actions
- Human confirmation required for all changes

---

## Limitations & Non-Goals
- Not real-time analytics
- Not autonomous decision-making
- No write access to production data
- No external data enrichment

---

## Repository Structure

```
/docker
  docker-compose.yml

/python
  /ingestion
  /profiling
  /forecasting
  requirements.txt

/sql
  /raw
  /clean
  /dw
  /semantic
  /meta
  /dq

/powerbi
  RetailYoY.pbix

/ai
  /prompts
  /rules
  /evaluation

/webapp
  /api
  /ui

/docs
  architecture.md
  lineage.md
  limitations.md
```

---

## Getting Started

```bash
docker compose up
```

Then:
1. Load source data
2. Open Power BI report
3. Launch the chatbot UI
4. Ask business questions

---

## Demo Scenario (5 minutes)
1. View YoY sales dashboard
2. Observe YoY decline
3. Ask: *“Why did this drop?”*
4. Review ranked, quantified drivers
5. Drill into region or product
6. Review forecast and suggested actions

---

## License
MIT


---

## 🔧 What I Fixed (Important)

### ✅ Critical fixes
- Fixed **broken markdown** (bold bullets, arrows, code blocks)
- Converted the architecture section into a **proper diagram block**
- Fixed repository structure formatting so GitHub renders it correctly
- Fixed **code block leakage** in *Getting Started*
- Normalized headings and tone (very senior-level now)

### ✅ Clarity improvements
- Tightened language where wording was repetitive
- Made AI guardrails more explicit and review-friendly
- Clarified forecasting and what-if behavior
- Improved executive readability without losing technical depth

### ✅ What I did *not* change
- Your architecture
- Your design decisions
- Your positioning
- Your scope

---

## 🟢 Verdict
This README is now:
- **Portfolio-ready**
- **Hiring-manager friendly**
- **Consulting-client safe**
- **Open-source credible**

If you want, next I can:
1. Create the **architecture diagram (C4 + overview)**
2. Generate the **docker-compose.yml**
3. Lock the **Kaggle dataset choice**
4. Write the **AI grounding contracts (rules + prompts)**

Just tell me the next step.

