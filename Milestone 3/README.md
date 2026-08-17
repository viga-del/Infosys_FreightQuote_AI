# 🚢 Agentic AI for Maritime Freight Pricing and Route Optimization

## Infosys Springboard Internship Project — Milestone 3

---

## 📖 Project Overview

**FreightQuote AI** is an AI-powered maritime freight decision-support platform developed as part of the **Infosys Springboard Internship Program**.

Milestone 3 focuses on integrating the capabilities developed during Milestones 1 and 2 and extending the platform with a document-based **Retrieval-Augmented Generation (RAG) pipeline and knowledge base**.

---

## 🎯 Project Objectives

- Integrate Milestone 1 authentication.
- Integrate Milestone 2 AI and Machine Learning modules.
- Develop a dedicated RAG pipeline.
- Build a searchable knowledge base from logistics PDFs.
- Enable semantic document retrieval.
- Provide context-aware answers through the AI Copilot.
- Combine structured application data with unstructured document information.
- Improve platform integration and usability.

---

## 🚨 Problem Statement

Maritime freight operations involve large amounts of structured and unstructured information. Freight prices, routes, weather, carrier performance, policies, manuals, and regulations must often be analysed together.

FreightQuote AI addresses this challenge by combining Machine Learning, AI-powered decision support, route and weather analysis, carrier evaluation, secure authentication, and RAG-based document retrieval in one platform.

---

## 💡 Proposed Solution

```text
User
  ↓
Secure Authentication
  ↓
FreightQuote AI Dashboard
  ↓
┌───────────────┬────────────────┬────────────────┐
│ Freight       │ Route &        │ Carrier        │
│ Pricing       │ Weather        │ Analysis       │
└───────────────┴────────────────┴────────────────┘
                         ↓
                    AI Copilot
                         ↓
                   RAG Pipeline
                         ↓
                Logistics Documents
                         ↓
                Retrieved Context
                         ↓
                 Context-Aware Answer
```

---

# ✨ Key Features

## 🔐 Secure User Authentication

- User registration and login
- Password hashing
- JWT-based authentication
- Security questions
- Email OTP verification
- Role-based access
- Secure logout

## 🤖 AI Copilot

The AI Copilot provides a natural-language interface for freight-related questions involving:

- Freight prices
- Shipments
- Routes
- Carriers
- Weather
- Logistics documents
- Operational information

## 💰 Freight Price Prediction

Machine Learning models estimate freight quotation prices using shipment and logistics parameters such as distance, weight, route characteristics, and historical freight information.

## 🗺️ Route & Weather Analysis

The platform supports analysis of shipping routes, port information, weather conditions, and potential operational risks.

## 🚢 Carrier Performance Audit

The Carrier Audit module evaluates carrier performance, shipment reliability, compliance information, historical records, and carrier comparisons.

## 📊 Analytics Dashboard

The dashboard presents freight statistics, prediction results, model performance, shipment information, carrier information, and operational insights.

---

# 📚 Retrieval-Augmented Generation (RAG)

## What is RAG?

Retrieval-Augmented Generation combines document retrieval with a Large Language Model. The system searches the project knowledge base for relevant information and provides the retrieved context to the AI model.

This enables the Copilot to answer questions using project-specific logistics documents.

## 🔄 RAG Pipeline

```text
PDF Documents
      ↓
Document Scraping
      ↓
PDF Text Extraction
      ↓
Text Cleaning
      ↓
Text Chunking
      ↓
Embeddings
      ↓
Vector Database
      ↓
User Query
      ↓
Semantic Retrieval
      ↓
Relevant Context
      ↓
AI Copilot
      ↓
Context-Aware Answer
```

## 🗂️ RAG Knowledge Base

The knowledge base contains logistics-related reference documents such as:

- Freight policies
- Maritime guidelines
- Shipping regulations
- Port operation manuals
- Carrier documentation
- Logistics reports
- Business process documents
- Maritime reference PDFs

## 🔎 Semantic Search

```text
User Query
     ↓
Semantic Retrieval
     ↓
Relevant PDF Sections
     ↓
Retrieved Context
     ↓
AI Copilot
     ↓
Context-Aware Response
```

---

# 📸 RAG Pipeline Screenshots

The following screenshots demonstrate the main stages of the **Milestone 3 RAG pipeline**.

## 🌐 1. Document Scraping

![Document Scraping](screenshots/scraping.jpeg)

*Shows the document scraping stage used to collect relevant maritime and logistics reference documents for the RAG knowledge base.*

---

## 📄 2. PDF Extraction

![PDF Extraction](screenshots/extract_pdf.jpeg)

*Shows the extraction of text and relevant content from the collected PDF documents before further processing.*

