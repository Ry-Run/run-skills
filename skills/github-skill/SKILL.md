---
name: github-skill
description: "Use GitHub MCP for remote repository state: files, branches, commits, issues, pull requests, reviews, releases, and code search on GitHub. Use it when the task is centered on GitHub-hosted data, rather than a local checkout or IDE session."
---

# GitHub Skill

## Quick start

Goal: operate on GitHub-hosted state directly when repository facts, PR state, issues, releases, or remote file changes matter.

Reference notes: `skills/github-skill/references/github-skill.md`

## Common read workflows

- Repository contents: `get_file_contents`, `list_branches`, `list_commits`
- PRs: `pull_request_read`, `list_pull_requests`, `search_pull_requests`
- Issues: `issue_read`, `list_issues`, `search_issues`
- Discovery: `search_code`, `search_repositories`, `search_users`
- Releases/tags: `get_latest_release`, `list_releases`, `list_tags`

## Common write workflows

- Issues and PR comments: `issue_write`, `add_issue_comment`, `reply_to_pull_request_comment`
- PR review flow: create pending review → add review comments → submit review
- Remote file changes: `create_or_update_file`, `push_files`, `delete_file`
- Branching and PRs: `create_branch`, `create_pull_request`, `update_pull_request`

## Workflow tips

1. Prefer read APIs first to confirm remote state.
2. Use search APIs when the target repo, PR, or symbol is not exact.
3. Use review-specific tools for review comments; use issue comments only for discussion.
4. For existing file updates, fetch the current SHA first.

## High-risk actions

Require explicit user confirmation before:
- merging PRs
- deleting files, versions, or repos
- pushing remote file changes on important branches
- creating branches/PRs on the user’s behalf if intent is ambiguous

## References

- Condensed notes: `skills/github-skill/references/github-skill.md`
