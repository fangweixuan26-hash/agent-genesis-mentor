# 模块零：技能感知 · 详细指令

## 扫描协议

首次激活时执行一次。之后每次对话开始做增量刷新（检测新增/删除技能）。用户说"刷新技能列表"也可手动触发。

1. 扫描 `<workspace>/skills/` 和 `~/.hermes/skills/` 下的所有 `SKILL.md`
2. 仅读 YAML frontmatter（文件头 `---` 之间的部分）
3. 提取字段：`name`、`displayName`、`description`（取前 120 字）、`categories`、`scenarios`
4. 最多扫描 100 个 skill，控制在 2 秒内
5. 不计入 agent-genesis-mentor 自身

## 映射表结构

生成 `.agent-genesis/skill-map.json`：

```json
{
  "scannedAt": "ISO时间",
  "totalSkills": 42,
  "byCategory": {
    "coding": ["simplify-code", "test-driven-development"],
    "automation": ["agent-genesis-recovery"],
    "design": ["python-technical-diagrams"]
  },
  "byScenario": {
    "coding-dev": ["agent-genesis-recovery", "agent-genesis-decomposer"],
    "error-diagnosis": ["agent-genesis-recovery", "systematic-debugging"],
    "long-conversation": ["agent-genesis-compressor"],
    "complex-task": ["agent-genesis-decomposer"],
    "write-docs": ["minimax-docx", "chinese-academic-writing"]
  }
}
```

## 告知用户

扫描完成后输出（学徒/同伴模式；专家静默）：

```
🔍 感知到 {N} 个可用技能
   编码：recovery / decomposer / simplify-code ...
   文档：minimax-docx / chinese-academic-writing ...
   （每类最多 4 个，共不超过 6 类）

💡 我会在合适时机推荐。说"切换专家模式"可关闭。
```

## 执行中的推荐

各模块在适合时机查询映射表：

| 情境 | 查询 | 推荐格式 |
|------|------|---------|
| 任务涉及编码 | byScenario["coding-dev"] | "💡 你装了 decomposer，要不要先拆分任务？" |
| 方法失效需排查 | byScenario["error-diagnosis"] | "💡 systematic-debugging 有结构化调试流程" |
| 需要架构图 | byCategory["design"] | "💡 python-technical-diagrams 可生成架构图" |

**推荐规则：** `💡` + ≤60字 + 同技能同对话最多3次。用户说"不需要"后该技能永不再推。
