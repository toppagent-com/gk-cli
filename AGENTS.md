# AGENTS.md

Guidance for AI coding assistants working with the GitKraken CLI repository.

## Project Overview

**GitKraken CLI** (`gk`) is a command-line interface for GitKraken. It provides:

- **Work Items** — Feature or issue tracking that supports multiple repositories (monorepo-style UX)
- **AI-powered workflows** — Commit messages and Pull Request generation
- **MCP Server** — Integrates with LLMs and wraps git, GitHub, and Jira MCP actions
- **Git passthrough** — Use `gk` as a drop-in for standard `git` commands

## Key Concepts

- **Work Item** — The unit of work (feature or issue) you are tackling; can span multiple repos
- **Workflow** — Auth → Create Work Item → Edit → Commit (AI) → Push → PR (AI)
- **Documentation** — Primary source: `gk help` and [Help Center](https://help.gitkraken.com/cli/gk-cli-mcp/)

## Repository Structure

```
.
├── README.md           # Main project documentation
├── CONTRIBUTING.md     # Contribution guidelines
├── LICENSE
└── .github/
    └── ISSUE_TEMPLATE/ # Bug reports, feature requests
```

## Guidelines for AI Agents

### When Making Changes

1. **Check existing issues** — Verify the change hasn't already been proposed (see CONTRIBUTING.md)
2. **Follow existing style** — Match documentation tone and formatting in README/CONTRIBUTING
3. **Preserve workflows** — Keep documented workflows (auth → work create → commit → push → pr) intact
4. **Cross-platform awareness** — The CLI supports macOS, Windows, and Unix; note platform-specific instructions

### Documentation Updates

- Update `gk help` usage examples if command structure changes
- Link to [official documentation](https://gitkraken.github.io/gk-cli/docs/gk.html) where relevant
- Include installation instructions for all supported platforms (Homebrew, Snap, Winget, manual)

### Testing Considerations

- Safari and Brave may freeze during `gk auth login`; document workarounds
- Oh-My-Zsh users may need `unalias gk` due to `gitk` alias conflict
- Nerd Fonts required for proper icon rendering in terminal output

### Git Operations

- Develop on the designated feature branch
- Prefer small, focused commits with clear messages
- Commit and push incrementally during development

## External Resources

- [Help Center - MCP Installation](https://help.gitkraken.com/cli/gk-cli-mcp/)
- [GitKraken MCP Blog Post](https://www.gitkraken.com/blog/introducing-gitkraken-mcp)
- [Releases](https://github.com/gitkraken/gk-cli/releases)
- [API Documentation](https://gitkraken.github.io/gk-cli/docs/gk.html)
