# Agentic AI for Maritime Freight Pricing and Route Optimization — Milestone 4

An AI-powered ocean freight intelligence platform built with **Streamlit**, **FastAPI**, and a locally-hosted **Qwen LLM** backend. The platform brings together route optimization, dynamic pricing, carrier analytics, weather risk, customs guidance, document automation, multilingual translation, PDF-based RAG, anomaly detection, and a digital twin simulation — all backed by a seeded SQLite database and role-based access control.

This README documents the Milestone 4 deliverable: the completed, end-to-end runnable application.

---

## 📌 Milestone 4 Scope

- [x] Final integration of all AI agents into a single Streamlit application
- [x] AI Copilot with grounded Q&A over the live database
- [x] Role-Based Access Control (Admin, Operations Manager, Freight Broker, etc.)
- [x] Local LLM microservice (FastAPI + Qwen) for grounded generation
- [x] Multilingual translation engine (NLLB-200, 20+ languages)
- [x] PDF/document RAG studio for customs & SOP documents
- [x] Anomaly detection, digital twin simulation, and knowledge graph visualization
- [x] End-to-end deployment via Streamlit + Cloudflare Tunnel

---

## 🧩 Key Features / Modules

| Module | Description |
|---|---|
| Admin Dashboard | Command-center view of shipments, quotes, and platform KPIs |
| AI Copilot | Grounded chat assistant that answers questions using live freight data |
| Agent 1 — Route Optimization | Interactive port-to-port route mapping and analysis |
| Agent 2 — Dynamic Freight Pricing | Real-time freight quote pricing engine |
| Agent 3 — Carrier Performance | Carrier capacity and performance analytics |
| Agent 4 — Weather & Freight Risk | Port weather overlays and risk scoring |
| Agent 5 — Margin Predictor | Yield/margin prediction across shipments |
| Agent 6 — Customs & Tariffs | Customs, tax, and compliance guidance |
| Agent 7 — Digital Bill of Lading | Document generation and management |
| Agent 8 — Incident Alerts & Translation | Real-time alerts plus 20+ language translation |
| Agent 9 — PDF SOP / RAG Studio | Upload and query customs/SOP PDFs with vector search |
| Anomaly Scanner | Isolation Forest–based anomaly detection across shipments/ports |
| Digital Twin | Monte Carlo trade-stress simulation of the freight network |
| Knowledge Graph | Visual graph of ports, carriers, shipments, and documents |
| Data Feed Center | Manual + bulk CSV ingestion into the live database |

---

## 🛠️ Tech Stack

- **Frontend:** Streamlit, Plotly, Folium
- **Backend:** FastAPI (local model microservice), SQLite
- **AI/ML:** PyTorch, Hugging Face Transformers (Qwen LLM), NLLB-200 (translation), scikit-learn (Isolation Forest)
- **Auth:** bcrypt-hashed credentials, custom RBAC layer
- **Deployment:** Google Colab (GPU runtime) + Cloudflare Tunnel for public access

---

## 🚀 Getting Started

### 1. Environment
This project is designed to run in **Google Colab** with a GPU runtime (for local LLM inference).

### 2. Run the notebook
Open `FreightQuote_AI_Complete_Code.ipynb` and run all cells top to bottom. This will:
1. Write out all application files into the `freight_app/` folder
2. Install required dependencies
3. Initialize and seed the SQLite database
4. Boot the FastAPI model microservice (Qwen backend)
5. Launch the Streamlit app and expose it via a Cloudflare Tunnel URL

### 3. Log in
Use the default demo credentials:

```
Email:    broker@infosys.com
Password: admin123
```

---

## 📂 Project Structure

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

## 🖼️ Screenshots

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
