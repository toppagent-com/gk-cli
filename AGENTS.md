# AGENTS.md

Guidance for AI coding agents working on the GitKraken CLI (`gk`) project.

## Project Overview

GitKraken CLI is a command-line tool for managing multiple Git repositories with a consistent UX. Key features include:

- **Work Items** — Track features/issues across multiple repos
- **AI-powered commits & PRs** — `gk work commit --ai` and `gk work pr create --ai`
- **MCP Server** — Integrates with AI apps (Cursor, Copilot, etc.)
- **Git passthrough** — Use `gk` as a drop-in for `git` commands

## Setup

- Authenticate: `gk auth login`
- Add a repo to a work item: `gk work add .`
- Create a work item: `gk work create "Description"`

## Development Workflow

```bash
gk work create "My work item"
# Edit files...
gk work commit --ai
gk work push
gk work pr create --ai
```

## Code Style & Conventions

- Check existing issues before opening new ones (see CONTRIBUTING.md)
- Use `gk help` and `gk [command] --help` for CLI command reference
- Prefer clear, descriptive commit messages; use `--ai` for AI-generated messages

## PR Guidelines

- Verify the bug or feature hasn't already been submitted
- Open an issue for significant changes before proposing a PR
- Use meaningful PR titles and descriptions

## Documentation

- README.md — User-facing docs, installation, workflows
- Help Center: https://help.gitkraken.com/cli/gk-cli-mcp/
- CLI docs: https://gitkraken.github.io/gk-cli/

## Known Considerations

- **Auth**: `gk auth login` may freeze in Safari/Brave — use Chrome or copy the URL to another browser
- **Oh-My-Zsh**: Run `unalias gk` if the shell aliases conflict with the CLI
- **Nerd Fonts**: Recommended for correct icon rendering in the terminal
