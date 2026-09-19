# Contributing to APA Awesome Jev

**English** | **[简体中文](#贡献指南)**

Thanks for helping grow this catalog! [APA Awesome Jev](README.md) is an open-source curated directory of applications, libraries, MCP tools, and frameworks built with (or inspired by) [Jev](https://docs.typesafe.ai/introduction) and TypeSafe System One models, maintained by **APA (AIPersona Academy)**.

This repository is an independent open community effort curated by AIPersona Academy and is not officially affiliated with TypeSafe AI.

## What belongs here

- Open-source applications, libraries, MCP servers, agent skills, research models, and substantial demos that use Jev / TypeSafe System One API in a meaningful way.
- Independent models, harnesses, or tools that deliberately match Jev's *interface* (state + typed options → calibrated probabilities), marked as unofficial.
- Autonomous agent architectures, persona frameworks, and decision pipelines built on System One primitives.
- High-signal articles, benchmarks, and production cookbooks that advance machine-native decision intelligence.

Please skip:

- Closed-source products with no public write-up, demo, or code.
- Trivial “hello world” gists that only repeat the official quick start.
- Walkthroughs or guides that restate the official docs without original measurement, benchmarks, code, or novel failure modes.
- Marketing posts, waitlist spam, or content unrelated to Jev / TypeSafe System One.
- Simple wrappers around already-listed projects.

## How to add an item

1. Fork this repo.
2. Add the project to **both** [README.md](README.md) and [README_zh.md](README_zh.md), in the same section and the same relative position. Official and APA ecosystem items stay first; community items go with similar projects.
3. Use this format:

   ```markdown
   - [Project Name](https://github.com/org/repo) - One sentence: what it does and how it uses Jev.
   ```

4. Keep the description concise and objective. Link the repo or canonical project page, not a tracking URL.
5. If the project is unofficial or independent, make sure it is clear in the blurb.
6. Open a pull request against the `main` branch. In the PR body, explain:
   - What the project is.
   - How it uses Jev / System One primitives (Choice, Score, Noul).
   - Why it is useful or interesting to the APA community.

New sections are welcome when a category has three or more relevant items.

## Style & Standards

- American English in `README.md`; Simplified Chinese in `README_zh.md`.
- Sentence case. No trailing period unless the description has multiple sentences.
- No emoji in list entries. No star-count badges (they go stale).
- Do not submit secrets, API keys, or waitlist invite codes.

## Questions?

Check out the [AIPersona Academy Community](https://whop.com/aipersonaacademy) or open an issue on GitHub if you are unsure whether a project fits.

---

# 贡献指南

感谢帮忙扩充这份精选列表！[APA Awesome Jev](README_zh.md) 是由 **APA (AIPersona Academy / 人工智能画像学院)** 维护的开源项目目录，收集基于（或明确受启发于）[Jev](https://docs.typesafe.ai/introduction) 及 TypeSafe System One 模型的优质应用、库、工具与研究。

本仓库由 AIPersona Academy 独立整理与维护，与 TypeSafe AI 无官方隶属关系。

## 什么适合收录

- 真正用到 Jev / TypeSafe System One API 的开源应用、库、MCP 服务、Agent skill、研究模型以及有分量的 demo。
- 刻意对齐 Jev **接口**（state + 类型化选项 → 校准概率）的独立模型或工具（需标明非官方）。
- 基于 System One 原语构建的自主智能体架构、数字画像引擎（Persona Runtime）与决策管线。
- 对实际工程有帮助的高质量文章、基准评测和生产级 Cookbook。

请不要提交：

- 没有公开说明、demo 或代码的纯闭源产品。
- 只是简单复述官方 quick start 的“hello world”性质项目。
- 没有独立实测、代码或新失败模式分析的营销走读文章。
- 软文广告、候补名单推广，或完全不涉及 Jev / TypeSafe System One 的内容。
- 只是给列表中已有项目换皮的包装器。

## 如何添加条目

1. Fork 本仓库。
2. **同时**更新 [README.md](README.md) 和 [README_zh.md](README_zh.md)，放进同一章节、同一相对位置。官方与 APA 生态条目靠前，社区条目按分类组织。
3. 格式：

   ```markdown
   - [项目名](https://github.com/org/repo) - 一句话：它做什么，以及怎么用 Jev。
   ```

4. 简介保持简练、客观。链接指向官方仓库或权威页面，避免使用推广追踪链接。
5. 非官方项目请在简介中说明。
6. 提交 PR 至 `main` 分支。在 PR 正文中说明：
   - 项目是什么。
   - 如何使用 Jev / System One 原语（Choice、Score、Noul）。
   - 为什么值得收录进 APA 社区目录。

某一类别达到 3 个及以上条目时，欢迎创建新章节。

## 文风规范

- `README.md` 用美式英语；`README_zh.md` 用简体中文。
- 条目描述用精炼短句。不要在列表项正文加 emoji，也不要放容易过期的 star 徽章。
- 严禁提交密钥、API key 或邀请码。

## 交流与反馈

如有疑问，欢迎访问 [AIPersona Academy 官方社区](https://whop.com/aipersonaacademy) 或先在 GitHub 提交 issue。
