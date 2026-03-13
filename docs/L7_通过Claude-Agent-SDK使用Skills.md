# 通过 Claude Agent SDK 使用 Skills

## 课程文件

您可以在 <a href="https://github.com/https-deeplearning-ai/sc-agent-skills-files/tree/main/L7" target="_blank">这里</a> 找到 L7 的所有文件，与视频中展示的内容有一些差异：
- 对每个子 Agent 使用了 `haiku` 作为模型
- 指定了要使用的确切 MCP 工具列表

以下是一些值得探索的关键文件：
- <a href="https://github.com/https-deeplearning-ai/sc-agent-skills-files/tree/main/L7/prompts" target="_blank">主 Agent 和子 Agent 的系统提示词</a>
- <a href="https://github.com/https-deeplearning-ai/sc-agent-skills-files/tree/main/L7/.claude/skills/learning-a-tool/" target="_blank">`learning-a-tool` 技能的文件</a>
- <a href="https://github.com/https-deeplearning-ai/sc-agent-skills-files/tree/main/L7/utils.py" target="_blank">utils.py</a>（消息格式化）
- <a href="https://github.com/https-deeplearning-ai/sc-agent-skills-files/tree/main/L7/agent.py" target="_blank">agent.py</a>
- <a href="https://github.com/https-deeplearning-ai/sc-agent-skills-files/tree/main/L7_notes/learning-mineru/" target="_blank">拍摄期间生成的学习指南</a>

要运行 Agent，请遵循 <a href="https://github.com/https-deeplearning-ai/sc-agent-skills-files/tree/main/L7/README.md" target="_blank">README 文件</a> 中的说明。您需要一个 Anthropic API 密钥（无需订阅）。

**关于费用：** 如果您使用 `haiku` 作为子 Agent 模型（主 Agent 使用 `sonnet`），运行相同请求大约花费 $3.43 的 API 费用；如果子 Agent 也使用 `sonnet`，则约为 $6.35。

### 课程中使用的提示词

**步骤一：** 开始研究过程
```
Help me get started with MinerU. Create a learning guide. Show me your plan first.
```
（帮我了解 MinerU 如何入门。创建一份学习指南。先给我展示你的计划。）

**注意：** Agent 可能需要大约 15 分钟才能完成。如果您想要更快的研究或更简单的学习指南，可以随时更新技能的指令和 Agent 定义。

**步骤二：** 审查并批准计划

您可以同意该计划，或提供您的反馈和建议。

**步骤三（可选）：** 导出到 Notion

如果您想尝试与 Notion 的 MCP 集成：
```
Write ./learning-mineru/resources.md to the "Resources" subpage under Learning in Notion. The subpage already exists. Use rich formatting. For Notion MCP: You can use the full range of Notion block types for proper formatting.
```

**注意：** 在课程使用的 Notion 账户中，我们创建了一个名为 `Learning` 的页面，其中有一个名为 `Resources` 的子页面。

## 更多高级选项

- <a href="https://platform.claude.com/docs/en/agent-sdk/python#example-advanced-permission-control" target="_blank">高级权限控制</a>
- <a href="https://platform.claude.com/docs/en/agent-sdk/python#building-a-continuous-conversation-interface" target="_blank">构建持续对话界面</a>（中断、新对话、退出）

## 参考资料

- <a href="https://platform.claude.com/docs/en/agent-sdk/overview" target="_blank">Claude Agent SDK 文档</a>
- <a href="https://platform.claude.com/docs/en/agent-sdk/python" target="_blank">Python Agent SDK</a>
- <a href="https://platform.claude.com/docs/en/agent-sdk/skills" target="_blank">SDK 中的 Agent Skills</a>
- <a href="https://github.com/anthropics/claude-agent-sdk-demos" target="_blank">Claude Agent SDK 演示项目</a>
