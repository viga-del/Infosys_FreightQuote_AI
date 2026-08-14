# 🚢 Agentic AI for Maritime Freight Pricing and Route Optimization

## Infosys Springboard Internship Project — Milestone 3

---

## 📖 Project Overview

**FreightQuote AI** is an AI-powered maritime freight decision-support platform developed as part of the **Infosys Springboard Internship Program**.

The platform brings together secure authentication, Machine Learning, AI-powered logistics assistance, freight pricing, route and weather analysis, carrier evaluation, analytics, and Retrieval-Augmented Generation (RAG) into a unified application.

**Milestone 3** focuses on integrating the capabilities developed during Milestones 1 and 2 and extending the platform with a document-based **RAG pipeline and knowledge base**. The milestone also improves the overall application workflow, documentation, and usability.

The objective is to provide logistics users with a single platform where they can securely access freight intelligence, generate predictions, analyse operational information, and ask questions using both structured application data and unstructured logistics documents.

---

## 🎯 Project Objectives

The main objectives of Milestone 3 are:

- Integrate the authentication functionality developed in Milestone 1.
- Integrate the AI and Machine Learning modules developed in Milestone 2.
- Develop a dedicated Retrieval-Augmented Generation pipeline.
- Build a searchable knowledge base from logistics-related PDF documents.
- Enable semantic document retrieval.
- Provide context-aware answers through the AI Copilot.
- Combine structured data, ML predictions, and retrieved document information.
- Improve the overall usability and integration of the FreightQuote AI platform.
- Maintain a modular architecture that can be extended with additional maritime intelligence features.

---

## 🚨 Problem Statement

Maritime freight operations involve large amounts of structured and unstructured information.

Freight prices can change based on shipment characteristics, route conditions, carrier performance, weather, and other operational factors. At the same time, logistics teams need to work with documents such as shipping policies, maritime guidelines, port manuals, carrier documents, and regulatory references.

Traditional workflows require users to manually search through these documents and separately analyse operational data. This can be time-consuming and may make decision-making less efficient.

**FreightQuote AI** addresses this problem by combining:

- Machine Learning-based predictions
- AI-powered decision support
- Route and weather analysis
- Carrier performance analysis
- Secure authentication
- Document retrieval using RAG
- Natural-language question answering

---

## 💡 Proposed Solution

FreightQuote AI provides a unified AI-powered platform for maritime freight analysis.

A typical workflow is:

```text
User
  │
  ▼
Secure Authentication
  │
  ▼
FreightQuote AI Dashboard
  │
  ├───────────────┬────────────────┬────────────────┐
  ▼               ▼                ▼                ▼
Freight        Route &         Carrier          Analytics
Pricing        Weather         Analysis         Dashboard
  │               │                │                │
  └───────────────┴────────────────┴────────────────┘
                          │
                          ▼
                    AI Copilot
                          │
                          ▼
                   RAG Pipeline
                          │
                          ▼
                 Logistics Documents
                          │
                          ▼
                 Retrieved Context
                          │
                          ▼
                  Context-Aware Answer
```

---

# ✨ Key Features

## 🔐 1. Secure User Authentication

The platform provides a complete authentication workflow.

### Registration

Users can create an account using:

- Username
- Email address
- Password
- Password confirmation
- Security question
- Security answer

Passwords are securely hashed before being stored.

### Login

Registered users can securely log in using their credentials. Successful authentication creates a secure session using JWT-based authentication.

### Password Recovery

The platform supports multiple password-recovery mechanisms:

- Security question verification
- Email OTP verification

### Additional Security

- Password hashing using bcrypt
- JWT-based sessions
- OTP verification
- Security questions
- Role-based access
- Secure logout
- Account protection mechanisms

---

## 🤖 2. AI Copilot

The AI Copilot provides a natural-language interface for interacting with the freight platform.

Users can ask questions related to:

- Freight prices
- Shipments
- Routes
- Carriers
- Weather
- Logistics documents
- Operational information

The Copilot can use application data and retrieved document context to generate more relevant responses.

---

## 💰 3. Freight Price Prediction

