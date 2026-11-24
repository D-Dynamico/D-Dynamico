<div align="center">

# Hi, I'm Dayanand Kori (DJK) 👋

**Backend · Applied AI · Healthcare tech**

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&pause=1200&color=4F46E5&center=true&vCenter=true&width=560&lines=Backend+%2B+applied+AI+engineer;Building+AI+you+can+actually+trust;Making+LLMs+stop+making+things+up" alt="Typing intro" />

</div>

---

## 🧑‍💻 About Me

I'm a final-year B.Tech student in Electronics and Communication at LNMIIT, and I'm also finishing a B.S. in Data Science and Applications at IIT Madras. My work sits between backend engineering and applied ML, and I care most about the part that usually gets skipped: making a system reliable once real users and real data show up.

Most of what I build pairs LLMs with deterministic checks, so the model can propose but something auditable has to verify. I'm especially drawn to AI in healthcare, data privacy, and the hallucination problem.

Outside code, I'm part of LNMIIT's Debate Society. I've competed in MUNs and Asian Parliamentary debates, helped organise MUNs on campus, and served as Vice Chairperson of a UNESCO committee. It's why I'm comfortable explaining technical decisions to non-technical people.

```python
class DJK:
    name      = "Dayanand Kori"
    based_in  = "Bengaluru, India"
    studying  = ["B.Tech ECE @ LNMIIT", "B.S. Data Science @ IIT Madras"]
    builds    = ["backends", "applied AI", "healthcare tech"]
    motto     = "Let the model propose. Let something auditable verify."
```

- 📚 Researching multi-hop QA efficiency with RAG for my BTP
- 🌱 Exploring evaluation harnesses and verification layers for LLM systems
- 💬 Ask me about LLM guardrails, healthcare software, or debating

---

## 💼 Experience

### 🏥 Research Intern · King's College London
*Summer 2026 · NephroTICK*

- Worked on NephroTICK, a paediatric nephrology decision-support platform built with clinicians, with NHS compliance requirements. It is still in development and not yet in trial deployment.
- The platform has a Flutter app for guardians and a React/Vite dashboard for clinicians, both served by a single FastAPI backend on PostgreSQL (SQLModel, Alembic).
- Built a two-tier, OTP-gated auth and role-based access layer so every query is scoped to the requesting clinician's own patients, with data handling designed around UK GDPR and Caldicott principles.
- Implemented a deterministic urine-dipstick analyser in OpenCV (reference card detection, affine rectification, Gray World colour normalisation, Delta-E matching) that reached 92.8% accuracy on a 28-sample validation set, with no trained model.
- Integrated a peer-built blood pressure centile classifier behind one service interface so both apps use a single scoring contract.
- Worked out requirements directly with clinicians and researchers, including time with the team in London.

`Python` `FastAPI` `PostgreSQL` `Flutter` `React` `OpenCV`

### 💻 Front-End Developer Intern · Social Artist
*May 2025 to July 2025*

- Built the front end of Social Artist's company website across 6+ pages.
- Cut first paint from 2.8 s to 1.3 s and lifted Lighthouse performance from 68 to 94 through asset tuning, responsive layouts, accessibility fixes, and semantic SEO.

---

## 🛠️ Featured Projects

> Click **How it works** under any project for the details.

### 🛡️ [Closo](https://github.com/D-Dynamico/Closo) · self-verifying financial reconciliation agent
Matches Razorpay payments, bank statements, and order ledgers, and explains what it can't match. **95.7% match rate, 100% verified accuracy** on unseen exceptions. Built for Razorpay's AI Buildathon.

`Python` `Pandas` `Gemini API` `Streamlit`

<details>
<summary><b>How it works</b></summary>
<br/>

- A 3-stage cascade: a rule-based matcher, then an LLM investigator, then an arithmetic verifier that re-checks every verdict against the raw records. The model never marks anything resolved on its own say-so.
- All financial math goes through auditable, reproducible functions instead of LLM-generated numbers.
- A full audit log lets any past run be replayed byte for byte with no network access, shown in a 5-screen Streamlit demo (live run, scorecard, drill-down, escalation queue, audit replay).

</details>

### 🏥 [MediHelp](https://github.com/D-Dynamico/MediHelp) · full-stack hospital platform
A production-deployed platform for admins, doctors, and patients, with token-theft detection, race-proof booking, live queues, and AI triage that falls back safely.

`React` `Express` `MongoDB` `Socket.IO` `Redis` `Razorpay`

<details>
<summary><b>How it works</b></summary>
<br/>

- Short-lived in-memory access tokens plus rotating httpOnly refresh tokens, with replay detection that revokes the whole token family on reuse.
- Authorization in depth: role checks, per-resource ownership checks, Zod validation on every request, and money and identity fields always re-derived on the server.
- A unique partial MongoDB index guarantees concurrent bookers resolve to exactly one appointment.
- Symptom triage runs a deterministic rules engine with red-flag detection, plus an optional Claude-powered upgrade behind a hard timeout and automatic fallback.
- Socket.IO queue board with ETAs from each doctor's rolling consult times, an auto-waitlist that re-offers cancelled slots, and idempotent, signature-verified Razorpay webhooks.

</details>

### 🕸️ [TraceAI](https://github.com/D-Dynamico/TraceAI) · a knowledge graph for your career
Turns a student's scattered certificates, projects, and internships into one connected graph, then walks it to suggest career paths. [**Live demo →**](https://trace-ai-eta.vercel.app/)

