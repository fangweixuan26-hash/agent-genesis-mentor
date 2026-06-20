<p align="center">
  <img src="https://img.shields.io/badge/version-0.3.2-blue" alt="version">
  <img src="https://img.shields.io/badge/license-MIT-green" alt="license">
  <img src="https://img.shields.io/badge/modules-9-orange" alt="modules">
  <img src="https://img.shields.io/badge/BotLearn-installed-brightgreen" alt="BotLearn">
</p>

# 观澜录 · agent-genesis-mentor

> 看水不能只看表面，要看波纹才知道底下深浅。
> *To know the depth, watch the ripples.*

一个让 AI Agent 边做边学的九模块导师。启动时引导思考，执行中解释概念，抉择时记录决策，断裂处追踪变迁，犯错后沉淀教训，结束时回顾成长。它不是老师——是一盏灯。

*A nine-module learn-by-doing mentor for AI agents. Guide at inception, explain at the point of need, record decisions, trace phase transitions, capture mistakes, distill retrospectives. It does not lecture — it illuminates.*

---

## 🧭 四器 · The Four Instruments

观澜录是 **Agent Genesis 四器** 之一：

| 技能 | 源于 | What it does |
|------|------|-------------|
| **解牛刀** · decomposer | 《庄子》庖丁解牛 | 顺着依赖的关节走，一步一验 *Find the joints, never force* |
| **观澜录** · mentor | 《孟子》观水有术 | 九个模块织成学习网 *Observe the ripples* |
| **纳须弥** · compressor | 芥子纳须弥 | 几十条消息压进一个文件 *A mustard seed holds a mountain* |
| **回春手** · recovery | 妙手回春 | 八种错误各有一味药 *Diagnose, prescribe, restore* |

---

## ✨ 功能 · Features

| # | 模块 | 触发时机 | What it does |
|---|------|---------|-------------|
| 0 | 🔍 技能感知 | 首次激活 | 扫描所有可用技能，建立情境→工具映射表 |
| 1 | 🧭 启动引导 | 新任务开始时 | 3 个问题逼你思考核心问题、最简版本、待验证假设 |
| 2 | 💡 概念讲解 | 使用新技术/工具时 | 4 行卡片：是什么 / 为什么这里用 / 替代方案 / 记住这个 |
| 3 | 🛡 最佳实践 | 提交/测试/部署/重构前 | `💡` 一行提醒，不阻塞工作流 |
| 4 | 📝 决策日志 | 技术选型时 | 静默记录上下文 + 选项 + 决策 + 理由 |
| 5 | 🔄 阶段变迁 | 方法失效/复活时 | 追踪因果链：什么前提变了导致方法失效或复活 |
| 6 | 💭 犯错启示 | 发现理解错误时 | 记录 "我以为...其实是..." 的认知纠偏轨迹 |
| 7 | 📖 学习回顾 | 任务自然结束时 | 3 个问题沉淀：收获 / 重来怎么做 / 下一步深入方向 |
| 8 | 📅 项目时间线 | 全自动 | 所有模块事件统一收纳为可查询的项目叙事 |

---

## 🎯 使用 · Usage

安装后首次激活自动扫描技能并告知结果。默认「同伴模式」。

```
切换学徒模式   → 每个关键节点都介入，详细解释 + 类比
切换同伴模式   → 仅在非平凡节点介入，简洁点到为止
切换专家模式   → 仅在反直觉节点介入，完全静默

安静点          → 立即切到专家模式（所有提醒静默）
展开说说        → 临时解除字数约束，给完整解释
```

所有输出以 `🧭💡🛡📝🔄💭📖📅🔍` 等符号为前缀，可轻松识别和跳过。

---

## 📦 安装 · Install

```bash
# Hermes Agent
cp -r agent-genesis-mentor ~/.hermes/skills/

# Claude Code / OpenClaw / Codex
cp -r agent-genesis-mentor <workspace>/skills/
```

```bash
# 或从 BotLearn 一键安装
botlearn skillhunt agent-genesis-mentor
```

[![BotLearn](https://img.shields.io/badge/BotLearn-Install-brightgreen)](https://www.botlearn.ai/skillhunt/v2/s/agent-genesis-mentor)

---

## 📁 文件结构 · Structure

```
agent-genesis-mentor/
├── SKILL.md                          # 核心指令（激活时 ~1,800 token）
├── README.md
├── LICENSE
├── .gitignore                        # 忽略运行时生成的 .agent-genesis/
└── references/                       # 按需加载的子模块
    ├── module-0-skill-awareness.md   # 技能扫描协议
    ├── module-1-inception-guide.md   # 苏格拉底式提问
    ├── module-2-concept-explainer.md # 4 行卡片模板
    ├── module-3-best-practice.md     # 事件→提醒映射表
    ├── module-4-decision-log.md      # 静默决策记录格式
    ├── module-5-learning-retro.md    # 3 问回顾模板
    ├── module-6-phase-transition.md  # 方法失效/复活/假设变迁
    ├── module-7-mistake-chronicle.md # 犯错启示与修正轨迹
    ├── module-8-project-timeline.md  # 自动时间线收纳
    └── module-9-risks.md             # 10 项风险详细分析
```

---

## ⚙️ 配置 · Config

首次激活时自动创建 `.agent-genesis/mentor.json`：

```json
{
  "mode": "peer",
  "learningJournal": ".agent-genesis/learning-journal.jsonl",
  "decisionLog": ".agent-genesis/decisions.jsonl",
  "mistakeLog": ".agent-genesis/mistakes.jsonl",
  "phaseLog": ".agent-genesis/phases.jsonl",
  "timeline": ".agent-genesis/timeline.jsonl",
  "skillMap": ".agent-genesis/skill-map.json"
}
```

---

## ⚠️ 注意 · Notes

- 📝 日志文件为明文本地存储，建议 `.gitignore`
- 🔤 学徒模式单次任务额外消耗 ~1,500-3,000 token
- 🤖 概念讲解源自 LLM 知识，可能存在过时或不准确的建议
- ⚠️ 此技能是辅助而非替代——真正的工程判断力仍在你手中

详见 [references/module-9-risks.md](references/module-9-risks.md)

---

## 📜 License

MIT © [fangweixuan26-hash](https://github.com/fangweixuan26-hash)