The platform uses Machine Learning to estimate freight quotation prices based on available shipment and logistics parameters.

Possible input factors include:

- Shipment information
- Distance
- Weight
- Route characteristics
- Transportation conditions
- Historical freight information

The prediction module helps users obtain faster and more consistent freight estimates.

---

## 🗺️ 4. Route & Weather Analysis

The route and weather module supports logistics planning by analysing:

- Shipping routes
- Port information
- Weather conditions
- Potential operational risks
- Route-related factors

This information can help users understand conditions that may affect freight movement.

---

## 🚢 5. Carrier Performance Audit

The Carrier Audit module evaluates carrier-related information to support logistics decisions.

It can analyse areas such as:

- Carrier performance
- Shipment reliability
- Compliance-related information
- Historical operational records
- Carrier comparison

---

## 📊 6. Analytics Dashboard

The analytics dashboard presents important freight and model information in an easier-to-understand format.

It can be used to review:

- Freight statistics
- Prediction results
- Model performance
- Shipment information
- Carrier information
- Operational insights

---

## 🔄 7. Model Retraining

The platform provides a foundation for retraining Machine Learning models when new logistics data becomes available.

```text
New Dataset
     ↓
Data Preparation
     ↓
Feature Processing
     ↓
Model Training
     ↓
Model Evaluation
     ↓
Performance Comparison
     ↓
Best Model
     ↓
Updated Prediction System
```

---

# 📚 Retrieval-Augmented Generation (RAG)

## What is RAG?

Retrieval-Augmented Generation combines document retrieval with a Large Language Model.

Instead of relying only on information stored inside the language model, the system first searches the project knowledge base for relevant information and then provides the retrieved context to the AI model.

This allows the Copilot to answer questions using project-specific documents.

---

## 🔄 RAG Pipeline

The Milestone 3 RAG workflow is:

```text
             PDF Documents
                  │
                  ▼
           Document Loading
                  │
                  ▼
           Text Extraction
                  │
                  ▼
             Text Cleaning
                  │
                  ▼
               Chunking
                  │
                  ▼
             Embeddings
                  │
                  ▼
          Vector Database
                  │
                  ▼
             User Query
                  │
                  ▼
        Semantic Similarity Search
                  │
                  ▼
          Relevant Documents
                  │
                  ▼
          Retrieved Context
                  │
                  ▼
             AI Copilot
                  │
                  ▼
          Context-Aware Answer
```

---

## 🗂️ RAG Knowledge Base

The knowledge base contains logistics-related reference documents.

Examples include:

- Freight policies
- Maritime guidelines
- Shipping regulations
- Port operation manuals
- Carrier documentation
- Logistics reports
- Business process documents
- Maritime reference PDFs

The documents are processed and converted into searchable representations so that relevant sections can be retrieved when a user asks a question.

---

## 🔎 Semantic Search

The RAG system uses semantic search rather than depending only on exact keyword matching.

For example:

```text
User Query:
"What documents explain customs procedures for a shipment?"

              ↓

Semantic Retrieval

              ↓

Relevant PDF Sections

              ↓

Context Provided to LLM

              ↓

AI Copilot Response
```

This makes it possible to retrieve conceptually relevant information even when the exact words used in the document and the user's question are different.

---

# 🧠 Artificial Intelligence

The AI layer uses:

- Qwen 2.5 Large Language Model
- Hugging Face Transformers
- Natural Language Processing
- AI Copilot
- Retrieval-Augmented Generation

The AI Copilot acts as the natural-language interface between the user and the platform's structured and unstructured information.

---

# 📈 Machine Learning

The FreightQuote AI platform uses Machine Learning for freight and logistics analysis.

Algorithms used across the project include:

- Random Forest
- Decision Tree
- Gradient Boosting
- Linear Regression
- Support Vector Regression (SVR)

The models are evaluated using appropriate performance metrics, and the strongest-performing model can be selected for deployment.

---

## 📊 Model Evaluation

### Classification Metrics

Classification models can be evaluated using:

- Accuracy
- Precision
- Recall
- F1 Score

### Regression Metrics

Regression models can be evaluated using:

- RMSE
- R² Score