`FastAPI` `React` `ChromaDB` `SQLite` `Gemini API` `ONNX`

<details>
<summary><b>How it works</b></summary>
<br/>

- Three-layer knowledge graph with a deterministic hybrid search router that combines structured and semantic retrieval.
- SQLite is the source of truth and ChromaDB is a rebuildable cache, so the index can always be regenerated.
- ONNX MiniLM embeddings keep retrieval fast without a GPU, and Gemini handles categorisation, vision, and career-path inference within tight free-tier limits.

</details>

### 💬 [Vera](https://github.com/D-Dynamico/VeraAI) · WhatsApp merchant engagement bot
Chats with local merchants and their customers in English and Hinglish, with **zero hallucinated numbers** because every figure is traced back to source data.

`Python` `FastAPI` `Gemini API`

<details>
<summary><b>How it works</b></summary>
<br/>

- A fact-validation layer traces every number in an outgoing message back to real data, so fabrication is structurally impossible rather than just discouraged in a prompt.
- Conversation-state handling for auto-replies, hostile messages, and changes of intent.
- Falls back to deterministic templates whenever the LLM is slow or unverifiable, for zero timeouts in production.

</details>

### ✉️ [AI Sales Agent](https://github.com/D-Dynamico/AI-Sales-Agent) · autonomous B2B outreach
Researches leads, drafts personalised cold emails, and fact-checks every claim before anything is sent. [**Live demo →**](https://ai-sales-agent.streamlit.app)

`Python` `LangChain` `OpenAI API` `Tavily` `SendGrid` `Streamlit`

<details>
<summary><b>How it works</b></summary>
<br/>

- An enrichment agent (LangChain and Tavily) writes a research brief, a drafter writes a sub-120-word email, and a sender delivers it with rate limiting.
- Unverifiable claims trigger a rewrite or go to human review.
- An evaluation harness over a golden lead set combines deterministic checks with an LLM judge to catch prompt regressions.
- Leads move through a SQLite state machine, with webhooks feeding replies and bounces back in for follow-ups.

</details>

### 🐳 [Ephemeral Environment Provisioner](https://github.com/D-Dynamico/ephemeral-env-provisioner) · preview environments on demand
A REST API that spins up an isolated Docker stack per request, each with its own network and an expiry timer that tears it down.

`FastAPI` `SQLAlchemy` `Celery` `Redis` `PostgreSQL` `Docker`

<details>
<summary><b>How it works</b></summary>
<br/>

- Async provisioning through Celery and Redis, with a lifecycle state machine from pending to stopped and a terminal failed state.
- A Celery beat sweep enforces expiry and claims rows before enqueueing, which prevents double teardown.
- Per-owner limits, unique active names, and clamped lifetimes are enforced at the API layer.

</details>

### 📊 [FlowMetrics](https://github.com/D-Dynamico/FlowMetrics) · logistics operations dashboard
Tracks SLA adherence and throughput across dispatch, transit, and delivery, then pins each SLA miss on its bottleneck leg, zone, and delay reason.

`Python` `FastAPI` `pandas` `React`

<details>
<summary><b>More projects</b></summary>
<br/>

- **[Hospital Management System](https://github.com/23F3002468/Hospital_Management_System)**: Flask app with role-based dashboards and scheduled Celery reports.
- **CompactRAG replication** (BTP): reproduced a paper on cutting LLM calls and token overhead in multi-hop question answering, now working on extensions.

</details>

---

## 🧰 Tech Stack

<div align="center">

**Languages**<br/>
<img src="https://skillicons.dev/icons?i=python,js,c,cpp,dart&theme=light" alt="Languages" />

**Backend and Data**<br/>
<img src="https://skillicons.dev/icons?i=fastapi,flask,express,nodejs,postgres,mongodb,sqlite,redis&theme=light" alt="Backend and data" />

**Frontend and Mobile**<br/>
<img src="https://skillicons.dev/icons?i=react,vue,flutter,html,css&theme=light" alt="Frontend and mobile" />

**ML, CV and Tools**<br/>
<img src="https://skillicons.dev/icons?i=opencv,numpy,docker,git,github,linux,postman,firebase&theme=light" alt="ML and tools" />
<img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/vscode/vscode-original.svg" height="48" alt="VS Code" />

<sub>Also: Excel / Google Sheets · AI tooling I use daily: Claude Code, Gemini and OpenAI APIs, LangChain, ChromaDB</sub>

</div>

---

## 🐍 Contribution Snake

<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/D-Dynamico/D-Dynamico/output/github-snake-dark.svg" />
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/D-Dynamico/D-Dynamico/output/github-snake.svg" />
  <img alt="Contribution snake" src="https://raw.githubusercontent.com/D-Dynamico/D-Dynamico/output/github-snake.svg" />
</picture>

</div>

---

## 🎯 Looking for a Role

I graduate in **May 2027** and I'm looking for **full-time new-grad roles** in software engineering, backend, and applied AI, ideally on a team where correctness matters: fintech, healthtech, developer tools, or anywhere LLMs need guardrails to be useful.

**What I bring:** end-to-end ownership (I was the main developer on a clinician-facing product), a habit of verifying model output instead of trusting it, and comfort working directly with non-technical users to figure out what to build.

<div align="center">

**Let's talk 👇**

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/dayanand-kori-075413280/)
[![Email](https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:dayukori@gmail.com)

</div>
