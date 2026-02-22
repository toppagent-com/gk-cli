# Agent Guidelines for GitKraken CLI

This document provides guidance for AI agents when working on the GitKraken CLI (`gk`) codebase.

## Project Overview

GitKraken CLI is a premium command-line interface for managing multiple repositories. Core concepts include:

- **Work Items** — The central unit of work; think of them as the feature or issue you're tackling. Enables multi-repo workflows with a monorepo-like UX.
- **MCP Server** — Provides tools for LLMs to work with git, GitHub, Jira, and GitKraken APIs.
- **AI Features** — AI-powered commit messages and Pull Request generation.

## Key Commands

```bash
gk auth login          # Authenticate
gk work create "..."   # Create a work item
gk work commit --ai    # Commit with AI-generated message
gk work push           # Push changes
gk work pr create --ai # Create PR with AI
gk work add ./path     # Add repo to current work item
```

The CLI also supports `git` command passthrough (e.g., `gk status`, `gk remote -v`).

## Development Guidelines

### Before Making Changes

1. Check existing issues to avoid duplicate work.
2. Open an issue for significant changes or bug fixes.
3. Follow the patterns established in the codebase.

### When Contributing

- Keep changes focused and well-scoped.
- Write clear, descriptive commit messages.
- Ensure any new code follows existing style and conventions.

### Confidentiality & Privacy

When working with user data (repos, commits, issues), treat it as sensitive. Do not expose credentials, tokens, or private repository information in logs, error messages, or documentation.

## Documentation

- `gk help` — Primary exploration tool for the CLI
- [GitKraken CLI Docs](https://gitkraken.github.io/gk-cli/docs/gk.html)
- [MCP Server Help](https://help.gitkraken.com/cli/gk-cli-mcp/)

## Support

See [CONTRIBUTING.md](./CONTRIBUTING.md) for contribution guidelines and feedback channels.
