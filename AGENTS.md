# Agent Instructions for GitKraken CLI

This document provides guidance for AI agents when working with the GitKraken CLI repository.

## Project Overview

**GitKraken CLI** (`gk`) is GitKraken on the command line. It provides:

- **Work Items** — Manage features/issues across multiple repos with a unified UX
- **AI-powered workflows** — Commit messages and Pull Request generation
- **MCP Server** — Integrates with git, GitHub, Jira, and GitKraken APIs
- **Git passthrough** — Use `gk` as a drop-in for standard `git` commands

## Repository Structure

This repository contains primarily documentation and project metadata:

| Path | Purpose |
|------|---------|
| `README.md` | Main documentation, installation, workflows, troubleshooting |
| `CONTRIBUTING.md` | Contribution guidelines |
| `.github/ISSUE_TEMPLATE/` | Bug reports and feature request templates |

## Key Conventions

- **Issue prefixes**: Feature requests use `[FEAT]` in the title
- **Documentation**: Official docs live at https://gitkraken.github.io/gk-cli/docs/gk.html
- **Help**: Users should run `gk help` for CLI exploration

## Common Workflows (for users)

```bash
gk auth login
gk work create "My new work item"
gk work commit --ai
gk work push
gk work pr create --ai
```

## Guidelines for AI Agents

1. **Documentation changes**: Update README.md, CONTRIBUTING.md, or docs as appropriate. Keep the existing structure and tone.

2. **Issue templates**: When suggesting or creating issues, use the templates in `.github/ISSUE_TEMPLATE/` — `feature_request.md` for features, `bug_report.yml` for bugs.

3. **Cross-references**: Link to the official documentation (https://gitkraken.github.io/gk-cli/docs/gk.html) when relevant.

4. **Consistency**: Match existing formatting — Markdown with clear headings, code blocks with `bash` for shell commands, tables for structured content.

5. **Scope**: This repo focuses on documentation; CLI source code may live elsewhere (e.g., releases at https://github.com/gitkraken/gk-cli/releases).
