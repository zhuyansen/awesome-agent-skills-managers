# Awesome Agent Skills Managers

[English](README.md)

**查找、安装、同步、整理 agent skill** 的开源工具,覆盖 Claude Code、Codex、Cursor 等编程 agent:命令行安装器、桌面应用、市场与目录、团队管理。共 176 个仓库,每个都由 [Agent Skills Hub](https://agentskillshub.top?utm_source=github&utm_medium=awesome-list) 读过 README 并做了安全评级。

带类型筛选的在线页面:**[https://agentskillshub.top/best/skill-management-tools/](https://agentskillshub.top/best/skill-management-tools/?utm_source=github&utm_medium=awesome-list)** · 每 8 小时刷新

## 到底装哪个

我们实跑了其中 16 个(14 个出了结果),结论如下。[完整实测结果](#tested)在下面。

- 🥇 **首选，装这个: [asm](https://github.com/luongnv89/asm)** `npm install -g agent-skill-manager`  
  14 个里唯一把带 curl | sh 脚本的 skill 标成高风险、默认不装的。一条命令装一整个文件夹的 skill，能删干净，也能装到 Codex。
- 🥈 **要在多个 agent 之间同步: [skillshare](https://github.com/runkids/skillshare)**  
  每次安装都会审计，把那个脚本报成了 HIGH，但你不拦它就照装。删掉的 skill 进回收站保留 7 天，一次 sync 覆盖所有 agent。
- 🥉 **团队想要清单和锁文件: [apm](https://github.com/microsoft/apm)** `pip install apm-cli`  
  包管理器：skill 写在清单里，装和删都精确。格式不合规的 skill 会被它拒收。它不对脚本做任何提示，所以加之前先读一遍。

**需要删 skill 的话别选:** skillfile (remove 只改清单，已装的文件夹留在原地); agent-skill-sync (按设计从不删除).

不管选哪个：14 个里有 12 个遇到带 curl | sh 脚本的 skill 不会停。安装前先看它的 scripts 文件夹，或者在本站查它的评级。

*排名规则：先看遇到风险 skill 怎么处理，再看能不能删干净，再看能不能同步到 Codex，最后看 GitHub 星数。*


## 这些管理工具长什么样

<table>
<tr>
<td align="center" valign="top" width="33%"><b>🧱 综合管理</b><br><sub>27 个仓库</sub><br><br><a href="https://github.com/pr-pm/prpm"><img src="assets/previews/pr-pm__prpm.gif" width="260" alt="pr-pm/prpm"></a><br><sub>管理整套 agent 配置:skill、MCP、提示词和设置。</sub><br><a href="#type-general"><b>查看列表 →</b></a></td>
<td align="center" valign="top" width="33%"><b>⌨️ 命令行安装</b><br><sub>54 个仓库</sub><br><br><a href="https://github.com/taito-project/taito"><img src="assets/previews/taito-project__taito.gif" width="260" alt="taito-project/taito"></a><br><sub>在终端里添加、删除、更新 skill。</sub><br><a href="#type-cli"><b>查看列表 →</b></a></td>
<td align="center" valign="top" width="33%"><b>🔄 多 Agent 同步</b><br><sub>9 个仓库</sub><br><br><sub>一份 skill 在多个 agent、多台机器间同步。</sub><br><a href="#type-sync"><b>查看列表 →</b></a></td>
</tr>
<tr>
<td align="center" valign="top" width="33%"><b>🖥 桌面与界面</b><br><sub>44 个仓库</sub><br><br><a href="https://github.com/Dimillian/CodexSkillManager"><img src="assets/previews/Dimillian__CodexSkillManager.jpg" width="260" alt="Dimillian/CodexSkillManager"></a><br><sub>桌面、网页和终端界面的 skill 管理应用。</sub><br><a href="#type-app"><b>查看列表 →</b></a></td>
<td align="center" valign="top" width="33%"><b>🔎 市场与目录</b><br><sub>37 个仓库</sub><br><br><sub>skill 的市场、目录和搜索引擎。</sub><br><a href="#type-registry"><b>查看列表 →</b></a></td>
<td align="center" valign="top" width="33%"><b>👥 团队管理</b><br><sub>5 个仓库</sub><br><br><sub>团队内的共享、版本和权限管理。</sub><br><a href="#type-team"><b>查看列表 →</b></a></td>
</tr>
</table>

## 目录

- [🧪 端到端实测](#tested)
- [🧱 综合管理](#type-general) (27)
- [⌨️ 命令行安装](#type-cli) (54)
- [🔄 多 Agent 同步](#type-sync) (9)
- [🖥 桌面与界面](#type-app) (44)
- [🔎 市场与目录](#type-registry) (37)
- [👥 团队管理](#type-team) (5)

## 什么样的仓库能上榜

1. 它管理 agent 的 skill 或插件:查找、安装、同步、更新或分享。单个 skill 或 skill 合集不算管理工具。
2. 它是能安装或运行的软件,不是链接合集或空仓库。
3. 它有 README。没有 README 就没法评级。
4. 50 星及以上只看是否切题;50 星以下还要过 README 质量线(展示效果、一条命令上手、说清产出、文档完整),并且至少 5 星。

这些问题由决策模型逐个读 README 回答,不是人工挑选。卡在线上的仓库可能判到任一边,归错了请提 issue。

<a id="tested"></a>
## 🧪 端到端实测

2026-10-09 我们实跑了其中 16 个,14 个可以评判。每个在用完即删的沙箱里由 Claude Code (Claude Opus 5.5) 调用,做同一件事:装 20 个测试 skill,再装一个带 `curl | sh` 安装脚本的 skill,删到只剩 5 个,并把这 5 个同步给 Codex。每一步之后都测了磁盘上有什么、Claude Code 加载了多少 token。

**发现:** 14 个里只有 1 个在风险 skill 面前停下(asm,默认不装);12 个没有任何警告就装了。上下文成本没有拉开差距:装 20 个 skill,每次会话多 345 到 396 个 token,用哪个工具都一样。

| # | 工具 | ★ | 遇到带 curl \| sh 脚本的 skill | 能删干净 | 同步到 Codex | 20 个 skill 每次会话多占 token | |
|---|---|---|---|---|---|---|---|
| 1 | [asm](https://github.com/luongnv89/asm) | 952 | 警告,默认不装 | 能 | 能 | +345 | [证据](https://agentskillshub.top/best-runs/skillmgr/luongnv89__asm.html) |
| 2 | [skillshare](https://github.com/runkids/skillshare) | 2,715 | 警告了,照装 | 能 | 能 | +382 | [证据](https://agentskillshub.top/best-runs/skillmgr/runkids__skillshare.html) |
| 3 | [apm](https://github.com/microsoft/apm) | 3,954 | 只显示来源,照装 | 能 | 能 | +345 | [证据](https://agentskillshub.top/best-runs/skillmgr/microsoft__apm.html) |
| 4 | [mcptoon](https://github.com/activeing123/mcptoon) | 214 | 只显示来源,照装 | 能 | 能 | +350 | [证据](https://agentskillshub.top/best-runs/skillmgr/activeing123__mcptoon.html) |
| 5 | [kasetto](https://github.com/pivoshenko/kasetto) | 209 | 只显示来源,照装 | 能 | 能 | +345 | [证据](https://agentskillshub.top/best-runs/skillmgr/pivoshenko__kasetto.html) |
| 6 | [skills-link](https://github.com/shanliuling/skills-link) | 198 | 只显示来源,照装 | 能 | 只同步到已安装的 agent | +345 | [证据](https://agentskillshub.top/best-runs/skillmgr/shanliuling__skills-link.html) |
| 7 | [agent-skills-cli](https://github.com/Karanjot786/agent-skills-cli) | 182 | 只显示来源,照装 | 能 | 能 | +345 | [证据](https://agentskillshub.top/best-runs/skillmgr/Karanjot786__agent-skills-cli.html) |
| 8 | [skills-cli](https://github.com/dhruvwill/skills-cli) | 14 | 只显示来源,照装 | 能 | 能 | +345 | [证据](https://agentskillshub.top/best-runs/skillmgr/dhruvwill__skills-cli.html) |
| 9 | [skillfile](https://github.com/eljulians/skillfile) | 173 | 只显示来源,照装 | 不能 | 能 | +349 | [证据](https://agentskillshub.top/best-runs/skillmgr/eljulians__skillfile.html) |
| 10 | [ai-agent-skills](https://github.com/MoizIbnYousaf/ai-agent-skills) | 1,147 | 一声不吭就装了 | 能 | 能 | +345 | [证据](https://agentskillshub.top/best-runs/skillmgr/MoizIbnYousaf__ai-agent-skills.html) |
| 11 | [skillfish](https://github.com/knoxgraeme/skillfish) | 322 | 一声不吭就装了 | 能 | 只同步到已安装的 agent | +345 | [证据](https://agentskillshub.top/best-runs/skillmgr/knoxgraeme__skillfish.html) |
| 12 | [skill-flow](https://github.com/VintLin/skill-flow) | 262 | 一声不吭就装了 | 能 | 只同步到已安装的 agent | +345 | [证据](https://agentskillshub.top/best-runs/skillmgr/VintLin__skill-flow.html) |
| 13 | [skills-management](https://github.com/nnnggel/skills-management) | 128 | 一声不吭就装了 | 能 | 能 | +396 | [证据](https://agentskillshub.top/best-runs/skillmgr/nnnggel__skills-management.html) |
| 14 | [agent-skill-sync](https://github.com/kina-cmd/agent-skill-sync) | 101 | 一声不吭就装了 | 不能 | 能 | +345 | [证据](https://agentskillshub.top/best-runs/skillmgr/kina-cmd__agent-skill-sync.html) |

**跑了,但这轮实测评不了:** capa (只装到项目目录（./.claude/skills），不装全局；它在项目里装好、清理并同步了，但我们的测量只看用户主目录。); skill-manager (不是安装工具：它是一个 skill，分析已装的 skill，并在 CLAUDE.md 里列出建议停用的。)

[全部结果、提示词和脚本](https://github.com/zhuyansen/agent-skills-hub/blob/main/ops/skillmgr-runs/RESULTS.md) · [https://agentskillshub.top/best/skill-management-tools/#test-results](https://agentskillshub.top/best/skill-management-tools/?utm_source=github&utm_medium=awesome-list#test-results)

<a id="type-general"></a>
## 🧱 综合管理

[在在线页面打开这一类,按星数排序 →](https://agentskillshub.top/best/skill-management-tools/?utm_source=github&utm_medium=awesome-list#type-general)

<table><tr>
<td align="center" valign="top"><a href="https://github.com/luml-ai/AGENTS.lock"><img src="assets/previews/luml-ai__AGENTS.lock.jpg" width="260" alt="luml-ai/AGENTS.lock"></a><br><sub><a href="https://github.com/luml-ai/AGENTS.lock">luml-ai/AGENTS.lock</a></sub></td>
</tr></table>

| 仓库 | 星数 | 做什么 | 安全评级 |
|---|---:|---|---|
| [microsoft/apm](https://github.com/microsoft/apm) | 4.0k | Agent 包管理器 | [SAFE](https://agentskillshub.top/skill/microsoft/apm/?utm_source=github&utm_medium=awesome-list) |
| [runkids/skillshare](https://github.com/runkids/skillshare) | 2.8k | 统一管理 AI 编程配置、skills、agents、rules、MCP 连接和 hooks，支持桌面应用或 CLI。 | [SAFE](https://agentskillshub.top/skill/runkids/skillshare/?utm_source=github&utm_medium=awesome-list) |
| [infragate/capa](https://github.com/infragate/capa) | 724 | capabilities.yaml 将 skill、工具、规则、子 agent、MCP 服务和插件接入 Cursor、Claude Code、Codex 等3… | [SAFE](https://agentskillshub.top/skill/infragate/capa/?utm_source=github&utm_medium=awesome-list) |
| [RealZST/HarnessKit](https://github.com/RealZST/HarnessKit) | 456 | 不只是 skill 管理器：跨 AI coding agent 管理 skill、MCP servers、plugins、hooks、CLIs、configs… | [SAFE](https://agentskillshub.top/skill/RealZST/HarnessKit/?utm_source=github&utm_medium=awesome-list) |
| [pivoshenko/kasetto](https://github.com/pivoshenko/kasetto) | 209 | 用 Rust 编写的声明式 AI agent 环境管理器 | [SAFE](https://agentskillshub.top/skill/pivoshenko/kasetto/?utm_source=github&utm_medium=awesome-list) |
| [sandbaseai/sandbase-skills](https://github.com/sandbaseai/sandbase-skills) | 203 | 88 个可安装的开源 Agent Skills，适用于研究、社交情报、营销和业务流程，兼容 Codex、Claude Code、Cursor、Gemini C… | [SAFE](https://agentskillshub.top/skill/sandbaseai/sandbase-skills/?utm_source=github&utm_medium=awesome-list) |
| [pr-pm/prpm](https://github.com/pr-pm/prpm) | 122 | AI 编程工具的通用注册表 | [SAFE](https://agentskillshub.top/skill/pr-pm/prpm/?utm_source=github&utm_medium=awesome-list) |
| [vanillagreencom/kendex](https://github.com/vanillagreencom/kendex) | 84 | 适用于 agent、skill、hook 和扩展的包管理器。编写一次，安装到所有 harness。包含 QOL 功能。 | [SAFE](https://agentskillshub.top/skill/vanillagreencom/kendex/?utm_source=github&utm_medium=awesome-list) |
| [mensfeld/craftdesk](https://github.com/mensfeld/craftdesk) | 67 | Claude Code 的 skill、agent 等 AI 资源包管理器 | [SAFE](https://agentskillshub.top/skill/mensfeld/craftdesk/?utm_source=github&utm_medium=awesome-list) |
| [itlackey/akm](https://github.com/itlackey/akm) | 62 | Agent Knowledge Manager (akm)：管理 AI agent 知识、记忆和 skill 的 CLI 工具。 | [SAFE](https://agentskillshub.top/skill/itlackey/akm/?utm_source=github&utm_medium=awesome-list) |
| [egebese/skill-manager](https://github.com/egebese/skill-manager) | 38 | 按项目自动禁用无关的 Claude Code skills，每次对话节省约 4,000 tokens。检测技术栈、评估 skill 相关性并注入 CLAUDE… | [SAFE](https://agentskillshub.top/skill/egebese/skill-manager/?utm_source=github&utm_medium=awesome-list) |
| [GrubbyLee/skill-manager](https://github.com/GrubbyLee/skill-manager) | 29 | 零依赖 CLI，用于扫描、推荐、去重、审计和可视化 Claude Code / Codex skill 与 MCP 服务器。 | [SAFE](https://agentskillshub.top/skill/GrubbyLee/skill-manager/?utm_source=github&utm_medium=awesome-list) |
| [seed-forge/harness-ai-kit](https://github.com/seed-forge/harness-ai-kit) | 25 | AI agent 资产管理器：42 个 skill、5 个 CLI、1 个插件，支持 Codex、Claude Code、Cursor、Kiro、DSH，涵盖… | [SAFE](https://agentskillshub.top/skill/seed-forge/harness-ai-kit/?utm_source=github&utm_medium=awesome-list) |
| [luml-ai/AGENTS.lock](https://github.com/luml-ai/AGENTS.lock) | 21 | Agents/Skills/MCPs 的包管理器 | [SAFE](https://agentskillshub.top/skill/luml-ai/AGENTS.lock/?utm_source=github&utm_medium=awesome-list) |
| [grimoire-rs/grimoire](https://github.com/grimoire-rs/grimoire) | 14 | AI-agent 配置管理器 grim：管理 skills、rules、agents、MCP servers、bundles，使用 OCI registry，… | [SAFE](https://agentskillshub.top/skill/grimoire-rs/grimoire/?utm_source=github&utm_medium=awesome-list) |
| [barleviatias/toolkit-ai](https://github.com/barleviatias/toolkit-ai) | 12 | AI 编程助手的包管理器，跨 Claude Code、Codex、Copilot 和 Cursor 管理 skill、agent 与 MCP | [SAFE](https://agentskillshub.top/skill/barleviatias/toolkit-ai/?utm_source=github&utm_medium=awesome-list) |
| [xhyqaq/skill-manager](https://github.com/xhyqaq/skill-manager) | 9 | 用于管理 skills。 | [SAFE](https://agentskillshub.top/skill/xhyqaq/skill-manager/?utm_source=github&utm_medium=awesome-list) |
| [Brattlof/skillet](https://github.com/Brattlof/skillet) | 8 | MCP 服务器、Agent Skills（SKILL.md）和 Claude Code 扩展的包管理器，支持 Claude Code、Cursor、Codex… | [SAFE](https://agentskillshub.top/skill/Brattlof/skillet/?utm_source=github&utm_medium=awesome-list) |
| [kunaltulsidasani/claude-reimagined](https://github.com/kunaltulsidasani/claude-reimagined) | 8 | 一键安装Claude Code、RTK、context-mode等，含hooks、MCP和39+skill，支持macOS/Linux | [SAFE](https://agentskillshub.top/skill/kunaltulsidasani/claude-reimagined/?utm_source=github&utm_medium=awesome-list) |
| [frmlabz/omnidev](https://github.com/frmlabz/omnidev) | 7 | 面向 coding agent 的能力包管理器，支持跨所有提供商发现、安装和管理 commands、subagents、skill 及自定义功能。 | [SAFE](https://agentskillshub.top/skill/frmlabz/omnidev/?utm_source=github&utm_medium=awesome-list) |
| [Asher-pro/skill-installer](https://github.com/Asher-pro/skill-installer) | 6 | 在 Claude Code 中安装任意 skill。 | [SAFE](https://agentskillshub.top/skill/Asher-pro/skill-installer/?utm_source=github&utm_medium=awesome-list) |
| [CoderAndyLee/skills-manager](https://github.com/CoderAndyLee/skills-manager) | 6 | 以安全为先的 Agent Skills 清单、审计、迁移、部署与恢复。 | [SAFE](https://agentskillshub.top/skill/CoderAndyLee/skills-manager/?utm_source=github&utm_medium=awesome-list) |
| [VersoXBT/skill-manager](https://github.com/VersoXBT/skill-manager) | 6 | Claude Code 插件——盘点已安装的所有 skill，检查结构并查找更新。免费、零依赖。 | [SAFE](https://agentskillshub.top/skill/VersoXBT/skill-manager/?utm_source=github&utm_medium=awesome-list) |
| [caioross/skilldepot-go](https://github.com/caioross/skilldepot-go) | 6 | SkillDepot 的官方 Go SDK，用于 AI Agent 技能市场 | [SAFE](https://agentskillshub.top/skill/caioross/skilldepot-go/?utm_source=github&utm_medium=awesome-list) |
| [lathe-cli/kitup](https://github.com/lathe-cli/kitup) | 6 | 用于捆绑式 Agent Skills 的共享安装器 SDK。 | [SAFE](https://agentskillshub.top/skill/lathe-cli/kitup/?utm_source=github&utm_medium=awesome-list) |
| [robertoatila/jarvis-skill-registry](https://github.com/robertoatila/jarvis-skill-registry) | 6 | 本地优先的 AI agent 认知运行时：有界上下文、持久记忆、工具/模型路由与验证执行。 | [SAFE](https://agentskillshub.top/skill/robertoatila/jarvis-skill-registry/?utm_source=github&utm_medium=awesome-list) |
| [lonewolfyx/skills-config](https://github.com/lonewolfyx/skills-config) | 5 | 面向 AI 编程 agent 的声明式 Git skill 管理器，在 skills.config.ts 中定义 skill，并在 npm install/p… | [SAFE](https://agentskillshub.top/skill/lonewolfyx/skills-config/?utm_source=github&utm_medium=awesome-list) |

<a id="type-cli"></a>
## ⌨️ 命令行安装

[在在线页面打开这一类,按星数排序 →](https://agentskillshub.top/best/skill-management-tools/?utm_source=github&utm_medium=awesome-list#type-cli)

<table><tr>
<td align="center" valign="top"><a href="https://github.com/yeasy/ask"><img src="assets/previews/yeasy__ask.jpg" width="260" alt="yeasy/ask"></a><br><sub><a href="https://github.com/yeasy/ask">yeasy/ask</a></sub></td>
</tr></table>

| 仓库 | 星数 | 做什么 | 安全评级 |
|---|---:|---|---|
| [MoizIbnYousaf/ai-agent-skills](https://github.com/MoizIbnYousaf/ai-agent-skills) | 1.1k | AI 编程 agent 通用 skill 安装与包管理器。一条命令支持 12+ 个运行时。npx ai-agent-skills | [SAFE](https://agentskillshub.top/skill/MoizIbnYousaf/ai-agent-skills/?utm_source=github&utm_medium=awesome-list) |
| [pathintegral-institute/mcpm.sh](https://github.com/pathintegral-institute/mcpm.sh) | 1.0k | CLI MCP 包管理器与注册中心，支持所有平台和客户端。搜索并配置 MCP servers，提供高级 Router 与 Profile 功能。 | [SAFE](https://agentskillshub.top/skill/pathintegral-institute/mcpm.sh/?utm_source=github&utm_medium=awesome-list) |
| [luongnv89/asm](https://github.com/luongnv89/asm) | 954 | AI 编程 agent 的通用 skill 管理器。 | [SAFE](https://agentskillshub.top/skill/luongnv89/asm/?utm_source=github&utm_medium=awesome-list) |
| [knoxgraeme/skillfish](https://github.com/knoxgraeme/skillfish) | 323 | AI 编程 agent 的 skill 管理器，跨 Claude Code、Cursor、Copilot 等安装、更新和同步 skill。 | [SAFE](https://agentskillshub.top/skill/knoxgraeme/skillfish/?utm_source=github&utm_medium=awesome-list) |
| [VintLin/skill-flow](https://github.com/VintLin/skill-flow) | 262 | 安装、管理并在 Claude Code、Cursor、Copilot 等编码 agent 间共享 skill。 | [SAFE](https://agentskillshub.top/skill/VintLin/skill-flow/?utm_source=github&utm_medium=awesome-list) |
| [activeing123/mcptoon](https://github.com/activeing123/mcptoon) | 218 | 零依赖 CLI：管理 MCP server 和 agent skill，优化 token、工具发现与上下文压缩。 | [SAFE](https://agentskillshub.top/skill/activeing123/mcptoon/?utm_source=github&utm_medium=awesome-list) |
| [shenysun/skills-manager](https://github.com/shenysun/skills-manager) | 197 | Skills Manager：从对话管理 agent skill，支持安装、导入、分发、更新和补全来源信息；适用于 Claude Code、Codex、Cur… | [SAFE](https://agentskillshub.top/skill/shenysun/skills-manager/?utm_source=github&utm_medium=awesome-list) |
| [Karanjot786/agent-skills-cli](https://github.com/Karanjot786/agent-skills-cli) | 182 | Agent Skills 通用 CLI：从 SkillsMP 获取并同步到 Cursor、Claude Code、GitHub Copilot、OpenAI… | [SAFE](https://agentskillshub.top/skill/Karanjot786/agent-skills-cli/?utm_source=github&utm_medium=awesome-list) |
| [eljulians/skillfile](https://github.com/eljulians/skillfile) | 174 | 搜索 110K+ 社区 skills，以声明式方式安装和跟踪，并部署到 Claude Code、Codex、Cursor、Antigravity 等 AI 编… | [SAFE](https://agentskillshub.top/skill/eljulians/skillfile/?utm_source=github&utm_medium=awesome-list) |
| [LobsterTrap/lola](https://github.com/LobsterTrap/lola) | 131 | Lola 可将 AI Context Modules 或 skill 打包，供多个 AI 助手使用。编写一次 skill，到处运行。 | [SAFE](https://agentskillshub.top/skill/LobsterTrap/lola/?utm_source=github&utm_medium=awesome-list) |
| [Soul-Brews-Studio/arra-oracle-skills-cli](https://github.com/Soul-Brews-Studio/arra-oracle-skills-cli) | 123 | 将 Oracle skills 安装到 Claude Code、OpenCode、Cursor 和 12+ 个 AI 编程代理 | [SAFE](https://agentskillshub.top/skill/Soul-Brews-Studio/arra-oracle-skills-cli/?utm_source=github&utm_medium=awesome-list) |
| [jacob-bd/universal-skills-manager](https://github.com/jacob-bd/universal-skills-manager) | 111 | AI 编程助手技能管理器：从 SkillsMP.com、SkillHub 和 ClawHub 发现、安装、同步 skill，支持 12 种 AI 工具及安全扫… | [SAFE](https://agentskillshub.top/skill/jacob-bd/universal-skills-manager/?utm_source=github&utm_medium=awesome-list) |
| [spences10/mcpick](https://github.com/spences10/mcpick) | 94 | 跨供应商 MCP 配置管理器：用一个 CLI 管理所有 AI 客户端中的 MCP 服务器和 skill，支持添加、切换和审计，内置安全机制 | [SAFE](https://agentskillshub.top/skill/spences10/mcpick/?utm_source=github&utm_medium=awesome-list) |
| [rolecraft-sh/rolecraft](https://github.com/rolecraft-sh/rolecraft) | 91 | AI agent 的 skill 管理器；每次安装执行安全扫描，管理 87 个 agent 的 skill 和 MCP servers；零依赖 CLI。 | [SAFE](https://agentskillshub.top/skill/rolecraft-sh/rolecraft/?utm_source=github&utm_medium=awesome-list) |
| [arkylab/aspm](https://github.com/arkylab/aspm) | 82 | 面向 AI 辅助开发的 Git 包管理器，类似 npm，支持 skills、agents、commands、hooks 等 AI 资源类型。 | [SAFE](https://agentskillshub.top/skill/arkylab/aspm/?utm_source=github&utm_medium=awesome-list) |
| [reorx/skm](https://github.com/reorx/skm) | 78 | 更好的 skill 管理器 | [SAFE](https://agentskillshub.top/skill/reorx/skm/?utm_source=github&utm_medium=awesome-list) |
| [Autoloops/upskill](https://github.com/Autoloops/upskill) | 69 | Autoloops upskill 注册表的 CLI 和 skill，在终端搜索、检查、报告和发布 agent skill | [SAFE](https://agentskillshub.top/skill/Autoloops/upskill/?utm_source=github&utm_medium=awesome-list) |
| [lingbol088-spec/auto-skill-installer](https://github.com/lingbol088-spec/auto-skill-installer) | 68 | AI agent skill 自动发现与安装器 | [SAFE](https://agentskillshub.top/skill/lingbol088-spec/auto-skill-installer/?utm_source=github&utm_medium=awesome-list) |
| [kcchien/skills-cli](https://github.com/kcchien/skills-cli) | 65 | 用于管理 Claude Code 和 Claude Desktop skill 的跨平台 CLI | [SAFE](https://agentskillshub.top/skill/kcchien/skills-cli/?utm_source=github&utm_medium=awesome-list) |
| [with-logic/crew](https://github.com/with-logic/crew) | 48 | agent skill 包管理器 | [SAFE](https://agentskillshub.top/skill/with-logic/crew/?utm_source=github&utm_medium=awesome-list) |
| [nattergabriel/reseed](https://github.com/nattergabriel/reseed) | 46 | 用于在项目间管理和分发 agent skills 的 CLI 工具 | [SAFE](https://agentskillshub.top/skill/nattergabriel/reseed/?utm_source=github&utm_medium=awesome-list) |
| [EfanWang/skills-manager](https://github.com/EfanWang/skills-manager) | 30 | 管理、安装、更新和追踪 agent skills（Claude Code、Cursor、Codex CLI） | [SAFE](https://agentskillshub.top/skill/EfanWang/skills-manager/?utm_source=github&utm_medium=awesome-list) |
| [Z-Bra0/Ski](https://github.com/Z-Bra0/Ski) | 29 | 通过 manifest、lockfile 和共享存储，从 Git 安装 AI agent skills 到 Claude、Codex、Cursor 和 Ope… | [SAFE](https://agentskillshub.top/skill/Z-Bra0/Ski/?utm_source=github&utm_medium=awesome-list) |
| [yeasy/ask](https://github.com/yeasy/ask) | 26 | Agent skill 包管理器：支持搜索、查询、安装和卸载。 | [SAFE](https://agentskillshub.top/skill/yeasy/ask/?utm_source=github&utm_medium=awesome-list) |
| [try-agora/qvr](https://github.com/try-agora/qvr) | 24 | quiver (qvr)：开源、Git 原生的 agent skill 包管理器，锁文件优先、兼容任意 registry，支持可复现的 agent 工作流。 | [CAUTION](https://agentskillshub.top/skill/try-agora/qvr/?utm_source=github&utm_medium=awesome-list) |
| [tiandee/awesome-skills-hub](https://github.com/tiandee/awesome-skills-hub) | 18 | AI IDE 的 skill 和规则包管理器，集中管理提示词并同步至 Antigravity、Cursor、Windsurf 和 Claude。 | [SAFE](https://agentskillshub.top/skill/tiandee/awesome-skills-hub/?utm_source=github&utm_medium=awesome-list) |
| [sbroenne/skillpm](https://github.com/sbroenne/skillpm) | 14 | 基于 npm 的 Agent Skills 包管理器。 | [SAFE](https://agentskillshub.top/skill/sbroenne/skillpm/?utm_source=github&utm_medium=awesome-list) |
| [avibe-bot/askill](https://github.com/avibe-bot/askill) | 13 | AI agent skill 包管理器 | [SAFE](https://agentskillshub.top/skill/avibe-bot/askill/?utm_source=github&utm_medium=awesome-list) |
| [jtianling/skills-manager](https://github.com/jtianling/skills-manager) | 13 | AI 编程工具的统一 skill 管理器，可部署到多个 AI 工具。 | [SAFE](https://agentskillshub.top/skill/jtianling/skills-manager/?utm_source=github&utm_medium=awesome-list) |
| [taito-project/taito](https://github.com/taito-project/taito) | 13 | taito 是本地 AI SKILL/AGENT 捆绑包的包管理器 | [SAFE](https://agentskillshub.top/skill/taito-project/taito/?utm_source=github&utm_medium=awesome-list) |
| [chrisvoncsefalvay/skillman](https://github.com/chrisvoncsefalvay/skillman) | 11 | Claude 技能管理器 | [SAFE](https://agentskillshub.top/skill/chrisvoncsefalvay/skillman/?utm_source=github&utm_medium=awesome-list) |
| [alexastrum/skl](https://github.com/alexastrum/skl) | 10 | 用 Go 编写的单二进制 Agent Skills CLI 管理器 | [SAFE](https://agentskillshub.top/skill/alexastrum/skl/?utm_source=github&utm_medium=awesome-list) |
| [ariasbruno/skillbase](https://github.com/ariasbruno/skillbase) | 10 | 本地 AI skill 管理器。按工作区仅链接必要内容，避免上下文过载。 | [SAFE](https://agentskillshub.top/skill/ariasbruno/skillbase/?utm_source=github&utm_medium=awesome-list) |
| [ashutoshsrivastava17/skill-library](https://github.com/ashutoshsrivastava17/skill-library) | 9 | 418个AI agent skills，覆盖31领域54角色；开源skill库支持多种LLM API。 | [SAFE](https://agentskillshub.top/skill/ashutoshsrivastava17/skill-library/?utm_source=github&utm_medium=awesome-list) |
| [itaywol/adeptability](https://github.com/itaywol/adeptability) | 9 | skill CLI：同步 agent skill 至 Claude Code、Cursor、Copilot、Codex、OpenCode，含扫描和哈希检测。 | [SAFE](https://agentskillshub.top/skill/itaywol/adeptability/?utm_source=github&utm_medium=awesome-list) |
| [joabgonzalez/ai-agents-skills](https://github.com/joabgonzalez/ai-agents-skills) | 9 | 用于在多个编码助手间分发 50+ 个 AI agent skill 的模块化 CLI | [SAFE](https://agentskillshub.top/skill/joabgonzalez/ai-agents-skills/?utm_source=github&utm_medium=awesome-list) |
| [singhharsh1708/kitbash](https://github.com/singhharsh1708/kitbash) | 9 | AI agent skills 的包管理器和编译器——编写一次，可在 Claude Code、Cursor、Codex、Copilot、Gemini CLI… | [SAFE](https://agentskillshub.top/skill/singhharsh1708/kitbash/?utm_source=github&utm_medium=awesome-list) |
| [osolmaz/skillflag](https://github.com/osolmaz/skillflag) | 8 | 用于列出和安装 agent skill 的 CLI 标志约定。随包发布工具的 skill，无需注册中心！ | [SAFE](https://agentskillshub.top/skill/osolmaz/skillflag/?utm_source=github&utm_medium=awesome-list) |
| [akshayaggarwal99/agentskills](https://github.com/akshayaggarwal99/agentskills) | 7 | 用于浏览和安装 anthropics/skills 中 skill 的 CLI | [SAFE](https://agentskillshub.top/skill/akshayaggarwal99/agentskills/?utm_source=github&utm_medium=awesome-list) |
| [dafage10086/agent-skill-manager](https://github.com/dafage10086/agent-skill-manager) | 7 | 涵盖渗透、逆向、注入、破解和游戏辅助脚本技能。 | [SAFE](https://agentskillshub.top/skill/dafage10086/agent-skill-manager/?utm_source=github&utm_medium=awesome-list) |
| [dcodesdev/clawd](https://github.com/dcodesdev/clawd) | 7 | 开源 Claude skill 集合。用于发现、搜索和安装扩展 Claude 能力的 Rust CLI 工具。 | [SAFE](https://agentskillshub.top/skill/dcodesdev/clawd/?utm_source=github&utm_medium=awesome-list) |
| [devrimcavusoglu/skern](https://github.com/devrimcavusoglu/skern) | 7 | 面向 AI 驱动开发 Agent 的批量 skill 管理器 | [SAFE](https://agentskillshub.top/skill/devrimcavusoglu/skern/?utm_source=github&utm_medium=awesome-list) |
| [xu-xiang/oneskill](https://github.com/xu-xiang/oneskill) | 7 | AI Agent 应用商店，发现并安装适用于 Claude Code、Cursor、Windsurf、Aider、Codex 和 Gemini 的 Skills | [SAFE](https://agentskillshub.top/skill/xu-xiang/oneskill/?utm_source=github&utm_medium=awesome-list) |
| [EYH0602/skillshub](https://github.com/EYH0602/skillshub) | 6 | 面向 agent skill 的统一包管理器，支持版本控制。 | [SAFE](https://agentskillshub.top/skill/EYH0602/skillshub/?utm_source=github&utm_medium=awesome-list) |
| [anyt-io/pspm-cli](https://github.com/anyt-io/pspm-cli) | 6 | 用于 agent skills 的 NPM：支持 skill 版本控制、私有 skills、lock files 等 | [SAFE](https://agentskillshub.top/skill/anyt-io/pspm-cli/?utm_source=github&utm_medium=awesome-list) |
| [fagom/agentkit](https://github.com/fagom/agentkit) | 6 | 用于 Claude AI agent skills 的 CLI 包管理器 | [SAFE](https://agentskillshub.top/skill/fagom/agentkit/?utm_source=github&utm_medium=awesome-list) |
| [glapsfun/gskill](https://github.com/glapsfun/gskill) | 6 | Gskill 是用于智能体 AI skill 的可复现包管理器 | [SAFE](https://agentskillshub.top/skill/glapsfun/gskill/?utm_source=github&utm_medium=awesome-list) |
| [gofastskill/fastskill](https://github.com/gofastskill/fastskill) | 6 | Agent AI Skills 的包管理器和运维工具包。FastSkill 支持技能的发现、安装、版本管理和部署。 | [SAFE](https://agentskillshub.top/skill/gofastskill/fastskill/?utm_source=github&utm_medium=awesome-list) |
| [hairyf/skills-manifest](https://github.com/hairyf/skills-manifest) | 6 | 轻量级 skill 清单管理器，支持项目级 skill 同步和协作配置。 | [SAFE](https://agentskillshub.top/skill/hairyf/skills-manifest/?utm_source=github&utm_medium=awesome-list) |
| [osulivan/skill4agent-cli](https://github.com/osulivan/skill4agent-cli) | 6 | skill4agent.com 提供的安装 Agent Skills 的命令行工具 | [SAFE](https://agentskillshub.top/skill/osulivan/skill4agent-cli/?utm_source=github&utm_medium=awesome-list) |
| [AruneshSingh/konstruct](https://github.com/AruneshSingh/konstruct) | 5 | AI agent skill 包管理器。 | [SAFE](https://agentskillshub.top/skill/AruneshSingh/konstruct/?utm_source=github&utm_medium=awesome-list) |
| [Bind/skillz.sh](https://github.com/Bind/skillz.sh) | 5 | agent 技能管理器 | [SAFE](https://agentskillshub.top/skill/Bind/skillz.sh/?utm_source=github&utm_medium=awesome-list) |
| [Xaviw/skills-manager](https://github.com/Xaviw/skills-manager) | 5 | agent skill 管理器：集中维护、按需安装并自动同步。 | [SAFE](https://agentskillshub.top/skill/Xaviw/skills-manager/?utm_source=github&utm_medium=awesome-list) |
| [tsvelovskiysv/claude-skill-router](https://github.com/tsvelovskiysv/claude-skill-router) | 5 | Claude Code Agent Skills 的语义路由器，从 65k 目录中查找并安装项目所需技能。 | [SAFE](https://agentskillshub.top/skill/tsvelovskiysv/claude-skill-router/?utm_source=github&utm_medium=awesome-list) |

<a id="type-sync"></a>
## 🔄 多 Agent 同步

[在在线页面打开这一类,按星数排序 →](https://agentskillshub.top/best/skill-management-tools/?utm_source=github&utm_medium=awesome-list#type-sync)

| 仓库 | 星数 | 做什么 | 安全评级 |
|---|---:|---|---|
| [shanliuling/skills-link](https://github.com/shanliuling/skills-link) | 197 | 用一条命令在 41+ 个 AI coding agent 间同步本地 skill。 | [SAFE](https://agentskillshub.top/skill/shanliuling/skills-link/?utm_source=github&utm_medium=awesome-list) |
| [nnnggel/skills-management](https://github.com/nnnggel/skills-management) | 128 | 管理和同步 AI coding agent skills 的 CLI 工具 | [SAFE](https://agentskillshub.top/skill/nnnggel/skills-management/?utm_source=github&utm_medium=awesome-list) |
| [kina-cmd/agent-skill-sync](https://github.com/kina-cmd/agent-skill-sync) | 101 | 扫描、分类（A/B/C/D）并同步 Codex、Claude Code、WorkBuddy 的 AI-agent SKILL.md 文件。零依赖 Python… | [SAFE](https://agentskillshub.top/skill/kina-cmd/agent-skill-sync/?utm_source=github&utm_medium=awesome-list) |
| [luna-prompts/skillnote](https://github.com/luna-prompts/skillnote) | 66 | 面向 AI 编程 agent 的开源 skill 注册中心，跨 Openclaw、Claude Code、Cursor、Codex、OpenHands、Ant… | [SAFE](https://agentskillshub.top/skill/luna-prompts/skillnote/?utm_source=github&utm_medium=awesome-list) |
| [huangrichao2020/pretty-skills](https://github.com/huangrichao2020/pretty-skills) | 54 | 跨 agent 的 skill 管理与推广工具，支持管理 skill、创建附带 PDF 或 PPT 讲解的 skill，支持各种 Agent。 | [SAFE](https://agentskillshub.top/skill/huangrichao2020/pretty-skills/?utm_source=github&utm_medium=awesome-list) |
| [dhruvwill/skills-cli](https://github.com/dhruvwill/skills-cli) | 14 | 用一条命令在所有 agent 工具间同步 AI agent skill | [SAFE](https://agentskillshub.top/skill/dhruvwill/skills-cli/?utm_source=github&utm_medium=awesome-list) |
| [tc9011/skills-manager](https://github.com/tc9011/skills-manager) | 11 | vercel-labs/skills 的 CLI 工具：同步 ~/.agents/ 到远程仓库，并自动链接 skills 到所有 agent。 | [SAFE](https://agentskillshub.top/skill/tc9011/skills-manager/?utm_source=github&utm_medium=awesome-list) |
| [AdamBartkiewicz/praxl-oss](https://github.com/AdamBartkiewicz/praxl-oss) | 9 | 开源 AI skill 管理器，在 Claude Code、Cursor、Codex、Copilot、Windsurf、Gemini 等工具间同步 SKILL… | [SAFE](https://agentskillshub.top/skill/AdamBartkiewicz/praxl-oss/?utm_source=github&utm_medium=awesome-list) |
| [Naoray/scribe](https://github.com/Naoray/scribe) | 5 | 面向 AI 编程 agent 的本地 skill 管理器。一个 SKILL.md，适配 Claude Code、Cursor、Codex、Gemini。锁文件… | [CAUTION](https://agentskillshub.top/skill/Naoray/scribe/?utm_source=github&utm_medium=awesome-list) |

<a id="type-app"></a>
## 🖥 桌面与界面

[在在线页面打开这一类,按星数排序 →](https://agentskillshub.top/best/skill-management-tools/?utm_source=github&utm_medium=awesome-list#type-app)

<table><tr>
<td align="center" valign="top"><a href="https://github.com/eatmoreduck/SkillManager"><img src="assets/previews/eatmoreduck__SkillManager.jpg" width="260" alt="eatmoreduck/SkillManager"></a><br><sub><a href="https://github.com/eatmoreduck/SkillManager">eatmoreduck/SkillManager</a></sub></td>
</tr></table>

| 仓库 | 星数 | 做什么 | 安全评级 |
|---|---:|---|---|
| [HKUDS/OpenSpace](https://github.com/HKUDS/OpenSpace) | 7.8k | OpenSpace：AI agent 的 skill 管理层 | [SAFE](https://agentskillshub.top/skill/HKUDS/OpenSpace/?utm_source=github&utm_medium=awesome-list) |
| [xingkongliang/skills-manager](https://github.com/xingkongliang/skills-manager) | 5.9k | 轻量桌面应用，用于管理、同步和整理 Claude Code、Codex、Cursor、Copilot、Gemini CLI 等 50 多种编程工具中的 AI… | [SAFE](https://agentskillshub.top/skill/xingkongliang/skills-manager/?utm_source=github&utm_medium=awesome-list) |
| [Shpigford/chops](https://github.com/Shpigford/chops) | 1.9k | macOS 应用，用于浏览、编辑和管理 Claude Code、Cursor、Codex、Windsurf 和 Amp 的 skill。 | [SAFE](https://agentskillshub.top/skill/Shpigford/chops/?utm_source=github&utm_medium=awesome-list) |
| [qufei1993/skills-hub](https://github.com/qufei1993/skills-hub) | 1.7k | 跨平台桌面应用，集中管理 Agent Skills，并同步到多个 AI 编程工具的全局 skills 目录 | [SAFE](https://agentskillshub.top/skill/qufei1993/skills-hub/?utm_source=github&utm_medium=awesome-list) |
| [Dimillian/CodexSkillManager](https://github.com/Dimillian/CodexSkillManager) | 1.4k | 用于管理 Codex skills 的 macOS 应用 | [SAFE](https://agentskillshub.top/skill/Dimillian/CodexSkillManager/?utm_source=github&utm_medium=awesome-list) |
| [skillsgate/skillsgate](https://github.com/skillsgate/skillsgate) | 1.4k | macOS≤0.7.0请手动更新：升级器可能无法重启且架构错误。0.7.2下载对应DMG：Apple Silicon选arm64，Intel选.dmg，将Sk… | [SAFE](https://agentskillshub.top/skill/skillsgate/skillsgate/?utm_source=github&utm_medium=awesome-list) |
| [skillhub-club/skillhub-desktop](https://github.com/skillhub-club/skillhub-desktop) | 599 | One desktop to manage your agent skills | [SAFE](https://agentskillshub.top/skill/skillhub-club/skillhub-desktop/?utm_source=github&utm_medium=awesome-list) |
| [buzhangsan/skills-manager-client](https://github.com/buzhangsan/skills-manager-client) | 503 | Skill Manager：管理 Claude Code Skills 的桌面应用，支持浏览、安装、导入和安全扫描。 | [SAFE](https://agentskillshub.top/skill/buzhangsan/skills-manager-client/?utm_source=github&utm_medium=awesome-list) |
| [yibie/skills-manager](https://github.com/yibie/skills-manager) | 453 | 用于在 Claude Code、Cursor、Copilot CLI、Codex、Gemini CLI 等编程 agent 间管理 skill 的原生 mac… | [SAFE](https://agentskillshub.top/skill/yibie/skills-manager/?utm_source=github&utm_medium=awesome-list) |
| [bruc3van/agent-skills-guard](https://github.com/bruc3van/agent-skills-guard) | 390 | 用于 Agent Skills 安全扫描和可视化管理的桌面应用 | [SAFE](https://agentskillshub.top/skill/bruc3van/agent-skills-guard/?utm_source=github&utm_medium=awesome-list) |
| [what1f/kitter](https://github.com/what1f/kitter) | 305 | 用 Rust 构建的轻量 Skill 管理器。一个库，仅包含各项目所需的 Skills。 | [SAFE](https://agentskillshub.top/skill/what1f/kitter/?utm_source=github&utm_medium=awesome-list) |
| [chrlsio/agent-skills](https://github.com/chrlsio/agent-skills) | 299 | 跨平台桌面应用，用于浏览、同步和管理 Claude Code、Cursor、Gemini CLI、Copilot 等平台的 AI agent skill。 | [SAFE](https://agentskillshub.top/skill/chrlsio/agent-skills/?utm_source=github&utm_medium=awesome-list) |
| [alvinunreal/lazyskills](https://github.com/alvinunreal/lazyskills) | 270 | agent 技能任务控制中心 | [SAFE](https://agentskillshub.top/skill/alvinunreal/lazyskills/?utm_source=github&utm_medium=awesome-list) |
| [scottcwy/skill-kits](https://github.com/scottcwy/skill-kits) | 201 | Skill-kits 是适用于任意 LLM 和多智能体工作流的单二进制 AI Agent Skills 管理工具。 | [SAFE](https://agentskillshub.top/skill/scottcwy/skill-kits/?utm_source=github&utm_medium=awesome-list) |
| [Rito-w/skills-manager](https://github.com/Rito-w/skills-manager) | 197 | 面向 AI IDE 的跨平台 skill 管理器。搜索 marketplace、本地下载并一键安装到 Claude、Cursor、Windsurf 等。 | [SAFE](https://agentskillshub.top/skill/Rito-w/skills-manager/?utm_source=github&utm_medium=awesome-list) |
| [tddworks/SkillsManager](https://github.com/tddworks/SkillsManager) | 170 | 用于发现、浏览和安装 AI 编程助手 skill 的 macOS 应用，管理 Claude Code 和 Codex 的 skill。 | [SAFE](https://agentskillshub.top/skill/tddworks/SkillsManager/?utm_source=github&utm_medium=awesome-list) |
| [cchao123/skills-manager](https://github.com/cchao123/skills-manager) | 125 | AI agent skill 的包管理器，支持跨 agent 共享、同步和部署。 | [SAFE](https://agentskillshub.top/skill/cchao123/skills-manager/?utm_source=github&utm_medium=awesome-list) |
| [khendzel/skills-janitor](https://github.com/khendzel/skills-janitor) | 122 | 清理 Claude Code 的 skill、subagent、MCP：移除浪费上下文内容、检测提示注入、显示 token 成本并修复删除。支持 Codex。 | [SAFE](https://agentskillshub.top/skill/khendzel/skills-janitor/?utm_source=github&utm_medium=awesome-list) |
| [luochang212/skill-zoo](https://github.com/luochang212/skill-zoo) | 117 | 桌面 Agent Skills 工具，集中存放所有 skill。 | [SAFE](https://agentskillshub.top/skill/luochang212/skill-zoo/?utm_source=github&utm_medium=awesome-list) |
| [MichengAI/dsh-skills-manager](https://github.com/MichengAI/dsh-skills-manager) | 103 | DSH Skills Manager：在 DeepSeek Harness 中加载并安全管理本机 Agent Skills | [SAFE](https://agentskillshub.top/skill/MichengAI/dsh-skills-manager/?utm_source=github&utm_medium=awesome-list) |
| [liuxingqitd/skills-hub](https://github.com/liuxingqitd/skills-hub) | 81 | 本地仪表盘，用于在 OpenClaw、Cursor、Claude Code 等工具间同步、安装和整理 AI 编程 agent skill | [SAFE](https://agentskillshub.top/skill/liuxingqitd/skills-hub/?utm_source=github&utm_medium=awesome-list) |
| [youzaiAGI/agent-skills-hub](https://github.com/youzaiAGI/agent-skills-hub) | 71 | 技能包管理 | [SAFE](https://agentskillshub.top/skill/youzaiAGI/agent-skills-hub/?utm_source=github&utm_medium=awesome-list) |
| [zunalabs/skills-manager](https://github.com/zunalabs/skills-manager) | 71 | 用于管理各主流 coding agent 的 AI agent skill 的桌面应用。 | [SAFE](https://agentskillshub.top/skill/zunalabs/skills-manager/?utm_source=github&utm_medium=awesome-list) |
| [robotbird/skillkit](https://github.com/robotbird/skillkit) | 66 | AI agent 技能管理器 | [CAUTION](https://agentskillshub.top/skill/robotbird/skillkit/?utm_source=github&utm_medium=awesome-list) |
| [Milktang0128/myskills](https://github.com/Milktang0128/myskills) | 60 | AI Skill Hub——桌面应用，用于发现、去重、整理和同步 Claude Code、Codex 的 skill 与共享库；提供 MCP server，支… | [SAFE](https://agentskillshub.top/skill/Milktang0128/myskills/?utm_source=github&utm_medium=awesome-list) |
| [ryderme/skill-manager](https://github.com/ryderme/skill-manager) | 56 | Skill Manager：通过符号链接管理 Claude Code、Codex、Cursor、OpenClaw 等工具的 skill。 | [SAFE](https://agentskillshub.top/skill/ryderme/skill-manager/?utm_source=github&utm_medium=awesome-list) |
| [asteroid-belt/skulto](https://github.com/asteroid-belt/skulto) | 51 | 离线且以安全为先的 agent skill 同步与管理工具 | [SAFE](https://agentskillshub.top/skill/asteroid-belt/skulto/?utm_source=github&utm_medium=awesome-list) |
| [mcp360/mTarsier](https://github.com/mcp360/mTarsier) | 50 | mTarsier：用于 Claude、Cursor、VS Code 及其他 AI 客户端的 MCP 和 skill 管理器。 | [SAFE](https://agentskillshub.top/skill/mcp360/mTarsier/?utm_source=github&utm_medium=awesome-list) |
| [ssssssanjiu/skill_manager](https://github.com/ssssssanjiu/skill_manager) | 50 | 本地 Web 面板管理 Claude Code skill：粘贴 GitHub URL 安装，符号链接托管、零复制；每日获取新发布 skill。零依赖。 | [SAFE](https://agentskillshub.top/skill/ssssssanjiu/skill_manager/?utm_source=github&utm_medium=awesome-list) |
| [umutbozdag/agent-skills-manager](https://github.com/umutbozdag/agent-skills-manager) | 41 | 在一个仪表盘中管理 Cursor、Claude 和 Agents 的所有 AI agent skill | [SAFE](https://agentskillshub.top/skill/umutbozdag/agent-skills-manager/?utm_source=github&utm_medium=awesome-list) |
| [razbakov/skill-mix](https://github.com/razbakov/skill-mix) | 36 | AI agent skill 管理层：在 Cursor、Codex 和 Claude Code 中发现、安装、限定范围、评分和更新 skill。 | [SAFE](https://agentskillshub.top/skill/razbakov/skill-mix/?utm_source=github&utm_medium=awesome-list) |
| [24KaratAu/openhub](https://github.com/24KaratAu/openhub) | 21 | AI 编程工具、MCP 服务器和 agent skill 的终端发现中心与包管理器，使用 Python 和 Textual 构建 | [SAFE](https://agentskillshub.top/skill/24KaratAu/openhub/?utm_source=github&utm_medium=awesome-list) |
| [ivanpham86/Claude-code-skill-manager](https://github.com/ivanpham86/Claude-code-skill-manager) | 17 | 桌面应用，可添加 GitHub 仓库为 skill 源，浏览并安装到 ~/.claude/skills/供 Claude Code 使用 | [SAFE](https://agentskillshub.top/skill/ivanpham86/Claude-code-skill-manager/?utm_source=github&utm_medium=awesome-list) |
| [mars2003/cherry-studio-skill-manager](https://github.com/mars2003/cherry-studio-skill-manager) | 12 | 跨平台的 Cherry Studio Skill 安装与管理工具 | [SAFE](https://agentskillshub.top/skill/mars2003/cherry-studio-skill-manager/?utm_source=github&utm_medium=awesome-list) |
| [yiwen65/SkillDock](https://github.com/yiwen65/SkillDock) | 12 | 面向 Claude Code、Codex 和自定义 agent 的本地优先 Git 工作区与 skill 符号链接安装器。 | [SAFE](https://agentskillshub.top/skill/yiwen65/SkillDock/?utm_source=github&utm_medium=awesome-list) |
| [sulfide2085/dsh-skill-manager](https://github.com/sulfide2085/dsh-skill-manager) | 11 | 在 DeepSeek Harness 设置页管理 DSH、Codex、Claude 技能：启停、GitHub 安装、本地 ZIP 导入（dsh-plugin… | [SAFE](https://agentskillshub.top/skill/sulfide2085/dsh-skill-manager/?utm_source=github&utm_medium=awesome-list) |
| [wzf1997/skills-manager](https://github.com/wzf1997/skills-manager) | 10 | 跨平台 AI Skills 管理工具 | [SAFE](https://agentskillshub.top/skill/wzf1997/skills-manager/?utm_source=github&utm_medium=awesome-list) |
| [alswl/skm](https://github.com/alswl/skm) | 8 | 一个轻量、本地优先的 AI skill 管理器 | [SAFE](https://agentskillshub.top/skill/alswl/skm/?utm_source=github&utm_medium=awesome-list) |
| [eatmoreduck/SkillManager](https://github.com/eatmoreduck/SkillManager) | 6 | SkillManager 是跨平台桌面应用，用于发现、整理、编辑和发布 Claude、Codex 及其他本地 agent 生态中的 AI agent skil… | [SAFE](https://agentskillshub.top/skill/eatmoreduck/SkillManager/?utm_source=github&utm_medium=awesome-list) |
| [oliwier-xiao/agent-skills-manager](https://github.com/oliwier-xiao/agent-skills-manager) | 6 | Omarchy 栏上的可搜索列表，汇总 Claude Code、OpenCode 和 Codex 加载的 skill、插件与 MCP server，显示每轮… | [SAFE](https://agentskillshub.top/skill/oliwier-xiao/agent-skills-manager/?utm_source=github&utm_medium=awesome-list) |
| [GuiKang0424/skills-manager-ui](https://github.com/GuiKang0424/skills-manager-ui) | 5 | Skills Manager集中管理skill，可一键安装到Cursor、Claude Code、Codex，支持扫描、搜索、安装和卸载。 | [SAFE](https://agentskillshub.top/skill/GuiKang0424/skills-manager-ui/?utm_source=github&utm_medium=awesome-list) |
| [nameczz/skill-sync](https://github.com/nameczz/skill-sync) | 5 | 用于通过 Git 同步 Codex skills 的本地 Web 和 CLI 管理器 | [SAFE](https://agentskillshub.top/skill/nameczz/skill-sync/?utm_source=github&utm_medium=awesome-list) |
| [victor-software-house/pi-skills-manager](https://github.com/victor-software-house/pi-skills-manager) | 5 | Pi 的交互式 skill 管理器，通过 pi-config 风格界面启用或禁用 skill | [SAFE](https://agentskillshub.top/skill/victor-software-house/pi-skills-manager/?utm_source=github&utm_medium=awesome-list) |
| [zhuyansen/skills-manager](https://github.com/zhuyansen/skills-manager) | 0 | 跨平台 AI Agent Skill 管理桌面应用。原项目 iamzhihuix/skills-manage 已从 GitHub 删除,这是保留下来的副本。 | [*待评级*](https://agentskillshub.top/skill/zhuyansen/skills-manager/?utm_source=github&utm_medium=awesome-list) |

<a id="type-registry"></a>
## 🔎 市场与目录

[在在线页面打开这一类,按星数排序 →](https://agentskillshub.top/best/skill-management-tools/?utm_source=github&utm_medium=awesome-list#type-registry)

| 仓库 | 星数 | 做什么 | 安全评级 |
|---|---:|---|---|
| [phuryn/pm-skills](https://github.com/phuryn/pm-skills) | 26.9k | PM Skills Marketplace：涵盖探索、战略、执行、发布和增长的 agent skill、命令与插件。 | [SAFE](https://agentskillshub.top/skill/phuryn/pm-skills/?utm_source=github&utm_medium=awesome-list) |
| [tech-leads-club/agent-skills](https://github.com/tech-leads-club/agent-skills) | 7.0k | 面向 AI 编程 agent 的 skill 注册表，支持 Antigravity、Claude Code、Cursor、Copilot 等扩展。 | [SAFE](https://agentskillshub.top/skill/tech-leads-club/agent-skills/?utm_source=github&utm_medium=awesome-list) |
| [davepoon/buildwithclaude](https://github.com/davepoon/buildwithclaude) | 3.6k | 查找Claude Code、Claude Desktop、Agent SDK、OpenClaw的Skills等扩展资源 | [SAFE](https://agentskillshub.top/skill/davepoon/buildwithclaude/?utm_source=github&utm_medium=awesome-list) |
| [jeremylongshore/tons-of-skills-marketplace](https://github.com/jeremylongshore/tons-of-skills-marketplace) | 2.8k | 模型无关的 agent-skills 平台，提供无 harness 的规范层、经验证的适配器和 ccpi 包管理器。 | [SAFE](https://agentskillshub.top/skill/jeremylongshore/tons-of-skills-marketplace/?utm_source=github&utm_medium=awesome-list) |
| [daymade/claude-code-skills](https://github.com/daymade/claude-code-skills) | 1.4k | Claude Code skills 市场，提供开发流程所需的 skills。 | [SAFE](https://agentskillshub.top/skill/daymade/claude-code-skills/?utm_source=github&utm_medium=awesome-list) |
| [binance/binance-skills-hub](https://github.com/binance/binance-skills-hub) | 1.1k | Binance Skills Hub 是技能市场，为 AI agent 提供原生加密货币访问能力 | [SAFE](https://agentskillshub.top/skill/binance/binance-skills-hub/?utm_source=github&utm_medium=awesome-list) |
| [mhattingpete/claude-skills-marketplace](https://github.com/mhattingpete/claude-skills-marketplace) | 680 | Claude Code 的软件工程工作流 skill：Git 自动化、测试和代码审查 | [SAFE](https://agentskillshub.top/skill/mhattingpete/claude-skills-marketplace/?utm_source=github&utm_medium=awesome-list) |
| [zhuyansen/agent-skills-hub](https://github.com/zhuyansen/agent-skills-hub) | 416 | 发现并比较开源 Agent Skills、工具和 MCP 服务器，提供质量评分、趋势分析和自动 GitHub 同步 | [SAFE](https://agentskillshub.top/skill/zhuyansen/agent-skills-hub/?utm_source=github&utm_medium=awesome-list) |
| [Leon-Drq/openagentskill](https://github.com/Leon-Drq/openagentskill) | 358 | AI agent 的 skill 层：AI Agent Skills 的 npm。 | [SAFE](https://agentskillshub.top/skill/Leon-Drq/openagentskill/?utm_source=github&utm_medium=awesome-list) |
| [buzhangsan/skill-manager](https://github.com/buzhangsan/skill-manager) | 321 | Skill Manager：从 GitHub 搜索、浏览并安装社区 skill，供 AI agent 使用 | [SAFE](https://agentskillshub.top/skill/buzhangsan/skill-manager/?utm_source=github&utm_medium=awesome-list) |
| [modu-ai/cowork-plugins](https://github.com/modu-ai/cowork-plugins) | 306 | 비개발자를 위한 한국 실무 AI 코워커 패밀리 — Claude Cowork·ChatGPT Work에서 /project 한 번으로 시작 | [SAFE](https://agentskillshub.top/skill/modu-ai/cowork-plugins/?utm_source=github&utm_medium=awesome-list) |
| [PramodDutta/qaskills](https://github.com/PramodDutta/qaskills) | 235 | QA Skills 目录：面向 AI 编程 agent 的测试专用 skill（Claude Code、Cursor、Copilot 等）。 | [SAFE](https://agentskillshub.top/skill/PramodDutta/qaskills/?utm_source=github&utm_medium=awesome-list) |
| [ahmedasmar/devops-claude-skills](https://github.com/ahmedasmar/devops-claude-skills) | 203 | 面向 DevOps 工作流的 Claude Code skill 市场 | [SAFE](https://agentskillshub.top/skill/ahmedasmar/devops-claude-skills/?utm_source=github&utm_medium=awesome-list) |
| [nextlevelbuilder/skillx](https://github.com/nextlevelbuilder/skillx) | 188 | SkillX.sh — AI agent skill 市场，支持语义搜索、排行榜、评分和 CLI。 | [SAFE](https://agentskillshub.top/skill/nextlevelbuilder/skillx/?utm_source=github&utm_medium=awesome-list) |
| [AElfProject/aelf-skills](https://github.com/AElfProject/aelf-skills) | 184 | 统一的 aelf skills 中心，用于 OpenClaw、Codex、Cursor 和 Claude Code 的发现、路由、引导和健康检查。 | [SAFE](https://agentskillshub.top/skill/AElfProject/aelf-skills/?utm_source=github&utm_medium=awesome-list) |
| [ARPAHLS/skillware](https://github.com/ARPAHLS/skillware) | 134 | 用于机器的模块化、自包含 skill 管理 Python 框架。 | [SAFE](https://agentskillshub.top/skill/ARPAHLS/skillware/?utm_source=github&utm_medium=awesome-list) |
| [agent-skills-hub/agent-skills-hub](https://github.com/agent-skills-hub/agent-skills-hub) | 112 | AI agent 技能库，适用于 OpenClaw、Claude Code、Gemini、Cursor、Antigravity 等平台。 | [SAFE](https://agentskillshub.top/skill/agent-skills-hub/agent-skills-hub/?utm_source=github&utm_medium=awesome-list) |
| [obie/skills](https://github.com/obie/skills) | 96 | Claude Code skill 市场：用于开发工作流的 skill | [SAFE](https://agentskillshub.top/skill/obie/skills/?utm_source=github&utm_medium=awesome-list) |
| [existential-birds/beagle](https://github.com/existential-birds/beagle) | 82 | Agent Skills：多语言/框架代码审查、文档、测试计划、AI写作检测、架构分析、Git工作流，支持 Claude Code、Codex 等 agent | [SAFE](https://agentskillshub.top/skill/existential-birds/beagle/?utm_source=github&utm_medium=awesome-list) |
| [ComeOnOliver/skillshub](https://github.com/ComeOnOliver/skillshub) | 65 | 一次 API 调用解析 skill。AI agent skill 注册表，节省 token，收录来自 500+ 个仓库的 5,000+ 个 skill。 | [SAFE](https://agentskillshub.top/skill/ComeOnOliver/skillshub/?utm_source=github&utm_medium=awesome-list) |
| [zeroclaw-labs/zeroclaw-skills](https://github.com/zeroclaw-labs/zeroclaw-skills) | 65 | ZeroClaw 官方 skill 注册库：社区贡献的 AI agent skill、工具和工作流 | [SAFE](https://agentskillshub.top/skill/zeroclaw-labs/zeroclaw-skills/?utm_source=github&utm_medium=awesome-list) |
| [modelstudioai/skills](https://github.com/modelstudioai/skills) | 58 | ModelStudio 驱动的精选、经验证的 Agent Skills。 | [SAFE](https://agentskillshub.top/skill/modelstudioai/skills/?utm_source=github&utm_medium=awesome-list) |
| [skilluse/skilluse](https://github.com/skilluse/skilluse) | 55 | Agent skill 注册表与 CLI | [SAFE](https://agentskillshub.top/skill/skilluse/skilluse/?utm_source=github&utm_medium=awesome-list) |
| [c-kick/hnl-agent-skills](https://github.com/c-kick/hnl-agent-skills) | 53 | 适用于 Claude Code 和 Codex 的可复用 agent skill 注册库 | [SAFE](https://agentskillshub.top/skill/c-kick/hnl-agent-skills/?utm_source=github&utm_medium=awesome-list) |
| [AmadeusITGroup/ai-primitives-hub](https://github.com/AmadeusITGroup/ai-primitives-hub) | 50 | 管理、分享、安装 GitHub Copilot 等 AI 助手的 Agents、Skills、Prompts、Instructions、MCP 集合的 VS… | [SAFE](https://agentskillshub.top/skill/AmadeusITGroup/ai-primitives-hub/?utm_source=github&utm_medium=awesome-list) |
| [Qsnh/skillsgist](https://github.com/Qsnh/skillsgist) | 27 | 可在 Cloudflare 上自行托管的私有 Agent Skills 注册中心。 | [SAFE](https://agentskillshub.top/skill/Qsnh/skillsgist/?utm_source=github&utm_medium=awesome-list) |
| [codebygarv/Ai-skills](https://github.com/codebygarv/Ai-skills) | 26 | 社区AI agent skill目录：Claude Code、Antigravity、Cursor Ai、kimi、deepseek、Mimo；npx安装。 | [SAFE](https://agentskillshub.top/skill/codebygarv/Ai-skills/?utm_source=github&utm_medium=awesome-list) |
| [nikships/skills-registry](https://github.com/nikships/skills-registry) | 22 | 你的 AI Agent Skills GitHub 注册表。一个仓库，适用于每个 agent 和设备，按需加载。 | [SAFE](https://agentskillshub.top/skill/nikships/skills-registry/?utm_source=github&utm_medium=awesome-list) |
| [kevinnft/ai-agent-skills](https://github.com/kevinnft/ai-agent-skills) | 13 | 191 个面向 Hermes Agent、Claude Code、Cursor 的署名优先 skill：一个安装器、28 个分类、可搜索目录。上游署名见 NO… | [SAFE](https://agentskillshub.top/skill/kevinnft/ai-agent-skills/?utm_source=github&utm_medium=awesome-list) |
| [gavinyao/skill-registry-manager](https://github.com/gavinyao/skill-registry-manager) | 10 | Claude Code skill 注册表管理工具，支持 YAML、远程/本地订阅、递归加载及 npx、git、本地复制安装。 | [SAFE](https://agentskillshub.top/skill/gavinyao/skill-registry-manager/?utm_source=github&utm_medium=awesome-list) |
| [cobibean/shared-skills-registry-mcp](https://github.com/cobibean/shared-skills-registry-mcp) | 8 | 用于可复用 AI-agent skill 的自托管注册表、仪表板和 MCP 接口。 | [SAFE](https://agentskillshub.top/skill/cobibean/shared-skills-registry-mcp/?utm_source=github&utm_medium=awesome-list) |
| [hgflima/harness-lab](https://github.com/hgflima/harness-lab) | 7 | Claude Code 的 AI agent harness 公共精选注册表，支持浏览、安装和管理 skill、command、agent、hook。 | [SAFE](https://agentskillshub.top/skill/hgflima/harness-lab/?utm_source=github&utm_medium=awesome-list) |
| [Bilal140202/the-lord-of-the-skills](https://github.com/Bilal140202/the-lord-of-the-skills) | 6 | AI agent skills 安装器：pip install lotr-skills，支持 Claude Code、Cursor、Codex | [SAFE](https://agentskillshub.top/skill/Bilal140202/the-lord-of-the-skills/?utm_source=github&utm_medium=awesome-list) |
| [The-Utopia-Studio/skills](https://github.com/The-Utopia-Studio/skills) | 6 | The Utopia Studio：4 个模块、301 个 skill，支持 Claude Code、Cursor 和 Agent Skills。 | [SAFE](https://agentskillshub.top/skill/The-Utopia-Studio/skills/?utm_source=github&utm_medium=awesome-list) |
| [latestaiagents/agent-skills](https://github.com/latestaiagents/agent-skills) | 5 | AI agent skill 和插件市场，涵盖开发、生产力、运营、营销等领域 | [SAFE](https://agentskillshub.top/skill/latestaiagents/agent-skills/?utm_source=github&utm_medium=awesome-list) |
| [nirholas/x402-skill-registry](https://github.com/nirholas/x402-skill-registry) | 5 | 可搜索的 x402 付费 agent skill 注册表：用签名条目注册，agent 按查询搜索。每个条目支持 Base 和 Solana 上的 USDC。 | [SAFE](https://agentskillshub.top/skill/nirholas/x402-skill-registry/?utm_source=github&utm_medium=awesome-list) |
| [terrylica/cc-skills](https://github.com/terrylica/cc-skills) | 0 | Claude Code Skills Marketplace：ADR 驱动开发、DevOps 自动化、ClickHouse 管理、语义化版本和效率工作流插件与… | [SAFE](https://agentskillshub.top/skill/terrylica/cc-skills/?utm_source=github&utm_medium=awesome-list) |

<a id="type-team"></a>
## 👥 团队管理

[在在线页面打开这一类,按星数排序 →](https://agentskillshub.top/best/skill-management-tools/?utm_source=github&utm_medium=awesome-list#type-team)

| 仓库 | 星数 | 做什么 | 安全评级 |
|---|---:|---|---|
| [iflytek/skillhub](https://github.com/iflytek/skillhub) | 5.2k | 面向企业的自托管开源 agent skill 注册中心，发布并管理 skill 包版本，通过 RBAC 和审计日志治理，支持 Docker 或 Kuberne… | [SAFE](https://agentskillshub.top/skill/iflytek/skillhub/?utm_source=github&utm_medium=awesome-list) |
| [FrancyJGLisboa/agent-skills-platform](https://github.com/FrancyJGLisboa/agent-skills-platform) | 2.4k | 构建经测试的 agent skill，通过用户自定义市场管理其生命周期：证据、发现、更新、回滚、隔离及向17个平台分发 | [SAFE](https://agentskillshub.top/skill/FrancyJGLisboa/agent-skills-platform/?utm_source=github&utm_medium=awesome-list) |
| [ginuim/skill-base](https://github.com/ginuim/skill-base) | 121 | AI coding agent 私有 skill 分发平台：通过轻量服务端和 skb CLI，在 Cursor、Claude Code、Codex、OpenC… | [SAFE](https://agentskillshub.top/skill/ginuim/skill-base/?utm_source=github&utm_medium=awesome-list) |
| [stacklok/toolhive-registry-server](https://github.com/stacklok/toolhive-registry-server) | 29 | 发现、管理和控制组织内 MCP 服务器及 agent skill 的访问权限 | [SAFE](https://agentskillshub.top/skill/stacklok/toolhive-registry-server/?utm_source=github&utm_medium=awesome-list) |
| [a14a-org/claudeskill-manager](https://github.com/a14a-org/claudeskill-manager) | 10 | 跨设备同步 Claude Code skills，采用零知识加密 | [SAFE](https://agentskillshub.top/skill/a14a-org/claudeskill-manager/?utm_source=github&utm_medium=awesome-list) |

**安全评级**是 Agent Skills Hub 对仓库 README 和安装步骤的评级。*待评级*表示目录还没评到它。

预览图是各项目 README 里图片的缩小副本,只收录采用宽松许可证的项目,版权归原作者所有。来源和许可证见 [assets/previews/NOTICE.md](assets/previews/NOTICE.md)。如需移除请提 issue。

## 相关合集

- [zhuyansen/awesome-claude-video-skills](https://github.com/zhuyansen/awesome-claude-video-skills), [zhuyansen/awesome-codex-ppt-skills](https://github.com/zhuyansen/awesome-codex-ppt-skills) —— 同样做法的合集。

## 推荐仓库

提一个 issue 附上 GitHub 链接。它会走和每个条目一样的评审;决定上不上榜的是上面的规则,不是星数。

---

机器可读版本:[`data/skills.json`](data/skills.json)。生成于 2026-10-10。
