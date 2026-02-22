# AGENTS.md – GitKraken CLI

Project-specific guidance for AI coding assistants working on this repository.

## Project Overview

This is the **GitKraken CLI** (`gk`) repository—a command-line tool for managing Work Items, AI-powered commits, PR generation, and Git operations. It includes an MCP server that integrates with Git, GitHub, and Jira. Supported on macOS, Windows, and Unix.

## Dos and Don'ts

**Do:**
- Keep documentation clear, concise, and aligned with the existing README tone
- Check existing issues before suggesting bug fixes or features (per CONTRIBUTING.md)
- Preserve existing workflows (auth → work create → commit → push → pr create)
- Use `gk` command examples when relevant; avoid generic `git` unless illustrating passthrough
- Follow Markdown best practices for `.md` files

**Don't:**
- Modify installation instructions without verifying current package managers (Homebrew, Snap, Winget, etc.)
- Change MCP server behavior or API references without confirming against Help Center docs
- Add platform-specific troubleshooting without referencing known issues (e.g., Safari/Brave localhost, Oh-My-Zsh alias)
- Introduce breaking changes to documented workflows

## Key Files

| File              | Purpose                                   |
|-------------------|-------------------------------------------|
| `README.md`       | Main documentation, installation, workflows |
| `CONTRIBUTING.md` | Contribution guidelines and issue process  |
| `.github/ISSUE_TEMPLATE/` | Bug reports and feature requests     |

## Commands

- **Validate Markdown**: Use a linter/formatter if available; otherwise ensure valid Markdown syntax
- **Check links**: Verify URLs in documentation (releases, Help Center, Nerd Fonts) are current

## Permissions

**No approval needed:**
- Reading and editing `.md` files, docs, and issue templates
- Proposing copy changes or structural improvements
- Suggesting new sections or examples

**Require confirmation:**
- Adding or changing external dependencies or scripts
- Modifying installation commands or binary paths
- Changing MCP or API integration details

## Documentation

- [GitKraken CLI Docs](https://gitkraken.github.io/gk-cli/docs/gk.html)
- [Help Center – MCP](https://help.gitkraken.com/cli/gk-cli-mcp/)
- [Releases](https://github.com/gitkraken/gk-cli/releases)
