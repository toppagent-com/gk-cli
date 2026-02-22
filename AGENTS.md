# AGENTS.md

Guidance for automated coding agents working in this repository.

## Repository scope

This checkout is documentation-focused for GitKraken CLI (`gk`).
At the time of writing, it primarily contains:

- `README.md` (primary product and usage documentation)
- `CONTRIBUTING.md` (contribution guidance)
- `.github/ISSUE_TEMPLATE/*` (issue templates and issue config)
- `LICENSE`

Assume documentation and template quality are the core concerns unless a task explicitly says otherwise.

## Editing rules

1. Keep documentation changes factual and verifiable.
   - Do not invent CLI flags, commands, URLs, or product behavior.
2. Preserve existing writing style and section structure in edited files.
3. Keep Markdown readable:
   - Use short paragraphs.
   - Prefer fenced code blocks with a language tag (for example, `bash`).
4. For GitHub issue templates:
   - Keep YAML valid (spaces only, no tabs).
   - Preserve required fields unless the task explicitly asks to change them.
   - Keep labels/titles such as `[BUG]` and `[FEAT]` aligned with current conventions.

## Validation checklist

Before finalizing changes:

1. Re-read edited files for clarity and accuracy.
2. Check Markdown/YAML formatting for obvious syntax issues.
3. Verify that changed links are well-formed and point to expected destinations.
4. Review the diff to ensure no unrelated edits were introduced.

## Commit guidance

- Prefer small, focused commits.
- Use descriptive commit messages (for example: `docs: clarify work item workflow`).
- Include a short summary of user-visible impact in PR/commit context where possible.
