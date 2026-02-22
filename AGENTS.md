# AGENTS.md

## Project Overview

GitKraken CLI (`gk`) is a command-line tool for managing multiple repositories, work items, AI-powered commits, pull request generation, and an MCP server for git and issue/PR hosting provider integration. It is available on macOS, Windows, and Linux.

## Repository Structure

- `README.md` — Main documentation covering installation, workflows, and configuration
- `CONTRIBUTING.md` — Contribution guidelines and issue reporting
- `LICENSE` — Copyright and license information (docs under CC BY 3.0 US)
- `.github/ISSUE_TEMPLATE/` — GitHub issue templates for bug reports and feature requests
- `images/` — Static images used in documentation

## Key Conventions

- This is a documentation and issue-tracking repository for the GitKraken CLI; it does not contain application source code.
- Issues should follow the templates in `.github/ISSUE_TEMPLATE/` — use `[BUG]` prefix for bugs and `[FEAT]` prefix for feature requests.
- Documentation is licensed under the Creative Commons Attribution 3.0 United States License.

## Writing Guidelines

- Keep documentation clear and concise.
- Use fenced code blocks with `bash` language tags for CLI examples.
- Maintain the existing structure and table of contents in `README.md` when adding new sections.
- When referencing CLI commands, use the `gk` prefix (e.g., `gk work create`, `gk auth login`).