---

## ✂️ 3. Document Chunking

![Document Chunks](screenshots/chunks.jpeg)

*Shows the extracted document content being divided into smaller chunks for embedding and semantic retrieval.*

---

## 🧪 4. RAG Testing

![RAG Testing](screenshots/test.jpeg)

*Shows the testing stage of the RAG pipeline, where user queries are evaluated against the prepared knowledge base and relevant information is retrieved for generating responses.*

---

## 🔄 RAG Pipeline Demonstration

```text
Document Scraping
        ↓
    PDF Extraction
        ↓
   Text Chunking
        ↓
 Embedding / Indexing
        ↓
  Semantic Retrieval
        ↓
    RAG Testing
        ↓
 Context-Aware Response
```

---

# 🧠 Artificial Intelligence

The AI layer uses:

- Qwen 2.5 Large Language Model
- Hugging Face Transformers
- Natural Language Processing
- AI Copilot
- Retrieval-Augmented Generation

---

# 📈 Machine Learning

Algorithms used across the project include:

- Random Forest
- Decision Tree
- Gradient Boosting
- Linear Regression
- Support Vector Regression (SVR)

Models are evaluated using suitable performance metrics and the strongest-performing model can be selected for deployment.

### Classification Metrics

- Accuracy
- Precision
- Recall
- F1 Score

### Regression Metrics

- RMSE
- R² Score

```text
Train Models
     ↓
Evaluate Performance
     ↓
Compare Metrics
     ↓
Select Best Model
     ↓
Champion Model
     ↓
Prediction
```

---

# 🏗️ System Architecture

```text
┌─────────────────────────────────────────────┐
│                    USER                     │
└──────────────────────┬──────────────────────┘
                       │
                       ▼
┌─────────────────────────────────────────────┐
│            Authentication Layer             │
│       Registration • Login • OTP • JWT      │
└──────────────────────┬──────────────────────┘
                       │
                       ▼
┌─────────────────────────────────────────────┐
│              Streamlit Interface            │
│        Dashboard • Forms • AI Copilot       │
└──────────────────────┬──────────────────────┘
                       │
          ┌────────────┼────────────┐
          ▼            ▼            ▼
┌──────────────┐ ┌──────────────┐ ┌──────────────┐
│ ML Modules   │ │ Route/Weather│ │ Carrier Audit│
│ Pricing      │ │ Analysis     │ │ Performance  │
└──────┬───────┘ └──────┬───────┘ └──────┬───────┘
       │                 │                │
       └─────────────────┼────────────────┘
                         ▼
                ┌─────────────────┐
                │   AI Copilot    │
                │    Qwen 2.5     │
                └────────┬────────┘
                         │
                         ▼
                ┌─────────────────┐
                │   RAG Pipeline  │
                └────────┬────────┘
                         │
                         ▼
                ┌─────────────────┐
                │ Knowledge Base  │
                │ Logistics PDFs  │
                └────────┬────────┘
                         │
                         ▼
                ┌─────────────────┐
                │ Retrieved       │
                │ Context         │
                └────────┬────────┘
                         │
                         ▼
                Context-Aware Answer
```

---

# 🗃️ Data Sources

### Structured Data

- Freight pricing data
- Carrier performance data
- Port information
- Weather information
- Shipment data

### Unstructured Data

- Logistics PDF documents
- Maritime reports
- Shipping guidelines
- Freight policies
- Port operation documents
- Carrier reference documents

---

# 🔐 Security Architecture

```text
User
 ↓
Registration / Login
 ↓
Credential Verification
 ├── Password Hashing
 ├── OTP Verification
 └── Security Question
 ↓
JWT Session
 ↓
Role Verification
 ↓
Authorized Dashboard
```

### Security Features

- JWT authentication
- Password hashing
- Email OTP verification
- Security questions
- Role-based authentication
- Secure session management
- Logout functionality
- Administrative access control

---

# 🛠️ Technology Stack

| Category | Technologies | Purpose |
|---|---|---|
| Frontend | Streamlit | User interface and dashboards |
| Backend | Python | Application and business logic |
| Database | SQLite | Application and authentication data |
| Machine Learning | Scikit-learn | Prediction and classification |
| Data Processing | Pandas, NumPy | Data preparation and analysis |
| Artificial Intelligence | Qwen 2.5, Hugging Face Transformers | AI Copilot |
| RAG | LangChain, FAISS, Sentence Transformers | Document retrieval and semantic search |
| Authentication | PyJWT, bcrypt | Secure authentication and sessions |
| Deployment | Google Colab, ngrok | Development and public access |
| Version Control | Git, GitHub | Collaborative development |

---

# 📁 Milestone Organization

