# AGENTS.md

## Project Overview

This is the public repository for **GitKraken CLI** (`gk`), a command-line tool for interacting with GitKraken. The repository hosts documentation, issue templates, and supporting assets. It does not contain application source code.

## Repository Structure

- `README.md` — Primary documentation: installation, workflows, configuration, and troubleshooting
- `CONTRIBUTING.md` — Contribution guidelines for external contributors
- `LICENSE` — Creative Commons Attribution 3.0 US (documentation license)
- `images/` — Image assets referenced by the README
- `.github/ISSUE_TEMPLATE/` — GitHub Issue templates for bug reports (`[BUG]` prefix) and feature requests (`[FEAT]` prefix)

## Guidelines for AI Agents

### Editing Documentation

- Keep language clear, concise, and consistent with the existing tone.
- Preserve the existing section structure and table of contents in `README.md`. If you add or remove a section, update the table of contents accordingly.
- Use fenced code blocks with the `bash` language tag for CLI commands and terminal output.
- Reference the `gk` command consistently (lowercase, backtick-wrapped in inline contexts).
- Do not add unnecessary badges, emojis beyond what already exists, or promotional language.

### Issue Templates

- Bug report template (`.github/ISSUE_TEMPLATE/bug_report.yml`) uses YAML-based forms. Feature request template (`.github/ISSUE_TEMPLATE/feature_request.md`) uses Markdown.
- Bug reports require a description and CLI version. Feature requests require a problem description, proposed solution, and alternatives considered.
- Blank issues are disabled (`config.yml`). All issues must use a template.
- Preserve the `[BUG]` and `[FEAT]` title prefixes in templates.

### Links and References

- GitKraken CLI documentation: https://help.gitkraken.com/cli/gk-cli-mcp/
- Releases: https://github.com/gitkraken/gk-cli/releases
- Legacy docs: https://gitkraken.github.io/gk-cli/docs/gk.html

### Commit Conventions

- Use clear, descriptive commit messages.
- Prefix with a type when appropriate (e.g., `docs:`, `fix:`, `chore:`).

### Things to Avoid

- Do not add application source code to this repository.
- Do not modify the LICENSE file without explicit instruction.
- Do not add dependencies or package manager files — this is a documentation-only repository.
