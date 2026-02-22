# AGENTS.md

This repository primarily contains **documentation** for GitKraken CLI (not the CLI source code). Use these guidelines when making changes as an automated agent.

## Repository layout

- `README.md`: Main landing page and usage/installation content.
- `CONTRIBUTING.md`: Contribution expectations (issues first for significant changes).
- `images/`: Screenshots referenced by Markdown.
- `.github/ISSUE_TEMPLATE/`: Issue forms/templates.

## What to change (and what not to)

- **Do**: Improve clarity, fix typos, update broken links, keep commands consistent, and update screenshots when the UI/output changes.
- **Don’t**: Invent new commands/features or change product claims without a clear source in this repo (or an explicitly provided reference).

## Markdown conventions

- **Keep headings stable**: The `README.md` Table of Contents uses section anchors; preserve heading text/levels or update the ToC accordingly.
- **Prefer fenced code blocks** with a language tag (for example `bash`) for multi-line snippets.
- **Use backticks for commands** (`gk auth login`) and filenames (`images/cli-header-wide.png`).
- **Prefer relative links** for files within this repo (for example `./images/...`).

## Images and other binary files

- Put new screenshots in `images/` and reference them relatively from Markdown.
- Keep files reasonably sized; avoid committing unnecessary large binaries.
- Use descriptive, lowercase, hyphenated filenames (for example `new-feature-output.png`).

## Suggested local checks (optional)

This repo may not have a formal test/lint setup. When possible:

- **Preview Markdown rendering** (GitHub preview is usually sufficient).
- **Sanity-check links** you touched (open them or use a link checker if available).
- If you want a quick lint pass and `node` is available:

```bash
npx -y markdownlint-cli2 "**/*.md"
```

## Pull request hygiene

- Keep changes scoped to the requested docs update.
- Avoid drive-by rewrites; prefer small, reviewable edits.
- Do not add secrets, tokens, customer data, or internal URLs to issues/templates/docs.
