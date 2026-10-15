# archify 使用教程

> archify 在各平台的安装与使用方式。详细请参考 [官方文档](https://archify.si/start.html?agent=cursor&type=architecture) 和 [GitHub README](https://github.com/tt-a1i/archify)。

## 🚀 30 秒起步

### 通用命令（大多数平台通用）

```bash
npx skills add tt-a1i/archify -g
```

### Cursor 显式非交互安装

```bash
npx -y skills add tt-a1i/archify --skill archify --agent cursor --global --copy --yes
```

### 不安装先试用

```bash
npx skills use tt-a1i/archify@archify --agent codex
```

## 📥 各平台详细安装

### 1️⃣ Cursor（你正在用）

```bash
# 方式 1：通用安装
npx skills add tt-a1i/archify -g

# 方式 2：显式非交互
npx -y skills add tt-a1i/archify --skill archify --agent cursor --global --copy --yes
```

安装位置：`~/.cursor/skills/`（用户级）或 `.cursor/skills/`（项目级）

### 2️⃣ Claude Code

```bash
npx skills add tt-a1i/archify -g
```

安装位置：`~/.claude/skills/` 或 `.claude/skills/`

### 3️⃣ Codex CLI

```bash
npx skills add tt-a1i/archify -g
```

或直接试用：

```bash
npx skills use tt-a1i/archify@archify --agent codex
```

### 4️⃣ OpenCode

```bash
npx skills add tt-a1i/archify -g
```

### 5️⃣ Kimi Work（推荐国内用户）

1. 打开 Kimi Work
2. 进入插件市场
3. 搜索 "Interactive Architecture Diagram"
4. 点击安装

### 6️⃣ Claude.ai

1. 下载 `archify.zip`
2. 进入 **Settings → Capabilities → Skills**
3. 上传 zip 文件

⚠️ 依赖沙箱是否支持 Node.js。

### 7️⃣ 其他平台

| 平台 | 安装命令 |
|------|---------|
| Hermes Agent | `hermes skills install skills-sh/tt-a1i/archify/archify -y` |
| DeepSeek Harness | `dsh plugin --profile web add @tt-a1i-1/archify-dsh@1.0.0` |

---

## 💡 常用 prompt 模板

### 模板 1：从一句描述开始（无仓库）

> Use Archify to draw: Browser → API → Redis cache → PostgreSQL fallback.

> Use Archify to draw: Web 请求先过 CDN，命中直接返回，未命中打 API，API 查 Redis，缓存未命中查 PostgreSQL。

### 模板 2：从代码仓库生成（带源码证据）

> Analyze this repository, then use archify to create a high-level runtime architecture diagram. Show 8–12 core components, one primary path, external dependencies, and trust boundaries. Put supporting detail in cards instead of adding more edges.

### 模板 3：流程图（CI/CD）

> Use Archify to draw the CI/CD workflow: 开发者 push → GitHub Actions 跑测试 → 构建 Docker 镜像 → 推送到镜像仓库 → ArgoCD 检测到变更 → 自动部署到 Staging → 人工审批后部署到 Production。

### 模板 4：事故复盘时序图

> Use Archify to create a sequence diagram for this incident:
> 
> 1. 14:00 用户请求失败率突增
> 2. 14:01 监控告警
> 3. 14:03 oncall 接到告警
> 4. 14:05 检查数据库连接池，发现被耗尽
> 5. 14:08 重启服务，临时恢复
> 6. 14:30 定位到是某上游服务异常重试导致
> 7. 14:45 联系上游团队修复

### 模板 5：ERD

> Use Archify to draw an ERD for my e-commerce database: users, orders, products, order_items, payments. Show all columns, primary/foreign/unique keys, and cardinality.

### 模板 6：继续迭代

生成图后可以追加：

> "Add authentication"  
> "Move auth to the left"  
> "Highlight the cache-miss path"  
> "Switch to the light theme"  
> "Show the rollback path in red"  
> "Remove the database"  

---

## 🎨 10 种图的适用场景速查

| 我想画... | 用什么图 | 示例 prompt |
|----------|---------|------------|
| 整个系统的组件关系 | Architecture | "8-12 components, primary path, trust boundaries" |
| CI/CD 流水线 | Workflow | "顺序、分支、异常" |
| 一次 API 调用的完整链路 | Sequence | "callers, callees, returns, timing" |
| 数据流向 + 敏感边界 | Data Flow | "sources, transforms, stores, boundaries" |
| 订单状态机 | Lifecycle | "states, events, retry, cancellation" |
| 数据库表结构 | ERD | "tables, columns, primary/foreign keys" |
| 类继承/依赖 | Class | "types, members, inheritance, dependencies" |
| 单亲层次结构 | Tree | "root, levels, what each branch contains" |
| 事故时间线 | Timeline | "timestamps, events, source lanes" |
| 单次请求耗时分布 | Waterfall | "spans, durations, nesting" |

---

## 🔧 进阶：CLI 直接调用

```bash
# 1. 健康检查
node archify/bin/archify.mjs doctor

# 2. 完整 demo
node archify/bin/archify.mjs demo /tmp/archify-demo

# 3. 看怎么画
node archify/bin/archify.mjs guide "Show CI/CD checks, approval, deploy, and rollback"

# 4. 校验 JSON
node archify/bin/archify.mjs validate workflow examples/agent-tool-call.workflow.json --quality showcase --json

# 5. 预览（loopback）
node archify/bin/archify.mjs preview workflow examples/agent-tool-call.workflow.json /tmp/workflow.html --quality showcase

# 6. 交付（生成最终 HTML 并自动打开）
node archify/bin/archify.mjs deliver workflow examples/agent-tool-call.workflow.json /tmp/workflow.html --quality showcase --open --json
```

## ⌨️ 查看器快捷键

| 操作 | 按键 |
|------|------|
| 打开 Diagram Guide | `?` |
| 搜索/聚焦节点 | `/` |
| 上下游追溯 | Focus 节点 → `Upstream` / `Downstream` |
| 探测路径 | `R` 或 `PATH` |
| 角色对比 | `L` 或 `LENS` |
| 打开总览雷达 | `M` 或 `MAP` |
| 进入演示模式 | `F` |
| 切换视觉风格 | `S` |
| 切换主题 | `T` |
| 打开导出 | `E` |
| 缩放/重置 | `+` / `-` / `0` |

## 🔗 稳定链接（可直接分享）

```
#focus=<id>
#focus=<id>&reach=upstream|downstream
#relation=<id>
#route=<source>~<target>
#lens=<kind>~<kind>
```

例如：

```
https://example.com/arch.html#focus=api&reach=downstream
```

---

## 💡 实用建议

1. **不要描述太多**：先画一个粗版本，再用对话补充细节
2. **想要可读性**：明确说"8-12 components, primary path"
3. **想要可分享**：直接发生成的 HTML 文件，对方无需安装任何东西
4. **离线使用**：`ARCHIFY_UPDATE_CHECK_DISABLED=1` 关闭网络请求
5. **节点超 20 个**：考虑拆成多张图或用 Tree
6. **事故复盘用 Timeline** + **接口调用用 Sequence** + **整体架构用 Architecture**，三件套

## 🪟 Windows 提示

- 安装时 PowerShell 默认允许 npx 即可
- 如果 `npx skills` 报 `npx: command not found`，升级 Node.js 到 ≥ 18
- 生成的文件直接双击 HTML 在浏览器打开即可
