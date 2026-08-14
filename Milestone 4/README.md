# Agentic AI for Maritime Freight Pricing and Route Optimization — Milestone 4

**Infosys Springboard Internship — Batch 1**


An AI-powered ocean freight intelligence platform built with **Streamlit**, **FastAPI**, and a locally-hosted **Qwen LLM** backend. The platform brings together route optimization, dynamic pricing, carrier analytics, weather risk, customs guidance, document automation, multilingual translation, PDF-based RAG, anomaly detection, and a digital twin simulation — all backed by a seeded SQLite database and role-based access control.


---

## 📌 Milestone 4 Scope

- [x] Final integration of all AI agents into a single Streamlit application
- [x] AI Copilot with grounded Q&A over the live database
- [x] Role-Based Access Control (Admin, Ops Manager, Dispatcher, Customer/Client)
- [x] Local LLM microservice (Qwen2.5-3B-Instruct, 4-bit) with automatic 1.5B fallback
- [x] Multilingual translation engine (NLLB-200, 20+ languages)
- [x] PDF/document RAG studio (FAISS + sentence-transformers) for customs & SOP documents
- [x] Anomaly detection, digital twin simulation, and knowledge graph visualization
- [x] End-to-end deployment via Streamlit + ngrok/Cloudflare Tunnel

---

## 1. Project Overview

FreightQuote AI is an agentic decision-support platform for an ocean-freight brokerage. It monitors global ports, calculates dynamic freight quotes, benchmarks carriers, tracks weather and customs risk, and exposes an LLM-powered copilot that answers routing, pricing, weather, and compliance questions using only **grounded database facts, live telemetry, and retrieved documents — never fabricated numbers**.

The platform mirrors FranchiseOps AI's architecture: nine specialised agents plus a shared platform layer (authentication, RBAC, translation, alerting, admin tooling), all running inside a single Streamlit application launched from Google Colab.

### 1.1 Design Principles

- **Grounded generation** — the LLM only answers from retrieved SQL facts, computed solver output (routes, quotes), or RAG-retrieved documents.
- **Transparent ML** — every predictive agent benchmarks several classical algorithms side-by-side and shows its work.
- **Role-aware** — every tab is gated by RBAC so an Ops Manager and an Admin see a different, appropriately-scoped menu.
- **Fail-soft** — if the 3B LLM can't load, the app automatically degrades to a 1.5B model rather than crashing.

---

## 2. Technology Stack

| Layer | Technology | Purpose |
|---|---|---|
| Frontend / UI | Streamlit + streamlit-option-menu | Multi-tab dashboard, sidebar navigation, chat UI |
| Tunnelling | ngrok / Cloudflare Tunnel | Exposes the Colab-hosted Streamlit app on a public URL |
| Backend language | Python 3 / FastAPI | All application, ML, and agent logic |
| Database | SQLite (via `db.py`, WAL mode + connection pooling, 64MB page cache) | Ports, shipments, carriers, freight_quotes, customs data, weather risk, and shared ops tables |
| LLM | Qwen2.5-3B-Instruct (4-bit, `transformers` + `bitsandbytes`) | Local, in-process natural-language reasoning over grounded facts |
| Fallback LLM | Qwen2.5-1.5B-Instruct | Automatic degrade path if the 3B model can't load |
| Translation | Facebook NLLB-200 (distilled-600M) | Offline translation of copilot answers & shipping documents (20+ languages) |
| RAG / Vector Search | FAISS + sentence-transformers + LangChain text splitters | Retrieval over uploaded customs manuals, carrier SOPs, contracts |
| Live weather | Open-Meteo REST API via `weather_context.py` | Real current-weather pull per port coordinate, feeding the weather risk agent |
| ML models (classical) | scikit-learn — RandomForest, GradientBoosting, DecisionTree, Logistic/Linear Regression, SVC/SVR, Isolation Forest | Per-agent prediction and anomaly detection |
| Visualization | Plotly Express / Plotly Graph Objects, Folium + streamlit-folium | All interactive charts, port network maps, and storm severity maps |
| Auth | PyJWT, bcrypt | OTP-based login, security questions, password hashing, RBAC |
| Reporting / Docs | ReportLab / FPDF | PDF Bill of Lading and quote document generation |
| Data | Kaggle / Faker | Realistic shipment, carrier, and port records for seeding |

