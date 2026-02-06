# Artifact-Driven Virtual Dev Team Skill / 基于文档驱动的虚拟开发团队 Skill

<p align="center">
  <b>A production-grade, artifact-driven virtual software development team running on OpenClaw.</b><br>
  一款运行在 OpenClaw 上的生产级、文档驱动型虚拟软件开发团队 Skill。
</p>

<p align="center">
  <a href="#-english-version">English</a> •
  <a href="#-中文版">简体中文</a> •
  <a href="#-repository-structure--目录结构">Structure</a> •
  <a href="#-license">License</a>
</p>

---

## 🇺🇸 English Version

### 🌍 Introduction
This Skill simulates a complete software development team composed of specialized Agents (PM, Designer, Engineer, QA), driven entirely by structured documents (**Artifacts**). Users express ideas via natural language, and the system automatically generates and maintains standardized development documents to ensure the process remains controllable and traceable.

### ✨ Key Highlights
- 🧠 **Artifact-Driven Workflow**: All progress is anchored to documents, not chat history.
- 🧑‍💼 **PM-Centric Interaction**: Single conversation entry point with clear responsibility.
- 🔄 **Safe Pause & Resume**: Development can be paused anytime without progress loss.
- 🔁 **Structured Change Management**: Natural language → ChangeRequest → PRD versioning.

### 🔄 Conversation State Model
The Skill maintains one of three states:
- `active_dev`: Development in progress.
- `paused_dev`: Development paused safely.
- `closed_dev`: Development completed.

---

## 🇨🇳 中文版

### 🌍 项目简介
本 Skill 在 OpenClaw 环境下模拟了一个完整的软件开发团队（包含 PM、设计师、工程师、QA），完全由结构化文档（**Artifacts**）驱动。用户通过自然语言表达想法，系统自动生成、维护并推进标准化开发文档，实现“对话自由 + 流程可控”。

### ✨ 项目亮点
- 🧠 **文档驱动工作流**：所有进度锚定在文档而非聊天记录，支持中断后完美恢复。
- 🧑‍💼 **以 PM 为中心的交互**：单一对话入口，责任边界清晰，决策权威。
- 🔄 **安全暂停与恢复**：开发可随时暂停，无需重复解释背景。
- 🔁 **结构化变更管理**：自然语言意图自动转化为 ChangeRequest，支持 PRD 版本控制。

### 🔄 会话状态模型
Skill 始终维护以下状态之一：
- `active_dev`：开发进行中。
- `paused_dev`：开发已安全暂停。
- `closed_dev`：开发已完成。

---

## 🏗️ Architecture Overview | 架构概览



```text
User (Natural Language) 
      ↓
   PM Agent 
      ↓
Structured Artifacts (PRD / ChangeRequest / Backlog ...)
      ↓
Other Specialized Agents (Architect / Dev / QA)
🗂️ Core Artifacts | 核心文档ArtifactPurpose作用PRDProduct requirement definition产品需求定义ChangeRequestControlled requirement changes受控的需求变更申请BacklogTask decomposition任务拆解清单Design SpecsUX / UI / API / DB设计规范 (UI/API/数据库)TestReportQA validationQA 验收报告📁 Repository Structure | 目录结构Plaintext.
├── agents/              # Role definitions (YAML)
├── artifacts.yaml       # Artifact relationship definitions
├── registry.yaml        # Orchestration & Scheduler rules
├── docs/                # Internal SOPs and templates
├── templates/           # PRD & ChangeRequest templates
└── README.md            # This document
🚀 How to Use | 使用方式Start with an idea: "I want to build a product that..."Talk naturally: No templates or forms required.Review Artifacts: Confirm the generated PRD or request changes.Pause & Resume: Simply say "Pause" or "Continue previous project".📜 LicenseLicensed under the MIT License.