### Model Selection

```text
Train Multiple Models
        ↓
Evaluate Performance
        ↓
Compare Metrics
        ↓
Select Best-Performing Model
        ↓
Champion Model
        ↓
Prediction
```

---

# 🏗️ System Architecture

```text
┌─────────────────────────────────────────────┐
│                  USER                       │
└──────────────────────┬──────────────────────┘
                       │
                       ▼
┌─────────────────────────────────────────────┐
│            Authentication Layer             │
│     Registration • Login • OTP • JWT       │
└──────────────────────┬──────────────────────┘
                       │
                       ▼
┌─────────────────────────────────────────────┐
│              Streamlit Interface            │
│       Dashboard • Forms • AI Copilot       │
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
                │  AI Copilot     │
                │   Qwen 2.5      │
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

# 🔄 Complete Project Workflow

1. The user opens the FreightQuote AI application.
2. The user registers or logs into the platform.
3. Authentication validates the user's credentials.
4. The system creates a secure authenticated session.
5. The user accesses the appropriate dashboard based on their role.
6. The user selects a freight or logistics module.
7. Machine Learning models process relevant operational data.
8. Route and weather information is analysed when required.
9. Carrier information is evaluated through the Carrier Audit module.
10. The user can ask questions through the AI Copilot.
11. If document-based information is required, the RAG pipeline searches the knowledge base.
12. Relevant document sections are retrieved.
13. The retrieved context is passed to the AI model.
14. The Copilot generates a context-aware response.
15. Analytics and prediction results are displayed through the dashboard.

---

# 📸 RAG Pipeline Screenshots

The following screenshots document the **Milestone 3 Retrieval-Augmented Generation (RAG) pipeline**. They focus only on the document-ingestion, knowledge-base, retrieval, evaluation, and answer-generation stages.

> **Note:** Keep the screenshot filenames below inside the `screenshots/` folder. If your actual filenames are different, update the image paths accordingly.

## 📚 RAG Pipeline Overview

![RAG Pipeline Overview](screenshots/rag_pipeline_overview.jpeg)

*Overview of the complete RAG workflow from document collection and preprocessing to semantic retrieval and grounded question answering.*

## 📄 PDF Document Discovery

![PDF Discovery](screenshots/rag_pdf_discovery.jpeg)

*Shows the logistics PDF documents collected and prepared as source material for the RAG knowledge base.*

## 🗂️ Knowledge Base Preparation

![Knowledge Base](screenshots/rag_knowledge_base.jpeg)

*Displays the prepared collection of maritime and logistics documents used by the retrieval system.*

## ✂️ Document Chunking

![Document Chunking](screenshots/rag_chunking.jpeg)

*Demonstrates how extracted document text is divided into smaller chunks before embedding and indexing.*

## 🧠 Embedding & Vector Index

![Vector Index](screenshots/rag_vector_index.jpeg)

*Shows the vector-index preparation stage used for semantic retrieval of relevant document sections.*

## 🔎 Semantic Search

![Semantic Search](screenshots/rag_semantic_search.jpeg)

*Demonstrates retrieval of document sections that are semantically relevant to a user's query.*

## 💬 RAG Question Answering

![RAG Question Answering](screenshots/rag_question_answering.jpeg)

*Shows a user query, retrieved context, and the resulting context-aware answer generated from the knowledge base.*

## 📊 RAG Evaluation Queries

![RAG Evaluation](screenshots/rag_evaluation.jpeg)

*Displays evaluation queries used to assess the quality and relevance of the RAG retrieval and answer-generation workflow.*

## 📈 RAG Evaluation Results

![RAG Evaluation Results](screenshots/rag_score_chart.jpeg)

*Visual representation of RAG evaluation results used to compare retrieval or response quality across test queries.*

## 📦 Generated RAG Artifacts

![RAG Artifacts](screenshots/rag_artifacts.jpeg)

*Shows the generated files and artifacts produced during the RAG pipeline, such as processed data, indexes, and evaluation outputs.*

---

# 🗃️ Data Sources

The platform works with structured datasets and unstructured documents.

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

The structured data supports Machine Learning and analytics, while the unstructured documents support the RAG knowledge base.

---

# 🔐 Security Architecture

Security is an important part of the FreightQuote AI platform.

```text
User
 │
 ▼
