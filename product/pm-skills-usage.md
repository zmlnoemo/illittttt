# pm-skills 使用教程

> pm-skills 在不同 AI 工具上的安装与使用方式汇总。详细请参考 [官方 README](https://github.com/phuryn/pm-skills)。

## 🚀 一句话起步

| 场景 | 用什么 |
|------|--------|
| 有了新点子 | `/discover` |
| 需要战略清晰 | `/strategy` |
| 写 PRD | `/write-prd` |
| 规划上线 | `/plan-launch` |
| 定义指标 | `/north-star` |

## 📥 安装方式（按工具分）

### 1️⃣ Claude Cowork（推荐 · 非开发者）

适合不想碰命令行的产品人。

1. 打开 **Customize**（左下角）
2. 进入 **Browse plugins** → **Personal** → **+**
3. 选择 **Add marketplace from GitHub**
4. 输入：`phuryn/pm-skills`
5. 9 个 plugin 自动安装完成

> 💡 之后可以直接用 `/discover`、`/strategy` 等命令。

---

### 2️⃣ Claude Code（CLI 开发者）

```bash
# 第一步：添加市场
claude plugin marketplace add phuryn/pm-skills

# 第二步：按需安装 plugin
claude plugin install pm-toolkit@pm-skills
claude plugin install pm-product-strategy@pm-skills
claude plugin install pm-product-discovery@pm-skills
claude plugin install pm-market-research@pm-skills
claude plugin install pm-data-analytics@pm-skills
claude plugin install pm-marketing-growth@pm-skills
claude plugin install pm-go-to-market@pm-skills
claude plugin install pm-execution@pm-skills
claude plugin install pm-ai-shipping@pm-skills
```

> 💡 建议一次全装，workflow 通常需要多个 plugin 协同。

---

### 3️⃣ Codex CLI（OpenAI）

```bash
# 添加市场
codex plugin marketplace add phuryn/pm-skills

# 安装 plugin
codex plugin add pm-toolkit@pm-skills
# ... 后面同 Claude Code
```

⚠️ **注意**：Codex 不支持 `/slash` 命令，commands 装上但用不了。

**替代方式**：用自然语言描述 workflow：

> Run product discovery on [idea]: brainstorm options, map assumptions, prioritize the risky ones, then design experiments — pause between each step.

或让 Codex 帮你把 commands 转成 skills：

> Read the command files in the pm-execution plugin and create equivalent Codex skills for the workflows I use most often.

---

### 4️⃣ Cursor（你正在用）

**只支持 skills，不支持 `/command`。** 需要手动复制。

```bash
# 1. 先 clone 仓库
git clone https://github.com/phuryn/pm-skills.git

# 2. 把 skills 复制到 .cursor/skills/
#    Windows PowerShell:
Copy-Item -Path "pm-skills\pm-*\skills\*" -Destination ".\.cursor\skills\" -Recurse -Force
```

之后在 Cursor 里就可以用自然语言触发 skill（无需 `/`），例如：

> What are the riskiest assumptions for our AI writing assistant idea?

Cursor 会自动加载相关 skill 框架回答你。

---

### 5️⃣ 其他工具

| 工具 | 复制到 |
|------|--------|
| Gemini CLI | `~/.gemini/skills/` |
| OpenCode | `.opencode/skills/` |
| Kiro | `.kiro/skills/` |

---

## 🧭 推荐使用路径

### 路径 A：完整产品立项（耗时 2-4 小时）

```
1. /discover 你的产品想法
2. /strategy → 9 节战略画布
3. /write-prd → 输出 PRD
4. /plan-launch → GTM 策略
5. /north-star → 北极星指标
```

### 路径 B：快速 PRD（30 分钟）

```
1. /write-prd [一句话想法]
2. /pre-mortem → 找漏洞
3. /write-stories user|job|wwa → 拆分需求
```

### 路径 C：日常 PM 工具

- 写 OKR → `/plan-okrs`
- Sprint 复盘 → `/sprint retro`
- 用户访谈 → `/interview prep|summarize`
- 竞品分析 → `/competitive-analysis`
- 简历打磨 → `/review-resume`

---

## 💡 小贴士

1. **安装后第一次使用命令前**先输入 `/help` 看看加载了哪些插件
2. **PM Brain 配合使用效果翻倍**：[pm-brain](https://github.com/phuryn/pm-brain) 让 AI 记住你的项目上下文
3. **遇到错误或 Windows 兼容问题**：官方在 README 末尾有 PowerShell 解决方案（监控 CoworkVMService）

---

## 🪟 Windows 用户特别提示

如果你用 Cowork 且 Windows 上不稳定（VM 启动失败），可执行官方提供的 PowerShell 脚本设置定时任务，监控 `CoworkVMService`，90% 的问题能解决。详见官方 README 末节。
