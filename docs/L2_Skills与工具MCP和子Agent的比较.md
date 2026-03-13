# Skills vs 工具、MCP 与子 Agent

## 幻灯片内容摘要

### Skills vs MCP

| 特征 | MCP | Skills |
|------|-----|--------|
| **用途** | 将您的 Agent 连接到外部系统和数据（数据库、API、服务） | 教会您的 Agent 如何处理这些数据 |
| **示例** | MCP 服务器连接到数据库 | 技能说明"使用此表中的 A 列和 B 列计算指标 X" |

MCP 提供*访问权限*，Skills 提供*专业知识*。


### Skills vs 工具（Tools）

| 特征 | 工具（Tools） | Skills |
|------|--------------|--------|
| **用途** | 为 Agent 提供完成任务所需的基本能力 | 用专业知识扩展 Agent 的能力 |
| **上下文** | 工具定义（名称、描述、参数）始终存在于上下文窗口中 | Skills 按需动态加载 |
| **灵活性** | 固定的能力集 | Skills 可以包含脚本作为按需使用的工具（"按需工具"） |



### Skills vs 子 Agent（Subagents）

| 特征 | 子 Agent（Subagents） | Skills |
|------|---------------------|--------|
| **用途** | 拥有自己独立的上下文和工具权限 | 为主 Agent 或其任何子 Agent 提供专业知识 |
| **运作方式** | 主 Agent 将任务委托给专用子 Agent，子 Agent 独立（并可能并行）工作并返回结果 | Skills 告知工作应如何完成 |
| **示例** | 代码审查子 Agent | 特定语言或框架的最佳实践技能 |

Skills 可以为主 Agent **和**其子 Agent 提供专业知识增强。



### 综合运用

**示例：客户洞察分析器**

| 组件 | 角色 |
|------|------|
| **Skill** | 关于如何分类反馈以及如何总结结论的指南 |
| **MCP 服务器** | Google Drive MCP 服务器，访问包含客户访谈记录和调查回复的 Drive 文件夹 |
| **子 Agent** | 访谈分析器、调查分析器 |



## 参考资料
* <a href="https://www.claude.com/blog/skills-explained" target="_blank">Skills 详解</a>
* <a href="https://support.claude.com/en/articles/12580051-teach-claude-your-way-of-working-using-skills" target="_blank">使用 Skills 教会 Claude 您的工作方式</a>
