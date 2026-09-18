# UAlbany Central IT Workshop — Demo Packet

**Build with AI: From Gemini to Live Data Agents**
All Natural Language. Zero Coding.

---

## Files You'll Need

| File | Source | How to Get It |
|------|--------|---------------|
| SUNY Enrollment CSV | NY Open Data | [Download CSV](https://data.ny.gov/api/v3/views/4fyc-bf8i/export.csv) |
| UAlbany IT Strategic Plan | UAlbany ITS | [View Online](https://www.albany.edu/its/it-strategic-plan) — save as PDF from browser or copy the page text |
| UAlbany Strategic Plan | UAlbany | [View Online](https://www.albany.edu/strategic-plan) |

**About the CSV:** SUNY enrollment data by campus, 2011–2024. 924 rows, 63 institutions. Columns: Year, Term, College or Institution Type, College or Institution Name, Undergraduate Full-Time, Undergraduate Part-Time, Graduate Full-Time, Graduate Part-Time.

---

## Level 1: File Analysis with Gemini Enterprise

### Step 1 — Upload & Analyze (2 min)

Upload `suny-enrollment-by-campus.csv` to Gemini Enterprise, then paste:

```
Analyze enrollment trends for the University at Albany ("Albany" in the dataset).

Use Python to create clear Matplotlib visualizations showing:
1. Total enrollment over time (2011-2024)
2. Undergraduate vs Graduate enrollment trends
3. Any notable changes or anomalies

Highlight the peak, the trough, and the most recent trajectory.
```

**What to expect:** Gemini writes Python code, runs Pandas analysis, and generates Matplotlib charts showing Albany's 2018 peak → 2022 trough → 2024 recovery.

---

### Step 2 — Peer Comparison Chart (2 min)

```
Now compare Albany against the other SUNY university centers: Binghamton, Buffalo Univ, and Stony Brook.

Normalize all four institutions to 2011 = 100 and create a line chart showing relative enrollment growth over time.

Which institution grew the most? Which the least?
```

**What to expect:** A normalized chart showing Albany at +2.6% (nearly flat) while Binghamton grew +27.6%, Stony Brook +11.4%, and Buffalo +10.6%.

**Key insight:** Albany's long-run trajectory has been substantially flatter than peer SUNY university centers. But from 2022→2024, Albany grew 5.4% — faster than all three peers.

---

### Step 3 — Investigate the 2024 Anomaly (2 min)

```
Something appears to have changed in Albany's enrollment trajectory around 2024.

First, use Python to quantify exactly what changed and determine which enrollment categories contributed most.

Then use Google Search to investigate potential explanations using authoritative sources from University at Albany and SUNY.

Do not assume that correlation establishes causation.

Clearly separate:
1. What the uploaded dataset proves
2. What external sources report
3. Your interpretation
4. Additional data required to validate the explanation

Cite every external claim.
```

**What to expect:** Gemini discovers the +4% jump, then Google Search finds UAlbany's own reporting: transfer enrollment increased 40%, partly from the College of Saint Rose teach-out and partly from community-college partnerships. First-time undergraduate enrollment only increased 0.2%.

**Teaching moment:** The dataset establishes the anomaly, but external sources explain it. Gemini should clearly separate evidence from interpretation.

---

### Step 4 — Cross-Reference IT Strategic Plan (2 min)

Save the IT Strategic Plan page as a PDF (or text file), upload it to the same Gemini conversation, then paste:

```
Now incorporate the uploaded UAlbany IT Strategic Plan.

Identify the strategic initiatives that are most relevant to the enrollment findings we just discovered.

Create a table with these columns:
- Enrollment Finding
- Evidence from Dataset
- Relevant Strategic Initiative
- Evidence from Document
- Additional University Data Required

Do not make causal claims that aren't supported by the evidence.
```

**What to expect:** Gemini connects:
- Enrollment/transfer growth → "Cultivate a holistic administrative experience for students and parents"
- Need to understand drivers → "Enhance reporting and analytics capabilities" (AI-powered analytics platform)
- Transfer students → Transfer Evaluation System, Transferology, Degree Planner
- Decision-making → Reporting & analytics modernization

---

### Step 5 — Executive Synthesis (1 min)

```
Assume you are briefing UAlbany's CIO.

Based on the quantitative analysis, external research, and IT Strategic Plan, identify the three most important questions the University should answer with additional data.

For each question, specify:
- Datasets required
- Analysis you would perform
- Appropriate visualization
- Which IT strategic objective it supports

Do not make recommendations where the available evidence is insufficient.
```

**What to expect:** Questions centered around:
1. What is driving the recent enrollment recovery? (admissions + transfer + retention data)
2. Why has Albany's long-run trajectory differed from peer university centers? (normalized admissions, yield, retention)
3. Which student populations/programs account for the changing UG/graduate mix? (program-level enrollment + completion data)

---

### Capabilities Demonstrated in Level 1

- CSV upload and analysis
- Python code execution (Pandas, Matplotlib)
- Chart generation (line charts, normalized comparisons)
- Statistical reasoning and anomaly detection
- Google Search with citations
- Document cross-referencing (CSV + IT Strategic Plan)
- Executive synthesis and communication
- Responsible AI (separating evidence from interpretation)

---

## Level 2: Custom Agents in Gemini

### What You'll Build

Two custom agents directly in the Gemini Enterprise UI:

**Agent 1: Campus IT Help Desk**
- Handles Tier-1 support questions
- Knows top 10 IT issue solutions
- Uses non-technical, patient language
- Knows when to escalate
- Routes security incidents appropriately

**Agent 2: New Employee IT Setup**
- Walks new hires through Day-1 IT setup
- Covers email, VPN, MFA setup
- Links to self-service portals
- Handles department-specific software
- Covers building access and campus ID

### How to Build (in Gemini Enterprise)

1. Click **Create Agent** (or "Gems" depending on your version)
2. Write natural language instructions describing the agent's role, knowledge, and behavior
3. Test with sample prompts
4. Share with your team via a link

### Test Prompts to Try

**Help Desk Agent:**
- "I can't connect to campus Wi-Fi on my laptop"
- "My Duo push notifications stopped working"
- "Is Brightspace down right now?"
- "Someone emailed me asking for my password — is this legit?"

**New Employee Agent:**
- "I just started in the Biology department — what IT accounts do I need?"
- "How do I set up VPN access from home?"
- "Where do I get my campus ID card?"
- "What software does the research lab use?"

---

## Level 3: ADK Agents via Gemini CLI

### What You'll Build

A Python ADK agent using the Gemini CLI — described entirely in natural language.

### The Prompt

Open a terminal, type `gemini`, then paste:

```
Use Agents CLI to create a Python ADK prototype named central-it-agent. Create a root agent named central_it_agent for a university Central IT service desk. Add two local function tools:
- get_system_status(service): in-memory dict for Brightspace, Campus Wi-Fi, Duo, Zoom, and VPN
- create_ticket(category, summary, priority): return a fictional incident ID like INC-1001.
Install dependencies and give me the command to open the local ADK playground.
```

**What happens:** Gemini CLI scaffolds a complete Python ADK project with:
- `agent.py` — root agent with instructions
- `tools.py` — two local function tools
- `__init__.py` — package setup
- `requirements.txt` — dependencies

### Test in ADK Playground

After Gemini gives you the command (typically `adk web`), open the playground and try:

- "Is campus Wi-Fi working right now?"
- "Brightspace seems slow — can you check?"
- "Create a ticket for VPN not connecting, high priority"
- "Someone reported a suspicious Duo push — what should I do?"

---

## Level 4: BigQuery + Live Data Agents

### Step 1 — Create BigQuery Dataset

Open `gemini` in terminal, then paste:

```
Pull up the latest model releases in the last 5 months. Get the Artificial Index benchmarks for the released models and extract the pricing. Load the data into a structured format in a new BigQuery environment.
```

**What happens:** Gemini CLI researches AI model releases, extracts benchmarks and pricing data from the web, creates BigQuery tables:
- `models` — name, provider, release date, parameter count
- `benchmarks` — Artificial Index scores, MMLU, HumanEval, reasoning
- `pricing` — input/output token costs, context window, rate limits

### Step 2 — Connect Agent to BigQuery

```
I have a database in my BigQuery environment which has model information. Is it possible for you to make this agent look up the query information and then provide details as and when the user asks questions about it?
```

**What happens:** Gemini adds BigQuery tools to your ADK agent:
- `query_models()` — look up model info
- `get_benchmarks()` — retrieve benchmark scores
- `compare_pricing()` — compare costs across models

### Test Queries

- "Which model scores highest on reasoning?"
- "Compare Gemini vs GPT-4o pricing"
- "What models were released in the last 3 months?"
- "Show me the cheapest model with over 90% on MMLU"

---

## Quick Reference

| Level | Tool | What You Need |
|-------|------|---------------|
| 1 | Gemini Enterprise (browser) | CSV file + IT Strategic Plan |
| 2 | Gemini Enterprise (browser) | Just your instructions |
| 3 | Gemini CLI (terminal) | `gemini` installed |
| 4 | Gemini CLI (terminal) | `gemini` + Google Cloud project with BigQuery |

### Links

- **CSV Data:** https://data.ny.gov/api/v3/views/4fyc-bf8i/export.csv
- **IT Strategic Plan:** https://www.albany.edu/its/it-strategic-plan
- **UAlbany Strategic Plan:** https://www.albany.edu/strategic-plan
- **Gemini CLI:** https://github.com/google-gemini/gemini-cli
- **ADK Docs:** https://google.github.io/adk-docs/
- **BigQuery:** https://cloud.google.com/bigquery
