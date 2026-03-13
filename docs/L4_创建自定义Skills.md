# 创建自定义 Skills

## 自定义 Skills 链接
- <a href="https://github.com/https-deeplearning-ai/sc-agent-skills-files/tree/main/L4/custom_skills/analyzing-time-series/" target="_blank">时间序列分析（analyzing time series）</a>
- <a href="https://github.com/https-deeplearning-ai/sc-agent-skills-files/tree/main/L4/custom_skills/generating-practice-questions/" target="_blank">生成练习题（generating practice questions）</a>

## 参考资料
完整的 Skills 创建最佳实践和规范，请查阅：
- <a href="https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices" target="_blank">技能编写最佳实践</a>
- <a href="https://agentskills.io/specification" target="_blank">规范说明</a>
- <a href="https://resources.anthropic.com/hubfs/The-Complete-Guide-to-Building-Skill-for-Claude.pdf?hsLang=en" target="_blank">为 Claude 构建 Skills 完全指南</a>

## 如何在 Claude Code 中禁用插件？

插件设计为可以按需开关。您可以在需要特定功能时启用它们，不需要时禁用，以减少系统提示词的上下文和复杂度。

- 使用 `/plugin` 命令：导航到 `installed`（已安装）选项卡，然后选择要禁用的插件。
- 使用命令行：
`claude plugin disable <plugin-name>`


## 幻灯片内容摘要

### SKILL.md 文件结构

一个技能文件包含两个主要部分：
1. **YAML 前置内容（Frontmatter）** —— 顶部的元数据
2. **正文内容（Body Content）** —— 下方的 Markdown 指令

### 前置内容必填字段

| 字段 | 约束条件 |
|------|---------|
| **name（名称）** | 最多 64 个字符；只能使用小写字母、数字和连字符；不能以连字符开头或结尾；必须与父目录名称匹配；推荐使用动名词形式（动词+-ing） |
| **description（描述）** | 最多 1024 个字符；非空；应描述技能的功能和使用时机；包含特定关键词以帮助 Agent 识别相关任务 |

### 前置内容可选字段

| 字段 | 约束条件 |
|------|---------|
| **license（许可证）** | 许可证名称或许可证文件的引用 |
| **compatibility（兼容性）** | 最多 500 个字符；说明环境要求 |
| **metadata（元数据）** | 任意键值对（如作者、版本） |
| **allowed-tools（允许的工具）** | 预先批准的工具列表，以空格分隔（实验性功能） |


### 正文内容

**没有格式限制**，但有以下建议：

#### 推荐的章节
- 分步骤操作说明
- 输入格式 / 输出格式 / 示例
- 常见的边缘情况

#### 实践建议
- 保持在 **500 行以内**
- 将详细参考材料移到单独文件中（显示基本内容，链接高级内容）
- 保持参考文件 **距 SKILL.md 一级深度**（避免嵌套文件引用）
- 清晰简洁，使用一致的术语
- 在文件路径中使用正斜杠，即使在 Windows 上也如此

#### 自由度等级

| 等级 | 描述 |
|------|------|
| **高自由度** | 基于文本的通用指示；多种方法都有效 |
| **中等自由度** | 说明包含可定制的伪代码、代码示例或模式；有首选模式，但可以接受一定变化 |
| **低自由度** | 说明指向特定脚本；必须遵循特定的执行顺序 |

#### 复杂工作流程
- 将复杂操作分解为清晰、顺序的步骤
- 如果工作流程变得庞大且步骤众多，考虑将其推送到单独文件中

### 可选目录

#### `/assets`（资产）
- **模板：** 文档模板、配置模板
- **图片：** 图表、Logo
- **数据文件：** 查找表、Schema

#### `/references`（参考资料）
- 包含 Agent 在需要时可以阅读的额外文档
- 保持每个参考文件的内容集中
- **注意：** 对于超过 100 行的参考文件，在顶部添加目录，以便 Agent 查看完整范围

#### `/scripts`（脚本）
- 清晰记录依赖项
- 脚本应有清晰的文档说明
- 错误处理应明确且有帮助
- **注意：** 在说明中明确 Claude 是应该执行脚本还是将其作为参考阅读


### 评估

#### 单元测试

使用以下内容定义测试用例：
- **skills（技能）**：要测试哪些技能
- **queries（查询）**：要运行的测试提示词
- **files（文件）**：要使用的输入文件
- **expected_behavior（预期行为）**：成功的标准

#### 测试用例示例
```json
{
  "skills": ["generating-practice-questions"],
  "queries": [
    "Generate practice questions from this lecture note and save it to output.md",
    "Generate practice questions from this lecture note and save it to output.tex",
    "Generate practice questions from this lecture note and save it to output.pdf"
  ],
  "files": ["test-files/notes.pdf", "test-files/notes.tex", "test-files/notes.pdf"],
  "expected_behavior": [
    "成功读取并提取输入文件。对于 PDF 输入，使用 pdfplumber。",
    "成功提取所有学习目标。",
    "生成 4 种类型的问题。",
    "遵循每种问题的指导方针。",
    "使用输出结构和正确的输出模板。",
    "LaTeX 输出成功编译。",
    "将生成的问题保存到名为 output 的文件中。"
  ]
}
```
**其他评估建议**：

- 获取**人工反馈**
- 在您计划使用的**所有模型**上进行测试
