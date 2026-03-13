# 在 Claude Code 中使用 Skills

## 课程代码库和文件

课程文件链接：
- <a href="https://github.com/https-deeplearning-ai/sc-agent-skills-files/tree/main/L6" target="_blank">课程使用的代码库</a>
- <a href="https://github.com/https-deeplearning-ai/sc-agent-skills-files/tree/main/L6/.claude/skills/" target="_blank">课程技能文件</a>
- <a href="https://github.com/https-deeplearning-ai/sc-agent-skills-files/tree/main/L6/.claude/agents" target="_blank">子 Agent 定义</a>
- <a href="https://github.com/https-deeplearning-ai/sc-agent-skills-files/tree/main/L6_notes/prompts.md" target="_blank">对话中使用的提示词</a>
- <a href="https://github.com/https-deeplearning-ai/sc-agent-skills-files/tree/main/L6_notes/clear.py" target="_blank">clear.py</a>

第一次在终端中运行应用程序时：
- 先执行 `uv sync`
- 激活虚拟环境：`source .venv/bin/activate`
- 尝试以下命令：
   - `task –help`
   - `task add "write the final report" -p high -d 2025-01-15`
   - `task list`
   - `task done 1`
   - `task list -a`

这是一个待办事项 CLI 应用的入门代码库。在课程中，我们演示了如何添加 edit（编辑）和 clear（清除）命令。您也可以通过添加 delete（删除）和 undo（撤销）命令来扩展该应用，或更改任务存储和显示的底层逻辑。

## Claude Code

如果这是您第一次尝试 Claude Code，可以查看以下课程：
- <a href="https://www.deeplearning.ai/short-courses/claude-code-a-highly-agentic-coding-assistant/" target="_blank">Claude Code：高度自主的编程助手</a>
- <a href="https://anthropic.skilljar.com/claude-code-in-action" target="_blank">Claude Code 实战</a>

如果您已完成这些课程并希望看到 Claude Code 的进阶课程，请告诉我们您希望涵盖哪些主题。

如果您没有 Anthropic 订阅，可以选择使用 API 密钥运行 Claude Code。使用 Sonnet 4.5 完成相同练习大约花费 $1.57。

## 在 Claude Code 中使用 Skills

在课程中，您了解了如何在项目级别添加技能。这里有一份 <a href="https://code.claude.com/docs/en/skills#where-skills-live" target="_blank">列表</a>，显示您的技能还可以存放在哪些位置。


### 前置内容中可以添加哪些额外字段？

除了 `name` 和 `description` 之外，在 Claude Code 中使用技能时，您还可以在前置内容中添加多个其他字段，例如 `allowed-tools`、`model`、`disable-model-invocation`、`user-invocable`、`argument-hint`、`context` 和 `agent`。这些字段大多是在我们录制课程后才添加的，这就是为什么我们没有机会在视频中介绍它们。您可以在文档 <a href="https://code.claude.com/docs/en/skills#frontmatter-reference" target="_blank">这里</a> 找到每个字段的描述。

### Claude Code 中的 Skills 调用方式

Claude Code 中的任何技能都可以由模型自动调用（如本课演示）或由用户手动调用。例如，如果您想调用 `adding-cli-command` 技能，可以输入 `/adding-cli-command`，然后描述要添加的命令。字段 `disable-model-invocation` 和 `user-invocable` 允许您进一步控制此行为，如 <a href="https://code.claude.com/docs/en/skills#control-who-invokes-a-skill" target="_blank">这里</a> 所述。

如果您发现 Claude Code 没有在需要时调用预期的技能，请确保：
- 添加技能后已重启 Claude Code
- 您的技能描述包含足够详细的信息，以便 Claude 理解何时使用它

您随时可以手动调用技能，或明确指示 Claude 使用特定技能。


### Skills 和斜杠命令已合并

在 Skills 引入之前，Claude Code 有一个叫做斜杠命令（slash commands）的功能。此功能允许您通过在 `.claude` 下的 `commands` 文件夹中保存 Markdown 文件来创建自定义命令。

自 1 月 23 日起，自定义斜杠命令已合并到技能中。这次合并是因为位于 `.claude/commands/review.md` 的文件和位于 `.claude/skills/review/SKILL.md` 的技能都会创建 `/review` 命令，工作方式相同。但技能提供了额外的可选功能：一个专用目录用于存放 `SKILL.md` 中可以引用的支持文件，以及用于控制您或 Claude 调用技能的前置内容选项。

### 子 Agent 与 Skills

在课程中，您了解了如何创建自定义子 Agent。Claude Code 还包含内置子 Agent，如 `Explore`、`Plan` 和 `General-Purpose`（<a href="https://code.claude.com/docs/en/sub-agents#built-in-subagents" target="_blank">内置子 Agent</a>）。

在子 Agent 中使用技能有两种方法：

- **方法一**：定义使用技能的自定义子 Agent（如课程中所示）

    创建子 Agent 时，您可以使用 `skills` 字段在子 Agent 启动时将技能内容注入其上下文。由于子 Agent 不会从父对话继承技能，您必须明确列出技能。调用子 Agent 时，`SKILL.md` 文件的完整内容会被注入到子 Agent 的上下文中。

    `code-reviewer` 子 Agent 的定义：
    ```
    ---
    name: code-reviewer
    description: "审查代码的质量、安全性和约定合规性。当用户要求审查、检查或验证代码时使用"
    tools: Bash, Glob, Grep, Read
    model: inherit
    color: purple
    skills: reviewing-cli-command
    ---
    ```

    在这种情况下，`reviewing-cli-command` 技能对您的主 Agent 和子 Agent 都可用。技能可以在需要时加载到主 Agent 的上下文中，也可以在调用子 Agent 时指导 `code-reviewer` 子 Agent。

    您也可以为 `code-reviewer` 子 Agent 列出多个技能。例如，您可以添加另一个用于审查以不同语言或框架编写的 CLI 命令的技能，或者添加一个用于审查 SQL 查询的技能（如果您希望应用的任务存储在数据库而非本地 JSON 文件中）。

- **方法二**：在子 Agent 中运行技能（课程中未展示）

    如果您希望技能始终在隔离的上下文中运行，需要在技能的前置内容中使用 `context: fork` 字段。技能运行时，默认情况下，内置的 `general-purpose` 子 Agent 接收技能内容作为其提示词或任务，在隔离的上下文中按技能指示运行，然后返回结果。如果您想让特定子 Agent（内置或自定义）与技能一起使用，需要在技能的前置内容中指定 `agent` 字段。

    例如，以下是一个示例 `SKILL.md` 文件：
    ```
    ---
    name: deep-research
    description: Research a topic thoroughly
    context: fork
    agent: Explore
    ---

    Research $ARGUMENTS thoroughly:

    1. Find relevant files using Glob and Grep
    2. Read and analyze the code
    3. Summarize findings with specific file references
    ```

    参考：<a href="https://code.claude.com/docs/en/skills#run-skills-in-a-subagent" target="_blank">在子 Agent 中运行 Skills</a>


## 参考资料

- 有关如何在 Claude Code 中使用 Skills 的更全面指南，请查看此 <a href="https://code.claude.com/docs/en/skills" target="_blank">文档</a>。

- 要了解有关 Claude Code 中子 Agent 的更多信息，请查看此 <a href="https://code.claude.com/docs/en/sub-agents" target="_blank">指南</a>。

- <a href="https://code.claude.com/docs/en/skills#troubleshooting" target="_blank">故障排除指南</a>。
