# pm-skills（PM Skills Marketplace）

> PM 的 AI 操作系统：把一线 PM 的方法论（Teresa Torres、Marty Cagan、Alberto Savoia 等）注入到 AI 工作流里。

- **原仓库**：[phuryn/pm-skills](https://github.com/phuryn/pm-skills)
- **作者**：Paweł Huryn（AI PM 教练 · 前 CPO · 创办 [The Product Compass Newsletter](https://www.productcompass.pm/)，13万+ 订阅）
- **License**：MIT
- **为什么收录**：把零散的 PM 框架、PRD 模板、OKR 方法系统化为可调用的 AI 能力，**通用 AI 只能给文字，它能给你结构**。

## 📦 内容规模

- **9 个 plugins**（覆盖完整产品流程）
- **69 个 skills**（PM 框架与领域知识）
- **42 个 chained workflows**（链式工作流）

## 🧩 9 个 Plugin 一览

| # | Plugin | 用途 | Skills | Commands |
|---|--------|------|--------|----------|
| 1 | `pm-product-discovery` | 创意、实验、假设测试、OST、用户访谈 | 13 | 5 |
| 2 | `pm-product-strategy` | 愿景、商业模式、定价、竞争分析 | 12 | 5 |
| 3 | `pm-execution` | PRD、OKR、路线图、Sprint、Retro | 16 | 11 |
| 4 | `pm-market-research` | 用户画像、细分、旅程图、市场规模 | 7 | 3 |
| 5 | `pm-data-analytics` | SQL 生成、队列分析、A/B 测试 | 3 | 3 |
| 6 | `pm-go-to-market` | 滩头市场、ICP、增长循环、battlecard | 6 | 3 |
| 7 | `pm-marketing-growth` | 营销创意、定位、价值主张、命名、NSM | 5 | 2 |
| 8 | `pm-toolkit` | 简历审查、法律文档、校对 | 4 | 5 |
| 9 | `pm-ai-shipping` | 文档化 AI 写的代码、安全审计、性能审计 | 2 | 5 |

## 🧠 核心概念

- **Skill**：PM 框架与领域知识（如 `prioritize-features`、`opportunity-solution-tree`）。AI 检测到相关对话时自动加载。
- **Command**：以 `/command-name` 触发的链式工作流（如 `/discover` = brainstorm → 假设识别 → 假设排序 → 实验设计）。
- **Plugin**：相关 skills + commands 的可安装包。

## 🎯 最常用的 5 个命令

| 命令 | 作用 |
|------|------|
| `/discover` | 完整产品发现循环 |
| `/strategy` | 9 节产品战略画布 |
| `/write-prd` | 从一个想法生成 PRD |
| `/plan-launch` | 完整 GTM 策略 |
| `/north-star` | 定义北极星指标 + 输入指标 |

## 📚 方法论来源

skill 基于以下大师作品构建：Teresa Torres、Marty Cagan、Alberto Savoia、Dan Olsen、Roger L. Martin、Ash Maurya、Strategyzer、Christina Wodtke、Anthony W. Ulwick（JTBD）、Sean Ellis 等。

## 🔗 配套工具

- **[pm-brain](https://github.com/phuryn/pm-brain)** — PM 的第二大脑（Markdown 文件夹）
- **[The Product Compass Newsletter](https://www.productcompass.pm/)** — 作者的免费周刊

## 📖 完整使用教程

见同目录下的 [`pm-skills-usage.md`](./pm-skills-usage.md) —— 含 Cursor / Claude Code / Cowork / Codex 等多种安装方式。
