# Database Design

# Argus AI

## Tagline

**An AI Operating System for Knowledge Work**

---

# Version Information

| Field | Value |
|-------|-------|
| Project | Argus AI |
| Version | 1.0 |
| Database | Microsoft SQL Server |
| Vector Database | ChromaDB |

---

# 1. Overview

Argus AI uses a hybrid storage architecture.

Structured application data is stored in Microsoft SQL Server, while semantic vector embeddings are stored in ChromaDB.

This separation allows transactional data and semantic search data to evolve independently while providing efficient retrieval performance.

---

# 2. Database Architecture

```
                Argus AI

                   │
        ┌──────────┴──────────┐
        │                     │
        ▼                     ▼

 Microsoft SQL Server      ChromaDB

        │                     │

 Users                 Document Embeddings
 Workspaces            Chunk Embeddings
 Documents             Metadata
 Chats
 Messages
 Reports
```

---

# 3. SQL Server Responsibilities

SQL Server stores all structured application data including:

- Users
- Authentication data
- Workspaces
- Uploaded documents
- Chat sessions
- Chat messages
- Generated reports

---

# 4. ChromaDB Responsibilities

ChromaDB stores:

- Document embeddings
- Chunk embeddings
- Semantic metadata

Only embeddings are stored in ChromaDB.

Business data always remains inside SQL Server.

---

# 5. Entity Relationship Overview

```
User
 │
 ├───────────┐
 │           │
 ▼           ▼

Workspace    Report

 │
 ├───────────────┐
 │               │
 ▼               ▼

Document      Chat

                 │
                 ▼

             Message
```

---

# 6. Tables

## Users

Stores registered users.

Columns

- id (UUID)
- full_name
- email
- password_hash
- created_at
- updated_at

Primary Key

- id

Unique

- email

---

## Workspaces

Stores user projects.

Columns

- id (UUID)
- user_id
- name
- description
- created_at
- updated_at

Relationship

Many Workspaces belong to one User.

---

## Documents

Stores uploaded document metadata.

Columns

- id (UUID)
- workspace_id
- filename
- original_filename
- file_type
- file_size
- storage_path
- upload_time
- processing_status

Relationship

Many Documents belong to one Workspace.

---

## Chats

Represents a conversation.

Columns

- id (UUID)
- workspace_id
- title
- created_at
- updated_at

Relationship

Many Chats belong to one Workspace.

---

## Messages

Stores every conversation message.

Columns

- id (UUID)
- chat_id
- sender
- message
- created_at

Relationship

Many Messages belong to one Chat.

---

## Reports

Stores AI-generated reports.

Columns

- id (UUID)
- workspace_id
- title
- report_type
- content
- created_at

Relationship

Many Reports belong to one Workspace.

---

# 7. Relationships

User

↓

Workspaces

↓

Documents

↓

Chats

↓

Messages

↓

Reports

The database follows a normalized relational design.

---

# 8. Indexing Strategy

Indexes will be created on:

Users

- Email

Workspaces

- User ID

Documents

- Workspace ID

Chats

- Workspace ID

Messages

- Chat ID

Reports

- Workspace ID

These indexes improve lookup performance.

---

# 9. File Storage Strategy

Uploaded files are **not stored directly inside SQL Server**.

Instead:

```
storage/

documents/

<workspace-id>/

annual_report.pdf

balance_sheet.pdf

contract.pdf
```

The database stores only:

- filename
- path
- metadata

This improves database performance and simplifies backup strategies.

---

# 10. ChromaDB Mapping

Each uploaded document is processed into chunks.

Each chunk contains:

- chunk_id
- document_id
- workspace_id
- embedding
- chunk_text
- metadata

This enables semantic retrieval while preserving the relationship to the original document.

---

# 11. Data Flow

Document Upload

↓

Save file to storage

↓

Store metadata in SQL Server

↓

Extract text

↓

Chunk document

↓

Generate embeddings

↓

Store embeddings in ChromaDB

↓

Document becomes searchable

---

# 12. Future Extensions

Future versions may introduce additional tables for:

- Teams
- Organization
- User Roles
- Shared Workspaces
- Notifications
- Audit Logs
- Tasks
- Bookmarks
- API Keys
- Plugin Configuration

These features are intentionally excluded from Version 1.

---

# 13. Design Principles

The database design follows these principles:

- Third Normal Form (3NF)
- Referential Integrity
- UUID-based Primary Keys
- Separation of Structured and Vector Data
- Scalable Workspace-Centric Design
- Extensible Schema
- Secure Storage of Credentials
- Minimal Data Duplication