---

## 3. System Architecture

Same four-layer agentic pattern as FranchiseOps AI, adapted to the maritime domain:

1. **Data Layer** — `seed_data.py` populates SQLite with ports, shipments, carriers, routes, freight quotes, customs requirements, and weather-risk snapshots.
2. **Reasoning Tools Layer** — nine agent modules covering routes, pricing, carriers, weather, margin, customs, documents, translation, and PDF RAG, each pairing SQL analytics with a multi-model ML benchmark and Plotly visuals.
3. **Orchestration Layer** — `intent_router.py` classifies a query into shipment / pricing / weather / customs, and includes a Haversine-distance route solver and a from-scratch freight-quote calculator (base rate × weight + BAF fuel surcharge + customs/terminal handling fee) for questions that need computed answers rather than a canned row lookup.
4. **Generation Layer** — `llm_engine.py` loads Qwen2.5-3B-Instruct in-process and generates the final grounded answer from the retrieved facts.

### 3.1 AI Copilot Answer Pipeline

1. `classify_intent()` maps the question to shipment / pricing / weather / customs / carrier domains.
2. `run_grounded_query()` pulls exact rows/aggregates from SQLite, or runs the dedicated route-distance / freight-quote solver for computed questions.
3. If no SQL tool matches, `execute_tool()` falls back to `rag_engine.answer_with_citation()` over the FAISS-indexed document store (customs manuals, carrier SOPs).
4. `generate_grounded_answer()` passes the retrieved facts into Qwen2.5-3B-Instruct with an explicit instruction to answer only from the provided context, in plain business language — never as SQL/Python code — then optionally translates via NLLB-200.

A sidebar status panel — **"🤖 Neural AI Model & GPU Status"** — shows live loading state for both the Qwen and NLLB engines (🟢 Active / 🟡 Loading).

---

## 4. Agent-by-Agent Reference

Menu order in the app runs sequentially: **AI Copilot → Agents 1-9 → Notifications → Knowledge Graph → Digital Twin → Anomaly Scanner → Data Feed Center → Admin Dashboard → Sign Out.** A previously-duplicate "Alerts & Incidents" tab was consolidated into Notifications.

### Agent 1 — Global Ocean Port & Route Intelligence
Telemetry and routing across monitored global and Indian ports.
- 🗺 Live interactive port network map (Folium) — ports colored green/orange/red by congestion, sized by active vessel count
- Dynamic route optimizer for any global port pair (Haversine great-circle distance + sailing-time estimate)
- Route/port risk classification bench
- AI Route Advisor for grounded routing recommendations

**ML models benchmarked:** RandomForest, GradientBoosting, DecisionTree, LogisticRegression, SVC
**Charts used:** Folium map, Bar, Scatter
**How to read it:** On the port map, marker colour encodes congestion severity — darker/red markers mean higher congestion and longer expected dwell time; hover for the exact congestion index.

### Agent 2 — Dynamic Freight Pricing & Rate Calculator
Calculates and benchmarks ocean freight quotes.
- From-to freight rate & cost calculator (base ocean rate + fuel surcharge + customs/terminal fee)
- Multi-model freight-pricing regression benchmark
- 🔬 Advanced Analytics tab: waterfall cost build-up (base → fuel → fees → final price), correlation heatmap, quote-value funnel by pipeline status
- AI Pricing Advisor

**ML models benchmarked:** RandomForestRegressor, GradientBoostingRegressor, DecisionTreeRegressor, LinearRegression
**Charts used:** Waterfall, Heatmap, Funnel, Bar
**How to read it:** The waterfall starts at base cost and adds each fee as a floating bar, ending at the final price — it shows exactly which line item is driving the total up.

### Agent 3 — Carrier Performance & Safety Audit
Benchmarks shipping carriers on safety, reliability, and fleet capacity.
- Carrier reliability radar and 8-parameter capacity simulator
- Multi-model carrier-reliability classification benchmark
- 🔬 Advanced Analytics tab: treemap of fleet by risk level (colored by rating), rating-vs-OTD scatter, correlation heatmap
- AI Carrier Advisor

**ML models benchmarked:** RandomForestClassifier, GradientBoostingClassifier, DecisionTreeClassifier, LogisticRegression, SVC
**Charts used:** Treemap, Scatter, Heatmap
**How to read it:** In the treemap, a large box in the "High Risk" branch that's also red-toned (low rating) is a contract to review first. Top-right of the scatter (high rating, high on-time %) are your most dependable carriers.

