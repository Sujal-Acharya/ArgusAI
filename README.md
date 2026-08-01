# Argus AI

> **An AI Operating System for Knowledge Work**

Argus AI is a modular, enterprise-grade AI platform designed to help professionals organize, retrieve, analyze, and generate knowledge from structured and unstructured data.

The first implementation focuses on **Financial Research**, while the core architecture is designed to support future domain packs such as Healthcare, Legal, Education, Cybersecurity, Compliance, and Enterprise Knowledge Management.

---

## Vision

Argus AI aims to become a reusable AI platform where domain-specific intelligence is built on top of a common foundation consisting of:

- Workspace Management
- Document Intelligence
- Retrieval-Augmented Generation (RAG)
- Multi-Agent Orchestration
- AI Chat
- Report Generation
- Semantic Search

Instead of building isolated AI applications for each industry, Argus AI provides a common platform that can be extended through specialized AI agents and tools.

---

# Key Features

## Version 1 (MVP)

- User Authentication
- Workspace Management
- AI Chat
- Document Upload
- PDF & Office Document Processing
- Retrieval-Augmented Generation (RAG)
- Multi-Agent AI Workflow
- Financial Research Assistant
- AI Report Generation
- Chat History

---

# Planned Future Features

- Healthcare Intelligence
- Legal Intelligence
- Cybersecurity Intelligence
- Education Assistant
- OCR
- Voice Interaction
- Knowledge Graph
- Team Collaboration
- Plugin Marketplace
- MCP Integration

---

# System Architecture

```
User
        │
        ▼
 Next.js Frontend
        │
        ▼
 FastAPI Backend
        │
        ▼
 LangGraph Orchestrator
        │
 ┌──────┼────────┐
 │      │        │
 ▼      ▼        ▼

Research  Finance  Document
 Agent     Agent     Agent

        │
        ▼

     RAG Engine
        │
 ┌──────┴─────────┐
 ▼                ▼

SQL Server     ChromaDB
```

---

# Tech Stack

## Frontend

- Next.js
- React
- TypeScript
- Tailwind CSS
- Axios
- React Query

---

## Backend

- FastAPI
- Python
- SQLAlchemy
- Alembic
- Pydantic

---

## AI Stack

- LangGraph
- LangChain
- ChromaDB
- OpenAI / Gemini APIs
- Retrieval-Augmented Generation (RAG)

---

## Database

- Microsoft SQL Server
- ChromaDB

---

## DevOps

- Git
- GitHub
- Docker *(planned)*
- GitHub Actions *(planned)*

---

# Project Structure

```
ArgusAI/

backend/
frontend/
docs/
storage/
logs/
scripts/

README.md
LICENSE
.gitignore
```

---

# Documentation

The project follows a documentation-first software engineering approach.

- Product Vision
- Product Requirements Document (PRD)
- Software Requirements Specification (SRS)
- Software Architecture
- Database Design
- Development Roadmap

All project documentation is available inside the `docs/` directory.

---

# Development Roadmap

- ✅ Product Vision
- ✅ Product Requirements Document
- ✅ Software Requirements Specification
- ✅ Software Architecture
- ✅ Database Design
- ✅ Development Roadmap

### Current Phase

🚀 Project Setup

---

# Repository Workflow

This project follows a professional Git workflow.

- Feature Branches
- Pull Requests
- Conventional Commits
- Incremental Development
- Documentation-Driven Design

---

# License

This project is licensed under the MIT License.

---

# Author

**Sujal Acharya**

Computer Science Engineer (Data Science)

Building production-grade AI systems with modern software engineering practices.

---

> **Argus AI is being developed as a portfolio-quality software engineering project with a focus on scalable architecture, clean code, modular AI design, and enterprise development practices.**
