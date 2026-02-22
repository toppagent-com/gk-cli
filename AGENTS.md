# AGENTS.md

This file provides guidance for AI coding agents working in this repository.

## Project Overview

This is the public repository for **GitKraken CLI** (`gk`), a command-line tool for interacting with Git repositories, issues, workspaces, and hosting providers. The CLI also ships an MCP server for AI integrations. The binary itself is closed-source; this repo serves as the documentation hub, issue tracker, and release distribution point.

## Repository Structure

- `README.md` — Primary documentation: installation, workflows, configuration, and troubleshooting.
- `CONTRIBUTING.md` — Guidelines for community contributions (bug reports and feature requests).
- `LICENSE` — Project license (documentation licensed under CC BY 3.0 US).
- `.github/ISSUE_TEMPLATE/` — Templates for bug reports (`bug_report.yml`) and feature requests (`feature_request.md`).
- `images/` — Image assets referenced by the README.

## Key Conventions

- There is no application source code in this repository. Changes are limited to documentation, issue templates, and related configuration.
- Markdown files should follow standard GitHub-flavored Markdown conventions.
- Shell examples in documentation use `bash` code fences.
- The CLI command is `gk`. All documentation examples should reference `gk` (not `gitkraken-cli`).

## Writing and Editing Documentation

- Keep language concise and user-focused.
- Preserve the existing table of contents in `README.md` when adding new sections, and add a corresponding link entry.
- Use fenced code blocks with the `bash` language tag for CLI examples.
- When documenting commands, show realistic usage examples rather than abstract syntax alone.
- Image assets belong in the `images/` directory and should be referenced with relative paths (`./images/...`).

## Issue Templates

- Bug reports use a structured YAML form (`.github/ISSUE_TEMPLATE/bug_report.yml`) with fields for description, CLI version, OS version, Git version, and supporting materials.
- Feature requests use a Markdown template (`.github/ISSUE_TEMPLATE/feature_request.md`) with sections for problem description, proposed solution, alternatives, and additional context.
- When modifying templates, preserve required field validations and placeholder text formatting.

## Common Tasks

| Task | How |
|---|---|
| Update installation instructions | Edit the relevant platform section in `README.md` under **Installation** |
| Add a new documentation section | Add the section to `README.md` and insert a link in the **Table of Contents** |
| Modify issue templates | Edit files under `.github/ISSUE_TEMPLATE/` |
| Add images | Place files in `images/` and reference with relative Markdown paths |