### Agent 4 — Global Weather Risk & Harbor Safety Intelligence
Monitors severe-weather risk at monitored ports using live Open-Meteo data.
- 🗺 Live storm-severity port map (Folium) — colour-coded from green (normal) to dark red (severe/cyclone)
- Wind speed vs wave height harbor-safety threshold scatter
- Multi-model weather-risk predictor
- AI Weather Advisor

**ML models benchmarked:** RandomForest, GradientBoosting, DecisionTree, LogisticRegression, SVC, LinearRegression
**Charts used:** Folium map, Bar, Scatter
**How to read it:** On the wind-speed vs wave-height scatter, points beyond the safety threshold represent ports where vessels should hold anchorage or reroute.

### Agent 5 — Freight Margin Optimizer & Profitability Intelligence
Analyses where margin is earned or lost across quotes.
- 10-parameter rate simulator and carrier yield matrix
- Multi-model freight-margin regression benchmark
- 🔬 Advanced Analytics tab: margin % box plot by carrier, cost-component correlation heatmap, margin distribution histogram
- AI Margin Advisor

**ML models benchmarked:** RandomForestRegressor, GradientBoostingRegressor, DecisionTreeRegressor, LinearRegression
**Charts used:** Box plot, Heatmap, Histogram
**How to read it:** A carrier with a low median and points below the box on the margin chart represents recurring low-margin deals worth renegotiating; a strong negative correlation between fuel surcharge and margin flags fuel volatility as your biggest margin risk.

### Agent 6 — Customs Intelligence & HS Code Compliance
Assesses regulatory clearance risk by country and cargo type.
- 8-parameter customs duty simulator and regulatory document matrix
- Multi-model regulatory clearance-risk benchmark
- 🔬 Advanced Analytics tab: sunburst of duty exposure by origin country & cargo (colored by clearance risk), duty-vs-risk scatter
- AI Customs Advisor

**ML models benchmarked:** RandomForestClassifier, GradientBoostingClassifier, DecisionTreeClassifier, LogisticRegression, SVC
**Charts used:** Sunburst, Scatter
**How to read it:** Inner ring = origin country, outer ring = cargo type; red-toned wedges need documents pre-staged well before arrival. Top-right of the scatter (high duty, high risk) are the lanes most likely to face delays.

### Agent 7 — Quote Document & Bill of Lading Generator (OCR)
Produces shipping paperwork from live quote data.
- Auto-generated freight quote PDF
- Bill of Lading document generator

### Agent 8 — Freight Document & Policy Translation Engine
Offline translation of freight documents and policies, brought to feature parity with the franchise project's translation agent.
- 📝 Real-time text translation and 📄 maritime document SOP translator
- 🔁 Batch translation of multiple SOPs at once
- 📚 Maritime trade glossary — BAF, TEU, HS Code, dwell time, etc.
- 🌐 Supported languages roster

### Agent 9 — Custom PDF Knowledge Base & Vector RAG Engine
Upload-your-own-document RAG workbench for customs manuals and carrier contracts.
- Upload PDFs for automatic chunking + FAISS indexing
- Natural-language Q&A grounded in the uploaded documents

### Notifications — Unified Real-Time Incident & Alert Center
The single alerts/incidents surface (a previously-duplicate "Agent 8: Alerts & Incidents" tab was consolidated into this one, since both read/wrote the same alerts table).
- Live incident feed with severity for shipment delays, weather holds, and customs issues
- One-click incident resolution

**Charts used:** Pie (severity breakdown)

---

## 5. Shared Platform Layer

### 5.1 Role-Based Access Control (RBAC)

| Role | Typical Access |
|---|---|
| Admin | All tabs, including the Admin Dashboard and full agent suite |
| Freight Broker / Regional Ops Manager | All agents and the AI Copilot, excluding the Admin Dashboard |
| Dispatcher | AI Copilot + a subset of operational agents |
| Customer / Client | AI Copilot plus quote-related agents only |

Authentication uses email + OTP (JWT-based) with security questions and an account lockout/cooldown policy after repeated failed attempts, handled in `auth.py`.

