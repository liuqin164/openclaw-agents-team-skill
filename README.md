# Artifact-Driven Virtual Dev Team Skill

<p align="center">
  <a href="#english">English</a> | <a href="#chinese">简体中文</a>
</p>

---

<a name="english"></a>
## 🇺🇸 English Version

> A production-grade, artifact-driven virtual software development team running on OpenClaw, designed for real-world product development.

### 🌍 Introduction
This Skill simulates a complete software development team composed of specialized Agents (PM, Designer, Engineer, QA), driven entirely by structured documents (Artifacts).

### ✨ Key Highlights
- 🧠 **Artifact-Driven Workflow**: All progress is anchored to documents, not chat history. Fully resumable after interruption.
- 🧑‍💼 **PM-Centric Interaction**: Single conversation entry point; clear responsibility & decision authority.
- 🔄 **Safe Pause & Resume**: Development can be paused at any time without progress loss.
- 🔁 **Structured Change Management**: Natural language → ChangeRequest → PRD versioning.
- 🧩 **Production-Ready SOP**: PRD Meta validation and version traceability.

### 🔄 Conversation State Model
The Skill maintains one of three states:
- `active_dev` – development in progress
- `paused_dev` – development paused safely
- `closed_dev` – development completed
Development always resumes from the latest **Artifact Anchor**.

### 🧠 Change Handling
Users do NOT fill forms. Instead:
1. User speaks naturally.
2. PM detects potential change.
3. System generates ChangeRequest (draft).
4. User confirms; Workflow continues safely.

---

<a name="chinese"></a>
## 🇨🇳 简体中文版

> 一款基于 OpenClaw 运行的、生产级文档驱动型虚拟软件开发团队，专为真实产品开发而设计。

### 🌍 项目简介
本 Skill 模拟了一个由专业 Agent（产品经理、设计师、工程师、QA）组成的完整软件开发团队，完全由结构化文档（Artifacts）驱动。用户通过自然语言对话表达想法，系统自动生成、维护并推进标准化开发文档，实现 **“对话自由 + 流程可控”**。

### ✨ 项目亮点
- 🧠 **文档驱动工作流**：所有进度锚定在文档而非聊天记录，支持中断后完美恢复。
- 🧑‍💼 **以 PM 为中心**：单一对话入口，责任边界清晰，决策权威。
- 🔄 **安全暂停与恢复**：开发过程可随时暂停，无需重复解释背景。
- 🔁 **结构化变更管理**：自然语言意图自动转化为 ChangeRequest，支持 PRD 版本控制。
- 🧩 **生产级 SOP**：内置 PRD 元数据校验与版本追溯机制。

### 🔄 会话状态模型
Skill 始终维护以下状态之一：
- `active_dev`：开发进行中
- `paused_dev`：开发已安全暂停
- `closed_dev`：开发已完成
开发流程始终从最新的 **文档锚点 (Artifact Anchor)** 恢复。

### 🧠 需求变更机制
用户无需填写复杂表单。
1. 用户自然语言表达意图。
2. PM 自动识别潜在变更。
3. 系统生成变更请求 (ChangeRequest) 草案。
4. 用户确认后，流程安全继续。

---

## 🧱 Architecture Overview | 架构概览

```text
User (Natural Language)
        ↓
    PM Agent
        ↓
Structured Artifacts (PRD / ChangeRequest / Backlog ...)
        ↓
Other Specialized Agents

## 🗂️ Core Artifacts | 核心文档

| Artifact | Purpose |
|-------|--------|
| PRD | Product requirement definition |
| ChangeRequest | Controlled requirement changes |
| Backlog | Task decomposition |
| Design Specs | UX / UI / API / DB |
| TestReport | QA validation |
🚀 How to Use | 使用方式
Start with an idea: “I want to build a product that ...”

Talk naturally: No templates. No forms.

Review Artifacts: Confirm generated PRD or request changes.

Pause anytime: “Let’s talk about something else.”

Resume later: “Continue the previous project.”

📁 Repository Structure | 目录结构
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

🔮 Optimization | 可扩展点
并行多项目支持 (Multi-project parallel support)

自动化回归检测 (Automated regression detection)

外部系统集成 (Jira / GitHub integration)

🧠 Design Philosophy | 设计哲学
用户自由表达，系统强制规范。(Users speak freely. The system enforces structure.)

表面人性化，底层机器般精准。(Human-friendly on the surface, machine-precise underneath.)

📜 License
MIT License
