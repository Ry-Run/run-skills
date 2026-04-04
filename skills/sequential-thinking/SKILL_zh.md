---
name: sequential-thinking
description: 使用 Sequential Thinking MCP 处理需要显式分步、可修正、可分支的复杂推理问题。适合结构化分析、规划和决策过程，而不是管理一个持久任务系统。
---

# Sequential Thinking Skill

## 快速上手

目标：当问题复杂、含糊、可能中途改假设时，把思考过程显式化，而不是在脑内黑箱完成。

主入口：
- `mcp__sequential_thinking__sequentialthinking`

参考资料：`skills/sequential-thinking/references/sequential-thinking_zh.md`

## 适用场景

- 有多个假设分支的复杂调试。
- 需要比较权衡的规划或设计。
- 中途可能推翻前面判断的问题。
- 多阶段分析，结论一开始并不清楚。

## 不适用场景

- 简单事实查询。
- 范围清晰的直接改代码任务。
- 明显直接执行更快的场景。

## 推荐工作流

1. 先估一个 `totalThoughts`。
2. 按顺序递增 `thoughtNumber`。
3. 发现方向变了，就显式标注 revision 或 branch。
4. 只有在结论真正稳定后才结束。

## 约束与红线

- 思考要服务决策，不要为了“显得认真”而冗长。
- 证据变化时，要敢于修正前面的判断。
- 它不能替代查代码、查文档、跑工具。

## 参考资料

- 摘录说明：`skills/sequential-thinking/references/sequential-thinking_zh.md`
