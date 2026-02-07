
<p align="right">
  <b>🇨🇳 简体中文</b> | <a href="README.md">🇺🇸 English</a>
</p>

# 基于文档驱动的虚拟开发团队 Skill

![版本](https://img.shields.io/badge/version-1.0.5-blue)
![许可证](https://img.shields.io/badge/license-MIT-green)

## 目录

- [项目简介](#项目简介)
- [功能特色](#功能特色)
- [安装与配置](#安装与配置)
- [核心概念](#核心概念)
- [工作流程](#工作流程)
- [目录结构](#目录结构)
- [Agents 介绍](#agents-介绍)
- [Artifacts 说明](#artifacts-说明)
- [Hook 自动化功能](#hook-自动化功能)
- [开发与扩展](#开发与扩展)
- [使用示例](#使用示例)
- [兼容性](#兼容性)
- [许可证](#许可证)
- [FAQ](#faq)

---

## 项目简介

`OpenClaw Dev Team` 是一个 **文档驱动、可复用的虚拟软件开发团队 Skill**，通过结构化 Agent 和 Artifact，覆盖从需求产生到 QA 验收的完整流程。  

主要特点：

- **PM 理解用户需求 → 自动创建项目目录**  
- **PRD 输出 → 自动写入文件夹 → README 占位符更新**  
- **支持多版本 PRD 管理与变更处理**  
- **全程日志记录和目录管理自动化**  

---

## 功能特色

1. **端到端虚拟开发团队支持**：PM、PJM、UX/UI 设计、架构师、前端/后端、QA  
2. **文档驱动流程**：所有需求和 PRD 都通过 Artifact 管理，可追溯  
3. **智能项目初始化**：自动创建 `$HOME/openclaw_workspace/project-{ProjectName}` 目录  
4. **PRD 与目录无缝衔接**：PRD 输出后自动写入项目目录，更新 README 占位符  
5. **智能变更处理**：小版本（v1.x）和主版本（v2.0）区分需求扩展和方向性变更  
6. **可配置运行环境**：domain_context / language / tone  

---

## 安装与配置

```bash
# 克隆仓库
git clone https://github.com/<your-username>/openclaw-agents-team-skill.git
cd openclaw-agents-team-skill

# 安装 OpenClaw >=0.5.0
pip install openclaw>=0.5.0

# 可选：自定义工作目录
export OPENCLAW_WORKSPACE=~/openclaw_workspace
````

> 默认工作目录为 `~/openclaw_workspace`，用于存放自动创建的项目文件夹和日志。

---

## 核心概念

* **Agent**：虚拟团队成员，每个角色有明确输入/输出 Artifact
* **Artifact**：文档或数据单元，如 `PRD`、`RawIdea`、`ChangeRequest`
* **Workflow Hooks**：自动化脚本，在特定阶段执行操作
* **Meta 区块**：PRD 文档首个章节，包含 Project Name、版本、作者等信息

---

## 工作流程

    用户提交需求
        |
        v
   PM 生成 PRD
        |
        v
   Before Hook: 创建项目文件夹 + README
        |
        v
    After Hook: 写入 PRD + 更新 README
        |
        v
   UX/UI/前后端/QA:执行开发与验收


**说明**：

1. 用户提交 **RawIdea / ChangeRequest**
2. PM Agent 生成 PRD（包含 Meta 区块）
3. Before Hook 自动创建项目文件夹和 README.md
4. After Hook 写入 PRD 并更新 README 占位符
5. 后续团队 Agent 基于 Artifact 执行开发和验收

---

## 目录结构（示例）

```text
openclaw-agents-team-skill/
├─ agents/
│  ├─ architect.yaml
│  ├─ backend.yaml
│  ├─ frontend.yaml
│  ├─ pjm.yaml
│  ├─ pm.yaml
│  ├─ qa.yaml
│  ├─ ui.yaml
│  └─ ux.yaml
├─ docs/
│  ├─ pm_conversation_templates.md
│  └─ pm_internal_sop.md
├─ examples/
│  ├─ basic_run.md
│  └─ custom_agent_override.md
├─ LICENSE
├─ README.md
├─ README_zh.md
├─ artifacts.yaml
├─ registry.yaml
├─ skill.yaml
├─ system_prompt.md
└─ $OPENCLAW_WORKSPACE/
    └─ project-{ProjectName}/
        ├─ README.md       # 自动生成，包含 PRD 占位符
        └─ project_prd.md  # PRD 文件
```

---

## Agents 介绍

| Agent            | 职责                 |
| ---------------- | ------------------ |
| PM               | 产品经理，生成 PRD，处理需求变更 |
| PJM              | 项目经理，协调开发进度        |
| UXDesigner       | 用户体验设计，生成原型与用户流程   |
| UIDesigner       | UI 设计师，生成界面设计      |
| Architect        | 系统架构设计             |
| BackendEngineer  | 后端开发               |
| FrontendEngineer | 前端开发               |
| QA               | 测试与验收              |

---

## Artifacts 说明

| Artifact      | 描述                          |
| ------------- | --------------------------- |
| RawIdea       | 用户原始想法或需求                   |
| ChangeRequest | 用户需求变更请求                    |
| PRD           | 产品需求文档（Markdown），包含 Meta 区块 |
| README.md     | 项目说明文件，自动生成，占位符包含 PRD 文件路径  |

---

## Hook 自动化功能

* **Before Stage Hook (PM)**：自动创建项目文件夹、生成 README、记录日志
* **After Stage Hook (PM)**：写入 PRD 文件、更新 README 占位符

---

## 开发与扩展

1. 自定义 Agent：在 `agents/` 文件夹添加 YAML
2. 扩展 Artifact 类型或增加 Hook 脚本
3. agent_policy 支持 full_replace / partial_extend

---

## 使用示例

Skill 激活名：`devteam`。

### 示例 1：Basic Run

```yaml
RawIdea:
  title: "自动化 PRD 生成演示"
  description: "系统自动生成 PRD 并创建项目文件夹，生成 README 占位符"
```

运行：

```bash
openclaw run skill devteam --input RawIdea.yaml
```

结果：

```
$HOME/openclaw_workspace/project-自动化_PRD_生成演示/
├─ README.md
└─ project_prd.md
```

---

### 示例 2：自定义 PM Agent

在 `agents/pm_custom.yaml`:

```yaml
role: Product Manager
stage: Planning
input:
  - RawIdea
output:
  - PRD
prompt: |
  你是自定义 PM Agent。
  输出 PRD，调用 Hook 创建项目文件夹，输出必须包含 Meta 区块。
```

运行：

```bash
openclaw run skill devteam --override agents/pm_custom.yaml --input RawIdea.yaml
```


## 兼容性

* OpenClaw >= 0.5.0
* 支持平台：Local / Cloud / Embedded

---

## 许可证

MIT License. 详情请参见 [LICENSE](LICENSE)。

---

## FAQ

**Q1:** 可以自定义项目文件夹位置吗？

> 可通过环境变量 `OPENCLAW_WORKSPACE` 自定义。

**Q2:** PRD Meta 中 Project Name 与 RawIdea.title 不一致怎么办？

> Hook 优先使用 PRD Meta 中 Project Name，RawIdea.title 仅作 fallback。

**Q3:** 支持多人并行生成 PRD 吗？

> 支持，workflow_policy.allow_parallel_execution: true。

**Q4:** 如何处理 ChangeRequest？

> PM 根据 SOP 判断生成小版本（v1.x）或主版本（v2.0），hook 自动写入新文件。

```