### 5.2 Admin Dashboard
- User management and role assignment
- System health (DB status, LLM/translation engine status)
- ML model performance ledger (accuracy/F1/R² per agent, logged to the `ml_metrics` table)
- Chat history and audit trail across users

### 5.3 Cross-Cutting Tools
- 🕸 **Knowledge Graph** — entity relationships (port ↔ route ↔ carrier)
- ⚡ **Digital Twin** — whole-network simulation
- 🚨 **Anomaly Scanner** — network-wide outlier detection
- 📡 **Data Feed Center** — raw operational data export/review

---

## 6. How to Interpret Every Chart Type Used

| Chart Type | What It Shows | How To Read It |
|---|---|---|
| Bar chart | Compares a metric across discrete categories | Taller bar = higher value. In model-comparison charts, the tallest bar is the best-performing algorithm. |
| Scatter plot | Relationship between two numeric variables | Diagonal pattern = correlation; points far from the main cloud are outliers worth investigating. |
| Box plot | Median, quartiles, and outliers of a distribution | Line in the box = median; box = middle 50% (IQR); whiskers = normal range; dots beyond = outliers. |
| Histogram + marginal box | Distribution of one numeric variable, with a box-plot summary on top | Tall bars = common range; the attached box plot shows median/outliers at a glance. |
| Sunburst chart | Hierarchical share-of-whole across nested categories (e.g. country → cargo) | Inner ring = top-level grouping, outer rings = sub-groups; segment size = magnitude at that level. |
| Treemap | Hierarchical share-of-whole as nested rectangles (e.g. carrier fleet by risk) | Bigger rectangle = bigger value — good for spotting the few large contributors among many small ones. |
| Waterfall chart | How a value builds up through sequential additions/subtractions (e.g. base cost → final price) | Each floating bar is one component; the final bar lands on the total value. |
| Funnel chart | Sequential drop-off through ordered stages (e.g. quote pipeline) | Widest bar at top = largest starting value; a big narrowing flags where value is lost. |
| Correlation heatmap | Pairwise correlation between numeric variables | Red = variables rise together; blue = inverse relationship; near-white = little relationship. |
| Folium map | Geographic plotting of ports with marker colour/size encoding a metric | Zoom/pan; hover a marker for exact values; colour typically encodes congestion or storm severity. |

### 6.1 Reading the Model-Comparison Benchmarks
Most agents train several classical ML algorithms on the same data split and plot their scores side-by-side. Classification tasks (carrier reliability, weather risk, customs clearance) are scored on accuracy/F1; regression tasks (freight pricing, margin) are scored on R²/RMSE. The app automatically selects the best-scoring model for live predictions elsewhere on the page.

---

## 7. Milestone 4 Workflow — Execution Sequence

The **RAG Engine** and the **Kaggle Data Pipeline** must be successfully prepared before integrating the final application. Follow this sequence in order:

1. **Kaggle / Faker Data Pipeline** — Load or generate the raw ports, shipments, carriers, and customs datasets (Kaggle sources + Faker synthetic augmentation) and validate schema/row counts before seeding.
2. **Database Seeding** — Run `seed_data.py` to populate SQLite (`db.py`, WAL mode) with ports, shipments, carriers, routes, freight quotes, customs requirements, and weather-risk snapshots.
3. **RAG Engine Preparation** — Chunk and embed customs manuals / carrier SOP documents with `sentence-transformers`, build the FAISS index, and verify `rag_engine.answer_with_citation()` returns grounded, cited results.
4. **LLM & Translation Engine Boot** — Load Qwen2.5-3B-Instruct (4-bit) with the Qwen2.5-1.5B-Instruct fail-soft fallback, and load the NLLB-200 translation engine; confirm both show 🟢 Active in the sidebar status panel.
5. **Agent Integration** — Bring Agents 1–9, Notifications, Knowledge Graph, Digital Twin, and Anomaly Scanner online inside the single Streamlit app, verifying each agent's SQL analytics, ML benchmark, and Plotly visuals render correctly.
6. **RBAC & Auth Verification** — Confirm OTP-based login, security questions, and role-scoped menus behave correctly for Admin, Ops Manager, Dispatcher, and Customer/Client roles.
7. **Final Application Integration** — Merge all agents and the shared platform layer into `app.py`, run end-to-end smoke tests, and launch via Streamlit + ngrok/Cloudflare Tunnel for public access.

