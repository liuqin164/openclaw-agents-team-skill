# 基于文档驱动的虚拟开发团队 Skill

<p align="right">
  <b>🇨🇳 简体中文</b> | <a href="README.md">🇺🇸 English</a>
</p>

> 一款基于 OpenClaw 运行的、生产级文档驱动型虚拟软件开发团队...
> **文档驱动（Artifact-driven）虚拟软件开发团队 Skill**

---

## 🌟 项目简介

本 Skill 模拟了一支完整的软件研发团队，由多个专业 Agent 组成：

- 产品经理（PM）
- 设计师（UX / UI）
- 架构师
- 前端 / 后端工程师
- 测试工程师（QA）

用户只需通过**自然语言对话**表达需求，  
系统会自动生成并推进 **标准化开发文档（Artifacts）**，  
在保证体验自然的同时，确保流程**可控、可恢复、可审计**。

---

## ✨ 核心亮点

### 🧠 Artifact-Driven（文档驱动，而非对话驱动）

- 所有进度都锚定在结构化文档上，而不是聊天记录
- 支持中断、重启、恢复，不丢状态

### 🧑‍💼 PM 单入口设计

- 所有用户对话统一由 PM Agent 承接
- 决策权集中，避免多 Agent 混乱判断

### 🔄 安全暂停 / 恢复开发

- 开发可随时暂停（safe pause）
- 可从最近的 Artifact 锚点继续，而非从头再来

### 🔁 需求变更可控

- 用户无需填写表单
- 自然语言 → ChangeRequest → PRD 新版本
- 内置「方向性变更判断 SOP」

### 📄 生产级 SOP

- PRD Meta 强校验
- 版本继承关系清晰
- 变更来源可追溯

---

## 🧱 系统架构概览

```text
用户（自然语言）
        ↓
     PM Agent
        ↓
   标准化 Artifact
(PRD / ChangeRequest / Backlog ...)
        ↓
  其他专业 Agent


🗂️ 核心 Artifacts
| Artifact      | 说明                    |
| ------------- | --------------------- |
| PRD           | 产品需求文档（带 Meta 校验）     |
| ChangeRequest | 需求变更请求（系统自动生成）        |
| Backlog       | 任务拆解清单                |
| Design Specs  | UX / UI / API / DB 设计 |
| TestReport    | 测试与验收结果               |


🔄 会话状态模型
Skill 在运行中始终维护以下三种状态之一：

active_dev：正在开发
paused_dev：开发已暂停（安全）
closed_dev：当前开发已结束

开发锚点（Development Anchor）
开发进度始终绑定到最近的一个稳定 Artifact，例如：

已批准的 PRD

草稿状态的 PRD

待确认的 ChangeRequest

这是恢复开发的唯一依据。

🧠 需求变更机制
用户不需要填写 ChangeRequest。

系统流程如下：

用户自然语言提出修改想法

PM 识别为潜在需求变更

系统自动生成 ChangeRequest（draft）

用户确认

触发 PRD 新版本或拒绝变更

🚀 使用方式
1️⃣ 提出想法
“我想做一个可以记录个人习惯的应用。”

2️⃣ 正常聊天
无需模板、无需表单。

3️⃣ 查看生成的 PRD
确认或提出修改意见。

4️⃣ 随时暂停
“我们先聊点别的。”

5️⃣ 随时恢复
“继续刚才那个项目。”

📁 推荐目录结构
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
🔮 可扩展方向
多项目并行支持

外部系统集成（Jira / GitHub）

变更频率与方向分析

自动回归测试触发

🧠 设计哲学
用户只管说人话，
系统负责守住结构。

表面自由，对内严谨。

📜 License
MIT License
