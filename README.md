# Claudian

**[English](README_en.md) | 中文**

![GitHub stars](https://img.shields.io/github/stars/AndySuen1/claudian?style=social)
![GitHub release](https://img.shields.io/github/v/release/AndySuen1/claudian)
![License](https://img.shields.io/github/license/AndySuen1/claudian)

![Preview](Preview.png)

一款将 Claude Code 作为 AI 协作者嵌入 Obsidian 笔记库的插件。你的笔记库将成为 Claude 的工作目录，赋予其完整的代理能力：文件读写、搜索、执行 bash 命令以及多步骤工作流。

## 功能特性

- **完整代理能力**：充分利用 Claude Code 的能力，在 Obsidian 笔记库中读取、写入、编辑文件，搜索内容，执行 bash 命令。
- **上下文感知**：自动附加当前聚焦的笔记，通过 `@` 提及文件，按标签排除笔记，包含编辑器中选中的文本（高亮），拖拽 vault 文件到输入框快速切换上下文，并支持访问外部目录以获取额外上下文。
- **视觉支持**：通过拖拽、粘贴或文件路径发送图片来进行图像分析。
- **内联编辑**：直接在笔记中编辑选中的文本或在光标位置插入内容，支持词级差异预览和只读工具访问以获取上下文。
- **指令模式（`#`）**：通过聊天输入直接向系统提示中添加精细的自定义指令，支持在模态框中查看/编辑。
- **斜杠命令**：创建可复用的提示模板，通过 `/命令` 触发，支持参数占位符、`@文件` 引用和可选的内联 bash 替换。
- **技能（Skills）**：使用可复用的能力模块扩展 Claudian，根据上下文自动调用，与 Claude Code 的技能格式兼容。
- **自定义代理**：定义 Claude 可调用的自定义子代理，支持工具限制和模型覆盖。
- **Claude Code 插件**：启用通过 CLI 安装的 Claude Code 插件，自动从 `~/.claude/plugins` 发现，并支持按笔记库配置。插件的技能、代理和斜杠命令可无缝集成。
- **MCP 支持**：通过模型上下文协议服务器（stdio、SSE、HTTP）连接外部工具和数据源，支持上下文保存模式和 `@` 提及激活。
- **高级模型控制**：在 Haiku、Sonnet 和 Opus 之间切换，通过环境变量配置自定义模型，精细调整思考预算，并启用支持 100 万上下文窗口的 Opus 和 Sonnet（需要 Max 订阅或额外用量）。
- **计划模式**：通过聊天输入中的 Shift+Tab 切换计划模式。Claudian 在实施前先进行探索和设计，提交计划供审批，可选择在新会话中批准、在当前会话中继续，或提供反馈。
- **Sandbox 模式**：工具栏中的 Sandbox 开关默认启用。启用时自动切换至 Haiku 模型并限制外部文件访问，提供轻量安全的沙箱环境；关闭时恢复原模型并开放外部访问权限。
- **会话标题显示**：单 Tab 模式下，标题栏在品牌名旁实时显示当前会话标题，方便快速识别对话内容。
- **安全性**：权限模式（YOLO/安全/计划）、安全阻止列表，以及带有符号链接安全检查的笔记库隔离。
- **Chrome 中的 Claude**：允许 Claude 通过 `claude-in-chrome` 扩展与 Chrome 交互。

## 环境要求

- 已安装 [Claude Code CLI](https://code.claude.com/docs/en/overview)（强烈建议通过原生安装方式安装 Claude Code）
- Obsidian v1.8.9+
- Claude 订阅/API 或支持 Anthropic API 格式的自定义模型提供商（[Openrouter](https://openrouter.ai/docs/guides/guides/claude-code-integration)、[Kimi](https://platform.moonshot.ai/docs/guide/agent-support)、[GLM](https://docs.z.ai/devpack/tool/claude)、[DeepSeek](https://api-docs.deepseek.com/guides/anthropic_api) 等）
- 仅支持桌面端（macOS、Linux、Windows）

## 安装

### 通过 GitHub Release 安装（推荐）

1. 从[最新版本](https://github.com/AndySuen1/claudian/releases/latest)下载 `main.js`、`manifest.json` 和 `styles.css`
2. 在笔记库的插件目录中创建名为 `claudian` 的文件夹：
   ```
   /path/to/vault/.obsidian/plugins/claudian/
   ```
3. 将下载的文件复制到 `claudian` 文件夹中
4. 在 Obsidian 中启用插件：
   - 设置 → 第三方插件 → 启用"Claudian"

### 使用 BRAT 安装

[BRAT](https://github.com/TfTHacker/obsidian42-brat)（Beta 审阅者自动更新测试器）允许你直接从 GitHub 安装并自动更新插件。

1. 从 Obsidian 社区插件安装 BRAT 插件
2. 在设置 → 第三方插件 中启用 BRAT
3. 打开 BRAT 设置，点击"Add Beta plugin"
4. 输入仓库 URL：`https://github.com/AndySuen1/claudian`
5. 点击"Add Plugin"，BRAT 将自动安装 Claudian
6. 在设置 → 第三方插件 中启用 Claudian

> **提示**：BRAT 将自动检查更新，并在有新版本时通知你。

### 从源码安装（开发用途）

1. 将此仓库克隆到笔记库的插件目录：
   ```bash
   cd /path/to/vault/.obsidian/plugins
   git clone https://github.com/AndySuen1/claudian.git
   cd claudian
   ```

2. 安装依赖并构建：
   ```bash
   npm install
   npm run build
   ```

3. 在 Obsidian 中启用插件：
   - 设置 → 第三方插件 → 启用"Claudian"

### 开发

```bash
# 监听模式
npm run dev

# 生产构建
npm run build
```

> **提示**：将 `.env.local.example` 复制为 `.env.local`，或运行 `npm install` 并设置笔记库路径，以在开发时自动复制文件。

## 使用方法

**两种模式：**
1. 点击侧边栏中的机器人图标，或使用命令面板打开聊天
2. 选中文本 + 快捷键 进行内联编辑

像使用 Claude Code 一样使用它——读取、写入、编辑、搜索笔记库中的文件。

### 上下文

- **文件**：自动附加当前聚焦的笔记；输入 `@` 附加其他文件
- **拖拽切换**：将 vault 中的文件拖拽到输入框，即可将其设置为当前笔记上下文
- **@提及下拉菜单**：输入 `@` 查看 MCP 服务器、代理、外部上下文和笔记库文件
  - `@Agents/` 显示可选择的自定义代理
  - `@mcp-server` 启用上下文保存模式的 MCP 服务器
  - `@folder/` 筛选来自该外部上下文的文件（例如 `@workspace/`）
  - 默认显示笔记库文件
- **选中内容**：在编辑器中选中文本，或在画布中选中元素，然后聊天——选中内容将自动包含
- **图片**：拖拽、粘贴或输入路径；为 `![[image]]` 嵌入配置媒体文件夹
- **外部上下文**：点击工具栏中的文件夹图标，访问笔记库以外的目录

### 功能

- **内联编辑**：选中文本 + 快捷键，直接在笔记中进行词级差异预览的编辑
- **指令模式**：输入 `#` 向系统提示添加精细指令
- **斜杠命令**：输入 `/` 使用自定义提示模板或技能
- **Sandbox 模式**：点击工具栏中的 Sandbox 开关切换沙箱状态。启用时切换至 Haiku 模型并限制外部访问；关闭时恢复原模型
- **技能**：将 `skill/SKILL.md` 文件添加到 `~/.claude/skills/` 或 `{vault}/.claude/skills/`，推荐使用 Claude Code 管理技能
- **自定义代理**：将 `agent.md` 文件添加到 `~/.claude/agents/`（全局）或 `{vault}/.claude/agents/`（笔记库专属）；通过聊天中的 `@Agents/` 选择，或提示 Claudian 调用代理
- **Claude Code 插件**：通过 设置 → Claude Code 插件 启用，推荐使用 Claude Code 管理插件
- **MCP**：通过 设置 → MCP 服务器 添加外部工具；在聊天中使用 `@mcp-server` 激活

## 配置

### 设置

**自定义**
- **用户名**：你的名字，用于个性化问候
- **排除标签**：阻止笔记自动加载的标签（例如 `sensitive`、`private`）
- **媒体文件夹**：配置笔记库存储附件的位置，用于嵌入图片支持（例如 `attachments`）
- **自定义系统提示**：附加到默认系统提示的额外指令（指令模式 `#` 保存到此处）
- **启用自动滚动**：切换流式传输期间自动滚动到底部（默认：开）
- **自动生成会话标题**：切换发送第一条用户消息后 AI 自动生成标题
- **标题生成模型**：用于自动生成会话标题的模型（默认：Auto/Haiku）
- **Vim 风格导航映射**：配置按键绑定，格式如 `map w scrollUp`、`map s scrollDown`、`map i focusInput`

**快捷键**
- **内联编辑快捷键**：触发对选中文本内联编辑的快捷键
- **打开聊天快捷键**：打开聊天侧边栏的快捷键

**斜杠命令**
- 创建/编辑/导入/导出自定义 `/命令`（可选择覆盖模型和允许的工具）

**MCP 服务器**
- 添加/编辑/验证/删除 MCP 服务器配置，支持上下文保存模式

**Claude Code 插件**
- 启用/禁用从 `~/.claude/plugins` 发现的 Claude Code 插件
- 用户范围插件在所有笔记库中可用；项目范围插件仅在匹配的笔记库中可用

**安全**
- **加载用户 Claude 设置**：加载 `~/.claude/settings.json`（用户的 Claude Code 权限规则可能绕过安全模式）
- **启用命令阻止列表**：阻止危险的 bash 命令（默认：开）
- **阻止的命令**：要阻止的模式（支持正则表达式，平台专属）
- **允许的导出路径**：笔记库外可导出文件的路径（默认：`~/Desktop`、`~/Downloads`）。支持 `~`、`$VAR`、`${VAR}` 和 `%VAR%`（Windows）。

**环境**
- **自定义变量**：Claude SDK 的环境变量（KEY=VALUE 格式，支持 `export ` 前缀）
- **环境代码片段**：保存和恢复环境变量配置

**高级**
- **Claude CLI 路径**：自定义 Claude Code CLI 路径（留空则自动检测）

## 安全与权限

| 范围 | 访问权限 |
|------|----------|
| **笔记库** | 完整读写（通过 `realpath` 确保符号链接安全） |
| **导出路径** | 仅写入（例如 `~/Desktop`、`~/Downloads`） |
| **外部上下文** | 完整读写（仅限当前会话，通过文件夹图标添加） |

- **YOLO 模式**：无需批准提示；所有工具调用自动执行（默认）
- **安全模式**：每次工具调用需要批准提示；Bash 需要精确匹配，文件工具允许前缀匹配
- **计划模式**：在实施前探索并设计计划。通过聊天输入中的 Shift+Tab 切换
- **Sandbox 模式**：工具栏开关（默认启用）。启用时自动切换至 Haiku 模型并禁止外部文件访问；关闭时恢复原模型并开放外部访问

## 隐私与数据使用

- **发送至 API**：你的输入、附加文件、图片和工具调用输出。默认：Anthropic；通过 `ANTHROPIC_BASE_URL` 自定义端点。
- **本地存储**：设置、会话元数据和命令存储在 `vault/.claude/`；会话消息存储在 `~/.claude/projects/`（SDK 原生）；旧版会话存储在 `vault/.claude/sessions/`。
- **无遥测**：除你配置的 API 提供商外，不进行任何追踪。

## 故障排除

### 找不到 Claude CLI

如果遇到 `spawn claude ENOENT` 或 `Claude CLI not found`，说明插件无法自动检测到你的 Claude 安装。这通常发生在使用 Node 版本管理器（nvm、fnm、volta）时。

**解决方案**：找到你的 CLI 路径，并在 设置 → 高级 → Claude CLI 路径 中设置。

| 平台 | 命令 | 示例路径 |
|------|------|----------|
| macOS/Linux | `which claude` | `/Users/you/.volta/bin/claude` |
| Windows（原生） | `where.exe claude` | `C:\Users\you\AppData\Local\Claude\claude.exe` |
| Windows（npm） | `npm root -g` | `{root}\@anthropic-ai\claude-code\cli.js` |

> **注意**：在 Windows 上，避免使用 `.cmd` 包装器。请使用 `claude.exe` 或 `cli.js`。

**备选方案**：在 设置 → 环境 → 自定义变量 中将 Node.js bin 目录添加到 PATH。

### npm CLI 和 Node.js 不在同一目录

如果使用 npm 安装的 CLI，请检查 `claude` 和 `node` 是否在同一目录：
```bash
dirname $(which claude)
dirname $(which node)
```

如果不同，Obsidian 等 GUI 应用可能找不到 Node.js。

**解决方案**：
1. 安装原生二进制文件（推荐）
2. 在设置 → 环境 中添加 Node.js 路径：`PATH=/path/to/node/bin`

**仍有问题？** [提交 GitHub Issue](https://github.com/AndySuen1/claudian/issues)，并附上你的平台信息、CLI 路径和错误消息。

## 架构

```
src/
├── main.ts                      # 插件入口
├── core/                        # 核心基础设施
│   ├── agent/                   # Claude Agent SDK 封装（ClaudianService）
│   ├── agents/                  # 自定义代理管理（AgentManager）
│   ├── commands/                # 斜杠命令管理（SlashCommandManager）
│   ├── hooks/                   # PreToolUse/PostToolUse 钩子
│   ├── images/                  # 图片缓存与加载
│   ├── mcp/                     # MCP 服务器配置、服务与测试
│   ├── plugins/                 # Claude Code 插件发现与管理
│   ├── prompts/                 # 代理系统提示
│   ├── sdk/                     # SDK 消息转换
│   ├── security/                # 批准、阻止列表、路径验证
│   ├── storage/                 # 分布式存储系统
│   ├── tools/                   # 工具常量与工具函数
│   └── types/                   # 类型定义
├── features/                    # 功能模块
│   ├── chat/                    # 主聊天视图 + UI、渲染、控制器、标签页
│   ├── inline-edit/             # 内联编辑服务 + UI
│   └── settings/                # 设置标签页 UI
├── shared/                      # 共享 UI 组件和模态框
│   ├── components/              # 输入工具栏组件、下拉菜单、选中高亮
│   ├── mention/                 # @提及下拉控制器
│   ├── modals/                  # 指令模态框
│   └── icons.ts                 # 共享 SVG 图标
├── i18n/                        # 国际化（10 种语言）
├── utils/                       # 模块化工具函数
└── style/                       # 模块化 CSS（→ styles.css）
```

## 路线图

- [x] Claude Code 插件支持
- [x] 自定义代理（子代理）支持
- [x] Chrome 中的 Claude 支持
- [x] `/compact` 命令
- [x] 计划模式
- [x] `rewind` 和 `fork` 支持（包括 `/fork` 命令）
- [x] `!command` 支持
- [x] 工具渲染器优化
- [x] 支持 100 万上下文的 Opus 和 Sonnet 模型
- [x] Sandbox 模式（自动切换 Haiku + 限制外部访问）
- [x] 拖拽 vault 文件到输入框快速切换上下文
- [x] 标题栏会话标题显示
- [ ] Codex SDK 集成
- [ ] 钩子及其他高级功能
- [ ] 更多功能即将推出！

## 许可证

基于 [MIT 许可证](LICENSE) 授权。

## 致谢

- [Obsidian](https://obsidian.md) 提供插件 API
- [Anthropic](https://anthropic.com) 提供 Claude 和 [Claude Agent SDK](https://platform.claude.com/docs/en/agent-sdk/overview)
- 原项目 [YishenTu/claudian](https://github.com/YishenTu/claudian) 提供基础实现
