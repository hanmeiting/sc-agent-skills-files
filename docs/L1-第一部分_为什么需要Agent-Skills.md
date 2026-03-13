# 为什么需要 Agent Skills？—— 第一部分

## 课程文件

**初始对话：** 以下是初始对话中使用的提示词和文件：

- <a href="https://github.com/https-deeplearning-ai/sc-agent-skills-files/tree/main/L1-partI/prompts_initial_conversation.md" target="_blank">提示词</a>
- <a href="https://github.com/https-deeplearning-ai/sc-agent-skills-files/tree/main/L1-partI/campaign_data_week1.csv" target="_blank">CSV 文件</a>
- <a href="https://github.com/https-deeplearning-ai/sc-agent-skills-files/tree/main/L1-partI/budget_reallocation_rules.md" target="_blank">预算重新分配规则</a>

**Skill 文件：** 您可以在 <a href="https://github.com/https-deeplearning-ai/sc-agent-skills-files/tree/main/L1-partI/skill/analyzing-marketing-campaign/" target="_blank">这里</a> 找到 `analyzing-marketing-campaign`（营销活动分析）技能的文件。

**上传技能后的对话：**
- <a href="https://github.com/https-deeplearning-ai/sc-agent-skills-files/tree/main/L1-partI/prompts_with_skills.md" target="_blank">提示词</a>
- <a href="https://github.com/https-deeplearning-ai/sc-agent-skills-files/tree/main/L1-partI/campaign_data_week1.csv" target="_blank">CSV 文件</a>
- <a href="https://github.com/https-deeplearning-ai/sc-agent-skills-files/tree/main/L1-partI/output_report_example/Marketing_Campaign_Report_Dec9-15.xlsx" target="_blank">拍摄期间生成的 Excel 报告</a>


## 如何尝试 Skills？

如果您没有 Claude 订阅，仍然可以使用免费计划在 Claude.ai 中体验技能（支持 Sonnet 4.5 或 Haiku 4.5）。自 1 月 26 日起，Skills 已对 Claude.ai 免费用户开放。

由于 Skills 是一个开放标准，您也可以在任何其他支持 Skills 的 AI 应用程序中尝试。您可以在 <a href="https://agentskills.io/home#adoption" target="_blank">这里</a> 找到支持平台的列表。

## 如何扩展 `analyzing-marketing-campaign` 技能？

您可以添加：
- 一个关于如何分析和修复数据质量问题的参考文件
- 一个包含您可能感兴趣的所有营销指标的参考文件
- 可以用数据进行的额外分析
- 未提供 CSV 时从数据库查询数据的说明

我们也邀请您思考自己的工作流程：
- 是否有一些您反复要求 Agent 遵循的指令？
- 您能否将它们整合成一个技能？
- 是否有一些特定的指导方针，希望您的 Agent 在特定任务中始终遵循？

**注意：** 本课程中展示的所有技能均用于教育目的。每个展示的技能都有改进和迭代的空间。

## 参考资料

* <a href="https://agentskills.io/home" target="_blank">Agent Skills 官网</a>
* <a href="https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview" target="_blank">Agent Skills Anthropic 文档</a>
* <a href="https://claude.com/blog/skills" target="_blank">博客：介绍 Agent Skills</a>

## Anthropic 课程
* <a href="https://anthropic.skilljar.com/introduction-to-agent-skills" target="_blank">Agent Skills 入门（搭配 Claude Code）</a>
