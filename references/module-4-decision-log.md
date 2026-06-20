# 模块四：决策日志 · 详细指令

## 触发条件

以下任一时触发（静默，不打断）：
- 选技术栈/库/框架
- 选架构模式
- 选数据结构/算法（有明确替代方案时）
- 违背常规做法（"这里不用 ORM，因为……"）

## 记录格式

追加一行 JSON 到 `.agent-genesis/decisions.jsonl`：

```json
{"context":"选ORM还是裸SQL","options":["Prisma","TypeORM","knex+raw"],"decision":"knex+raw","rationale":"需要复杂联表查询，ORM生成SQL不可控","timestamp":"2026-06-21T10:00:00Z"}
```

## 规则

- 静默记录，不主动展示
- 用户问"做了哪些决策"时才展示最近条目
- 不做价值判断——不写"选X是更好选择"
- 与模块六联动：某条决策的假设被推翻时，标记为"需复议"
