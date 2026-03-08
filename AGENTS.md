## Cursor Cloud specific instructions

This is a **documentation-only repository** for the GitKraken CLI (`gk`). It contains no source code, no build system, no application to run, and no automated tests. The actual CLI is closed-source and distributed as pre-built binaries.

### Repository contents

- `README.md` — main product documentation
- `CONTRIBUTING.md` — contribution guidelines (issues/feedback only)
- `LICENSE` — Creative Commons Attribution 3.0 US
- `.github/ISSUE_TEMPLATE/` — GitHub issue templates (bug reports, feature requests)
- `images/` — documentation images/GIFs

### Lint

Markdown files can be linted with `markdownlint-cli2`:

```bash
markdownlint-cli2 "**/*.md"
```

Note: the existing docs have ~30 pre-existing lint warnings (mostly line-length and missing alt-text). These are not regressions.

### Preview

To preview rendered markdown locally, use `grip` (Python-based GitHub-style renderer):

```bash
grip 0.0.0.0:6419
```

Then open `http://localhost:6419/` in a browser.

### Key caveats

- There is no `package.json`, `Makefile`, `Dockerfile`, or any build/test infrastructure.
- Contributions to this repo are limited to documentation edits and GitHub issue management.
- Do not attempt to install or build a CLI binary from this repo — the source code is not here.
