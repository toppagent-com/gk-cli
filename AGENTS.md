# AGENTS.md

This file provides guidance to AI coding agents working in this repository.

## Project Overview

This is the community and documentation repository for **GitKraken CLI** (`gk`). It does not contain application source code — the CLI binary is distributed separately. The repo houses:

- `README.md` — primary documentation covering installation, workflows, configuration, and troubleshooting.
- `CONTRIBUTING.md` — contribution guidelines for bug reports and feature requests.
- `LICENSE` — license terms (documentation licensed under CC BY 3.0 US).
- `.github/ISSUE_TEMPLATE/` — GitHub issue templates for bugs and feature requests.
- `images/` — screenshots and assets referenced by the documentation.

## Working with This Repository

### Content and Formatting

- All documentation is written in Markdown. Follow existing formatting conventions (heading levels, code block languages, link styles).
- Use fenced code blocks with the `bash` language tag for CLI commands and examples.
- Keep the Table of Contents in `README.md` in sync when adding or removing sections.
- Reference images using relative paths (`./images/filename.png`).

### Issue Templates

- Bug report template is in YAML format (`.github/ISSUE_TEMPLATE/bug_report.yml`).
- Feature request template is in Markdown format (`.github/ISSUE_TEMPLATE/feature_request.md`).
- Template chooser config is at `.github/ISSUE_TEMPLATE/config.yml`.

### Commit Conventions

- Use descriptive commit messages. Prefix with a type when appropriate (e.g., `docs:`, `fix:`, `chore:`).
- Keep commits focused on a single logical change.

### What NOT to Do

- Do not add application source code; this is a documentation-only repo.
- Do not fabricate CLI command output or feature details — refer to the official GitKraken CLI help (`gk help`) or the [Help Center](https://help.gitkraken.com/cli/gk-cli-mcp/) for accurate information.
- Do not remove or modify the LICENSE file without explicit instruction.
