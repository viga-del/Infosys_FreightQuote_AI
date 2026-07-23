# FreightQuote AI — Milestone 2

## What Milestone 2 adds on top of Milestone 1

Milestone 1 delivered the core authentication module — JWT session handling,
a Streamlit login/registration UI, SQLite-backed credentials, and Gmail OTP
verification. Milestone 2 unifies that security gateway with a multi-agent
ML core and an LLM Copilot, and adds three hardening layers:

1. **Progressive account lockout** — 3rd failed login locks the account for
   5 minutes, the 4th for 15 minutes, and the 5th locks it permanently until
   an Admin unlocks it from the Admin Dashboard.
2. **OTP resend rate limiting** — resend cooldowns escalate 60s → 3min → 5min → 1hr.
3. **Real-time password strength checker** — Weak (<5 chars, blocked) /
   Average (5-9 chars, allowed with a warning) / Good (10+ chars).

On top of that, Milestone 2 introduces:

- **Three autonomous ML agents** (Dynamic Pricing, Route Delay Classifier,
  Carrier Compliance Sentinel), each trained on 2 Kaggle datasets and
  comparing 7 algorithms before a champion model is selected and logged.
- **An AI Copilot** powered by Qwen2.5-3B-Instruct (4-bit NF4), which answers
  free-form logistics questions and synthesises the 3 agents' outputs into a
  structured JSON audit action.
- **A fully functional Admin Dashboard** with Add / Delete / Unlock user
  lifecycle controls and an ML Model Card tab.

## Tech Stack

| Layer | Technology |
|---|---|
| UI | Streamlit |
| Auth | bcrypt, PyJWT, SQLite |
| ML | scikit-learn, joblib |
| LLM | Qwen2.5-3B-Instruct (4-bit via bitsandbytes/transformers) |
| Tunnel | pyngrok |
| Data | kagglehub (with seeded synthetic fallback) |

## System Architecture

| Phase | Module / Component | Responsibility |
|---|---|---|
| Phase 1: Security Gateway | `auth.py` | Login, Registration, Forgot Password (Gmail OTP), progressive lockout, password strength. Stores hashed credentials & lockout state in SQLite. |
| Phase 2: Domain Intelligence | `train_ml_freight.py`, model files | Agent 1: Dynamic Pricing, Agent 2: Route Delay Classifier, Agent 3: Carrier Compliance Sentinel. |
| Phase 3: Generative Advisory | `llm_engine_freight.py` | Synthesises the 3 agents' numerical outputs into executive shipping strategies + a structured JSON audit action. |
| Phase 4: System Administration | `admin_dash.py` | Add / Delete / Unlock users, ML Model Card — restricted to `role == 'Admin'`. |

## Indian Port Coverage

| Port | Code | Region | Specialty |
|---|---|---|---|
| Mumbai (JNPT) | INNSA1 | West Coast | Container & general cargo hub |
| Mundra | INMUN1 | West Coast | Largest private port, bulk + container |
| Chennai | INMAA1 | East Coast | Automobile & industrial exports |
| Cochin | INCOK1 | South-West Coast | Transshipment & spices/seafood |

## Setup — Colab Secrets & Kaggle API

1. In Colab, click the 🔑 **Secrets** icon in the left sidebar.
2. Add each of: `JWT_SECRET_KEY`, `ADMIN_EMAIL_ID`, `ADMIN_PASSWORD`,
   `NGROK_AUTHTOKEN`, `HF_TOKEN`, and optionally `EMAIL_ID`, `EMAIL_PASSWORD`,
   `KAGGLE_USERNAME`, `KAGGLE_KEY`. Toggle notebook access **ON** for each.
3. For a Kaggle token: log in at kaggle.com → profile picture → Settings →
   API → **Create New Token**. This downloads `kaggle.json` containing your
   username and key — put those two values into the `KAGGLE_USERNAME` /
   `KAGGLE_KEY` secrets. The notebook trains on synthetic data automatically
   if these aren't set.
4. For Gmail OTP: enable 2-Step Verification on the sending Gmail account,
   then create an **App Password** (Google Account → Security → App
   Passwords) and use that as `EMAIL_PASSWORD`. If unset, OTPs print to the
   notebook console instead — the app still works end to end.

## How to Run

1. Open `FreightQuote_AI_Milestone2.ipynb` in Google Colab.
2. **Runtime → Change runtime type → T4 GPU → Save.**
3. Run every cell top to bottom, in order. Step 6 trains and saves all 3 ML
   agents; Step 7 launches the app and prints a public HTTPS URL.
4. Log in with your `ADMIN_EMAIL_ID` / `ADMIN_PASSWORD` (defaults:
   `infosys@ai` / `admin@123`).
5. Run Step 8 when finished to stop the app and free GPU memory.

## Screenshots

- `screenshots/home.png` — Home page KPI overview
- `screenshots/copilot.png` — AI Copilot prompt + response
- `screenshots/pricing_calculator.png` — ML Pricing Calculator input + predicted cost
- `screenshots/admin_model_card.png` — Admin Panel → ML Model Card tab
- `screenshots/admin_user_actions.png` — Admin Panel → Add / Delete / Unlock actions
- `screenshots/lockout_otp.png` — A triggered lockout message and an OTP cooldown message



