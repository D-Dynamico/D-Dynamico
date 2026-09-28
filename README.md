<div align="center">

# Hi, I'm Dayanand Kori (DJK) 👋

**Software engineer in the making, focused on backends and AI systems you can actually trust**

Final-year ECE @ LNMIIT · B.S. Data Science @ IIT Madras · Research Intern @ King's College London

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&pause=1200&color=4F46E5&center=true&vCenter=true&width=560&lines=Backend+%2B+ML+engineer;Healthcare+AI+and+data+privacy;Making+LLMs+stop+making+things+up" alt="typing intro" />

</div>

---

## About Me

I'm a final-year student at LNMIIT (B.Tech, Electronics and Communication) and I'm also completing a B.S. in Data Science and Applications at IIT Madras. My work sits between backend engineering and applied ML, and I care most about the part that usually gets skipped: making a system reliable once real users and real data show up.

That interest shows up in most of what I build. I like pairing LLMs with deterministic checks, so the model can propose but something auditable has to verify. I'm especially drawn to AI in healthcare, data privacy, and the hallucination problem in LLMs.

This summer I've been working with King's College London on a paediatric nephrology decision-support platform, which taught me a lot about building software where privacy rules and clinicians' time both matter.

Outside code, I'm part of LNMIIT's Debate Society. I've competed in MUNs and Asian Parliamentary debates, helped organise MUNs on campus, and served as Vice Chairperson of a UNESCO committee. It's why I'm comfortable explaining technical decisions to non-technical people.

- 🔭 Currently building NephroTICK at King's College London
- 📚 Researching multi-hop QA efficiency with RAG for my BTP
- 🌱 Exploring evaluation harnesses and verification layers for LLM systems
- 📍 Bengaluru, India

---

## Experience

### 🏥 Summer Research Intern, King's College London
*Summer 2026 · NephroTICK*

- Worked on NephroTICK, a paediatric nephrology decision-support platform built with clinicians, with NHS compliance requirements. It is still in development and not yet in trial deployment.
- The platform has a Flutter app for guardians and a React/Vite dashboard for clinicians, both served by a single FastAPI backend on PostgreSQL (SQLModel, Alembic).
- Built a two-tier, OTP-gated auth and role-based access layer so every query is scoped to the requesting clinician's own patients, with data handling designed around UK GDPR and Caldicott principles.
- Implemented a deterministic urine-dipstick analyser in OpenCV (reference card detection, affine rectification, Gray World colour normalisation, Delta-E matching) that reached 92.8% accuracy on a 28-sample validation set, with no trained model.
- Integrated a peer-built blood pressure centile classifier behind one service interface so both apps use a single scoring contract.
- Worked out requirements directly with clinicians and researchers, and spent a month in London with the team.

`Python` `FastAPI` `PostgreSQL` `Flutter` `React` `OpenCV`

### 💻 Front-End Developer Intern, Social Artist
*May 2025 to July 2025*

- Built the front end of the company website across 6+ pages, working directly with the client on scope.
- Cut first paint from 2.8 s to 1.3 s and lifted Lighthouse performance from 68 to 94 through asset tuning, responsive layouts, accessibility fixes, and semantic SEO.

---

## Featured Projects

### 🛡️ [Closo](https://github.com/D-Dynamico/Closo): self-verifying financial reconciliation agent
Built for Razorpay's AI Buildathon (Track 04: AI Finance Controller). It matches Razorpay payments, bank statements, and internal order ledgers, and explains the exceptions it can't match.

- A 3-stage cascade: a rule-based matcher first, then an LLM investigator, then an arithmetic verifier that re-checks every verdict against the raw records. The model never marks anything resolved on its own say-so.
- Resolved 150-record batches with a 95.7% match rate and 100% verified accuracy on unseen exceptions.
- All financial math goes through auditable, reproducible functions instead of LLM-generated numbers.
- Full audit log lets any past run be replayed byte for byte with no network access, plus a 5-screen Streamlit demo (live run, scorecard, drill-down, escalation queue, audit replay).

`Python` `Pandas` `Gemini API` `Streamlit`

### 🏥 [MediHelp](https://github.com/D-Dynamico/MediHelp): full-stack hospital platform
A production-deployed platform with admin, doctor, and patient roles, built with security and concurrency in mind.

- Auth uses short-lived in-memory access tokens plus rotating httpOnly refresh tokens, with theft and replay detection that revokes the whole token family on reuse.
- Authorization is enforced in depth: role checks, per-resource ownership checks, Zod validation on every request, and money and identity fields always re-derived on the server.
- A unique partial MongoDB index guarantees concurrent bookers resolve to exactly one appointment, so there is no double-booking.
- AI symptom triage: a deterministic rules engine with red-flag detection, plus an optional Claude-powered upgrade behind a hard timeout and automatic fallback.
- Live queue and token board over Socket.IO with ETAs from each doctor's rolling consult times, an auto-waitlist that re-offers cancelled slots, and Razorpay payments with idempotent, signature-verified webhooks.

`React` `Express` `MongoDB` `Socket.IO` `Redis` `Razorpay`

### 🕸️ [TraceAI](https://github.com/D-Dynamico/TraceAI): a knowledge graph for your career
Connects a student's certificates, skills, projects, and internships into one connected narrative, and traverses the graph to surface career paths. Deployed live. [Live demo](https://trace-ai-eta.vercel.app/)

