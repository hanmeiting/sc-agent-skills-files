# 通过 Claude API 使用 Skills

## 课程文件

您可以在 <a href="https://github.com/https-deeplearning-ai/sc-agent-skills-files/tree/main/L5" target="_blank">这里</a> 找到本课的 Notebook 和所有所需的输入文件。

要运行 Notebook，您需要创建一个包含 Anthropic API 密钥的 `.env` 文件（无需 Claude 订阅）：

`ANTHROPIC_API_KEY="your-key"`

您可以从 <a href="https://platform.claude.com/dashboard" target="_blank">Claude 开发者平台</a> 获取密钥。

**关于费用：** 请注意，运行所有 Notebook 单元格一次约花费 $0.67 的 API 费用。

如果您不想运行 Notebook，可以：
- 查看 <a href="https://github.com/https-deeplearning-ai/sc-agent-skills-files/tree/main/L5/lesson_5.ipynb" target="_blank">已运行输出的 Notebook</a>（与视频中完全一致）
- 查看 <a href="https://github.com/https-deeplearning-ai/sc-agent-skills-files/tree/main/L5/sample_outputs/" target="_blank">生成的示例输出</a>

您也可以在 Claude.ai 中尝试相同的自定义技能。

## 注意事项
- 这里是 <a href="https://platform.claude.com/docs/en/agents-and-tools/tool-use/code-execution-tool#pre-installed-libraries" target="_blank">沙箱环境中预安装库的列表</a>
- 流式传输（Streaming）：本课的 Notebook 未实现 Messages API 的流式传输。因此，当您运行单元格获取响应时，可能需要等待几分钟。如果您想实现流式传输，可以查看 <a href="https://platform.claude.com/docs/en/build-with-claude/streaming" target="_blank">这里</a> 的文档。
- 要查看如何使用 API 配合 Agent Skills 的更多示例（例如多轮对话），请务必查看此 <a href="https://platform.claude.com/docs/en/build-with-claude/skills-guide" target="_blank">指南</a>。

## 额外参考资料
- <a href="https://platform.claude.com/docs/en/agents-and-tools/tool-use/code-execution-tool" target="_blank">代码执行工具</a>
- <a href="https://platform.claude.com/docs/en/build-with-claude/files" target="_blank">Files API</a>
- <a href="https://github.com/anthropics/claude-cookbooks/tree/main/skills" target="_blank">Claude Cookbook：Skills 示例</a>
