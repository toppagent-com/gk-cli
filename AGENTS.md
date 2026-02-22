# AGENTS.md

Guidance for AI agents working in this repository.

## Repository purpose

This repo primarily contains **documentation and issue templates** for GitKraken CLI (`gk`).

## Key paths

- `README.md`: Main product documentation/landing page (installation, workflows, troubleshooting).
- `images/`: Screenshots referenced by `README.md`.
- `.github/ISSUE_TEMPLATE/`: GitHub issue templates.

## Conventions for changes

- **Match the existing Markdown style** in `README.md` (headings, tone, code fences, spacing).
- **Keep the Table of Contents in sync** if you add/remove/rename top-level sections.
- **Prefer relative links** for in-repo content (e.g., `./images/...`).
- **Be careful with heading anchors**: changing a heading can break TOC links and external deep links.
- **CLI commands**:
  - Use fenced code blocks with `bash` for multi-line command examples.
  - Use backticks for inline commands/flags (e.g., `gk work create`).
- **Images**:
  - Add new images under `images/`.
  - Use descriptive, kebab-case filenames (e.g., `work-create-example.png`).
  - Avoid committing unnecessarily large binaries; optimize screenshots when possible.
  - Ensure every referenced image path exists.

## What to avoid

- Don’t introduce new build systems, dependencies, or generated files unless the change explicitly requires it.
- Don’t add long-lived processes (watch servers, dev servers) to verification steps.

## Verification checklist (docs-only)

Before committing:

- Ensure Markdown renders cleanly (headings/code blocks/lists).
- Confirm all links you changed still point to the intended destination.
- Confirm all `README.md` image references exist under `images/`.
- Scan for obvious typos and broken formatting.

## Git hygiene

- Keep commits small and descriptive (docs changes are usually one commit).
- Don’t reformat unrelated sections.