- Three-layer knowledge graph with a deterministic hybrid search router that combines structured and semantic retrieval.
- SQLite is the source of truth and ChromaDB is a rebuildable cache, so the index can always be regenerated.
- ONNX MiniLM embeddings keep retrieval fast without a GPU, and the Gemini free tier handles categorisation, vision, and career-path inference within tight rate limits.
- Shipped with a plan spec, engineering notes, and an architecture diagram.

`FastAPI` `React` `ChromaDB` `SQLite` `Gemini API` `ONNX`

### 💬 [Vera](https://github.com/D-Dynamico/VeraAI): WhatsApp merchant engagement bot
An AI bot that talks to local merchants and their customers over WhatsApp, including natural Hindi-English (Hinglish).

- A fact-validation layer traces every number in an outgoing message back to source data, so fabricated figures are structurally impossible rather than just discouraged in a prompt.
- Conversation-state handling for auto-replies, hostile messages, and changes of intent.
- Falls back to deterministic templates whenever the LLM is slow or produces something unverifiable, which gave zero timeouts and zero hallucinated numbers in production.

`Python` `FastAPI` `Gemini API`

### ✉️ [AI Sales Agent](https://github.com/D-Dynamico/AI-Sales-Agent): autonomous B2B outreach
Enriches leads, drafts personalised cold emails, and sends them, with checks at every step. [Live demo](https://ai-sales-agent.streamlit.app)

- Pipeline: an enrichment agent (LangChain and Tavily) writes a research brief, an email drafter writes a sub-120-word email, and a sender handles delivery with rate limiting.
- Every factual claim in a draft is verified against retrieved evidence before sending. Unverifiable claims trigger a rewrite or go to human review.
- An evaluation harness over a golden lead set combines deterministic checks with an LLM judge to catch prompt regressions.
- Leads move through a state machine in SQLite (enriched, drafted, sent, replied or bounced) with webhooks feeding replies back in for follow-ups.

`Python` `LangChain` `OpenAI API` `Tavily` `SendGrid` `Streamlit`

### 🐳 [Ephemeral Environment Provisioner](https://github.com/D-Dynamico/ephemeral-env-provisioner)
A REST API that spins up isolated Docker stacks on demand, one per request, each with its own network and a TTL after which it is torn down. Built with per-PR preview environments in mind.

- Async provisioning through Celery and Redis, with a lifecycle state machine from pending to stopped and a terminal failed state.
- A Celery beat sweep enforces TTLs and claims rows before enqueueing, which prevents double teardown.
- Per-owner limits, unique active names, and clamped TTLs are enforced at the API layer.

`FastAPI` `SQLAlchemy` `Celery` `Redis` `PostgreSQL` `Docker`

### 📊 [FlowMetrics](https://github.com/D-Dynamico/FlowMetrics): logistics operations dashboard
Tracks SLA adherence, turnaround time, and throughput by zone across dispatch, transit, and delivery legs, then does root cause analysis on SLA misses by attributing each one to its bottleneck leg, zone, and delay reason.

`Python` `FastAPI` `pandas` `React`

### More
- **[Hospital Management System](https://github.com/23F3002468/Hospital_Management_System)**: Flask app with role-based dashboards and scheduled Celery reports.
- **CompactRAG replication** (BTP): reproduced a paper on cutting LLM calls and token overhead in multi-hop question answering, now working on extensions.

---

## Tech Stack

**Languages**

![Python](https://skillicons.dev/icons?i=python,js,c,cpp,dart&theme=light)

**Backend and Data**

![Backend](https://skillicons.dev/icons?i=fastapi,flask,express,nodejs,postgres,mongodb,sqlite,redis&theme=light)

**Frontend and Mobile**

![Frontend](https://skillicons.dev/icons?i=react,vue,flutter,html,css&theme=light)

**ML and Computer Vision**

![ML](https://skillicons.dev/icons?i=opencv,numpy&theme=light)

**Tools and Platforms**

<img src="https://skillicons.dev/icons?i=docker,git,github,linux,postman,firebase,powerbi&theme=light" height="48" alt="Tools" /> <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/vscode/vscode-original.svg" height="48" alt="VS Code" />

**AI tooling I work with daily:** Claude Code, plus the Gemini and OpenAI APIs, LangChain, and ChromaDB for RAG work.

---

## Contribution Snake

<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/D-Dynamico/D-Dynamico/output/github-snake-dark.svg" />
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/D-Dynamico/D-Dynamico/output/github-snake.svg" />
  <img alt="Contribution snake" src="https://raw.githubusercontent.com/D-Dynamico/D-Dynamico/output/github-snake.svg" />
</picture>

</div>

---

## 🚀 Looking for a Role

I'm looking for **internships and 2027 new-grad roles** in software engineering, backend, and applied AI, ideally on a team where correctness matters: fintech, healthtech, developer tools, or anywhere LLMs need guardrails to be useful.

**What I bring:** end-to-end ownership (I've been the main developer on a clinician-facing product), a habit of verifying model output instead of trusting it, and comfort working directly with non-technical users to figure out what to build.

**Open to:** on-site or remote roles.

## 📫 Reach Me

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/dayanand-kori-075413280/)
[![Email](https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:dayukori@gmail.com)
