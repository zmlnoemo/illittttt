# archify

> 一句话把你的想法、计划、代码库变成可交互的架构图 / 流程图 / 时序图。

- **原仓库**：[tt-a1i/archify](https://github.com/tt-a1i/archify)
- **官网**：[archify.si](https://archify.si)
- **当前版本**：v3.1.0（2026-10-14）
- **License**：MIT
- **里程碑**：GitHub Trending 全语言周榜 #1（2026-09-01），登过 QbitAI 首页
- **为什么收录**：写技术文档时画架构图是最费时间的活；archify 让你用一句话生成**可分享、可交互、有源码链接**的图，输出还是单一 HTML 文件，方便嵌入 Confluence、Notion 或直接发给同事。

## 🎯 它解决什么问题

- 给一个项目画架构图 → 用自然语言描述 + agent 自动扫代码生成
- 写技术方案要画流程图 → 不用打开 draw.io / Figma
- 复盘事故要画时序图 → 把日志喂给 agent 直接出图
- 团队分享系统设计 → 输出单一 HTML，发给任何人都能交互

## 🧠 它不是什么

- ❌ 不是通用画图工具（不是 draw.io、Figma 替代）
- ❌ 不是 Mermaid 主题包装
- ❌ 不是可视化编辑器（不支持手动拖拽）

**它是什么**：技术意图 → 通信制品（technical intent → communication artifact）。

## 🧩 10 种图表类型

| 类型 | 适用场景 | 在 prompt 里说明什么 |
|------|---------|---------------------|
| **Architecture** | 组件、服务、存储、边界 | 范围、核心组件、主路径 |
| **Workflow** | CI/CD、审批、工具调用、Runbook | 参与者、顺序、分支、异常 |
| **Sequence** | API 调用、缓存兜底、auth、异步追踪 | 调用方、被调方、返回、时序 |
| **Data Flow** | 管道、lineage、PII、消费者 | 来源、转换、存储、边界 |
| **Lifecycle** | 状态、重试、等待、终态 | 状态、事件、重试与取消路径 |
| **ERD** | 数据库 schema | 表、每个列、主外键、基数 |
| **Class** | 类、接口、类型关系 | 类型、成员、继承/实现/组合/依赖 |
| **Tree** | 单亲层次：仓库、模块、能力拆解 | 根、层级、每分支内容 |
| **Timeline** | 事故复盘、发布历史 | 时间戳、事件、源泳道 |
| **Waterfall** | 单次请求/agent 运行的耗时分布 | 跨度、起始/时长、嵌套、是否实测 |

> 不知道用哪个？直接问 agent："我想画 XXX，用哪种图？"

## 🏗️ 内部实现亮点

| 设计原则 | 说明 |
|---------|------|
| **Layout judgment over auto-layout** | Agent 决定层级、间距、路由，而不是通用自动布局 |
| **Typed JSON IR** | 每种模式都有 schema 和可复现源 |
| **Atomic validation before delivery** | 交付前过 schema、layout、HTML/SVG、route、label-to-route 5 道闸 |
| **Failures come with a repair receipt** | 失败时返回稳定 rule code + 主体 + 实测证据 + 修复建议 |
| **Last-good live preview** | 桌面循环看一个 JSON 文件，未通过校验前一直显示上次通过的图 |
| **Truthful interaction** | focus、upstream/downstream reach、route、role 对比、stories 都基于已声明的节点和关系，**不发明拓扑** |
| **Source evidence (optional)** | 证据节点标记 `SRC n`，可点开 GitHub commit-pin 的文件/行；普通图无此特性 |
| **Portable by default** | 产物是单一 HTML，导出仍保持完整图，不带 viewer 临时状态 |

## 🛠️ 支持平台

| 平台 | 安装位置 | 能力 |
|------|---------|------|
| **Cursor** | `~/.cursor/skills/` 或 `.cursor/skills/` | 完整 |
| **Claude Code** | `~/.claude/skills/` 或 `.claude/skills/` | 完整 |
| **Codex CLI** | `~/.agents/skills/` 或 `.agents/skills/` | 完整 |
| **OpenCode** | `~/.config/opencode/skills/` / `.opencode/skills/` / `.agents/skills/` | 完整 |
| **GitHub Copilot** | 支持 | — |
| **Kimi Work** | 插件市场搜 "Interactive Architecture Diagram" | 完整 |
| **Claude.ai** | 上传 `archify.zip` 到 Capabilities → Skills | 依赖沙箱 Node.js |
| **Hermes Agent** | `hermes skills install skills-sh/tt-a1i/archify/archify -y` | 社区维护 |
| **DeepSeek Harness** | `dsh plugin --profile web add @tt-a1i-1/archify-dsh@1.0.0` | 社区维护，需 Node ≥22.19 或 ≥24 |

## 📦 环境要求

- **Node.js** ≥ 18（部分集成 ≥ 22.19）
- 网络：可选（只用于更新检查；可设 `ARCHIFY_UPDATE_CHECK_DISABLED=1` 完全离线）

## 🎬 一句话起步

```bash
npx skills add tt-a1i/archify -g
```

然后在 agent 里说：

> Use Archify to draw: Browser → API → Redis cache → PostgreSQL fallback.

## 📚 完整使用教程

见同目录的 [`archify-usage.md`](./archify-usage.md) —— 含 Cursor / Claude Code / Codex 等多平台安装命令、prompt 模板、常见用法。
