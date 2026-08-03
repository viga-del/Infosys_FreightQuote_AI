# FreightQuote AI – Enterprise AI-Powered Maritime Brokerage Platform

**Infosys Springboard Internship Project – Milestone 3**

---

## Project Overview

FreightQuote AI is an AI-powered enterprise maritime brokerage platform developed as part of the Infosys Springboard Internship Program. The platform simplifies and automates freight quotation generation, shipment analysis, carrier evaluation, and logistics decision-making using Artificial Intelligence, Machine Learning, and Retrieval-Augmented Generation (RAG).

The project integrates secure authentication, intelligent freight pricing, route and weather analysis, carrier auditing, analytics, and an AI Copilot into a single unified application.

Milestone 3 focuses on integrating the work completed in Milestone 1 and Milestone 2 while extending the application with a Retrieval-Augmented Generation (RAG) pipeline, a document knowledge base, and collaborative project documentation.

---

## Project Objectives

- Develop an enterprise-grade AI-powered freight quotation system.
- Automate freight pricing using Machine Learning.
- Assist logistics managers through an AI-powered Copilot.
- Analyze shipping routes and weather conditions.
- Evaluate carrier performance and compliance.
- Build a Retrieval-Augmented Generation (RAG) pipeline for document-based question answering.
- Integrate all milestones into a single modular application.
- Maintain collaborative software development using GitHub.

---

## Problem Statement

The maritime logistics industry faces several challenges in generating freight quotations due to dynamic pricing, varying carrier performance, changing weather conditions, and the large volume of logistics documents. Manual quotation generation is time-consuming, error-prone, and inefficient.

FreightQuote AI addresses these challenges by leveraging Artificial Intelligence, Machine Learning, and Retrieval-Augmented Generation (RAG) to automate freight quotation generation, provide intelligent logistics recommendations, and retrieve relevant information from logistics documents.

---

## Proposed Solution

FreightQuote AI provides an enterprise-level solution that combines secure authentication, AI-powered freight prediction, carrier evaluation, weather analysis, intelligent document retrieval, and an AI Copilot into a single platform.

The platform enables logistics managers to make informed decisions by utilizing machine learning models for prediction and RAG-powered document retrieval for context-aware responses.

---

## Key Features

- Secure User Authentication
- AI Copilot powered by the Qwen 2.5 LLM
- Freight Price Prediction
- Route & Weather Analysis
- Carrier Performance Audit
- Analytics Dashboard
- Model Retraining
- Admin Dashboard
- Retrieval-Augmented Generation (RAG)
- PDF Knowledge Base
- Semantic Search
- Intelligent Question Answering

---

## System Architecture

```
User
  ↓
Authentication Module
  ↓
AI Copilot
  ↓
Machine Learning Agents
  ↓
Analytics Dashboard
  ↓
RAG Pipeline
  ↓
Knowledge Base
  ↓
SQLite Database
```

---

## Project Workflow

1. User logs into the application.
2. Authentication verifies user credentials.
3. User accesses AI modules.
4. Machine Learning predicts freight pricing.
5. Route & Weather module analyzes shipment conditions.
6. Carrier Audit evaluates carrier performance.
7. RAG pipeline retrieves relevant information from logistics documents.
8. AI Copilot generates context-aware responses.
9. Analytics Dashboard displays business insights.
10. Admin manages users and monitors system activities.

---

## Datasets Used

- Freight Pricing Dataset
- Carrier Performance Dataset
- Port Information Dataset
- Weather Dataset
- Shipment Dataset
- Logistics Documents (PDF)
- Maritime Reports

These datasets are used for model training, prediction, analytics, and document retrieval.

---

## Documentation Used

The RAG knowledge base contains documents such as:

- Freight Policies
- Maritime Guidelines
- Shipping Regulations
- Port Operations Manuals
- Carrier Documentation
- Logistics Reports
- Business Process Documents
- PDF Reference Materials

---

## Security Features

- JWT Authentication
- Password Hashing
- Email OTP Verification
- Security Questions
- Role-Based Authentication
- Admin Controls
- Secure Session Management

---

## Performance Metrics

Machine learning models are evaluated using:

- Accuracy
- Precision
- Recall
- F1 Score
- RMSE
- R² Score

The best-performing model is selected as the Champion Model for deployment.

---

## Development Workflow

The project follows Agile software development practices:

```
Requirement Analysis → System Design → Module Development → Testing → Integration → Deployment → Documentation
```

