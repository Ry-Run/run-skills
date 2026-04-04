---
name: shrimp-task-manager
description: 使用 Shrimp Task Manager MCP 做结构化任务分析、拆解、执行指导、追踪与验收校验。适合需要依赖关系和完成检查的任务系统管理，而不是只把推理链条显式展开。
---

# Shrimp Task Manager Skill

## 快速上手

目标：把大任务变成可分析、可拆解、可跟踪、可验收的任务系统。

参考资料：`skills/shrimp-task-manager/references/shrimp-task-manager_zh.md`

## 最适合的场景

- 有依赖关系的多步骤实现。
- 研究成分较重的工程任务。
- 需要明确验收标准和进度追踪。
- 想在宣称完成前，先做评分式验证。

## 推荐工作流

1. 先分析任务：`analyze_task` 或 `plan_task`
2. 再拆解：`split_tasks`
3. 一次处理一个任务：`list_tasks`、`get_task_detail`、`execute_task`
4. 现实变化时更新任务：`update_task`
5. 完成后验证：`verify_task`

## 重要行为说明

- `execute_task` 只给执行指导，不会替你完成任务。
- `verify_task` 必须基于真实结果，对照记录的标准评分。
- 技术调研跨多轮时，用 `research_mode` 保持上下文。

## 约束与红线

- 不能臆造需求，先收集证据再规划。
- 任务粒度要适中，依赖关系要写清楚。
- 没有充分理由时，不要删除未完成任务。

## 参考资料

- 摘录说明：`skills/shrimp-task-manager/references/shrimp-task-manager_zh.md`
