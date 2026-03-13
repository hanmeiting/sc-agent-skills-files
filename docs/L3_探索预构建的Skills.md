# 探索预构建的 Skills

## 预构建 Skills

* <a href="https://github.com/anthropics/skills/tree/main/skills" target="_blank">Anthropic 技能列表</a>
* <a href="https://github.com/anthropics/skills/tree/main/skills/pptx" target="_blank">pptx（PowerPoint 技能）</a>
* <a href="https://github.com/anthropics/skills/tree/main/skills/skill-creator" target="_blank">Skill 创建器</a>

## 第一部分：更新营销技能

在视频中，我们将营销技能更新为使用 BigQuery MCP 服务器从 BigQuery 表格获取数据，而不再需要提供 CSV 文件：

- <a href="https://github.com/https-deeplearning-ai/sc-agent-skills-files/tree/main/L3/prompts.md#part-1-updating-the-marketing-skill" target="_blank">本部分使用的提示词</a>
- <a href="https://github.com/https-deeplearning-ai/sc-agent-skills-files/tree/main/L3/updated_marketing_skill/analyzing-marketing-campaign/" target="_blank">拍摄期间获得的营销技能更新文件</a>

您可以设置一个 BigQuery 表格来尝试这部分内容（下方有说明链接），或者设置一个本地数据库。例如，您可以设置一个本地 SQLite 数据库，将此 <a href="https://github.com/https-deeplearning-ai/sc-agent-skills-files/tree/main/L3/campaign_performance_4weeks.csv" target="_blank">CSV 文件</a> 导入数据库，并使用此 <a href="https://github.com/modelcontextprotocol/servers-archived/tree/main/src/sqlite" target="_blank">MCP 服务器</a>。您也可以完全跳过此部分。

- 可选：<a href="https://github.com/https-deeplearning-ai/sc-agent-skills-files/tree/main/L3/additional_references/table_setup.md#bigquery-setup" target="_blank">设置 BigQuery 表格的说明</a>
- 可选替代方案：<a href="https://github.com/https-deeplearning-ai/sc-agent-skills-files/tree/main/L3/additional_references/table_setup.md#sqlite-setup" target="_blank">设置 SQLite 表格的说明</a>

**注意**：由于 BigQuery MCP 服务器是本地 MCP 服务器，我们使用的是 Claude Desktop（而非 Claude.ai）。在 Claude.ai 中，您只能使用远程 MCP 服务器。

## 第二部分：创建品牌指南技能

- <a href="https://github.com/https-deeplearning-ai/sc-agent-skills-files/tree/main/L3/brand_guidelines_files/" target="_blank">品牌指南文件</a>
- <a href="https://github.com/https-deeplearning-ai/sc-agent-skills-files/tree/main/L3/prompts.md#part-2--creating-the-brand-guideline-skill" target="_blank">第二部分使用的提示词</a>
- <a href="https://github.com/https-deeplearning-ai/sc-agent-skills-files/tree/main/L3/brand_guidelines_skill/craftedwell-brand/" target="_blank">拍摄期间获得的技能文件</a>

## 第三部分：实现完整工作流程

- <a href="https://github.com/https-deeplearning-ai/sc-agent-skills-files/tree/main/L3/prompts.md#part-3-implementing-the-entire-workflow" target="_blank">第三部分使用的提示词</a>
- <a href="https://github.com/https-deeplearning-ai/sc-agent-skills-files/tree/main/L3/output_report_example/CraftedWell_Weekly_Report_Dec16-22.pptx" target="_blank">拍摄期间生成的幻灯片</a>

幻灯片可能需要几分钟生成，且可能与视频中的样式完全不同。
