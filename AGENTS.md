# AGENTS.md

## Project Overview

AI affiliate portal ("AI Super-Portal 2026") — a static single-page site listing AI tools with searchable/filterable cards, copy-to-clipboard prompts, and affiliate links. All user-facing content is in Norwegian (`lang="no"`).

## Architecture

- **No build system** — pure vanilla HTML, CSS, and JavaScript. No package manager, no bundler, no transpiler.
- `index.html` is the entire application (markup, styles, and scripts are all inline).
- `tools.json` is the data source; the page fetches it at runtime via `fetch('tools.json')`.
- Fallback data (`FALLBACK_TOOLS`) is hardcoded in `index.html` in case `tools.json` fails to load.

### File Structure

```
index.html        # Full application (HTML + CSS + JS)
tools.json        # AI tools data (array of tool objects)
README.md         # Project documentation (Norwegian)
CONTRIBUTING.md   # Contribution guidelines (legacy content from GitKraken CLI fork)
LICENSE           # License (legacy content from GitKraken CLI fork)
AGENTS.md         # This file
.github/          # Issue templates (legacy content from GitKraken CLI fork)
```

> **Note**: `CONTRIBUTING.md`, `LICENSE`, and `.github/` contain placeholder/legacy content from the original GitKraken CLI repo this was forked from. They do not reflect this project's actual contribution guidelines or license.

### Tool Object Schema (`tools.json`)

Each entry in the `tools` array:

```json
{
  "name": "string",
  "category": "tekst | bilde | video | lyd | kode | web | seo | analyse | automasjon",
  "desc": "string (short Norwegian description)",
  "prompt": "string (example prompt for the tool)",
  "link": "string (affiliate URL, or '#' as placeholder)",
  "commission": "string (e.g. '30% Fast', 'Varierer')"
}
```

### Design System

Fonts: **Outfit** (body), **JetBrains Mono** (code/prompts). Loaded from Google Fonts.

CSS custom properties defined in `:root`:

| Token            | Value     | Usage                    |
|------------------|-----------|--------------------------|
| `--primary`      | `#00d2ff` | Links, accents, CTA bg   |
| `--secondary`    | `#3a7bd5` | Gradients                |
| `--accent`       | `#a855f7` | Purple highlights        |
| `--dark`         | `#0a0e17` | Page background          |
| `--card-bg`      | `#131a2b` | Card backgrounds         |
| `--card-border`  | `#1e293b` | Card/input borders       |
| `--text`         | `#f1f5f9` | Primary text             |
| `--text-muted`   | `#94a3b8` | Secondary/muted text     |

Category badge colors are defined per-category via `.badge.<category>` CSS rules.

### JavaScript Architecture

- `loadTools()` — fetches `tools.json`, falls back to `FALLBACK_TOOLS` on error, then calls `renderTools()`.
- `renderTools()` — filters `aiTools` array by `currentFilter` (category) and `searchQuery` (text match on name, desc, prompt, category), then builds card DOM elements with `innerHTML`.
- `copyPrompt(id, btn)` — copies prompt text via `navigator.clipboard.writeText()`, shows "Kopiert!" feedback for 2 seconds.
- `escapeHtml(text)` — sanitizes tool data before inserting into the DOM.
- Filter buttons and search input have event listeners that update state and re-render.

### Known Considerations

- **Newsletter section**: The email signup form at the bottom is not connected to any backend. It is purely presentational.
- **Affiliate links**: All tool links currently point to `#` (placeholder). Replace with real affiliate URLs in `tools.json`.
- **XSS**: Tool `name`, `link`, and `commission` are inserted via `innerHTML` without escaping. Only `prompt` is escaped via `escapeHtml()`. Keep `tools.json` trusted.

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

Wait ~1 second for the server to start, then test with:

```bash
curl -s -o /dev/null -w "%{http_code}" http://localhost:8080/
```

Expected: `200`.

### Manual Testing

After starting the dev server, use the `computerUse` subagent to open `http://localhost:8080` in Chrome and verify:

1. Page loads with the "AI Super-Portal 2026" heading and disclaimer banner visible.
2. All 20 tool cards render (from `tools.json`).
3. Category filter buttons work — clicking a category shows only matching cards, clicking "Alle" shows all.
4. Search input filters cards in real time by name, description, prompt, or category.
5. "Kopier prompt" buttons change to "Kopiert!" with a green background on click.
6. Cards have hover effects (lift + blue border glow).
7. The layout is responsive — cards reflow into fewer columns at narrower widths.

### Automated Testing

There are no automated tests. The project has no test framework or package manager. If adding tests, use a standalone HTML page or a simple Node.js script that fetches from the local server.

## Code Guidelines

- **Language**: UI text and content are in Norwegian. Use Norwegian for user-facing strings.
- **Single-file architecture**: All styles and scripts live inside `index.html`. Keep them there unless the project is migrated to a build system.
- **Data changes**: To add, remove, or modify AI tools, edit `tools.json` only. Do not modify the `FALLBACK_TOOLS` array in `index.html` unless also updating `tools.json`.
- **Categories**: Valid values are `tekst`, `bilde`, `video`, `lyd`, `kode`, `web`, `seo`, `analyse`, `automasjon`. Adding a new category requires adding a corresponding `.badge.<category>` CSS rule and a `<button class="filter-btn" data-filter="<category>">` in the HTML.
- **Affiliate links**: Replace `"link": "#"` with actual affiliate URLs. The disclaimer banner at the top of the page is legally required under Norwegian advertising law — do not remove it.
- **No build step**: Do not introduce bundlers, transpilers, or package managers without explicit approval.
- **Accessibility**: Use semantic HTML elements, maintain keyboard navigability, and ensure sufficient color contrast.
- **Security**: Escape any user-controlled or dynamic content before inserting via `innerHTML`. Currently only `prompt` is escaped; if tool data comes from an untrusted source, escape all fields.
