# GitHub MCP：摘录说明

这个参考文档用于确认 GitHub MCP 的主要工具分组。

## 只读操作

- 仓库 / 文件：`get_file_contents`、`list_branches`、`get_commit`、`list_commits`
- Issue：`issue_read`、`list_issues`、`search_issues`
- PR：`pull_request_read`、`list_pull_requests`、`search_pull_requests`
- Release / Tag：`get_latest_release`、`get_release_by_tag`、`list_releases`、`list_tags`
- 搜索 / 发现：`search_code`、`search_repositories`、`search_users`

## 写入操作

- Issue：`issue_write`、`add_issue_comment`
- PR 评论 / Review：`add_reply_to_pull_request_comment`、`pull_request_review_write`、`add_comment_to_pending_review`
- 分支 / 文件：`create_branch`、`create_or_update_file`、`push_files`、`delete_file`
- PR 生命周期：`create_pull_request`、`update_pull_request`、`merge_pull_request`

## 关键规则

- 按作者筛 PR 时，用 `search_pull_requests`，不要用 `list_pull_requests`。
- 更新已有文件时，必须带当前 blob SHA。
- 代码审查意见应使用 review 相关接口，而不是普通 issue comment。
