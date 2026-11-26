# AI Agent 扩展学习笔记

---

## 1. 我目前用的 AI 应用 + 重点对比的两个 Agent

### 1.1 我目前有的

- **ChatGPT/Codex**：OpenAI 出的，最主流的通用对话 AI。我一般拿它当"什么都先问一句"的起点，问概念、改文字、起标题都行。
- **Gemini**：Google 的多模态模型，能直接看图、读长文档。我主要用它处理截图和长材料。
- **豆包**：字节跳动的 AI 助手，中文对话最顺，手机上也能用。我用来快速查中文资料、把书面语改成口语化表达。
- **Grok Bot**：xAI 的 Grok，因为它需要订阅，并且目前我不太需要用到 Grok，所以尚未探索。
- **Claude**：Anthropic 的 AI，长文档和代码能力口碑好。被卡在认证这一块，气死我了。
- **夸克**：阿里的 AI 浏览器，把 AI 搜索、网盘、扫描整合在一起。因为不需要截图，可以直接快捷 AI，多用于查题方面。
- **WorkBuddy**：我用到最多的 AI。图形界面 Agent，技能在面板里一键开关，笔记、PPT、文档、知识库这类需求都能接，而且相当于免费，而且支持多个 LLM，只要提示词准确，并根据需要不断调整，实际效果还不错。之前耳机驱动把电脑文件弄丢了，就是 WorkBuddy 帮我找回的。
- **Antigravity**：网络问题目前已经解决了，但卡在了扫码验证，所以尚未探索。
- **OpenCode**：开源的终端 Agent，都在命令行里干活。特点是模型可以自选，而且可以接 Opus 4.5 等强大的 LLM，目前还在探索阶段。
- **DeepSeek Harness**：一个智能体框架，因为我在 Claude Code 上接了 DeepSeek 的 API，所以目前 DSH 用得比较少了。
- **Hermes**：Nous Research 推出的 MIT 协议开源自主智能体，自带自学习闭环与持久记忆，支持多模型、多部署方式与丰富工具，与小龙虾类似，目前对它的了解不多，还在探索阶段。
- **Claude Code**：Claude 的命令行版，由于各种原因，目前只能先接入 DeepSeek 的模型先使用，写代码能力挺不错。**Antigravity** 登录时的网络问题就是它帮我解决的，整体体验还可以，可以辅助 Git 工作。

---

## 2. GPT / Codex 侧盘点

### 2.1 MCP 服务

- **chrome-devtools**：Google 官方出的 MCP，把 Chrome 开发者工具接到 Agent 上。它能让 Agent 直接操控一个真实 Chrome，看控制台报错、抓网络请求、录性能 trace、截图、跑 Lighthouse 审计、模拟手机屏幕。
- **context7**：文档检索类 MCP，由 Upstash 维护，索引了 9000 多个库的官方文档，地址是 `https://mcp.context7.com/mcp`。作用是实时拉取我正在用的框架当前版本的文档和代码示例，专治 AI 拿旧版 API 或凭空编一个不存在的函数。
- **github**：GitHub 官方 MCP，作用是让我在对话里直接操作 GitHub，查 issue、看 PR、读仓库内容，不用切到网页，可以配合 Git 工作。
- **figma**：设计稿相关的 MCP，本来能读设计稿、把设计稿转成代码。但卡在了 Google 验证这一块，目前尚未解决。

### 2.2 Skill

- **caveman**：一个"说话风格"Skill，让 Agent 回答极简、主要是省 token，但代码、命令、路径、数值、报错这些技术内容一个字不改。
- **hypit**：视频制作类 Skill，让 Agent 当"导演"，调图像、视频、音频模型生成素材，再写组件把素材编排成片子，还支持 SVML、SVS 这类创作语法。偏视频方向，属于个人喜好。
- **impeccable**：前端界面质量工作流。覆盖设计新页面、重构旧页面、UX 审查、无障碍、响应式、性能、设计系统，还能截图看渲染结果再改。
- **playwright-dev**："如何开发 Playwright 本身"的指南，讲的是加 API、加 MCP 工具、加 CLI 命令、改 vendor 依赖。
- **ppt-master**：生成 PPT 的 Skill，内置 20 种图表类型、8 大类配色，能直接产出可编辑的 .pptx 文件。适配课程汇报、答辩展示这类需求。
- **taste-skill**（design-taste-frontend）：反"AI 味"的前端设计 Skill，专做公司官网、落地页、产品站。它强制单一设计系统、真实照片和产品截图、克制动效。
- **find-skills**：元技能，不知道装什么的时候，让 AI 按我的场景和需求去搜合适的 Skill。相当于给"找技能"。
- **huashu-design**（花叔设计）：一句话交付设计的 Skill，能出网页、可点击 App 原型、可编辑 PPT、信息图。需求说不清时它先给六个视觉方向的缩略图，让我挑三个再做真稿，交付前还有设计体检。
- **figma**：从 Figma 设计稿生成内容。
- **hyperframes**：这一组的核心。HeyGen 开源的框架，让我用普通 HTML 加 GSAP 写动画，再渲染成 MP4 视频。
- **hyperframes-cli**：配套的命令行工具，用来预览、lint 检查、逐帧 diff 对比和最终渲染。
- **hyperframes-registry**：现成的区块和组件库，约 450 个可复用块，写动画时直接拿来拼。
- **media-use**：在作品里使用图片、音频、视频等媒体素材的规范。
- **remotion-to-hyperframes**：把已有的 Remotion 迁移到 HyperFrames，还带逐帧对比验证，确认迁移后画面一致。