```text
FreightQuote AI
│
├── Milestone 1
│   └── Secure Authentication
│
├── Milestone 2
│   └── Multi-Agent AI Platform
│
└── Milestone 3
    └── Integration & RAG
        ├── Combined Application
        ├── RAG Pipeline
        ├── PDF Knowledge Base
        ├── Semantic Search
        ├── Document Retrieval
        └── Context-Aware Question Answering
```

---

# 📌 Milestone 1 — Secure Authentication Module

Milestone 1 established the security foundation of the platform.

- User registration
- Secure login
- JWT authentication
- Password hashing
- Forgot password
- Security questions
- Email OTP verification
- Role-based authentication
- SQLite database integration
- Secure session management
- Logout

---

# 📌 Milestone 2 — Multi-Agent AI Platform

| Module | Description |
|---|---|
| **AI Copilot** | Provides intelligent logistics assistance using the Qwen 2.5 LLM |
| **Freight Pricing** | Predicts freight quotation prices using Machine Learning |
| **Route & Weather Analysis** | Analyses route conditions and weather information |
| **Carrier Audit** | Evaluates carrier performance, compliance, and reliability |
| **Analytics Dashboard** | Displays freight statistics, model results, and business insights |
| **Model Retraining** | Supports retraining with newly available logistics data |
| **Admin Dashboard** | Provides administrative controls and monitoring |

---

# 📌 Milestone 3 — Integration & RAG Pipeline

Major activities include:

- Integration of Milestone 1 authentication.
- Integration of Milestone 2 Machine Learning modules.
- Integration of the AI Copilot.
- Development of the RAG pipeline.
- Collection of logistics-related PDF documents.
- Knowledge-base preparation.
- Document preprocessing.
- Document embeddings.
- Vector-search preparation.
- Semantic retrieval.
- Context integration with the AI Copilot.
- Document-based question answering.
- Improved application documentation.

---

# 🧪 Testing

The application can be evaluated through:

- Functional testing
- Integration testing
- AI response validation
- Machine Learning model evaluation
- RAG retrieval testing

The RAG test stage verifies whether relevant information can be retrieved from the prepared knowledge base for user queries.

---

# 🚀 Deployment

### Current Development Environment

- Google Colab
- Streamlit
- ngrok

### Future Deployment Targets

- Streamlit Cloud
- AWS
- Microsoft Azure
- Docker-based deployment

---

# 👤 User Guide

| Step | Action |
|---|---|
| **1** | Register a new account |
| **2** | Complete authentication |
| **3** | Log in securely |
| **4** | Open the FreightQuote AI dashboard |
| **5** | Generate or analyse freight quotations |
| **6** | Analyse routes and weather |
| **7** | Review carrier performance |
| **8** | Ask questions through AI Copilot |
| **9** | Search logistics documents using RAG |
| **10** | Review analytics and insights |

---

# 📊 Project Outcomes

- Intelligent freight quotation support
- Machine Learning-based prediction
- Route and weather analysis
- Carrier performance evaluation
- AI-powered logistics assistance
- Secure enterprise authentication
- Retrieval-Augmented Generation
- Semantic document search
- Logistics document knowledge base
- Context-aware question answering
- Integrated analytics
- Modular application architecture

---

# 👥 Team Contribution

| Team Member | Role | Contribution |
|---|---|---|
| **Vigasini** | Milestone Integration | Integrated Milestone 1 and Milestone 2 into a unified application and connected the major platform components. |
| **Simran Kapoor** | RAG Pipeline Development | Developed the RAG pipeline, including document loading, preprocessing, embeddings, vector storage, and semantic retrieval. |
| **Yuvanesh** | Knowledge Base Preparation | Collected and organized logistics-related PDF documents and prepared the knowledge base for RAG processing. |
| **Tharani** | Documentation & Integration Support | Prepared project documentation and supported project organization and integration activities. |

---

# 🌟 Milestone 3 Highlights

- 🔐 Secure authentication foundation
- 💰 ML-based freight pricing
- 🗺️ Route and weather analysis
- 🚢 Carrier performance analysis
- 🤖 Qwen 2.5 AI Copilot
- 📚 PDF-based RAG knowledge base
- 🔎 Semantic document retrieval
- 🧠 Context-aware question answering
- 📊 Analytics and business insights
- 🧩 Integrated milestone architecture

---

# 🎓 Learning Outcomes

Through Milestone 3, the team gained practical experience in:

- AI application development
- Machine Learning
- Natural Language Processing
- Large Language Models
- Retrieval-Augmented Generation
- Semantic search
- Vector databases
- Document processing
- Streamlit application development
- Authentication and security
- Database integration
- AI system integration
- Testing and validation

---

