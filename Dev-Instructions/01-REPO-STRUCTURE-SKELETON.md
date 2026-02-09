You are an expert software engineer. Create a repository skeleton for a project named "insightforge-decisionlens".

Goal:
- Generate the exact folder structure and minimal skeleton files listed below.
- Provide ONLY:
  1) A bash script (Linux/Mac/Git Bash) that creates all folders and files.
  2) A PowerShell script (Windows) that creates all folders and files.
  3) The minimal contents for each file that needs content (README stubs, .env.example, networks.md, docs stubs, python __init__.py, common/db.py, scripts/init.sql).
- Do NOT include explanations. Do NOT include extra files. Do NOT add dependencies or code beyond minimal stubs.

Rules:
- Scripts must be idempotent (safe to re-run).
- Use UTF-8.
- Create empty placeholder file for powerbi/InsightForge_DecisionLens.pbix if it doesn’t exist (do not generate a real PBIX).
- Use LF line endings in bash output; PowerShell can use default.
- File contents must match exactly what I specify below.

Repository structure to create:

insightforge-decisionlens/
├── README.md
├── LICENSE
├── .gitignore
├── .env.example
├── docker/
│   ├── docker-compose.yml
│   └── networks.md
├── python/
│   ├── ingestion/
│   │   ├── __init__.py
│   │   └── README.md
│   ├── profiling/
│   │   ├── __init__.py
│   │   └── README.md
│   ├── forecasting/
│   │   ├── __init__.py
│   │   └── README.md
│   ├── common/
│   │   ├── __init__.py
│   │   └── db.py
│   └── requirements.txt
├── sql/
│   ├── raw/
│   │   └── README.md
│   ├── clean/
│   │   └── README.md
│   ├── dw/
│   │   └── README.md
│   ├── semantic/
│   │   └── README.md
│   ├── meta/
│   │   └── README.md
│   └── dq/
│       └── README.md
├── powerbi/
│   └── InsightForge_DecisionLens.pbix
├── ai/
│   ├── prompts/
│   │   └── README.md
│   ├── rules/
│   │   └── README.md
│   └── evaluation/
│       └── README.md
├── webapp/
│   ├── api/
│   │   └── README.md
│   └── ui/
│       └── README.md
├── worker/
│   └── README.md
├── docs/
│   ├── architecture.md
│   ├── lineage.md
│   ├── limitations.md
│   └── client-explainer.md
└── scripts/
    └── init.sql

Minimal file contents to write:

.env.example (exact):
# SQL
RW_SQL_HOST=
RO_SQL_HOST=
SQL_USER=
SQL_PASSWORD=

# API
DECISIONLENS_API_KEY=
GATEWAY_API_KEY=

# CONFIG
ENV=local

docker/networks.md (exact):
# Docker Network Isolation

- RW SQL is on a private network
- Only worker + ingestion containers can access RW
- RO SQL is accessible to Power BI and DecisionLens
- DecisionLens has no route to RW SQL

python/ingestion/README.md (exact):
Loads source data into raw schema (idempotent, append-safe).

python/profiling/README.md (exact):
Computes data-quality statistics stored in dq schema.

python/forecasting/README.md (exact):
Generates versioned forecasts for AI explanations.

sql/raw/README.md (exact):
Raw, untouched source tables.
No business logic.

sql/clean/README.md (exact):
Standardized, validated tables for analytics.

sql/dw/README.md (exact):
Star schema (facts + dimensions).

sql/semantic/README.md (exact):
Approved read-only business views.
Used by Power BI and DecisionLens.

ai/prompts/README.md (exact):
System and task prompts for DecisionLens.
No free-form SQL allowed.

ai/rules/README.md (exact):
Business guardrails, scope limits, explanation rules.

ai/evaluation/README.md (exact):
Golden questions and expected evidence.

worker/README.md (exact):
Background jobs:
- RW → RO sync
- anomaly detection
- executive summaries

docs/architecture.md (exact):
System architecture and C4 diagrams.

docs/lineage.md (exact):
Data lineage: raw → clean → dw → semantic → AI answers.

docs/limitations.md (exact):
Limitations & non-goals.

docs/client-explainer.md (exact):
Client one-pager explainer (PDF-ready).

scripts/init.sql (exact):
-- Bootstrap script placeholder

python/common/db.py (minimal stub):
- Provide a small placeholder with a function signature connect() and a comment “TODO: implement”.
- No real credentials.

README.md and LICENSE and .gitignore:
- Create as empty files (0 bytes) for now.

docker/docker-compose.yml and python/requirements.txt:
- Create as empty files (0 bytes) for now.

Output format:
1) Bash script in a single fenced code block labeled bash.
2) PowerShell script in a single fenced code block labeled powershell.
3) Then provide a list of file paths that were created (no prose).
