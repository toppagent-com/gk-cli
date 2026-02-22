# AGENTS.md

This repository is primarily **documentation and assets** for GitKraken CLI (Markdown + images). There is no application build, test suite, or CI workflow defined in this repo today—most work is editing `README.md`, issue templates, and image references.

## What to change (and where)

- **Primary documentation**: `README.md`
- **Contribution guidelines**: `CONTRIBUTING.md`
- **Issue templates**: `.github/ISSUE_TEMPLATE/`
- **Images used in README**: `images/`
- **Images used in GitHub UI/docs**: `.github/images/`

## Editing guidelines

- **Keep Markdown GitHub-friendly**
  - Prefer standard GitHub-flavored Markdown (GFM).
  - Use fenced code blocks with a language tag when possible (e.g. ```bash).
  - Keep headings stable so existing anchors keep working.
  - If you change headings that appear in the README Table of Contents, update the ToC accordingly.

- **Images**
  - Prefer **relative paths** like `./images/...` so rendering works on GitHub.
  - Add meaningful alt text when practical (avoid empty `![](...)` unless it’s purely decorative).
  - Don’t rename or move existing images unless you also update every reference.
  - If adding new images, keep file sizes reasonable (compress large PNGs/GIFs when possible).

- **Links**
  - Prefer stable URLs (official docs/help center/blog) and avoid ephemeral links.
  - When changing links, verify the new target is correct and publicly accessible.

## Local validation (quick checks)

There’s no required tooling, but before committing you should:

- **Render check**: confirm `README.md` renders on GitHub (headings, code blocks, images).
- **Reference check**: ensure all `![](...)` image paths exist in the repo.
- **Basic lint (optional)**: if you have `markdownlint` installed, run it and fix obvious issues.

## Making changes safely

- Prefer **small, focused commits** (one logical change per commit).
- Avoid large reflows/rewraps of Markdown unless necessary; keep diffs readable.
- Don’t introduce new build tooling/config files unless explicitly requested.

## Git expectations

- Use clear commit messages (docs-only changes are fine), e.g.:
  - `docs: clarify MCP server description`
  - `docs: update install steps for Ubuntu`
  - `docs: fix broken image link`
- If your change is substantial or policy-affecting, align it with `CONTRIBUTING.md` (open an issue first when appropriate).

