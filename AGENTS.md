# AGENTS.md

Guidance for coding agents working in this repository.

## Repository scope

- This repository currently contains project documentation and assets for GitKraken CLI.
- Primary files are `README.md`, `CONTRIBUTING.md`, and images under `images/`.
- There is no build, test, or lint pipeline defined in this repo at this time.

## Primary goals

1. Keep documentation accurate and consistent with GitKraken CLI behavior.
2. Preserve existing tone: concise, practical, and user-focused.
3. Minimize churn: prefer targeted edits over broad rewrites.

## Editing rules

- Use Markdown that is easy to read in raw form.
- Keep command examples copy/paste ready.
- Prefer relative links for local files and images.
- Do not invent commands, flags, URLs, or product capabilities.
- Keep platform-specific instructions clearly separated (macOS, Linux/Unix, Windows).
- Preserve existing headings where possible to avoid breaking deep links.

## Content expectations

- When adding or updating commands, match the `gk` CLI naming used in `README.md`.
- If behavior is uncertain, leave a clear TODO or note rather than guessing.
- Favor short sections and bullet lists over dense paragraphs.
- Ensure new screenshots or images are stored in `images/` and referenced with relative paths.

## Safety checks before finishing

- Verify Markdown links and image paths are valid.
- Check for obvious typos and formatting issues.
- Confirm any changed instructions still align with the rest of the docs.
- Keep unrelated files untouched.

## Non-goals

- Do not add speculative roadmap details.
- Do not add dependency or tool setup steps that are not required by this repository.
