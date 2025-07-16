# 📝 Product Requirements Document (PRD)

**Title**: OneLake CLI Tool  
**Author**: Sruly Taber  
**Date**: 2025-07-15  
**Status**: Final  
**Stakeholders**: Fabric Engineering, OneLake Platform Team, DataOps, Governance, PM

---

## 🎯 Overview

The OneLake CLI is a command-line interface designed to enable users to discover and manage data assets in Microsoft Fabric's OneLake. It focuses on metadata inspection, file and table management, and automation—not querying or data transformation.

---

## 🧩 Problem Statement

Users lack a lightweight, scriptable interface to explore and manage OneLake contents. Current tools (e.g., notebooks, SQL clients) are optimized for querying, not for metadata discovery, automation, or DevOps workflows.

---

## 🎯 Goals

- Enable secure, authenticated access to OneLake.
- Provide intuitive commands for navigating files, folders, and delta tables.
- Support metadata inspection and lightweight management operations.
- Facilitate scripting and automation via structured output.

---

## 🚫 Non-Goals

- Executing SQL queries or running notebooks.
- Performing data transformations or analytics.

---

## 🧠 Assumptions

- Users have access to Microsoft Fabric and OneLake.
- OneLake APIs and delta table metadata endpoints are available.
- Authentication is handled via Microsoft Entra ID.

---

## 🧪 Success Metrics

- CLI adoption by internal Fabric teams.
- Reduction in time to discover and inspect tables.
- Number of automation scripts using the CLI.
- Positive feedback from early adopters.

---

## 🧱 Functional Requirements

### 🥇 High Priority

#### 1. Authentication
- `login`, `logout`, `whoami`
- Authenticate via Microsoft Entra ID.
- Store session token securely in memory or encrypted config.

#### 2. Configuration Management
- `config set/get`
- Manage default workspace, lakehouse, output format (json/yaml/table).

#### 3. Navigation & Discovery
- `ls`, `tree`
- List files, folders, and tables in a workspace/lakehouse.
- Support recursive and non-recursive modes.

#### 4. Table Management
- `tables list`
- `tables describe <table>`
- Show schema, partitioning, properties, and delta metadata.

#### 5. Workspace & Lakehouse Management
- `workspaces list`
- `lakehouses list`
- `lakehouses describe`
- Show metadata and contents.

#### 6. Structured Output
- `--json`, `--yaml`, `--table`
- Enable integration with scripts and automation tools.

---

### 🥈 Medium Priority

#### 7. File Operations
- `files upload/download`
- `files rm/mv/cp`
- `files stat`
- Manage files and folders in OneLake.

#### 8. Delta Table Utilities
- `tables history <table>`
- Show delta log commit history and operations.

#### 9. Search
- `search <query>`
- Search for files or tables by name, tag, or metadata.

#### 10. Data Preview
- `preview <table>`
- `sample <file>`
- Show first N rows of a table or lines of a file (non-query).

#### 11. Export & Integration
- `export schema <table>`
- Export schema to JSON or Avro.
- `generate notebook <table>`
- Generate a Fabric notebook stub.

---

### 🥉 Low Priority

#### 13. Delta Internals
- `delta inspect <table>`
- `delta diff <version1> <version2>`
- Inspect delta log files and compare versions.

#### 14. Interactive Shell
- `onelake shell`
- Launch an interactive CLI session with autocomplete.

---

## 🛠 Non-Functional Requirements

- **Cross-platform**: Windows, macOS, Linux.
- **Extensible**: Modular command architecture.
- **Secure**: Token-based auth, no plaintext credentials.
- **Performant**: Fast metadata access and file listing.
- **User-friendly**: Helpful errors, `--help` on all commands.

---

## 🗺 Roadmap

### Phase 1: MVP
- Authentication
- Navigation & discovery
- Table metadata
- Workspace/lakehouse listing
- Config management

### Phase 2: File & Metadata Management
- File operations
- Metadata and tagging
- Delta table history

### Phase 3: Advanced Features
- Search
- Schema export
- Notebook generation
- Delta inspection
- Interactive shell

---
