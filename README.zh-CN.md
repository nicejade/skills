**注意：** 本仓库包含 Anthropic 为 Claude 实现的技能（Skills）。有关 Agent Skills 标准的信息，请参阅 [agentskills.io](http://agentskills.io)。

# 技能 (Skills)
技能是包含指令、脚本和资源的文件夹，Claude 会动态加载这些内容，以提高在专业任务中的表现。技能教导 Claude 如何以可重复的方式完成特定任务，无论是按照公司的品牌指南创建文档，还是使用组织特定的工作流分析数据，亦或是自动化个人任务。

欲了解更多信息，请查看：
- [什么是技能？](https://support.claude.com/en/articles/12512176-what-are-skills)
- [在 Claude 中使用技能](https://support.claude.com/en/articles/12512180-using-skills-in-claude)
- [如何创建自定义技能](https://support.claude.com/en/articles/12512198-creating-custom-skills)
- [通过 Agent Skills 为智能体赋能](https://anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills)

# 关于本仓库

本仓库包含了一系列展示 Claude 技能系统可能性的示例技能。这些技能涵盖了从创意应用（艺术、音乐、设计）到技术任务（测试 Web 应用、MCP 服务器生成）再到企业工作流（沟通、品牌管理等）的各个领域。

每个技能都独立包含在各自的文件夹中，其中 `SKILL.md` 文件包含了 Claude 使用的指令和元数据。浏览这些技能，为创建你自己的技能寻找灵感，或了解不同的模式和方法。

本仓库中的许多技能都是开源的（Apache 2.0）。我们还包含了驱动 [Claude 文档功能](https://www.anthropic.com/news/create-files)的文档创建与编辑技能，位于 [`skills/docx`](./skills/docx)、[`skills/pdf`](./skills/pdf)、[`skills/pptx`](./skills/pptx) 和 [`skills/xlsx`](./skills/xlsx) 子目录中。这些是源码可用（source-available）而非开源的，但我们希望将其分享给开发者，作为在生产级 AI 应用中使用复杂技能的参考。

## 免责声明

**这些技能仅用于演示和教学目的。** 虽然 Claude 中可能已提供其中一些功能，但 Claude 实际的表现和行为可能与这些技能中显示的有所不同。这些技能旨在说明模式和可能性。在将技能用于关键任务之前，请务必在自己的环境中进行彻底测试。

# 技能集 (Skill Sets)
- [./skills](./skills): 创意与设计、开发与技术、企业与沟通以及文档技能的示例
- [./spec](./spec): Agent Skills 规范
- [./template](./template): 技能模板

# 在 Claude Code、Claude.ai 和 API 中尝试

## Claude Code
你可以通过在 Claude Code 中运行以下命令，将本仓库注册为插件市场：
```
/plugin marketplace add anthropics/skills
```

然后，安装特定的技能集：
1. 选择 `Browse and install plugins`
2. 选择 `anthropic-agent-skills`
3. 选择 `document-skills` 或 `example-skills`
4. 选择 `Install now`

或者，直接通过以下命令安装插件：
```
/plugin install document-skills@anthropic-agent-skills
/plugin install example-skills@anthropic-agent-skills
```

安装插件后，只需提及即可使用。例如，如果你从市场安装了 `document-skills` 插件，可以要求 Claude Code ：“使用 PDF 技能从 `path/to/some-file.pdf` 中提取表单字段。”

## Claude.ai

这些示例技能已在 Claude.ai 的付费计划中提供。

要使用本仓库中的任何技能或上传自定义技能，请按照 [在 Claude 中使用技能](https://support.claude.com/en/articles/12512180-using-skills-in-claude#h_a4222fa77b) 中的说明操作。

## Claude API

你可以通过 Claude API 使用 Anthropic 预置的技能，并上传自定义技能。详见 [Skills API 快速入门](https://docs.claude.com/en/api/skills-guide#creating-a-skill)。

# 创建基础技能

创建技能非常简单——只需一个文件夹，其中包含一个带有 YAML Frontmatter 和指令的 `SKILL.md` 文件。你可以使用本仓库中的 **template-skill** 作为起点：

```markdown
---
name: my-skill-name
description: 简要描述该技能的作用及适用场景
---

# 我的技能名称

[在此添加 Claude 在启用此技能时将遵循的指令]

## 示例
- 使用示例 1
- 使用示例 2

## 指南
- 指南 1
- 指南 2
```

Frontmatter 仅需两个字段：
- `name` - 技能的唯一标识符（小写，用连字符代替空格）
- `description` - 对技能作用及适用场景的完整描述

下方的 Markdown 内容包含 Claude 将遵循的指令、示例和指南。更多详情请参阅 [如何创建自定义技能](https://support.claude.com/en/articles/12512198-creating-custom-skills)。

# 合作伙伴技能

技能是教导 Claude 更好使用特定软件的好方法。当我们发现合作伙伴提供的优秀示例技能时，可能会在此突出显示：

- **Notion** - [适用于 Claude 的 Notion 技能](https://www.notion.so/notiondevs/Notion-Skills-for-Claude-28da4445d27180c7af1df7d8615723d0)

# 优秀 Agent Skills 示例

## 创意与设计

- [brand-guidelines](/skills/brand-guidelines/): 将 Anthropic 官方品牌色彩和排版应用于任何可能受益于 Anthropic 外观和感觉的 Artifact。适用于需要应用品牌色彩、风格指南、视觉格式或公司设计标准的情况。
- [canvas-design](/skills/canvas-design/): 使用设计哲学在 .png 和 .pdf 文档中创建精美的视觉艺术。当用户要求创建海报、艺术品、设计或其他静态作品时，应使用此技能。创作原创视觉设计，严禁复制现有艺术家的作品以避免侵犯版权。
- [slack-gif-creator](/skills/slack-gif-creator/): 为 Slack 优化创作动画 GIF 的知识和工具。提供限制、验证工具和动画概念。当用户请求为 Slack 制作动画 GIF 时使用，例如“为 Slack 制作一个 X 正在做 Y 的 GIF”。
- [theme-factory](/skills/theme-factory/): 为 Artifact 设置主题风格的工具包。这些 Artifact 可以是幻灯片、文档、报告、HTML 落地页等。预设了 10 种带有配色/字体的内置主题，可应用于任何已创建的 Artifact，也可即时生成新主题。

## 开发与技术

- [algorithmic-art](/skills/algorithmic-art/): 使用 p5.js 通过种子随机性和交互式参数探索创建算法艺术。当用户请求使用代码、生成式艺术、算法艺术、流场或粒子系统创作艺术时使用。创作原创算法艺术，而非复制现有艺术家的作品。
- [artifacts-builder](/skills/artifacts-builder/): 使用现代前端技术（React、Tailwind CSS、shadcn/ui）创建复杂的、多组件的 claude.ai HTML Artifact。适用于需要状态管理、路由或 shadcn/ui 组件的复杂 Artifact，而非简单的单文件 HTML/JSX。
- [developer-growth-analysis](/skills/developer-growth-analysis/): 分析你最近的 Claude Code 聊天记录，以识别编码模式、开发差距和改进领域，从 HackerNews 整理相关的学习资源，并自动将个性化的成长报告发送到你的 Slack 私信中。
- [frontend-design](/skills/frontend-design/): 创建具有高设计质量的、独特且生产级的组件界面。当用户要求构建 Web 组件、页面、Artifact、海报或应用（如网站、落地页、仪表板、React 组件、HTML/CSS 布局或美化 Web UI）时使用。生成创意十足、打磨精细且避免平庸 AI 审美的代码和 UI 设计。
- [langsmith-fetch](/skills/langsmith-fetch/): 通过从 LangSmith Studio 获取执行追踪来调试 LangChain 和 LangGraph 智能体。适用于调试智能体行为、调查错误、分析工具调用、检查内存操作或检查智能体性能。自动获取最近追踪并分析执行模式。需要安装 langsmith-fetch CLI。
- [mcp-builder](/skills/mcp-builder/): 创建高质量 MCP（模型上下文协议）服务器的指南，使 LLM 能够通过精心设计的工具与外部服务交互。适用于构建集成外部 API 或服务的 MCP 服务器，无论是使用 Python (FastMCP) 还是 Node/TypeScript (MCP SDK)。
- [web-artifacts-builder](/skills/web-artifacts-builder/): 使用现代前端技术（React、Tailwind CSS、shadcn/ui）创建复杂的、多组件的 claude.ai HTML Artifact。适用于需要状态管理、路由或 shadcn/ui 组件的复杂 Artifact。
- [webapp-testing](/skills/webapp-testing/): 使用 Playwright 与本地 Web 应用交互并进行测试的工具包。支持验证前端功能、调试 UI 行为、捕获浏览器截图并查看浏览器日志。
- [youtube-downloader](/skills/video-downloader/): 下载具有自定义质量和格式选项的 YouTube 视频。当用户要求下载、保存或抓取 YouTube 视频时使用。支持多种质量设置（最佳、1080p、720p、480p、360p）、多种格式（mp4、webm、mkv）以及仅下载 MP3 音频。

## 商务与沟通

- [content-research-writer](/skills/content-research-writer/): 通过进行研究、添加引用、改进引子、迭代大纲并对每个章节提供实时反馈，协助撰写高质量内容。将你的写作过程从个人努力转变为协作伙伴关系。
- [internal-comms](/skills/internal-comms/): 帮助撰写各类内部沟通文件的资源集，使用公司偏好的格式。每当要求撰写内部沟通（状态报告、领导层更新、第三方更新、公司简报、FAQ、事故报告、项目更新等）时，Claude 都应使用此技能。
- [invoice-organizer](/skills/invoice-organizer/): 通过读取杂乱的文件、提取关键信息、一致地重命名并将其分类到逻辑文件夹中，自动整理发票和收据以备税务审计。将数小时的手工簿记转变为数分钟的自动化整理。
- [lead-research-assistant](/skills/lead-research-assistant/): 通过分析你的业务、搜索目标公司并提供可行的联系策略，为你的产品或服务识别高质量的潜在客户。非常适合销售、业务开发和市场营销专业人员。
- [meeting-insights-analyzer](/skills/meeting-insights-analyzer/): 分析会议记录和录音，以发现行为模式、沟通见解和可行的反馈。识别你何时回避冲突、使用冗余词、主导对话或错失倾听机会。非常适合寻求提高沟通和领导技能的专业人士。
- [tailored-resume-generator](/skills/tailored-resume-generator/): 分析职位描述并生成量身定制的简历，突出相关经验、技能和成就，以最大限度地提高面试机会。

## 文档处理

- [doc-coauthoring](/skills/doc-coauthoring/): 引导用户完成协同创作文档的结构化工作流。当用户想要撰写文档、提案、技术规范、决策文档或类似的结构化内容时使用。此工作流帮助用户高效转移上下文、通过迭代精炼内容并验证文档对读者的有效性。
- [docx](/skills/document-skills/docx/): 全面的文档创建、编辑和分析，支持修订追踪、批注、格式保留和文本提取。当 Claude 需要处理专业文档（.docx 文件）以进行以下操作时：(1) 创建新文档，(2) 修改或编辑内容，(3) 处理修订，(4) 添加批注，或其他文档任务。
- [pdf](/skills/document-skills/pdf/): 全面的 PDF 处理工具包，用于提取文本和表格、创建新 PDF、合并/拆分文档以及处理表单。当 Claude 需要填写 PDF 表单或大规模程序化处理、生成或分析 PDF 文档时使用。
- [pptx](/skills/document-skills/pptx/): 演示文稿的创建、编辑和分析。当 Claude 需要处理演示文稿（.pptx 文件）以进行以下操作时：(1) 创建新文稿，(2) 修改或编辑内容，(3) 处理布局，(4) 添加批注或演讲者备注，或其他演示文稿任务。
- [xlsx](/skills/document-skills/xlsx/): 全面的电子表格创建、编辑和分析，支持公式、格式、数据分析和可视化。当 Claude 需要处理电子表格（.xlsx, .xlsm, .csv, .tsv 等）以进行以下操作时：(1) 创建带有公式和格式的新表，(2) 读取或分析数据，(3) 在保留公式的情况下修改现有表，(4) 数据分析和可视化，或 (5) 重新计算公式。

## 其他工具

- [changelog-generator](/skills/changelog-generator/): 通过分析提交历史、对更改进行分类并将技术提交转化为清晰、面向客户的发布说明，自动从 git 提交创建面向用户的更新日志。
- [competitive-ads-extractor](/skills/competitive-ads-extractor/): 从广告库（Facebook, LinkedIn 等）提取并分析竞争对手的广告，以了解哪些信息、问题和创意方法有效。
- [connect](/skills/connect/): 将 Claude 连接到任何应用。发送电子邮件、创建 Issue、发布消息、更新数据库——在 Gmail, Slack, GitHub, Notion 等 1000 多个服务中执行实际操作。
- [connect-apps](/skills/connect-apps/): 将 Claude 连接到外部应用。当用户想要发送电子邮件、创建 Issue、发布消息或在外部服务中执行操作时使用。
- [domain-name-brainstormer](/skills/domain-name-brainstormer/): 为你的项目生成创意域名构思，并在多个顶级域名（.com, .io, .dev, .ai 等）中检查可用性。
- [file-organizer](/skills/file-organizer/): 通过理解上下文、查找重复项、建议更好的结构并自动执行清理任务，智能地组织你计算机上的文件和文件夹。
- [image-enhancer](/skills/image-enhancer/): 提高图像质量，特别是截图，通过增强分辨率、锐度和清晰度。非常适合为演示文稿、文档或社交媒体帖子准备图像。
- [raffle-winner-picker](/skills/raffle-winner-picker/): 从列表、电子表格或 Google 表格中为抽奖和竞赛随机抽取中奖者。确保公平、无偏见且透明的选择。
- [skill-creator](/skills/skill-creator/): 创建有效技能的指南。当用户想要创建新技能（或更新现有技能）以扩展 Claude 的专业知识、工作流或工具集成能力时使用。
- [skill-share](/skills/skill-share/): 一个创建新 Claude 技能并通过 Slack 自动分享的技能，用于无缝团队协作和技能发现。
- [template-skill](/skills/template-skill/): 用技能的描述及 Claude 应当何时使用它来替换此内容。
