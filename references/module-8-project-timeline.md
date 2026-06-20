# 模块八：项目时间线 · 详细指令

全自动。所有模块写入日志时自动追加时间线条目。

## 触发

任何模块（四/五/六/七）写入日志时，追加一条时间线条目到 `.agent-genesis/timeline.jsonl`。

## 条目标格式

```json
{"timestamp":"2026-06-21T10:00:00Z","source":"decision","summary":"选定 knex+raw 而非 Prisma","detailRef":"decisions.jsonl:第3条","milestone":null}
```

`source` 取值：`decision` | `phase-transition` | `mistake` | `retrospective` | `skill-recommendation`
`milestone`：用户说"好了/完成了/上线了"时标记为非 null。

## 用户查询

| 用户说 | 行为 |
|-------|------|
| "看看项目时间线" | 按时间倒序列最近 20 条 |
| "有哪些里程碑" | 筛选 `milestone != null` |
| "犯过哪些错" | 筛选 `source == "mistake"` |
| "有哪些决策需复议" | 筛选 `source == "decision"` + 交叉比模块六推翻的假设 |

## 阶段摘要

两个里程碑之间发生了什么：

```
📅 「项目脚手架」→「文件上传 v1 上线」

   3 个决策 · 1 次假设推翻 · 学到流式处理+worker_threads
```

- 不做数据分析/图表——这是专业工具的活
- 不做 AI 总结——让未来的 Agent/用户自己浏览
- 时间线是"可导航的记忆"
