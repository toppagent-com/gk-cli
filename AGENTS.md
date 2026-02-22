## AGENTS.md

Guidance for AI agents (and humans) making changes in this repository.

## What this repo is

This repository is primarily **documentation and GitHub issue templates** for GitKraken CLI (`gk`). It does not contain the CLI source code in this workspace snapshot.

## Repository layout

- `README.md`: Main landing page and usage/workflow examples.
- `CONTRIBUTING.md`: Contribution guidance (currently minimal).
- `.github/ISSUE_TEMPLATE/`: Issue and feature request templates.
- `images/`: Images referenced by the README.

## How to make changes safely

- **Prefer small, focused edits**: keep diffs easy to review.
- **Preserve existing style**:
  - Keep headings, emojis, and tone consistent with `README.md`.
  - Use fenced code blocks with the correct language (typically `bash`).
- **Don’t break docs**:
  - If you change a heading that is linked in the Table of Contents, update the ToC anchor links.
  - Keep image paths relative (e.g. `./images/...`) and ensure files exist in `images/`.
  - Avoid adding large/binary assets unless necessary; prefer reusing/optimizing existing images.
- **Command examples must be accurate**:
  - Use commands that exist (`gk ...`, `git ...`) and match the documented workflow.
  - Don’t invent flags or output—if you can’t verify, phrase it as guidance (e.g. “run `gk <cmd> --help`”).
- **Issue templates**:
  - YAML indentation is significant; keep `.yml` formatting valid.
  - Keep required fields aligned with what maintainers likely need (version, OS, repro steps, logs).

## “Done” checklist for doc-only changes

- **Markdown renders cleanly** (lists/code blocks/links look right).
- **Links and paths are correct** (especially images under `images/`).
- **Spelling/grammar pass** for user-facing text.
- **No unrelated reformatting** (avoid noisy whitespace-only changes).

## Git hygiene (for agents)

- Keep commits **descriptive and scoped** (e.g. “Add AGENTS.md with repo-specific guidelines”).
- Don’t modify generated/binary files unless required by the change.
