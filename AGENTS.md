# AGENTS.md

This file provides guidance for AI coding agents working in this repository.

## Project Overview

This is the public-facing repository for **GitKraken CLI** (`gk`), a command-line tool for managing Git workflows across multiple repositories. The repo primarily contains documentation, images, and GitHub issue templates — not the CLI source code itself.

## Repository Structure

- `README.md` — Main documentation covering installation, usage, workflows, configuration, and troubleshooting.
- `CONTRIBUTING.md` — Contribution guidelines for bug reports and feature requests.
- `LICENSE` — Project license.
- `images/` — Screenshots and banner images referenced in the README.
- `.github/ISSUE_TEMPLATE/` — GitHub issue templates.
- `.github/images/` — Additional GitHub-related images.

## Guidelines for Changes

### Documentation

- Keep the README's table of contents in sync when adding or removing sections.
- Preserve the existing heading hierarchy (`##` for top-level sections, `###` for subsections).
- Use fenced code blocks with the `bash` language tag for CLI examples.
- When referencing `gk` commands, use inline code formatting (backticks).
- Images are stored in `images/` and referenced with relative paths (`./images/filename.png`).

### Markdown Style

- Use ATX-style headings (`#`, `##`, `###`).
- Use `---` for horizontal rules between installation platform sections.
- Leave a blank line before and after headings, code blocks, and lists.
- Do not add trailing whitespace to lines.

### Contributing and Issues

- The `CONTRIBUTING.md` file has a TODO placeholder for contribution rules — any additions should follow the existing bullet-point format.
- Issue templates live in `.github/ISSUE_TEMPLATE/`.

### Links

- The CLI releases are hosted at `https://github.com/gitkraken/gk-cli/releases`.
- Documentation links should point to the GitKraken Help Center at `https://help.gitkraken.com/`.
- When adding external links, prefer named references over bare URLs in prose.
