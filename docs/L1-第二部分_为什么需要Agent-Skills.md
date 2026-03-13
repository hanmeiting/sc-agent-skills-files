# 为什么需要 Agent Skills？—— 第二部分

## 幻灯片内容摘要

### 什么是 Agent Skills？

Agent Skills 是一种轻量级、开放格式，用于扩展 AI Agent 的能力。一个技能（Skill）是一个由有组织的文件组成的文件夹，包含指令、脚本、资产和资源，Agent 可以发现并使用它们来准确执行特定任务。

### 我们以往对 Agent 的理解

- 专用 Agent：研究 Agent、编程 Agent、金融 Agent、营销 Agent
- 每个 Agent 都有自己的窄领域、自己的架构和特定工具

### 新范式

- **通用 Agent** 使用代码作为通用接口
- 简单的架构：Bash 和文件系统
- 但它们需要**上下文和领域专业知识**才能可靠地完成工作
- Skills 提供程序性知识和公司/团队/用户特定的上下文，Agent 可以按需加载

### Skills 能实现什么

| 类别 | 示例 |
|------|------|
| **领域专业知识** | 品牌指南和模板、法律审查流程、数据分析方法 |
| **可重复的工作流程** | 每周营销活动审查、客户通话准备工作流、季度业务回顾 |
| **新能力** | 创建演示文稿、生成 Excel 表格或 PDF 报告、构建 MCP 服务器 |

### 没有 Skills 时

- 每次都要描述您的指令和需求
- 每次都要打包所有参考资料和支持文件
- 手动确保工作流程或输出始终保持一致

### Skills 的关键特征

1. **可移植性（Portable）：** 您可以在不同的支持 Skills 的 Agent 中重复使用相同的技能：
    - Claude Code
    - Claude.ai
    - Claude Agent SDK
    - Claude API

    Agent Skills 现在是一个**开放标准**，已被越来越多的 Agent 产品所采用。

2. **可组合性（Composable）：** Skills 可以组合构建复杂的工作流程。例如：
    - **公司品牌技能**：提供品牌指南（字体、颜色、Logo）
    - **PowerPoint 技能**：创建幻灯片演示文稿
    - **BigQuery 技能**：提供营销相关的数据库 Schema
    - **营销活动分析技能**：分析营销数据

### Skills 如何工作？—— 渐进式披露

Skills 可以包含大量信息，您可能拥有数百个技能。为了保护上下文窗口，Skills 采用**渐进式披露**方式：

| 层级 | 加载时机 |
|------|---------|
| **元数据**（YAML 前置内容：名称、描述） | 始终加载 |
| **指令**（SKILL.md 主体内容） | 触发时加载 |
| **资源**（参考文件、脚本） | 按需加载 |

### Skill 结构示例

根据 Agent Skills 规范：
- SKILL.md 是必须的
- 可选目录：references（参考文件）、scripts（脚本）和 assets（资产）

由于某些技能是在 Agent Skills 成为开放标准之前开发的，您会看到一些技能（例如下面的 PDF 技能）并不严格遵循标准格式。

```
analyzing-marketing-campaign/
├── SKILL.md
└── references/
    └── budget_reallocation_rules.md
```

```
pdf/
├── SKILL.md
├── forms.md
├── reference.md
└── scripts/
    ├── check_fillable_fields.py
    ├── convert_pdf_to_images.py
    ├── extract_form_field_info.py
    └── fill_pdf_form_with_annotations.py
```

```
designing-newsletters/
├── SKILL.md
├── references/
│   └── style-guide.md
└── assets/
    ├── header.png
    ├── icons/
    └── templates/
        ├── newsletter.html
        └── layout.docx
```

## 参考资料

- <a href="https://agentskills.io/what-are-skills" target="_blank">什么是 Skills？</a>
- <a href="https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview#how-skills-work" target="_blank">Skills 的工作原理</a>
- <a href="https://www.youtube.com/watch?v=CEvIs9y1uog" target="_blank">Barry Zhang & Mahesh Murag 在 AI Engineer's Fair 上的演讲</a>
