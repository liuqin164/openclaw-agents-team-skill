# Artifact-Driven Virtual Dev Team Skill  
# 基于文档驱动的虚拟开发团队 Skill

> A production-grade, artifact-driven virtual software development team  
> running on OpenClaw, designed for real-world product development.

---

## 🌍 Introduction | 项目简介

This Skill simulates a complete software development team composed of
specialized Agents (PM, Designer, Engineer, QA),
driven entirely by structured documents (Artifacts).

用户通过自然语言对话表达想法，  
系统自动生成、维护并推进标准化开发文档，  
实现 **“对话自由 + 流程可控”**。

---

## ✨ Key Highlights | 项目亮点

- 🧠 **Artifact-Driven Workflow**
  - All progress is anchored to documents, not chat history
  - Fully resumable after interruption or restart

- 🧑‍💼 **PM-Centric Interaction**
  - Single conversation entry point
  - Clear responsibility & decision authority

- 🔄 **Safe Pause & Resume**
  - Development can be paused and resumed at any time
  - No loss of progress, no repeated explanation

- 🔁 **Structured Change Management**
  - Natural language → ChangeRequest → PRD versioning
  - Directional change detection built-in

- 🧩 **Production-Ready SOP**
  - PRD Meta validation
  - Version traceability
  - Change auditability

---

## 🧱 Architecture Overview | 架构概览

User (Natural Language)
↓
PM Agent
↓
Structured Artifacts
(PRD / ChangeRequest / Backlog ...)
↓
Other Specialized Agents


---

## 🗂️ Core Artifacts | 核心文档

| Artifact | Purpose |
|-------|--------|
| PRD | Product requirement definition |
| ChangeRequest | Controlled requirement changes |
| Backlog | Task decomposition |
| Design Specs | UX / UI / API / DB |
| TestReport | QA validation |

---

## 🔄 Conversation State Model | 会话状态模型

The Skill maintains one of three states at all times:

- `active_dev` – development in progress
- `paused_dev` – development paused safely
- `closed_dev` – development completed

Development always resumes from the latest **Artifact Anchor**.

---

## 🧠 Change Handling | 需求变更机制

Users do NOT fill forms.

Instead:

1. User speaks naturally
2. PM detects potential change
3. System generates ChangeRequest (draft)
4. User confirms
5. Workflow continues safely

---

## 🚀 How to Use | 使用方式

### Step 1: Start with an idea
> “I want to build a product that ...”

### Step 2: Talk naturally
No templates. No forms.

### Step 3: Review generated PRD
Confirm or request changes.

### Step 4: Pause anytime
> “Let’s talk about something else.”

### Step 5: Resume later
> “Continue the previous project.”

---

## 📁 Repository Structure | 目录结构

```text
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
🔮 Optimization & Extensibility | 可扩展点
Multi-project parallel support

Automated regression detection

External system integration (Jira / GitHub)

Analytics on change patterns

🧠 Design Philosophy | 设计哲学
Users speak freely.
The system enforces structure.

Human-friendly on the surface,
machine-precise underneath.

📜 License
MIT License