> ⚠️ Do not attempt step 5 (Agent Integration) until steps 1–3 (Data Pipeline + RAG Engine) complete successfully — several agents and the AI Copilot depend on both being ready.

---

## 8. Getting Started

### 8.1 Environment
This project is designed to run in **Google Colab** with a GPU runtime (for local LLM inference).

### 8.2 Run the notebook
Open `FreightQuote_AI_Complete_Code.ipynb` and run all cells top to bottom. This will:
1. Write out all application files into the `freight_app/` folder
2. Install required dependencies
3. Initialize and seed the SQLite database
4. Boot the FastAPI model microservice (Qwen backend)
5. Launch the Streamlit app and expose it via a public tunnel URL

### 8.3 Log in
Use the default demo credentials:

```
Email:    broker@infosys.com
Password: admin123
```

---

## 9. Project Structure

```
freight_app/
├── app.py                     # Main Streamlit entry point
├── admin_dash.py               # Admin dashboard
├── ai_copilot.py                # Grounded AI chat assistant
├── agent1_route.py .. agent9_pdf_rag.py   # Individual AI agent modules
├── anomaly_scanner.py          # Isolation Forest anomaly detection
├── digital_twin.py             # Network simulation engine
├── knowledge_graph.py          # Graph visualization
├── rbac.py                     # Role-based access control
├── auth.py                     # Authentication logic
├── db.py                       # SQLite connection layer
├── seed_data.py                # Demo data seeding
├── llm_engine.py                # LLM inference client
├── translation_engine.py        # NLLB translation engine
├── rag_engine.py                # PDF/document RAG pipeline
├── model_server.py              # FastAPI microservice for the LLM
├── config.py / ui_theme.py / notifications.py / data_feed_center.py
└── requirements.txt
```

---

## 10. Screenshots

### Login & Access
![Login Screen](./screenshots/login.png)
*Secure sign-in screen with role-based demo credentials.*

### Admin Dashboard
![Admin Dashboard](./screenshots/admin_dashboard.png)
*Command-center overview of shipments, quotes, and platform-wide KPIs.*

### AI Copilot
![AI Copilot](./screenshots/ai_copilot.png)
*Grounded chat assistant answering questions using live freight data.*

### Route Optimization (Agent 1)
![Route Optimization](./screenshots/agent1_route.png)
*Interactive port-to-port route mapping and optimization analysis.*

### Dynamic Freight Pricing (Agent 2)
![Freight Pricing](./screenshots/agent2_pricing.png)
*Real-time dynamic pricing engine for freight quotes.*

### Carrier Performance (Agent 3)
![Carrier Performance](./screenshots/agent3_carrier.png)
*Carrier capacity, reliability, and performance analytics.*

### Weather & Freight Risk (Agent 4)
![Weather Risk](./screenshots/agent4_weather.png)
*Live port weather overlays and shipment risk scoring.*

### Margin Predictor (Agent 5)
![Margin Predictor](./screenshots/agent5_margin.png)
*Predicted yield and margin outlook across active shipments.*

### Customs & Tariffs (Agent 6)
![Customs Tariffs](./screenshots/agent6_customs.png)
*Customs, tax, and compliance guidance for cross-border shipments.*

### Digital Bill of Lading (Agent 7)
![Bill of Lading](./screenshots/agent7_docs.png)
*Automated generation and management of shipping documents.*

### Alerts & Translation (Agent 8)
![Alerts and Translation](./screenshots/agent8_alerts.png)
*Real-time incident alerts alongside 20+ language translation support.*

### PDF SOP / RAG Studio (Agent 9)
![PDF RAG Studio](./screenshots/agent9_pdf_rag.png)
*Upload and query customs/SOP PDFs using retrieval-augmented search.*

### Anomaly Scanner
![Anomaly Scanner](./screenshots/anomaly_scanner.png)
*Isolation Forest–based detection of anomalies across shipments and ports.*

### Digital Twin Simulation
![Digital Twin](./screenshots/digital_twin.png)
*Monte Carlo trade-stress simulation of the global freight network.*

### Knowledge Graph
![Knowledge Graph](./screenshots/knowledge_graph.png)
*Interactive graph linking ports, carriers, shipments, and documents.*

### Data Feed Center
![Data Feed Center](./screenshots/data_feed_center.png)
*Manual and bulk CSV data ingestion into the live database.*

---
