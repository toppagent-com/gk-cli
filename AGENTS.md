# AGENTS.md

This file provides guidance for AI agents working with the GitKraken CLI repository.

## Project Overview

This repository hosts documentation and issue tracking for **GitKraken CLI** (`gk`), a command-line interface for GitKraken. The CLI focuses on "Work Items" for multi-repo workflows, AI-powered commit messages and PR generation, and an MCP server for git/GitHub/Jira integration.

The CLI binary itself is closed-source; this repo contains documentation, issue templates, and supporting assets.

## Repository Structure

- `README.md` — Primary documentation: installation, usage, workflows, troubleshooting
- `CONTRIBUTING.md` — Contribution guidelines for bug reports and feature requests
- `LICENSE` — License information (documentation under CC BY 3.0 US)
- `.github/ISSUE_TEMPLATE/` — GitHub issue templates for bugs and feature requests
- `images/` — Screenshots and images used in documentation

## Key Conventions

- Documentation is written in Markdown.
- Bug reports use the structured YAML-based issue template (`.github/ISSUE_TEMPLATE/bug_report.yml`).
- Feature requests use the Markdown-based issue template (`.github/ISSUE_TEMPLATE/feature_request.md`).
- Bug report titles should be prefixed with `[BUG]` and feature requests with `[FEAT]`.
- Check existing issues before creating new ones to avoid duplicates.

## Working with This Repository

- There is no build system, test suite, or linter — the repo is purely documentation.
- Changes should focus on clarity, accuracy, and consistency with existing Markdown formatting.
- When editing `README.md`, preserve the existing table of contents and section structure.
- Code examples in documentation use `bash` fenced code blocks.
- Image assets live in the `images/` directory and are referenced with relative paths (`./images/...`).

## CLI Reference

The CLI binary is `gk`. Key commands for documentation purposes:

- `gk auth login` — Authenticate with GitKraken
- `gk work create` — Create a work item
- `gk work commit --ai` — AI-powered commit
- `gk work push` — Push changes
- `gk work pr create --ai` — AI-powered PR creation
- `gk help` — Display help
- `gk setup` — System configuration info

The CLI also supports git command passthrough (e.g., `gk status`, `gk remote -v`).