---

## 3. WorkBuddy 侧盘点

- **文章去 AI 味工具**（humanizer）：识别并改掉文本里的 AI 写作套话、重复句式和机械表达，让文字读起来像人写的。
- **WPS Office 全家桶**：四引擎自动识别本机装的是 WPS、MS Office 还是 LibreOffice，没有也能用纯 Python 处理，支持排序筛选、图表、公式。
- **办公文档三件套**：处理 Word、Excel、PDF，支持排序筛选、合并拆分、格式转换、加水印和交付前检查。交作业、整理资料时实用。
- **PPT master**：专业 PPT 生成，支持 20 种图表类型、8 大类温和配色，产出可直接编辑的 .pptx。
- **Proactive Agent**：让 Agent 从"被动等你下指令"变成"主动预判需求、持续改进"的行为型技能。
- **Skill Creator**：教我怎么写一个结构良好的 Skill，包括触发条件、指令写法、附带脚本的组织方式。
- **Skill Vetter**：装第三方 Skill 之前先做安全审查，检查来源和脚本风险，很实用。
- **ima-skills**：接 IMA 的 OpenAPI，做笔记管理和知识库操作。
- **Github**：用 `gh` 命令行操作 GitHub，能管 issue、PR、CI。
- **Summarize**：总结网页、PDF、TXT、播客、YouTube 内容，快速消化学习资料。
- **dev-expert**：编程专家助手。
- **Agent Browser**：浏览器自动化 CLI，让 Agent 操作网页、填表单、截图。
- **技能发现 · Find Skills**：按场景让 AI 自己找最合适的技能，和 Codex 侧的 find-skills 对应。
- **self-improvement**：把经验、错误和纠正记下来，让 Agent 越用越顺。

---

## 4. 搜索关键词与资源链接

### 4.1 MCP 服务

- **chrome devtools mcp**：`https://github.com/ChromeDevTools/chrome-devtools-mcp`
- **context7 mcp**：`https://context7.com`，MCP 地址 `https://mcp.context7.com/mcp`
- **github copilot mcp**：`https://api.githubcopilot.com/mcp/`
- **figma mcp**：`https://mcp.figma.com/mcp`

### 4.2 Skill（GPT / Codex 侧）

- **caveman**：`https://github.com/JuliusBrussee/caveman`
- **hypit**：`https://github.com/hypit-ai/hypit`
- **impeccable skill 前端设计**：`https://github.com/pbakaus/impeccable`
- **playwright-dev**：`https://github.com/microsoft/playwright/tree/main/.claude/skills/playwright-dev`
- **ppt-master**：`https://github.com/hugohe3/ppt-master`
- **taste skill frontend 反 AI 味**：`https://github.com/Leonxlnx/taste-skill`
- **find-skills**：`https://github.com/vercel-labs/skills/tree/main/skills/find-skills`
- **huashu design 花叔设计**：`https://github.com/alchaincyf/huashu-design`
- **hyperframes 视频框架**：`https://github.com/heygen-com/hyperframes`
- **hyperframes-cli**：`https://github.com/heygen-com/hyperframes/tree/main/skills/hyperframes-cli`
- **hyperframes-registry**：`https://github.com/heygen-com/hyperframes/tree/main/skills/hyperframes-registry`
- **media-use**：`https://github.com/heygen-com/hyperframes/tree/main/skills/media-use`
- **remotion-to-hyperframes**：`https://github.com/heygen-com/hyperframes/tree/main/skills/remotion-to-hyperframes`
- **skills add**：`https://skills.sh`

### 4.3 Skill（WorkBuddy 侧）

- **humanizer 文章去 AI 味**：`https://github.com/blader/humanizer`
- **WPS Office 全家桶**：`https://github.com/lc2panda/wps-skills`
- **办公文档三件套**：`https://github.com/anthropics/skills/tree/main/skills`
- **PPT master**：`https://github.com/hugohe3/ppt-master`
- **Proactive Agent**：`https://github.com/halthelobster/proactive-agent`
- **Skill Creator**：`https://github.com/anthropics/skills/tree/main/skills/skill-creator`
- **Skill Vetter**：`https://github.com/app-incubator-xyz/skill-vetter`
- **ima-skills**：`https://ima.qq.com/agent-interface`
- **Github**：`https://cli.github.com/`
- **Summarize**：`https://github.com/steipete/summarize`
- **dev-expert**：`https://api.skillhub.cn/user_814dbe54/dev-expert`
- **Agent Browser**：`https://github.com/vercel-labs/agent-browser`
- **技能发现 · Find Skills**：`https://github.com/vercel-labs/skills/tree/main/skills/find-skills`
- **self-improvement**：`https://github.com/peterskoett/self-improving-agent`