Registration / Login
 │
 ▼
Credential Verification
 │
 ├── Password Hashing
 ├── OTP Verification
 └── Security Question
 │
 ▼
JWT Session
 │
 ▼
Role Verification
 │
 ▼
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
│       ├── Registration
│       ├── Login
│       ├── JWT
│       ├── Password Recovery
│       ├── Security Questions
│       └── Gmail OTP
│
├── Milestone 2
│   └── Multi-Agent AI Platform
│       ├── Freight Pricing
│       ├── Route & Weather Analysis
│       ├── Carrier Audit
│       ├── AI Copilot
│       ├── Analytics
│       └── Admin Dashboard
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

### Implemented Features

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

Milestone 2 introduced the main AI and Machine Learning capabilities.

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

Milestone 3 extends the earlier milestones through application integration and document intelligence.

### Major Activities

- Integrated the Milestone 1 authentication functionality.
- Integrated the Milestone 2 Machine Learning modules.
- Integrated the AI Copilot.
- Developed a dedicated RAG pipeline.
- Collected logistics-related PDF documents.
- Prepared and organized the document knowledge base.
- Implemented document preprocessing.
- Generated document embeddings.
- Created a vector-search layer.
- Implemented semantic retrieval.
- Connected retrieved context with the AI Copilot.
- Added document-based question answering.
- Improved application documentation and demonstration workflow.

---

# 🧪 Testing

The application can be evaluated through several levels of testing.

### Functional Testing

Verifies whether individual features work as expected.

Examples:

- Registration
- Login
- OTP verification
- Password recovery
- Freight prediction
- RAG search
- AI Copilot

### Integration Testing

Verifies communication between:

- Authentication and dashboard
- ML models and application interface
- RAG pipeline and AI Copilot
- Database and application modules

### AI Response Validation

Checks whether the AI Copilot provides responses based on the available application and retrieved document context.

### Machine Learning Evaluation

Models are evaluated using suitable classification and regression metrics.

---

# 🚀 Deployment

### Current Development Environment

- Google Colab
- Streamlit
- ngrok

Google Colab provides a convenient development environment, especially when GPU resources are required for the Qwen 2.5 model.

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

Milestone 3 results in a more integrated and intelligent FreightQuote AI platform.

### Major Outcomes

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

This project was completed collaboratively by a team of four members as part of the **Infosys Springboard Internship Program**.

| Team Member | Role | Contribution |
|---|---|---|
| **Vigasini** | Milestone Integration | Integrated Milestone 1 and Milestone 2 into a unified application; connected authentication, AI modules, analytics, and administrative functionality; verified compatibility between integrated components. |
| **Simran Kapoor** | RAG Pipeline Development | Developed the RAG pipeline; implemented document loading, preprocessing, embedding generation, vector storage, semantic retrieval, and integration of retrieved context with the AI model. |
| **Yuvanesh** | Knowledge Base Preparation | Collected logistics-related PDF documents and supporting reference materials; organized the knowledge base and prepared documents for RAG processing and retrieval. |
| **Tharani** | Documentation & Integration Support | Prepared project documentation, maintained milestone documentation, supported project organization and integration activities, and ensured consistency of project information across milestones. |

---

# 🌟 Milestone 3 Highlights

The major achievement of Milestone 3 is the transition from separate AI and authentication modules into a more connected **maritime freight intelligence platform**.

### Key Highlights

- 🔐 Secure authentication foundation
- 💰 ML-based freight pricing
- 🗺️ Route and weather analysis
- 🚢 Carrier performance analysis
- 🤖 Qwen 2.5 AI Copilot
- 📚 PDF-based RAG knowledge base
- 🔎 Semantic document retrieval
- 🧠 Context-aware question answering
- 📊 Analytics and business insights
- 🔄 Model evaluation and retraining support
- 🧩 Integrated milestone architecture

---



## 🎓 Learning Outcomes

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
- Collaborative software development

---


