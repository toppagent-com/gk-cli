# AGENTS.md

## Project Overview

AI affiliate portal ("AI Super-Portal 2026") — a static single-page site listing AI tools with searchable/filterable cards, copy-to-clipboard prompts, and affiliate links. Content is in Norwegian. The repo also contains a bank comparison TSX project (`banktopp.htlm.txt` in uploads) intended for v0.dev / Vercel deployment.

## Architecture

- **No build system** — pure vanilla HTML, CSS, and JavaScript.
- `index.html` is the entire application (markup, styles, and scripts are all inline).
- `tools.json` is the data source; the page fetches it at runtime via `fetch('tools.json')`.
- Fallback data is hardcoded in `index.html` in case `tools.json` fails to load.

### File Structure

```
index.html        # Full application (HTML + CSS + JS)
tools.json        # AI tools data (array of tool objects)
README.md         # Project documentation (Norwegian)
CONTRIBUTING.md   # Contribution guidelines
LICENSE           # License
.github/          # Issue templates
```

### Tool Object Schema (`tools.json`)

Each tool entry follows this shape:

```json
{
  "name": "string",
  "category": "tekst | bilde | video | lyd | kode | web | seo | analyse | automasjon",
  "desc": "string",
  "prompt": "string",
  "link": "string (URL or '#' placeholder)",
  "commission": "string"
}
```

## Development Environment

### Running Locally

No dependencies to install. Serve the directory with any static file server:

```bash
# Python 3
python3 -m http.server 8080

# Node.js (npx)
npx serve . -l 8080
```

Then open `http://localhost:8080`.

**Important**: Opening `index.html` directly via `file://` will cause `fetch('tools.json')` to fail due to CORS restrictions. Always use a local HTTP server.

### Deployment

The site is deployed on **Netlify** as a static site. No build command or output directory configuration is needed — Netlify serves the repo root directly.

- Ensure `index.html` exists at the repo root.
- No `netlify.toml` or `_redirects` file is currently present. If SPA-style routing or custom redirects are needed, create one.

## Cursor Cloud Specific Instructions

### Running the Dev Server

```bash
cd /workspace && python3 -m http.server 8080 &
```

### Manual Testing

After starting the dev server, use the `computerUse` subagent to open `http://localhost:8080` in Chrome and verify:

1. The page loads without a 404 or blank screen.
2. Tool cards render from `tools.json`.
3. Category filter buttons work (click a category, verify cards filter).
4. Search input filters cards by name/description/prompt.
5. "Kopier prompt" buttons copy text and show "Kopiert!" feedback.

### Automated Testing

There are no automated tests. If adding tests, consider a lightweight approach such as a simple Node.js script or HTML-based test page, since the project has no build tooling or package manager.

## Code Guidelines

- **Language**: UI text and content are in Norwegian. Use Norwegian for user-facing strings.
- **Single-file architecture**: All styles and scripts live inside `index.html`. Keep them there unless the project is migrated to a build system.
- **Data changes**: To add, remove, or modify AI tools, edit `tools.json` only. Do not modify the `FALLBACK_TOOLS` array in `index.html` unless also updating `tools.json`.
- **Categories**: Valid values are `tekst`, `bilde`, `video`, `lyd`, `kode`, `web`, `seo`, `analyse`, `automasjon`. Adding a new category requires adding a corresponding `.badge.<category>` CSS rule and a filter button in the HTML.
- **Affiliate links**: Replace `"link": "#"` with actual affiliate URLs. The disclaimer banner at the top of the page is legally required under Norwegian advertising law.
- **No build step**: Do not introduce bundlers, transpilers, or package managers without explicit approval.
- **Accessibility**: Use semantic HTML elements, maintain keyboard navigability, and ensure sufficient color contrast.
