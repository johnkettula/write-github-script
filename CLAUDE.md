# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

This is a GitHub Learning Lab course template for **"GitHub Actions: Using GitHub Script"**. It is a starter/template repository that students fork to learn how to use the [`github-script`](https://github.com/actions/github-script) action to interact with the GitHub API directly inside GitHub Actions workflow files.

There is no application source code, build system, or test suite. The repository's contents are intentionally minimal — it exists to be extended with GitHub Actions workflows as part of the course.

## Repository Structure

- `README.md` — Course introduction directing students to the open issue to get started.
- `LICENSE` — MIT license.
- `.github/ISSUE_RESPONSES/comment.md` — A templated comment response, posted automatically via a workflow when issues are opened with the `bug` label.

## Key Conventions

### `.github/ISSUE_RESPONSES/`
This directory holds Markdown templates used as automated issue/PR comment bodies. When adding new response templates, follow the pattern of `comment.md`: plain Markdown, no frontmatter.

### Adding GitHub Actions Workflows
Course workflows go in `.github/workflows/`. They should use the `actions/github-script` action to interact with the GitHub API (e.g., posting comments, labeling issues, closing PRs) using the `github` and `context` objects provided by the action.

Example workflow pattern:
```yaml
- uses: actions/github-script@v7
  with:
    script: |
      github.rest.issues.createComment({
        issue_number: context.issue.number,
        owner: context.repo.owner,
        repo: context.repo.repo,
        body: 'Hello from github-script!'
      })
```

## Development Branch

Active development happens on `claude/add-claude-documentation-Qac6S`. Push changes there and open a PR against `master`.