---

## Testing

- Unit Testing
- Integration Testing
- Functional Testing
- User Acceptance Testing
- AI Response Validation
- Machine Learning Model Evaluation

---

## Repository Structure Overview

```
Milestone 1 – Authentication
        ↓
Milestone 2 – Multi-Agent AI Platform
        ↓
Milestone 3 – RAG Pipeline
        ↓
Knowledge Base
        ↓
Project Documentation
        ↓
Final Integrated Application
```

---

## Deployment

**Current:**
- Google Colab
- Ngrok
- Streamlit

**Future targets:**
- Streamlit Cloud
- Azure
- AWS
- Docker

---

## User Guide

| Step | Action |
|------|--------|
| 1 | Register a new account |
| 2 | Login securely |
| 3 | Access AI Copilot |
| 4 | Generate freight quotations |
| 5 | Analyze routes and weather |
| 6 | Evaluate carrier performance |
| 7 | Query logistics documents using RAG |
| 8 | View analytics dashboard |
| 9 | Admin manages users and system activities |

---

## Project Outcomes

- Intelligent Freight Quotation
- AI-Assisted Decision Making
- Machine Learning Prediction
- Retrieval-Augmented Generation
- Enterprise Authentication
- Multi-Agent AI Platform
- Intelligent Analytics
- Knowledge-Based Question Answering
- Collaborative Software Development

---

## Milestone Overview

### Milestone 1 – Secure Authentication Module

Milestone 1 focused on developing a secure authentication system for the FreightQuote AI platform.

**Features Implemented:**
- User Registration
- Secure Login
- JWT Authentication
- Password Hashing
- Forgot Password
- Security Questions
- Email OTP Verification
- Role-Based Authentication
- SQLite Database Integration

### Milestone 2 – Multi-Agent AI Platform

Milestone 2 introduced the core AI-powered logistics modules.

| Module | Description |
|--------|-------------|
| AI Copilot | Provides intelligent logistics assistance using the Qwen 2.5 Large Language Model |
| Agent 1 – Freight Pricing | Predicts freight quotation prices using Machine Learning |
| Agent 2 – Route & Weather Analysis | Analyzes shipping routes and weather conditions to support logistics planning |
| Agent 3 – Carrier Audit | Evaluates carrier performance, compliance, and shipment reliability |
| Analytics Dashboard | Displays freight statistics, model performance, and business insights |
| Model Retraining | Retrains machine learning models using newly available logistics datasets |
| Admin Dashboard | Provides administrative features including user management, monitoring, and analytics |

### Milestone 3 – Project Integration & RAG Pipeline

Milestone 3 focuses on integrating all previous work and extending the application with Retrieval-Augmented Generation (RAG).

**Major Activities:**
- Integration of the Milestone 1 Authentication Module.
- Integration of the Milestone 2 AI and Machine Learning modules.
- Development of a dedicated RAG notebook.
- Collection and organization of logistics PDF documents.
- Document preprocessing and knowledge base preparation.
- Vector database creation.
- Enterprise documentation.
- GitHub collaboration using branches and Pull Requests.

---

## Artificial Intelligence

- Qwen 2.5 Large Language Model
- Hugging Face Transformers
- AI Copilot
- Natural Language Processing
- Retrieval-Augmented Generation (RAG)

---

## Machine Learning

The FreightQuote AI platform uses multiple machine learning algorithms for prediction and analysis:

- Random Forest
- Decision Tree
- Gradient Boosting
- Linear Regression
- Support Vector Regression (SVR)

The best-performing model is selected for deployment after evaluation.

---

## RAG Knowledge Base

The RAG pipeline retrieves information from logistics-related documents and provides context-aware answers. The knowledge base includes:

- Shipping Guidelines
- Maritime Reports
- Freight Policies
- Logistics Manuals
- Port Information
- PDF Documents
- Business Documentation

The retrieved context is supplied to the Large Language Model to generate accurate responses.

---

## Technology Stack

| Category | Technologies |
|----------|--------------|
| Frontend | Streamlit |
| Backend | Python |
| Database | SQLite |
| Machine Learning | Scikit-learn, Pandas, NumPy |
| Artificial Intelligence | Hugging Face, Transformers, Qwen 2.5 LLM |
| Retrieval-Augmented Generation | LangChain, FAISS, Sentence Transformers |
| Deployment | Google Colab, Ngrok |
| Version Control | Git, GitHub |

