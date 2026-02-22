# AGENTS.md

## Project Overview

This repository is the public-facing documentation and issue-tracking hub for **GitKraken CLI** (`gk`). The CLI binary itself is closed-source; this repo contains documentation, installation instructions, GitHub issue templates, and related assets.

## Repository Structure

```
.
├── README.md              # Primary documentation: features, installation, workflows, troubleshooting
├── CONTRIBUTING.md        # Guidelines for community contributions and feedback
├── LICENSE                # CC BY 3.0 US (documentation license)
├── images/                # Screenshot and banner assets referenced by docs
└── .github/
    ├── ISSUE_TEMPLATE/    # Bug report and feature request templates
    └── images/            # GitHub-specific image assets
```

## Guidelines for AI Agents

### Editing Documentation

- All user-facing documentation lives in `README.md`. Keep it as the single source of truth for CLI usage, installation, and troubleshooting.
- `CONTRIBUTING.md` covers community interaction guidelines. Keep it concise and welcoming.
- Preserve the existing table of contents in `README.md` and update it when adding or removing sections.
- When adding new sections to `README.md`, place them in a logical order and add a corresponding entry to the Table of Contents.

### Markdown Conventions

- Use ATX-style headers (`## Heading`) with a blank line before and after.
- Use fenced code blocks with a language identifier (e.g., ` ```bash `) for all command examples.
- Reference images using relative paths from the repo root (e.g., `./images/filename.png`).
- Prefer bullet lists (`-`) over numbered lists unless order matters.
- Keep lines at a reasonable length for readability but do not hard-wrap prose at a fixed column.

### Images and Assets

- Store all image assets in the `images/` directory at the repo root.
- Use PNG format for screenshots.
- Reference images with relative Markdown syntax: `![alt text](./images/filename.png)`.

### Issue Templates

- Bug report template is in `.github/ISSUE_TEMPLATE/bug_report.yml` (YAML-based GitHub form).
- Feature request template is in `.github/ISSUE_TEMPLATE/feature_request.md` (Markdown-based).
- Template chooser configuration is in `.github/ISSUE_TEMPLATE/config.yml`.

### Commit Messages

- Use conventional-style prefixes: `docs:`, `fix:`, `chore:`, etc.
- Keep the subject line under 72 characters.
- Reference related GitHub issues when applicable (e.g., `docs: update install instructions (#123)`).

### Things to Avoid

- Do not add or modify any application source code — this repo contains only documentation.
- Do not add dependencies or build tooling unless explicitly requested.
- Do not remove or rename existing image files without updating all Markdown references.
- Do not change the LICENSE file without explicit instruction.
