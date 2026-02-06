
<p align="right">
  <a href="README_zh.md">🇨🇳 简体中文</a> | <b>🇺🇸 English</b>
</p>

# Artifact-Driven Virtual Development Team Skill

> A production-ready virtual software development team  
> running on OpenClaw, powered by artifact-driven workflows.

---

## 🌍 Introduction

This Skill simulates a complete software development team composed of
specialized Agents, including:

- Product Manager (PM)
- UX / UI Designers
- Architect
- Frontend & Backend Engineers
- QA Engineer

Users communicate purely through **natural language**.
The system transforms conversations into **structured development artifacts**,
ensuring that development is controllable, resumable, and auditable.

---

## ✨ Key Features

### 🧠 Artifact-Driven, Not Chat-Driven

- Progress is anchored to documents, not chat history
- Fully resumable after interruption or restart

### 🧑‍💼 PM-Centric Interaction

- Single conversational entry point
- Clear authority and responsibility

### 🔄 Safe Pause & Resume

- Development can be paused at any time
- Resume from the latest artifact anchor

### 🔁 Controlled Change Management

- No forms required for users
- Natural language → ChangeRequest → PRD versioning
- Built-in directional change detection SOP

### 📄 Production-Grade SOP

- PRD Meta validation
- Clear version lineage
- Auditable change history

---

## 🧱 Architecture Overview

```text
User (Natural Language)
        ↓
     PM Agent
        ↓
   Structured Artifacts
(PRD / ChangeRequest / Backlog ...)
        ↓
 Other Specialized Agents

🗂️ Core Artifacts
| Artifact      | Description                                       |
| ------------- | ------------------------------------------------- |
| PRD           | Product Requirement Document with Meta validation |
| ChangeRequest | Controlled requirement change                     |
| Backlog       | Task decomposition                                |
| Design Specs  | UX / UI / API / DB                                |
| TestReport    | QA and acceptance results                         |


🔄 Conversation State Model

The Skill always maintains one of three states:

active_dev – development in progress

paused_dev – development safely paused

closed_dev – development completed

Development Anchor

Progress is always tied to the most recent stable artifact, such as:

Approved PRD

Draft PRD

Pending ChangeRequest

This artifact is the single source of truth for resuming work.

🧠 Change Handling

Users never fill out ChangeRequest forms.

Workflow:

User speaks naturally

PM detects potential change

System generates ChangeRequest (draft)

User confirms

New PRD version is created if needed

🚀 How to Use
Step 1: Start with an idea

“I want to build an app that helps people track habits.”

Step 2: Talk naturally

No templates. No forms.

Step 3: Review generated PRD

Confirm or request changes.

Step 4: Pause anytime

“Let’s talk about something else.”

Step 5: Resume anytime

“Continue the previous project.”

📁 Recommended Repository Structure
.
├── agents/
│   ├── pm.yaml
│   └── ...
├── artifacts.yaml
├── registry.yaml
├── docs/
│   ├── pm_internal_sop.md
│   └── pm_conversation_templates.md
├── templates/
│   ├── PRD_TEMPLATE.md
│   └── ChangeRequest.md
└── README.md

🔮 Future Improvements

Multi-project parallel execution

External integrations (Jira / GitHub)

Change pattern analytics

Automated regression workflows

🧠 Design Philosophy

Users speak freely.
The system enforces structure.

Human-friendly on the surface,
machine-precise underneath.

📜 License

MIT License