---

## Project Structure

```
Infosys_FreightQuote_AI/
│
├── README.md
│
├── Milestone_1/
│   ├── Milestone1.ipynb
│   ├── README.md
│   ├── app.py
│   ├── db.py
│   ├── auth.py
│   ├── utils.py
│   ├── requirements.txt
│   ├── users.db
│   └── screenshots/
│
├── Milestone_2/
│   ├── FreightQuote_AI_Milestone2.ipynb
│   ├── README.md
│   ├── auth.py
│   ├── db.py
│   ├── admin_dash.py
│   ├── ui_theme.py
│   ├── train_ml_freight.py
│   ├── llm_engine_freight.py
│   ├── requirements.txt
│   ├── users.db
│   └── screenshots/
│
└── Milestone_3/
    ├── FreightQuote_AI_M1_M2_Combined.ipynb
    ├── RAG_Pipeline.ipynb
    ├── README.md
    └── evaluation_queries.md
```

---

## Milestone 3 Workflow

1. Integrated Milestone 1 Authentication Module.
2. Integrated Milestone 2 AI and Machine Learning modules.
3. Developed a dedicated RAG Pipeline notebook.
4. Collected and organized logistics-related PDF documents.
5. Prepared the document knowledge base for semantic retrieval.
6. Configured the Retrieval-Augmented Generation workflow.
7. Organized the project structure and documentation.
8. Managed collaboration using GitHub branches and Pull Requests.

---

## Team Contribution

This project was completed collaboratively by a team of four members.

| Name | Role | Contribution |
|------|------|---------------|
| **Vigasini** | Milestone Integration | Integrated Milestone 1 and Milestone 2 into a single unified application; ensured seamless interaction between authentication, AI modules, analytics, and administrative functionalities; verified compatibility between all integrated components; organized the GitHub repository structure; managed GitHub branches, commits, and Pull Requests. |
| **Simran Kapoor** | RAG Pipeline Development | Developed a dedicated notebook for the Retrieval-Augmented Generation (RAG) pipeline; implemented document loading, embedding generation, vector storage, and semantic retrieval; integrated the retrieved context with the AI model for intelligent responses. |
| **Yuvanesh** | Knowledge Base Preparation | Collected logistics-related PDF documents and supporting reference materials; organized and maintained the project knowledge base; prepared documents for preprocessing and retrieval within the RAG pipeline. |
| **Tharani** | Documentation & Repository Management | Prepared comprehensive project documentation; created and maintained the README files; organized the GitHub repository structure; assisted in project organization and integration support; verified documentation consistency across milestones. |

---

## Future Enhancements

- Live Shipping APIs
- Real-Time Vessel Tracking
- Advanced Predictive Analytics
- Cloud Deployment
- Multi-Language AI Support
- Mobile Application
- Enterprise Reporting Dashboard

---

## GitHub Collaboration Workflow

The project followed a collaborative GitHub workflow. Each team member:

- Cloned the repository.
- Created an individual branch from the `main` branch.
- Completed their assigned Milestone 3 task.
- Committed and pushed their changes.
- Created a Pull Request.
- Had their changes reviewed and merged into `main` by the project maintainer.

This workflow ensured smooth collaboration, version control, and code quality throughout the project.

---

## Repository Guidelines

- Each contributor works on a separate Git branch.
- Changes are committed with meaningful commit messages.
- Pull Requests are created for all major updates.
- Code is reviewed before merging into the main branch.
- Documentation is updated whenever new features are added.
- Project structure is kept modular and easy to maintain.

---

## Project Highlights

- Enterprise AI-Powered Freight Management
- Secure Authentication System
- Multi-Agent AI Architecture
- Machine Learning-Based Freight Prediction
- Route & Weather Analysis
- Carrier Audit & Compliance Evaluation
- Analytics Dashboard
- AI Copilot using Large Language Models
- Retrieval-Augmented Generation (RAG)
- Document Knowledge Base
- GitHub Collaborative Development
- Professional Documentation

---

## References

- Infosys Springboard Internship Guidelines
- Hugging Face Documentation
- Streamlit Documentation
- Scikit-learn Documentation
- LangChain Documentation
- FAISS Documentation
- Python Documentation
- GitHub Documentation

---

## License

This project was developed for educational purposes as part of the **Infosys Springboard Internship Program**.

All rights belong to the respective project team members and Infosys Springboard.
