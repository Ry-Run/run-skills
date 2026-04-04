---
name: github-skill
description: 使用 GitHub MCP 处理 GitHub 上的远端仓库状态：文件、分支、提交、Issue、PR、Review、Release 与代码搜索。适合任务核心在 GitHub 托管数据上，而不是本地工作区或 IDE 会话时使用。
---

# GitHub Skill

## 快速上手

目标：当你关心的是 GitHub 上的真实状态，而不是本地 checkout 时，直接操作远端事实。

参考资料：`skills/github-skill/references/github-skill_zh.md`

## 常用只读流程

- 仓库内容：`get_file_contents`、`list_branches`、`list_commits`
- PR：`pull_request_read`、`list_pull_requests`、`search_pull_requests`
- Issue：`issue_read`、`list_issues`、`search_issues`
- 发现与检索：`search_code`、`search_repositories`、`search_users`
- Release / Tag：`get_latest_release`、`list_releases`、`list_tags`

## 常用写入流程

- Issue / PR 讨论：`issue_write`、`add_issue_comment`、`reply_to_pull_request_comment`
- Review 流程：先建 pending review，再加 review comment，最后 submit
- 远端文件修改：`create_or_update_file`、`push_files`、`delete_file`
- 分支与 PR：`create_branch`、`create_pull_request`、`update_pull_request`

## 推荐工作流

1. 先读远端状态，再决定是否写入。
2. 目标不精确时，优先用 search 系列接口。
3. 代码审查意见要用 review comment，不要混用普通 issue comment。
4. 更新已存在文件前，先拿当前 SHA。

## 高风险动作

以下操作前必须获得明确确认：
- 合并 PR
- 删除文件、版本或仓库内容
- 向重要分支直接推送远端文件修改
- 在用户意图不明确时替用户创建分支或 PR

## 参考资料

- 摘录说明：`skills/github-skill/references/github-skill_zh.md`
