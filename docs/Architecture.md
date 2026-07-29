# Software Architecture

# ArgusAI

**An AI Operating System for Knowledge Work**

---

# 1. Introduction

This document defines the high-level architecture of Argus AI.

The platform is designed as a modular, domain-agnostic AI Operating System where reusable platform services remain independent from domain-specific intelligence modules.

Financial Research is the first supported domain, while future implementations may include Healthcare, Legal, Education, Cybersecurity, Compliance, Insurance, and Enterprise Knowledge Management.

---

# 2. Architecture Principles

Argus AI is designed around the following principles:

- Modular Architecture
- Separation of Concerns
- Scalability
- Extensibility
- Loose Coupling
- High Cohesion
- API First Design
- Domain Independence
- Explainable AI
- Security by Design

---

# 3. High-Level System Architecture

```
                    User
                      │
                      ▼
            Next.js Frontend
                      │
                      ▼
             FastAPI Backend
                      │
          ┌───────────┴────────────┐
          │                        │
          ▼                        ▼
 Authentication             AI Orchestrator
                                  │
                ┌─────────────────┼─────────────────┐
                ▼                 ▼                 ▼
         Document Agent    Research Agent    Finance Agent
                │                 │                 │
                └──────────┬──────┴───────┬─────────┘
                           ▼              ▼
                    RAG Engine       External APIs
                           │
              ┌────────────┴────────────┐
              ▼                         ▼
        Microsoft SQL Server      ChromaDB
```

---

# 4. Architecture Layers

The application is divided into independent layers.

## Presentation Layer

Responsibilities:

- User Interface
- Authentication Screens
- Chat Interface
- Workspace Dashboard
- Report Viewer

Technology

- Next.js
- React
- TypeScript
- Tailwind CSS

---

## API Layer

Responsibilities

- REST APIs
- Authentication
- Request Validation
- Response Serialization
- Error Handling

Technology

- FastAPI
- Pydantic

---

## Business Layer

Responsibilities

- Business Logic
- Workspace Management
- User Management
- Report Management
- Document Management

---

## AI Layer

Responsibilities

- Agent Orchestration
- Tool Calling
- Prompt Management
- Decision Making

Technology

- LangGraph
- LangChain

---

## Retrieval Layer

Responsibilities

- Document Retrieval
- Semantic Search
- Embedding Search
- Context Construction

Technology

- ChromaDB

---

## Database Layer

Responsibilities

- User Data
- Workspace Data
- Chat History
- Reports
- Metadata

Technology

- Microsoft SQL Server

---

# 5. AI Architecture

The AI system follows a Multi-Agent Architecture.

```
                  User Query
                       │
                       ▼
              LangGraph Orchestrator
                       │
      ┌────────────────┼─────────────────┐
      ▼                ▼                 ▼
Document Agent   Research Agent   Finance Agent
      ▼                ▼                 ▼
 Report Agent     News Agent      Risk Agent
                       │
                 Final Response
```

Each agent performs a single specialized responsibility.

---

# 6. AI Agents

## Orchestrator Agent

Responsibilities

- Understand user intent
- Decide execution plan
- Assign tasks
- Merge responses

---

## Document Agent

Responsibilities

- Read uploaded files
- Summarize documents
- Answer document questions

---

## Research Agent

Responsibilities

- Retrieve relevant information
- Search vector database
- Build research context

---

## Finance Agent

Responsibilities

- Analyze financial statements
- Compare companies
- Explain financial metrics

---

## News Agent

Responsibilities

- Retrieve market news
- Summarize developments
- Identify trends

---

## Report Agent

Responsibilities

- Generate professional reports
- Build executive summaries
- Export PDF

---

# 7. Retrieval-Augmented Generation (RAG)

The retrieval pipeline follows:

```
Upload Document
        │
        ▼
Text Extraction
        │
        ▼
Chunking
        │
        ▼
Embedding Generation
        │
        ▼
Store Embeddings
        │
        ▼
User Query
        │
        ▼
Semantic Search
        │
        ▼
Relevant Context
        │
        ▼
LLM
        │
        ▼
Final Response
```

---

# 8. Database Architecture

## Microsoft SQL Server

Stores:

- Users
- Workspaces
- Documents
- Chats
- Messages
- Reports
- Metadata
- Permissions
- Audit Logs

---

## ChromaDB

Stores:

- Embeddings
- Document Chunks
- Semantic Metadata

---

# 9. Workspace Architecture

Each workspace contains:

```
Workspace
│
├── Documents
├── Conversations
├── AI Reports
├── Notes
├── Bookmarks
└── Activity History
```

Future versions may include collaboration and task management.

---

# 10. Security Architecture

Security principles:

- JWT Authentication
- Password Hashing
- Secure File Upload
- Input Validation
- SQL Injection Protection
- XSS Protection
- CSRF Protection
- HTTPS
- Role-Based Access Control (Future)

---

# 11. External Integrations

Current

- LLM APIs
- Financial APIs
- News APIs

Future

- Bloomberg
- Alpha Vantage
- SEC EDGAR
- Yahoo Finance
- MCP Servers

---

# 12. Scalability Strategy

The architecture supports:

- Additional AI Agents
- Multiple Industries
- Cloud Deployment
- Microservices
- Distributed Vector Databases
- Enterprise Authentication
- Multi-Tenant SaaS

No architectural redesign should be required when expanding the platform.

---

# 13. Folder Architecture

```
ArgusAI/

backend/
    app/
    api/
    core/
    agents/
    rag/
    services/
    repositories/
    database/
    models/
    schemas/
    utils/
    tests/

frontend/

docs/

scripts/

storage/

logs/
```

---

# 14. Future Architecture

Argus AI is designed to become an AI Operating System rather than a single application.

Future domains include:

- Finance
- Healthcare
- Legal
- Education
- Cybersecurity
- Compliance
- Insurance
- Enterprise Knowledge Management

Each domain will extend the platform by introducing specialized AI agents and tools while sharing the same authentication, retrieval, workspace, and orchestration infrastructure.
