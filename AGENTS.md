# AGENTS.md

Instructions for AI coding agents working on the GitKraken CLI (`gk`) project.

## Project Overview

GitKraken CLI is a premium CLI for managing multiple repositories with familiar git commands. Key features include:
- **Work Items** – Group repos/features for focused development
- **AI-powered commits and PRs** – `gk work commit --ai`, `gk work pr create --ai`
- **MCP Server** – Integrates with LLMs and wraps git, GitHub, and Jira

## Rules

### Do
- Check existing issues before proposing changes or fixes
- Follow patterns established in the codebase
- Keep documentation in sync with code changes
- Use conventional commit-style messages when applicable
- Reference the [Help Center](https://help.gitkraken.com/cli/gk-cli-mcp/) for MCP-related changes

### Don't
- Add dependencies without explicit approval
- Make security-sensitive changes without review
- Modify authentication flows or token handling without caution
- Assume macOS-only behavior; support macOS, Windows, and Unix

## Technical Notes

- **Installation targets**: macOS (Homebrew), Unix/Ubuntu (Snap, .deb, .rpm), Windows (Winget)
- **Nerd Fonts**: CLI uses Nerd Fonts for icons; consider terminal compatibility
- **Oh-My-Zsh**: `gk` conflicts with Oh-My-Zsh's `gitk` alias

## Useful Commands

```bash
# Validate setup
gk setup

# View help
gk help

# Run tests (when available)
go test ./...
```

## Permissions

| Action                         | Permission      |
|--------------------------------|-----------------|
| Read files, run lint/format    | No approval     |
| Edit docs, fix typos           | No approval     |
| Add/remove packages, CI config | Requires review |
| Auth or token logic changes    | Requires review |

## Resources

- [Documentation](https://gitkraken.github.io/gk-cli/docs/gk.html)
- [Releases](https://github.com/gitkraken/gk-cli/releases)
- [MCP Introduction](https://www.gitkraken.com/blog/introducing-gitkraken-mcp)
