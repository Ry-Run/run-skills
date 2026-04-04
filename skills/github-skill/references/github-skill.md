# GitHub MCP: notes (condensed)

Use this reference to confirm major tool families.

## Read operations

- Repository/files: `get_file_contents`, `list_branches`, `get_commit`, `list_commits`
- Issues: `issue_read`, `list_issues`, `search_issues`
- Pull requests: `pull_request_read`, `list_pull_requests`, `search_pull_requests`
- Releases/tags: `get_latest_release`, `get_release_by_tag`, `list_releases`, `list_tags`
- Search/discovery: `search_code`, `search_repositories`, `search_users`

## Write operations

- Issues: `issue_write`, `add_issue_comment`
- PR comments/reviews: `add_reply_to_pull_request_comment`, `pull_request_review_write`, `add_comment_to_pending_review`
- Branches/files: `create_branch`, `create_or_update_file`, `push_files`, `delete_file`
- PR lifecycle: `create_pull_request`, `update_pull_request`, `merge_pull_request`

## Important rules

- For PR author filtering, use `search_pull_requests` instead of `list_pull_requests`.
- For existing file updates, supply the current blob SHA.
- Review comments belong in review APIs, not issue comments.
