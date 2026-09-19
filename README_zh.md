# APA Awesome Jev [![Awesome](https://awesome.re/badge.svg)](https://awesome.re) [![Curated by AIPersona Academy](https://img.shields.io/badge/Curated%20by-AIPersona%20Academy-8A2BE2.svg)](https://whop.com/aipersonaacademy) [![APA 生态](https://img.shields.io/badge/APA-%E7%94%9F%E6%80%81-059669.svg)](https://whop.com/aipersonaacademy) [![License: CC0-1.0](https://img.shields.io/badge/License-CC0_1.0-lightgrey.svg)](LICENSE)

由 **APA (AIPersona Academy / 人工智能画像学院)** 精选与维护的 [Jev](https://docs.typesafe.ai/introduction) 应用、库、工具与生态资料汇总。Jev 是 TypeSafe 的旗舰 [System One](https://docs.typesafe.ai/concepts/system-one) 机器原生决策模型。

**[English](README.md)** | **[简体中文](README_zh.md)**

> 传入 state 和类型化问题，直接得到代码可用的结构化答案。

Jev 于 2026 年 9 月 15 日开放 early access。本目录由 **AIPersona Academy (APA)** 官方策划与维护，旨在赋能全球软件工程师、自主 Agent 开发者及 AI Persona 架构师。本列表为独立社区项目，与 TypeSafe AI 无隶属关系。欢迎提交 PR 与社区贡献 — 生态正在飞速壮大！

## 目录

- [Jev 是什么？](#jev-是什么)
- [🧭 生态项目分类快速导航表](#-生态项目分类快速导航表)
- [APA (AIPersona Academy) 生态与旗舰项目](#apa-aipersona-academy-生态与旗舰项目)
- [官方资源](#官方资源)
- [社区与 AIPersona Academy 官方阵地](#社区与-aipersona-academy-官方阵地)
- [SDK 与客户端](#sdk-与客户端)
- [应用](#应用)
- [Demo 与游戏](#demo-与游戏)
- [Agent 工具](#agent-工具)
- [研究与开源模型](#研究与开源模型)
- [Cookbook](#cookbook)
- [模式](#模式)
- [文章](#文章)
- [贡献](#贡献)
- [社区贡献与生态构建者](#-社区贡献与生态构建者)
- [维护团队](#维护团队)
- [许可证](#许可证)

## Jev 是什么？

大语言模型生成文本。Jev 不生成文本。它针对一份 *state* 评估类型化 *问题*，返回代码可以直接分支、排序、路由的值，并附带校准概率与置信度。

| 问题类型 | 用途 | 返回值 |
| --- | --- | --- |
| [Choice](https://docs.typesafe.ai/primitives/choice) | 从给定选项中选一个 | `choice`、`probabilities`、`confidence` |
| [Score](https://docs.typesafe.ai/primitives/score) | 按量规给 state 打分 | `score`、`probabilities`、`confidence` |
| [Noul](https://docs.typesafe.ai/primitives/noul) | 这句话为真吗？ | `noul`（0–1） |

同一次请求里的问题会对同一份 state 并行求值。问题尽量原子，组合逻辑写在你的代码里。

> **💡 APA Persona 架构师视角：**  
> 在 **APA (AIPersona Academy)**，我们将 System One 模型视作自主 AI Persona（智能画像/智能体）的“自主神经系统”。传统的 LLM 聊天循环在处理机械控制流时既慢又昂贵，且概率未校准。APA 架构将确定性的类型化毫秒级判断（Jev）与生成式 Persona 彻底解耦，确保智能体在控制流与策略边界上具备零幻觉风险、微秒级响应与严格的置信度栅栏。

## 🧭 生态项目分类快速导航表

按功能领域分类整理的 Jev 与 System One 精选开源工具、应用与框架全景导航：

| 领域分类 | 开源项目 | 简要概述 | 核心原语 |
| :--- | :--- | :--- | :---: |
| **🛡️ 网络安全与 EDR** | [Jev-AV 与 Jev Guard](https://github.com/newuser7171/antivirus) | 文件防病毒、URL 威胁检测、Windows 实时 EDR 哨兵与 Android APK 审计 | `Choice`, `Score`, `Noul` |
| | [Jev Moderation Bot](https://github.com/brainstormity/Jev-Moderation-Bot) | Discord 实时垃圾信息/诈骗链接检测与成员行为画像机器人 | `Choice`, `Noul` |
| | [tripwire](https://github.com/noelzappy/tripwire) | 在 LLM 响应上运行 100ms 级别、带置信度门控的安全检查中间件 | `Noul` |
| | [TypeSafe AdBlock](https://github.com/realZachi/typesafe-adblock) | 智能判断 DOM 节点是否为广告并将其移除的 Chrome 扩展 | `Noul` |
| **🤖 智能体与运行时** | [APA 自主 Persona 引擎](https://github.com/AiPersonacademy/apa-persona-engine) | 确定性状态路由、情感效价调制与安全网关的多智能体企业级运行时 | `Choice`, `Score` |
| | [APA Agent 决策 Harness](https://github.com/AiPersonacademy/apa-agent-harness) | 面向 Claude Code、Codex 与 Cursor 的安全策略路由与轨迹验证脚手架 | `Choice`, `Score`, `Noul` |
| | [ProgressGate](https://github.com/AshutoshVJTI/progressgate) | 监控智能体循环语义停滞（CONTINUE / WARN / REPLAN / HALT） | `Choice` |
| | [Foreman](https://github.com/thruwire/foreman) | 软件工厂循环：评估代码实现完整度、测试覆盖与人工接管需求 | `Choice`, `Noul` |
| | [jev-harness](https://github.com/AntonioCoppe/jev-harness) | 生产级封装层：策略路由、置信度门控、影子模式与评测 CLI | `Choice`, `Score` |
| **🔎 代码检索与开发工具** | [Jev Code Finder](https://github.com/Peu77/JevFind) | 基于自然语言查询定位文件相关度与精准代码行置信度的搜索 CLI | `Choice`, `Score` |
| | [blink](https://github.com/ellipsis-dev/blink) | 使用 walker 智能体集群在代码库中回答自然语言查询的搜索工具 | `Choice` |
| | [Every](https://github.com/sufianetaouil/every) | 针对每个函数提出 yes/no 问题并按 Noul 概率排序的代码搜索 CLI | `Noul` |
| | [Supercov](https://github.com/supercorp-ai/supercov) | 针对编程智能体的代码质量与测试覆盖打分工具，指引优先修改位置 | `Score` |
| | [Jev Review](https://github.com/devagrawal09/jev-review) | 分阶段代码审查工作流与本地看板 | `Choice`, `Score` |
| **📊 数据智能与采集** | [APA 爬取与市场情报套件](https://github.com/AiPersonacademy/apa-scraping-suite) | 抗检测社群情报采集套件，毫秒级筛查买家痛点与营销 Hook | `Choice`, `Noul` |
| | [Jev Search](https://github.com/superagents-lab/jev-search) | 利用 Jev 判断挑选搜索来源、时间范围与重排检索结果的 Web 搜索 | `Choice`, `Noul` |
| | [neo4jev](https://github.com/jexp/neo4jev) | 在 Neo4j 图数据库节点上选择关系走向的束搜索漫游工具 | `Choice` |
| | [sqlite3-jev](https://github.com/mattn/sqlite3-jev) | 将 Jev 评估原语暴露为原生 SQL 函数的 SQLite C 扩展 | `Choice`, `Score`, `Noul` |
| | [jevql](https://github.com/kylemclaren/jevql) | 原生 Postgres SQL 批处理引擎，直接在服务端运行 Jev 判定 | `Choice`, `Score`, `Noul` |
| **🎮 游戏、仿真与机器人** | [Jev 玩星际争霸](https://github.com/phyous/tsai-sc) | 初代星际争霸战役结构化状态测试平台，带概率轨迹与运行记录 | `Choice` |
| | [Jev × 文明 II](https://github.com/phyous/tsai-civ2) | 浏览器文明 II 决策平台，Jev 决定帝国科技、城市治理与部队调动 | `Choice` |
| | [Jev Drone](https://github.com/RomanSlack/jev-drone) | MuJoCo 四旋翼模拟：底层控制留给代码，Jev 负责战术决策 | `Choice` |
| | [jev-askable-arm](https://github.com/TarunTomar122/jev-askable-arm) | 零样本英语目标驱动的 Franka 机械臂运动控制 | `Choice` |
| **🌐 Web、实时与金融** | [hono-jev-router](https://github.com/yusukebe/hono-jev-router) | 实验性 Hono 路由中间件：将请求匹配至自然语言路由描述 | `Choice` |
| | [Jev Trader](https://github.com/jarrodwatts/jev-trader) | 基于 Monad 区块在 Kuru 订单簿上执行买卖决策的高频交易 Demo | `Choice` |
| | [Human Compiler](https://github.com/asfarsadewa/human-compiler) | 评估职场沟通文本的被动攻击与紧急程度，输出 rustc 风格诊断 | `Score` |
| | [JEVMETER](https://github.com/ChetasLua/jevmeter) | 针对视频内容进行逐句实时 Jev 打分并生成 16:9 动态遮罩 | `Score` |
| | [jev-audio-beeper](https://github.com/santos-sanz/jev-audio-beeper) | 466ms 低延迟音频辱骂检测并自动打码消音 | `Noul` |
| **📱 浏览器与移动端** | [jev-ego](https://github.com/romaluev/jev-ego) | 基于 ego lite 的浏览器智能体，单次请求完成操作与目标选择 | `Choice` |
| | [jev-browser](https://github.com/Ying-Kai-Liao/jev-browser) | 基于 Playwright 快照决策点击/输入的自动化工具与 MCP 服务 | `Choice` |
| | [Mobile Jev](https://github.com/droidrun/mobile-jev) | 基于 Mobilerun 的免 ADB 安卓自动化智能体 | `Choice` |
| | [Unclutter](https://github.com/kitze/unclutter) | 自动识别非必要网页元素并通过本地规则隐藏的浏览器扩展 | `Choice` |


## APA (AIPersona Academy) 生态与旗舰项目

由 **AIPersona Academy (APA)** 打造的旗舰架构、Agent 蓝图与 System One 赋能工具包：

- [APA 爬取与市场情报套件](https://github.com/AiPersonacademy/apa-scraping-suite) - 专为 AI Persona 研究打造的零鉴权、抗检测社群情报采集套件。利用 Jev `Noul` 和 `Choice` 毫秒级筛查帖子相关度、提取真实买家痛点并给营销 Hook 打分，避免昂贵的大模型全文摘要。
- [APA 自主 Persona 运行时引擎](https://github.com/AiPersonacademy/apa-persona-engine) - AIPersona Academy 设计的企业级多智能体运行时。在多智能体交互中部署 Jev 进行即时状态路由、情感效价调制与置信度安全网关。
- [APA Agent 决策 Harness](https://github.com/AiPersonacademy/apa-agent-harness) - 适用于 Claude Code、Codex、Cursor 与 Antigravity 的即插即用安全脚手架，在工具执行前运行 Jev 风险评分，并在执行后验证完成度。
- [AIPersona Academy 实战大师课与社区](https://whop.com/aipersonaacademy) - 官方体系化课程与动手实验，涵盖 Jev 决策流设计、Choice/Score/Noul 原语模式、投机扇出（Speculative Fan-out）以及生产级 Agent 策略工程。
- [APA Persona 实用配方库 (Cookbooks)](cookbooks/) - 意图路由 Persona、实时社交情绪监控探针及自动化直接响应广告文案评估的精选实战指南。

## 官方资源

- [TypeSafe](https://typesafe.ai) - 官网、候补名单与产品介绍。
- [文档](https://docs.typesafe.ai/introduction) - 入门、原语、模式、API 与 SDK。建议从 [Quick start](https://docs.typesafe.ai/introduction/quickstart) 开始。
- [Playground](https://console.typesafe.ai/playground) - 粘贴 state、添加问题，在浏览器里看类型化结果。
- [API keys](https://console.typesafe.ai/settings/keys) - TypeSafe API 密钥控制台（`TYPESAFE_API_KEY`）。
- [HTTP API](https://docs.typesafe.ai/api) - `POST https://api.typesafe.ai/v1/systemone`。
- [Workflow evals](https://evals.typesafe.ai) - 公开的评测方法与各模型结果。
- [GitHub 组织](https://github.com/typesafe-ai) - 官方开源仓库。
- [Agent skill](https://docs.typesafe.ai/agent-skill) - 给 Claude Code、Codex 等编程 Agent 用的技能包（[`typesafe-ai/skills`](https://github.com/typesafe-ai/skills)）。
- [Jev 1.13 jaggedness](https://docs.typesafe.ai/model-jaggedness/jev-1.13) - 当前公开模型已知的毛边与失败模式。
- [Introducing System One Models and Jev](https://typesafe.ai/blog/introducing-system-one-models-and-jev) - 发布博文：架构、定价、Doom / Wikiracing demo、FAQ。
- [Vercel AI Gateway 上的 Jev](https://vercel.com/ai-gateway/models/jev) - 托管的 `typesafe-ai/jev`，走 AI SDK `evaluate`，不必等 TypeSafe waitlist。
- [Manifesto](https://typesafe.ai/manifesto) - 主张给软件用的机器原生智能，而不是聊天。
- [The Bitterest Lesson](https://typesafe.ai/blog/bitterest-lesson) - 优化错任务，规模再大也盖不过。
- [AI: too good to be true, too bad to be useful](https://typesafe.ai/blog/ai-too-good-to-be-true-too-bad-to-be-useful-typesafe-ai) - 自动化不该用偏好对齐过的聊天模型。

## 社区与 AIPersona Academy 官方阵地

- [AIPersona Academy 官方中心](https://whop.com/aipersonaacademy) - 官方学术与实践中心，提供前沿实操课程、技术白皮书与 Agent 生产模板。
- [AIPersona Academy 官方社区](https://whop.com/aipersonaacademy) - APA 官方社区，汇聚 AI Agent 开发者、数字 Persona 工程师与 System One 研究者。
- [APA X @aipersonaacad](https://x.com/aipersonaacad) - 第一时间获取机器原生决策与自主智能体工程动态。
- [Discord](https://discord.gg/typesafe) - TypeSafe 官方服务器。Builder demo 在 [Show and Tell](https://discord.com/channels/1483217544214085663/1483217545040232493)。
- [X @typesafeai](https://x.com/typesafeai) - 产品与研究动态。
- [LinkedIn](https://www.linkedin.com/company/typesafe-ai/) - 公司公告与招聘。

## SDK 与客户端

官方在前，社区在后。除非另行说明，社区包与 TypeSafe 无隶属关系。

- [Python SDK](https://github.com/typesafe-ai/typesafe-sdk-python) - 官方客户端。`pip install typesafe-sdk`。文档：[Python SDK](https://docs.typesafe.ai/sdk/python)。
- [JavaScript / TypeScript SDK](https://github.com/typesafe-ai/typesafe-sdk-js) - 官方客户端。`npm install @typesafe-ai/sdk`。文档：[JavaScript SDK](https://docs.typesafe.ai/sdk/javascript)。
- [System One adapter（Python）](https://github.com/typesafe-ai/system-one-adapter-python) - 官方提供的 `TypeSafeClient` 替身，后端走 LLM API，方便用同一套问题对比 Jev 与聊天模型。`pip install system-one-adapter`。
- [Vercel AI SDK provider](https://ai-sdk.dev/providers/ai-sdk-providers/typesafe-ai) - `@ai-sdk/typesafe-ai` + `experimental_evaluate`。可用 `typeSafeAi.evaluationModel('jev-latest')`，或 Gateway id `typesafe-ai/jev`。
- [Elixir SDK](https://github.com/nshkrdotcom/typesafe_sdk) - 社区 Hex 包 [`typesafe_sdk`](https://hex.pm/packages/typesafe_sdk)，支持 `system_one` 与模型列表。文档：[HexDocs](https://hexdocs.pm/typesafe_sdk)。
- [Jev（Elixir OTP）](https://github.com/dannote/jev) - Hex 包 [`jev`](https://hex.pm/packages/jev)：把 Jev 当成对等 GenServer，答案以消息到达再 pattern match，测试可以不碰网络
- [Ruby SDK](https://github.com/joshmn/typesafe-sdk) - 社区 Ruby 3.1+ 客户端：Noul / Choice / Score、重试、模型列表、线程安全连接池。没有异步客户端。
- [RubyLLM TypeSafe](https://github.com/kieranklaassen/ruby_llm-typesafe) - RubyLLM 2 的 TypeSafe provider，带离线模型元数据和类型化响应。
- [typesafe-ai-rails](https://github.com/GenieRobot/typesafe-ai-rails) - 基于官方 Python SDK 的 Rails 集成：配置、用量/成本遥测、可选置信度策略。
- [Rust SDK (typesafe-ai-rs)](https://github.com/gilljon/typesafe-ai-rs) - 独立的异步 / 阻塞 System One 客户端。
- [TypeSafe AI for Rust](https://github.com/Twister915/typesafe-ai) - 另一个 Rust 客户端：异步 + 阻塞传输、类型化响应、可观测重试。
- [typesafe-rs](https://github.com/AbdelStark/typesafe-rs) - 追求低延迟的 Rust 传输 SDK，目标与官方客户端行为一致。
- [s1-rs](https://github.com/AbdelStark/s1-rs) - 给 Choice / Score / Noul 的 Rust derive 层，支持类型化问题集、置信度门控和无网络测试。
- [Advocaat](https://github.com/pithings/advocaat) - 小巧的 TypeScript 客户端，带 chances、choices 和 scores 辅助函数。
- [Scala / ZIO SDK](https://github.com/jamesward/zio-typesafe-ai) - 社区 ZIO 客户端，带 noul / choice / score 的小型 DSL。
- [.NET SDK](https://github.com/saibimajdi/typesafe-dotnet-sdk) - 社区客户端，支持类型化提问和带置信度的答案。
- [PHP SDK](https://github.com/Butochnikov/typesafe-sdk-php) - 非官方 PHP 客户端：类型化 DTO、Promise 与异常。被下面的 Laravel 包使用。
- [Laravel TypeSafe Jev](https://github.com/Butochnikov/laravel-typesafe-jev) - 非官方 Laravel 12/13 集成：配置、门面、作用域 DI，以及基于 PHP SDK 的录制测试替身。
- [jev-go](https://github.com/Gaurav-Gosain/jev-go) - 非官方 Go 客户端，用于类型化判断与校准概率。`go get github.com/Gaurav-Gosain/jev-go`。
- [Stumble/jev-go](https://github.com/Stumble/jev-go) - 非官方零依赖 Go SDK，支持直连 TypeSafe 与走 Vercel AI Gateway，带类型化提问、重试、交互式 CLI 与可安装的 Agent skill。
- [jevclient](https://github.com/AboveColin/jevclient) - 非官方异步 Python 客户端（`pip install jevclient`）。类型化的 Noul / Choice / Score 辅助函数，独立于官方 `typesafe-sdk`。
- [LlamaIndex Jev](https://github.com/WiktorB2004/llama-index-jev) - 基于官方 Python SDK 的非官方 LlamaIndex 重排器（`JevRerank`）与路由（`JevSingleSelector` / `JevMultiSelector`）。
- [Swift SDK](https://github.com/ainame/swift-typesafe) - 非官方 Swift 6.4 客户端，对齐 Python SDK 0.6.0 API，支持 Linux。
- [TypeSafe AI Swift SDK](https://github.com/alterhq/typesafe-sdk-swift) - 非官方零依赖 Swift 6 客户端，支持 Choice / Score / Noul，严格并发，可配置认证与重试，支持无网络测试。

## 应用

把 Jev 放进真实循环的开源产品与 demo。

- [Jev Ultrafast](https://github.com/browser-use/jev-ultrafast) - 来自 [Browser Use](https://github.com/browser-use) 的浏览器 Agent。Jev 在一次请求里同时选中操作和 DOM 元素；小 LLM 只有遇到 `TYPE_TEXT` 时才写文本。苏黎世 → 伦敦查 Google Flights 约 7 秒。含库、本地检查器和实测数据。
- [JevBrowserExt](https://github.com/chy4pro/JevBrowserExt) - Jev Ultrafast 的 Chrome 扩展（Manifest V3）端口：Jev 在一次请求里选好操作和 DOM 元素，小文本模型写入输入值，可在用户自己的标签页里跑，后端支持 OpenRouter、TypeSafe 或 Cloudflare；附带 17 个任务的无头 Chromium 测试套件与记录轨迹。
- [jev-ego](https://github.com/romaluev/jev-ego) - 基于 [ego lite](https://lite.ego.app/) 的浏览器 Agent：一次 TypeSafe 请求选好操作与下标元素；带 Agent 面向的 observe/act/suggest/step CLI。
- [jev-browser](https://github.com/Ying-Kai-Liao/jev-browser) - 非官方浏览器自动化：LLM 规划目标，Jev 在 Playwright 快照上决定每次点击/输入（约 300 ms/次）。提供库、CLI 与 MCP 服务（`npx -y -p jev-browser jev-browser-mcp`）。
- [Jev Browser (Vlad Terin)](https://github.com/vlad-terin/jev-browser) - Agent skill + 运行时：Codex 规划，Jev 选元素，runner 负责执行与单步校验。
- [typesafe-computer-use](https://github.com/awlevin/typesafe-computer-use) - macOS computer-use 循环：OCR 屏幕，Jev 分类下一步动作，然后点击。每步约 0.0002 美元。
- [Mobile Jev](https://github.com/droidrun/mobile-jev) - 基于 [Mobilerun](https://mobilerun.ai) 的安卓 Agent：Jev 决定每次点击。打开 Uber、从 SFO 到金门大桥到付款界面约 21 秒 / 9 步动作。提供在线 studio、CLI 与轨迹回放。不用 ADB。
- [Unclutter](https://github.com/kitze/unclutter) - Chrome / Firefox 扩展：Jev 识别非必要页面元素；后续访问由本地模板规则隐藏。
- [TypeSafe AdBlock](https://github.com/realZachi/typesafe-adblock) - Chrome 扩展：Jev 判断 DOM 元素是不是广告并将其移除。BYOK，无后端。作者称之为 demo，不是真广告拦截器。
- [HA-Jev](https://github.com/AboveColin/HA-Jev) - 非官方 Home Assistant 集成：针对实体状态的类型化提问变成传感器与自动化动作，带目标选择器，从用户自己的实体构建状态，并提供用量、成本和日预算实体。
- [Every](https://github.com/sufianetaouil/every) - 语义代码搜索 CLI：对每个函数问一个 yes/no 问题，按 Noul 概率排序。
- [blink](https://github.com/ellipsis-dev/blink) - 代码库搜索：一组 walker 询问 Jev 哪个文件能回答自然语言查询。
- [Jev Code Finder](https://github.com/Peu77/JevFind) - 基于 Jev 的语义代码搜索 CLI：根据自然语言描述评估文件路径相关性，并精准定位代码行与置信度。
- [Jev Search](https://github.com/superagents-lab/jev-search) - 非官方网页搜索应用，用 Jev 的 Choice 和 Noul 判断挑选来源、时间范围和候选 query，再对通过 Search1API 取回的结果排序。
- [neo4jev](https://github.com/jexp/neo4jev) - Neo4j 图漫游：在每个节点上让 Jev 选择走哪条关系，对对数概率做 beam search。
- [hono-jev-router](https://github.com/yusukebe/hono-jev-router) - 实验性 Hono 路由：Jev 把传入请求匹配到自然语言路由描述。
- [sqlite3-jev](https://github.com/mattn/sqlite3-jev) - SQLite C 扩展：通过 libcurl 把 `jev_noul` / `jev_choice` / `jev_score` 暴露为 SQL 函数。
- [jevql](https://github.com/kylemclaren/jevql) - 针对原生 Postgres 的非官方 psql 风格 CLI 与 Go/TypeScript/Python SDK：直接在普通 SQL 里写 `jev()` / `jev_prob` / `jev_choice` / `jev_score`，无需数据库插件，SQL 在服务端跑，Jev 批量评估剩余行。
- [jev-resilience](https://github.com/Vicente-MD/jev-resilience) - 非官方 Spring WebFlux starter：用 Jev 识别静默 HTTP 200 失败的语义熔断器。
- [tripwire](https://github.com/noelzappy/tripwire) - 非官方 AI SDK 中间件与兼容 OpenAI 的代理：在每个 LLM 响应上并行跑 7 项 Jev 检查，耗时约 100 ms，带置信度门控。
- [ProgressGate](https://github.com/AshutoshVJTI/progressgate) - 检测 Agent 循环中的语义停滞：Jev 评估轨迹；代码返回 CONTINUE / WARN / REPLAN / HALT。
- [jev-harness](https://github.com/AntonioCoppe/jev-harness) - 围绕 Jev 的非官方生产层：策略、置信度门控、影子模式、recipes 与评测 CLI。
- [jev-tree](https://github.com/reachjalil/jev-tree) - 在分类树上递归 Choice，突破 Jev 的 255 选项上限。
- [jev-shell-history](https://github.com/mrnugget/jev-shell-history) - Fish 风格的 zsh 自动建议：打字时由 Jev 给最近历史排序。
- [Supercov](https://github.com/supercorp-ai/supercov) - 给编程 Agent 用的代码质量与测试覆盖评估：Jev 给每个源文件打分，让 Agent 知道先改哪里。
- [Jev Review](https://github.com/devagrawal09/jev-review) - 分阶段代码审查工作流与本地看板，由聚焦的 Jev 调用驱动。
- [Foreman](https://github.com/thruwire/foreman) - 软件工场循环：Codex 实现，Jev 独立判断完整度、测试以及是否需要人工介入。
- [Jev Drone](https://github.com/RomanSlack/jev-drone) - MuJoCo 四旋翼：控制与安全留在代码里，Jev 处理较慢的战术判断。
- [Jev 玩星际争霸](https://github.com/phyous/tsai-sc) - 针对初代星际争霸共享版战役的结构化状态测试平台，带已验证的运行记录与概率轨迹。
- [Jev × 文明 II](https://github.com/phyous/tsai-civ2) - 浏览器跑初代文明 II；Jev 决定帝国、城市、科研与单位行动。实验性质，尚无实测获胜。
- [Jev Moderation Bot](https://github.com/brainstormity/Jev-Moderation-Bot) - 基于 Jev Choice 与 Noul 的 Discord 审核机器人：实时检测垃圾信息与诈骗链接、分析成员行为画像并支持动态误报纠错。
- [Jev-AV 与 Jev Guard](https://github.com/newuser7171/antivirus) - 基于 Jev System One 的 AI 杀毒软件、URL 威胁检测、Windows 实时进程 EDR 哨兵与 Android APK 安全分析器，支持 CustomTkinter 桌面 GUI 与批量分流。
- [Jev Trader](https://github.com/jarrodwatts/jev-trader) - 每个 Monad 区块在 Kuru 的 MON-USDC 订单簿上做一次买/卖决策。在线 demo：[jev-trader.vercel.app](https://jev-trader.vercel.app/)。
- [Human Compiler](https://github.com/asfarsadewa/human-compiler) - 粘贴职场客套话，Jev 给被动攻击、紧急程度和信息密度打分，代码输出 rustc 风格诊断。在线体验：[human-compiler.asfarlab.fun](https://human-compiler.asfarlab.fun)。
- [JEVMETER](https://github.com/ChetasLua/jevmeter) - 针对任意视频的实时 Jev 打分表：每句话都打分，渲染成 16:9 剪辑。Demo 见 [Chetaslua](https://x.com/chetaslua/status/2100473581251748216)。
- [jev-audio-beeper](https://github.com/santos-sanz/jev-audio-beeper) - 低延迟音频辱骂检测：Jev 下判断，ffmpeg 约 466 ms 内哔掉对应片段，不重写整轨。
- [jev-askable-arm](https://github.com/TarunTomar122/jev-askable-arm) - 仿真 Franka 机械臂上的零样本英语目标，Jev 负责串联硬编码原语。
- [jev-codex-router](https://github.com/0xNatoshi/jev-codex-router) - 逐轮 Codex 路由：Jev 选择模型、思考深度和速度模式。
- [jev-router](https://github.com/gargpratyush/jev-router) - 给 Claude Code 和 Codex 用的逐轮路由：Jev 把简单任务派给快速模型，把困难任务派给强模型。`npm i -g jev-router`。
- [jev-secret-detection](https://github.com/teyhouse/jev-secret-detection) - diff 敏感信息检测器，Jev 结论具备可复现性。
- [commit-miner](https://github.com/devanshbatham/commit-miner) - 用 Jev 给 commit diff 分类的 Rust CLI：修 bug、安全/CWE 与修改类型。输出 HTML/CSV 报告。
- [jev-eval-agent](https://github.com/vinilana/jev-eval-agent) - Jev 早期测试的公开评测 harness。
- [Jev Logs](https://github.com/reachjalil/jevlogs) - OpenTelemetry 日志分类：在大模型看归档前，由 Jev 给诊断价值与优先级打分。
- [智能家居助手 demo](https://docs.typesafe.ai/demos/smart-home) - 官方对[投机扇出（speculative fan-out）](https://docs.typesafe.ai/patterns/fan-out)的交互式 demo：一次问很多题，代码只保留相关答案，LLM 仅负责拆分和闲聊。源码预计随正式发布在 GitHub 开放。
- [jev.nvim](https://github.com/valentynkit/jev.nvim) - Neovim 插件：用 Treesitter 把 buffer 拆成函数，用 Jev 对自然语言问题打分，在 quickfix 窗口按概率排序。
- [jev-skip](https://github.com/valentynkit/jev-skip) - 浏览器扩展：读取 YouTube 字幕轨，在片头结束前在进度条上标注分段赞助概率，不依赖群众数据库，实测 23 个视频里抓到 SponsorBlock 77% 的赞助时长，每个视频成本 0.0008 美元。

## Demo 与游戏

玩具、在线页面与实时 Agent。大部分在发布后 48 小时内成形。

- [Yes / No](https://yesno.coderai.dev) - 免注册 Noul demo。提问，得到 yes / no / maybe，需要时会调用网页搜索。
- [Jev Tetris](https://jev-omega.vercel.app) - Jev 根据空洞、堆叠高度和凹凸度选旋转与列。
- [Jev Pac-Man](https://jev-pacman.ephraimduncan.com) - 迷宫表达为 JSON；Jev 实时在每个岔路口选方向。
- [typesafe-mario](https://github.com/fhshaik/typesafe-mario) - 从模拟器结构化状态玩超级马里奥兄弟。
- [jev-doom-agent](https://github.com/lukaske/jev-doom-agent) - 浏览器原生 Doom，带 Chocolate Doom WASM、空间状态与实时决策遥测。
- [jev-gomoku](https://github.com/mizchi/jev-gomoku) - MoonBit 客户端 + Jev 对打五子棋；文章：[jev 同士に五目並べで対战させた](https://zenn.dev/mizchi/articles/jev-plays-gomoku)。
- [jev-t-rex-runner](https://github.com/joshlarsen/jev-t-rex-runner) - Jev 玩的 Chrome 小恐龙。
- [snake-jev](https://github.com/siroccomask/snake-jev) - 贪吃蛇：每局做出几百次类型化转向决策。
- [Jev Guard](https://guard-jev.vercel.app) - 评论审核演练场。
- [Hollow Creek](https://hollow-creek-sigma.vercel.app) - 村庄 NPC 每 tick 对你进行*判断*（做什么、什么感受），而不是聊天。
- [Jev 情绪 demo](https://jev-demo.vercel.app) - 持续说好话或坏话；结构化状态记录情绪变化。
- [Jev Room](https://jev-room.moe136231.chatgpt.site) - 一句话 → 6 个房间配置。Jev 选择，应用渲染。
- [TypeSafe 打字机](https://typesafe-demo.val.run/) - 在线 Val Town demo：打字时实时更新 16 项类型化判断。发布推文见 [Steve Krouse](https://x.com/stevekrouse/status/2100287368221659289)。
- [got-jev](https://github.com/phureewat29/got-jev) - 《权力的游戏》角色扮演（扮演琼恩·雪诺）。故事模型写场景；Jev 判断身在何处、危险程度有多高、底下该配什么背景音乐。
- [Little Airways](https://github.com/lbotinelly/jev-little-airways) - 玩具群岛空中交通管制：Jev 根据每架飞机的局部状态判断备降/紧急情况/谁先降落，耗时约 150 ms。
- [jev-plays-pokemon-red](https://github.com/valentynkit/jev-plays-pokemon-red) - PyBoy 上的宝可梦红版：确定性代码控制路线与算术，Jev 仅在分支处做选择，每回合濒死预测都用 Brier 对照模拟器内存状态打分。
- [jev-canvas](https://github.com/gaborishka/jev-canvas) - 在 tldraw 画布上用语音和摄像头追踪的手指作画；Jev 根据每次局部语音听写决定动作、目标与放置位置。支持英语与乌克兰语指令。

## Agent 工具

把 Jev 暴露给编程 Agent 与 MCP 客户端的工具。

- [APA Agent 决策 Harness](https://github.com/AiPersonacademy/apa-agent-harness) - 适用于 Claude Code、Codex、Cursor 与 Antigravity 的生产级决策脚手架，具备置信度门控策略路由、影子模式与执行轨迹验证。
- [TypeSafe agent skill](https://github.com/typesafe-ai/skills) - 官方技能包：原语、模式以及如何组织评测。Claude Code：`claude plugin marketplace add typesafe-ai/skills`，然后 `claude plugin install typesafe@typesafe-ai`。其他 Agent：`npx skills add typesafe-ai/skills --skill typesafe-ai`。
- [fast-jev-compaction](https://github.com/tamaratran/fast-jev-compaction) - Claude Code 插件与 npm 库：由 Jev 给工具调用打分并剔除过时项，而不是粗暴总结上下文。
- [SkillRanker](https://github.com/Dicklesworthstone/skillranker) - Rust CLI：Jev 根据实时会话上下文为下一步该用哪个 Agent skill 排序，带 Claude Code hooks。
- [Jevbridge](https://github.com/gamesonrblx/Jevbridge) - 非官方 ACP/MCP 适配器：让 Codex、Claude、Grok 与 OpenCode 身边多出类型化 Jev 决策与 computer use。
- [eve](https://github.com/vercel/eve) - Vercel 的 Agent 框架。实验性 `autoModel` 默认调用 Gateway `typesafe-ai/jev` 从允许列表中挑语言模型。
- [jev-mcp](https://github.com/jkudish/jev-mcp) - 封装三个 cookbook 模式的 Node MCP：`jev_verify`（引文核查）、`jev_screen`（提示词注入/护栏）、`jev_find`（不依赖 embedding 的语义排序）。`npx -y github:jkudish/jev-mcp`。
- [Jev MCP (Python)](https://github.com/blakestone-x/jev-mcp) - Python MCP 服务：提供 classify、score、check、match 与 screen 工具。
- [Jev Review MCP](https://github.com/NiazMorshed2007/jev-review) - 本地优先 MCP：Claude Code、Codex、Cursor 与 OpenCode 边写代码边获得 Jev 的结构化质量审查。与上面的 [Jev Review](#应用) 不是同一项目。
- [typesafe-mcp](https://github.com/itsmostafa/typesafe-mcp) - 面向 Claude Desktop、Claude Code 和 Codex 的 Go CLI 与单二进制 MCP。
- [pi-typesafe](https://github.com/DevMortimer/pi-typesafe) - Pi 扩展：带同意管理与密钥管理的单一 TypeSafe 客户端，支持批量 `typesafe_evaluate` 和可脱网测试的传输层。
- [pi-jev](https://github.com/y0usaf/pi-jev) - 带影子模式工具调用门控、输出评判与类型化 `jev_ask` 的 Pi 扩展。
- [pi-warden](https://github.com/DevMortimer/pi-warden) - 基于 pi-typesafe 的 Pi 护栏：拦截工具结果而不是弹窗；对照项目规则文件进行写入检查。
- [pi-jev-auto-mode](https://github.com/jomatsu/pi-jev-auto-mode) - Pi 自动模式：Jev 在语义上批准 `bash` / `write` / `edit`，无法决定时默认 fail closed。
- [Bicameral](https://github.com/AbdelStark/bicameral) - Pi 编程 harness：LLM 负责写，Jev 提供策略、循环检测和审查的类型化反射。明确不是沙箱。
- [jev-pref](https://github.com/doeixd/jev-pref) - 把 AGENTS.md 偏好变成 Jev 驱动的 AI linter：在 `jev-pref.json` 里写针对项目的语义审查规则，对照 diff、暂存文件或 PR 检查，把发现反馈给编程 Agent。`npx jev-pref setup`。
- [ask-jev-skill](https://github.com/shantanugoel/ask-jev-skill) - Hermes skill：Agent 需要做边界明确的决策时向 Jev 提问。
- [jev-system-architect](https://github.com/samtay32/jev-system-architect) - 搜寻脆弱语义逻辑并将其转化为 Choice / Score / Noul 边界的技能包。
- [augustus](https://github.com/24601/Augustus) - 设计判断技能：把 Choice/Score/Noul 映射到经典方法（决策论、重排、路由），带组合代数、问题设计诊断与可证伪验证门。
- [jev-browser MCP](https://github.com/Ying-Kai-Liao/jev-browser) - 同上项目；提供 `browser_do`、`browser_check`、`browser_choose` 等 MCP 工具，Agent 不用读完整快照就能操作页面。
- [jev-ego](https://github.com/romaluev/jev-ego) - 同上项目；在运行中的 ego lite TaskSpace 上做 observe/act/suggest/step。
- [jev-axi](https://github.com/shiftynick/jev-axi) - CLI + Claude Code / Codex hooks：Jev 在 shell 命令执行前评估危险程度，对拉取的文本做提示词注入筛查，常规命令本地快速裁决，不发往远端。
- [jev-belay](https://github.com/valentynkit/jev-belay) - Claude Code Stop hook：在轻信“已完成”之前检查上下文痕迹，仅在文件被修改但尚无通过检查时消耗一次 4 题 Jev 调用，所有出错分支均 fail open。
- [jev-commit](https://github.com/valentynkit/jev-commit) - Pre-commit hook：单次 Jev 调用判断 commit message 是否契合暂存区的 diff，揪出遗留调试代码和未提及的修改，且仅在检测到凭据泄露时阻断。

## 研究与开源模型

受 Jev 接口启发的独立工作。这些不是 TypeSafe 官方模型。

- [jevlike](https://github.com/vinnylarouge/jevlike) - 训练单 pass 小打分器：输入 context + N 个文本选项，输出各选项的概率。含 Doom / 国际象棋视觉 demo 和 Wikispeedia 下一步点击例子。明确*不是*复现 TypeSafe 架构或 RLCD。
- [openjev](https://github.com/TheoLeeCJ/openjev) - 能否在单张家用 RTX 3090 上跑类似 Jev 的东西？读选项 logit，不生成文本。不是 TypeSafe 的模型。
- [PocketJev](https://github.com/NullPo-jp/PocketJev) - iPhone 上的端侧视觉决策，走 MLX + Qwen3-VL 选项 logits。摄像头 + 3 选 1，不生成文本，约 1 秒，不保存照片。
- [jev-visual](https://github.com/hr98w/jev-visual) - Apple Silicon 上的教学用 Jev 式视觉推理：共享多模态上下文、候选打分、分拣工厂 / 打砖块 / 手势 demo。不是 TypeSafe 的模型。
- [jevmlx](https://github.com/bnsd55/jevmlx) - 面向 Apple Silicon 上任意 MLX 模型的 Jev 风格并行受限决策：单次 forward pass 输出符合 schema 的 JSON。
- [JEVfire](https://github.com/kikoncuo/jevfire) - 通过 vLLM 为 CUDA LLM 提供受 Jev 启发的并行决策，带浏览器马里奥 demo（本地约 71 ms/动作）。
- [decider](https://github.com/Mapika/decider) - Qwen3.5-2B 微调，单 pass 输出带校准概率的类型化决策。非官方；不是 TypeSafe 架构。
- [LitJev](https://github.com/zhengxuyu/litjev) - 对 Jev 的复现：把任意 Qwen 模型变成快速决策模型，提供同款 `/v1/systemone` 接口（Choice、Score、Noul），无需训练，不生成回答文本。非官方；不是 TypeSafe 模型。
- [PlayJev](https://github.com/OmniJev/PlayJev) - Qwen3.5-0.8B-Base 微调后玩 10 款浏览器游戏（从 448 px 帧画面输入）：每步一次 forward pass，从选项字母直接读出游戏选项列表上的概率分布，不生成文本。权重开源，10 款游戏可在浏览器试玩。非官方；不是 TypeSafe 模型。
- [typesafe-ai-benchmark](https://github.com/iammrduncan/typesafe-ai-benchmark) - 在 Cerebras 上对同批 System One 问题对比 Jev 与 Qwen 3.8 27B。视频：[Shannon](https://x.com/iamMrDuncan/status/2100467548298899918)。
- [Jev Rerank Bench](https://github.com/anessbelbati/jev-rerank-bench) - 重排对比实验，带原始响应、打分代码、不确定性区间与详尽说明。
- [Jev 垃圾邮件评测](https://github.com/bitnovus/jev-spam-eval) - 针对训练过的 TF-IDF 基线的零样本垃圾邮件探索，附后验调优警示。
- [Jev 钓鱼邮件 Benchmark](https://github.com/anisselbd/jev-phishing-bench) - 2000 封邮件：Jev 对比 Claude Haiku 4.5 判断是否点击，比校准度、延迟和成本。Haiku 在此评测中准确率胜出。
- [jev-agent-failure-benchmark](https://github.com/TokenTrim/jev-agent-failure-benchmark) - Who&When Pro（注入式 Agent 失败）：Jev 与强 LLM 在判断“谁/哪步/什么错误类别”上的对比。
- [jev-sec-bench](https://github.com/Gaurav-Gosain/jev-sec-bench) - 基于 jev-go 在公开语料上做的盲测提示词注入与脆弱代码检测基准。
- [Jev DSPy Lab](https://github.com/jmanhype/jev-dspy-lab) - 非官方 DSPy 伴生库，可录制并回放 TypeSafe 调用，同时测量校准度、选择性风险、置信度门控弃权、延迟、token 与模型成本。
- [jevcal](https://github.com/abhixhek/jevcal) - 非官方 CLI：在你自己的标注数据上为每个问题拟合置信度阈值以达到目标准确率，在留出集上验证，展示还有多少流量需要 LLM 回退，并在 Jev 更新打乱锁定的阈值时阻断 CI。
- [ASSAY-001](https://github.com/jourdanlabs/assay-001) - 独立预注册核验：Banking77 / CLINC150 上测 Jev 校准与类型安全。结论分裂，日志全公开。文章：[donttrustme.ai](https://donttrustme.ai/assay-001.html)。
- [Jev search rerank eval](https://github.com/zhuyansen/jev-search-rerank-eval) - 9831 对标注：Jev rerank 对照 BM25 / bge-m3，并量化评委循环偏差。融合最好；Jev 单独打不过 embedding。
- [吸烟史抽取评测](https://github.com/vclic/smoking-extraction-benchmark) - 1000 条合成病历：Jev 对 OpenAI structured outputs，比准确率、成本和延迟。

## Cookbook

官方与 APA 可直接照着改的工作流。完整目录：[console cookbooks](https://console.typesafe.ai/docs/cookbooks) 与 [文档索引](https://docs.typesafe.ai/llms.txt)。

- [APA Persona 状态路由指南](cookbooks/persona-state-routing.md) - AIPersona Academy 蓝图：利用 Jev Choice 和 Score 实现自主 Agent Persona 状态跳转，达到 0 毫秒幻觉延迟。
- [APA 社交情绪与策略护栏](cookbooks/social-sentiment-guardrails.md) - 毫秒级内容安全评分、提示词注入筛查与置信度门控。
- [APA 买家画像痛点与意向评分](cookbooks/buyer-persona-scoring.md) - 自动提取买家异议、量化痛点烈度并分类购买意向。
- [Parallel questions](https://docs.typesafe.ai/cookbooks/parallel_questions) - 对同一份 state 批量提问；一次调用代替 N 次。
- [Line-by-line search](https://docs.typesafe.ai/cookbooks/semantic_find) - 用 Choice 给几百行 id 打分，再用 Noul 检查「到底有没有答案」。
- [Re-ranking](https://docs.typesafe.ai/cookbooks/rerank_typesafe) - BM25 短名单，再对每个 query–候选对问一次 TypeSafe。
- [Guardrails for LLMs](https://docs.typesafe.ai/cookbooks/llm_guardrails) - 筛 LLM 的入站/出站消息；概率阈值写在代码里。
- [Double-checking citations](https://docs.typesafe.ai/cookbooks/citation_check) - Choice 判断引文上下文是否支撑主张；低置信度交给人工。
- [Classifying RAG passages](https://docs.typesafe.ai/cookbooks/classifying_rag_passages) - 在回答模型之前保留、标记或丢掉检索段落（矛盾、注入等）。
- [Function calling](https://docs.typesafe.ai/cookbooks/function_calling) - 把自然语言请求映射到普通类型化函数与闭集参数。
- [Skill suggestion](https://docs.typesafe.ai/cookbooks/skill_suggestion) - 给 Agent 技能目录排序，只细读前几名。
- [Hierarchical classification](https://docs.typesafe.ai/cookbooks/hierarchical_classification) - 在深层分类树上用 Choice 概率做 beam search。
- [SDE cascade](https://docs.typesafe.ai/cookbooks/sde_cascade) - 两阶段结构化抽取级联（mini → 校验 → 推理）。
- [Date extraction](https://docs.typesafe.ai/cookbooks/date_extraction_cookbook) - 先问文档里点名的日期部件，再在代码里解析校验。
- [Pre-parsed value extraction](https://docs.typesafe.ai/cookbooks/pre_parsed_value_extraction_cookbook) - 正则出候选，再让 Jev 选出目标片段。
- [Knowledge graph entity alignment](https://docs.typesafe.ai/cookbooks/entity_alignment) - 打分：合并 / 不链接 / 交给策展人。
- [Autoresearch feature discovery](https://docs.typesafe.ai/cookbooks/autoresearch_feature_discovery) - 把 TypeSafe 问题当成数值特征，喂给监督学习。
- [Classification using confidence](https://docs.typesafe.ai/cookbooks/classification_using_confidence) - 置信度够才报细分类，否则上爬一层。
- [Structure recovery](https://docs.typesafe.ai/cookbooks/autoformat) - 从丢掉格式的纯文本重建 Markdown。
- [Self-consistency: nouls](https://docs.typesafe.ai/cookbooks/consistency_noul_cookbook) / [choices](https://docs.typesafe.ai/cookbooks/consistency_choice_cookbook) - 不确定的概率走人工审核，同时保留原始数值。

## 模式

来自文档与 AIPersona Academy 工程标准的架构配方。

- [Speculative fan-out](https://docs.typesafe.ai/patterns/fan-out) - 一次问很多题（包括可能用不上的），在代码里过滤。
- [Confidence-gated routing](https://docs.typesafe.ai/patterns/confidence-routing) - 答案告诉你*是什么*；置信度告诉你*要不要动手*。
- [Composite scoring](https://docs.typesafe.ai/patterns/composite-scoring) - 原子分数，权重由你的代码掌控。
- [Intent routing](https://docs.typesafe.ai/patterns/intent-routing) - 先分类，再交给确定性逻辑、专用 LLM 或人。

另见：[How to build with TypeSafe](https://docs.typesafe.ai/concepts/how-to-build-with-system-one)、[用例地图](https://docs.typesafe.ai/concepts/use-case-map)、[置信度](https://docs.typesafe.ai/confidence)。

## 文章

独立实测、实验与报道。官方博文见 [官方资源](#官方资源)。

- [Mini-Vibe Check: TypeSafe's Jev Judged Everything I’ve Written in 0.7 Seconds](https://every.to/also-true-for-humans/mini-vibe-check-typesafe-s-jev-judged-everything-i-ve-written-in-0-7-seconds) - Every 的 Mike Taylor 用 Jev 扫过自己的写作语料。
- [TypeSafe AI debuts model for machines that plays Doom](https://www.theregister.com/ai-and-ml/2026/09/16/typesafe-ai-debuts-model-for-machines-that-plays-doom/5296711) - 发布新闻报道。
- [TypeSafeのJevを正しく驚く、それってLLMでできませんか？](https://zenn.dev/nwn/articles/824026c76116e0) - 用 Gemma 的 logit 并行复现 JSON 捷径，并在公开 Mario harness 上对比 Jev 与 LLM。
- [jev 同士に五目並べで対戦させた](https://zenn.dev/mizchi/articles/jev-plays-gomoku) - Jev 对打五子棋，带源码和耗时日志。
- [Jev: one judge call, or twelve dimension scores? I measured both on three tasks](https://agentjournal.dev/blog/llm-judge-vs-feature-extraction/) - 独立实测：三个分类任务上，每行一次直接提问 vs 12–14 个 Jev 维度加本地拟合权重，附 token 成本、置信区间与误报率。
- [Testing Jev on public and private data: classifier or filter?](https://amankumar.ai/blogs/jev-measured) - 16000 次调用对照 gpt-5.4-mini 与 gpt-5.6-luna：哪里赢、哪里崩、阈值怎么定。

## 相关

- [PyPI 上的 typesafe-ai](https://pypi.org/project/typesafe-ai/) - 社区注册的重定向包。真正该装的是 `typesafe-sdk`；此名用于挡住 slopsquatting。与 TypeSafe 无隶属关系。

## 贡献

见 [CONTRIBUTING.md](CONTRIBUTING.md)。简而言之：开一个 PR，加上项目链接和一句话简介。项目应当有用、有趣，并且真正基于 Jev（或明确受其接口启发）。

## 👥 社区贡献与生态构建者

特别鸣谢为 Jev 与 System One 生态做出卓越开源贡献的开发者与工程师：

<table>
  <tr>
    <td align="center">
      <a href="https://github.com/Peu77">
        <img src="https://github.com/Peu77.png" width="80px;" alt="Peu77" style="border-radius:50%;"/><br />
        <sub><b>Emil Ebert (@Peu77)</b></sub>
      </a><br />
      <sub><a href="https://github.com/Peu77/JevFind">Jev Code Finder</a> 作者</sub>
    </td>
    <td align="center">
      <a href="https://github.com/brainstormity">
        <img src="https://github.com/brainstormity.png" width="80px;" alt="brainstormity" style="border-radius:50%;"/><br />
        <sub><b>brainstormity (@brainstormity)</b></sub>
      </a><br />
      <sub><a href="https://github.com/brainstormity/Jev-Moderation-Bot">Jev Moderation Bot</a> 作者</sub>
    </td>
    <td align="center">
      <a href="https://github.com/newuser7171">
        <img src="https://github.com/newuser7171.png" width="80px;" alt="newuser7171" style="border-radius:50%;"/><br />
        <sub><b>newuser7171 (@newuser7171)</b></sub>
      </a><br />
      <sub><a href="https://github.com/newuser7171/antivirus">Jev-AV & Jev Guard</a> 作者</sub>
    </td>
  </tr>
</table>

*想要将你的开源项目收录在此？欢迎提交 PR 或在 [AIPersona Academy 官方社区](https://whop.com/aipersonaacademy) / [@aipersonaacad](https://x.com/aipersonaacad) 与我们联系。*

## 维护团队

由 **APA (AIPersona Academy / 人工智能画像学院)** 倾力策划与持续维护 — 赋能全球自主 AI Persona 架构师与 System One 研究者。

## 许可证

[CC0 1.0](LICENSE) — 本列表贡献到公有领域。
