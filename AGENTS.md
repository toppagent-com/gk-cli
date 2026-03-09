# AGENTS.md — Developer & AI Agent Guide

## Project Overview

This repository contains two related web products owned by **NorwegianSpark SA** (`Org no. 834 984 172`):

1. **AI Super-Portal** (`index.html` + `tools.json`) — A static single-page site listing AI tools with searchable/filterable cards, copy-to-clipboard prompts, and affiliate links. Content is in Norwegian. Deployed to Netlify.
2. **Banktopp** (`banktopp.htlm.txt`) — A full-featured React 19 + TypeScript + Tailwind single-file component for a Norwegian bank comparison site. Intended for deployment via [v0.dev](https://v0.dev) → Vercel.

**Language**: Norwegian (Bokmål) for all user-facing copy. Code comments and variable names may be in English.

---

## Architecture

- **No build system** — pure vanilla HTML, CSS, and JavaScript.
- `index.html` is the entire application (markup, styles, and scripts are all inline).
- `tools.json` is the data source; the page fetches it at runtime via `fetch('tools.json')`.
- Fallback data is hardcoded in `index.html` in case `tools.json` fails to load.

### File Structure

```
index.html          # Full application (HTML + CSS + JS)
tools.json          # AI tools data (array of tool objects)
banktopp.htlm.txt   # Banktopp React/TS component (drag into v0.dev to deploy)
images/             # Static image assets
README.md           # Project documentation (Norwegian)
CONTRIBUTING.md     # Contribution guidelines
LICENSE             # License
.github/            # Issue templates
AGENTS.md           # This file
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

---

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
- If a page returns 404 on Netlify, verify the requested URL path matches an actual file in the repo.

---

## Banktopp (`banktopp.htlm.txt`)

### Tech Stack
- React 19 + TypeScript
- Vite (local dev), React Router v7
- Tailwind CSS (utility classes inlined via CSS-in-JS string)
- `framer-motion` (animations), `sonner` (toasts), `zod` (validation), `lucide-react` (icons)

### Design Tokens
| Token | Value |
|---|---|
| `--accent-primary` | `#F5C842` (Gold) |
| `--accent-secondary` | `#2DD4BF` (Jade) |
| `--bg` | `#04040A` |
| Font display | `Playfair Display` |
| Font body | `DM Sans` |
| Font mono | `JetBrains Mono` |

### Bank Data Interface (`Bank`)
Key fields: `id`, `slug`, `name`, `type` (`neobank | traditional | savings | business | student | crypto`), `rating`, `is_sponsored`, `affiliate_url`, `apy`, `monthly_fee`, `pros[]`, `cons[]`, `ratings{}` (app/fees/returns/access/support/security).

### Deployment
1. Copy the full contents of `banktopp.htlm.txt`
2. Paste into [v0.dev](https://v0.dev) as a new component
3. Deploy to Vercel directly from v0.dev

### Pages Implemented
`Home`, `Banks`, `Category`, `Detail`, `Compare`, `Quiz`, `About`, `Advertise`, `Privacy`, `Terms`, `404`

### Local Testing
Since this is a single `.tsx` file intended for v0.dev, local testing requires a Vite + React project:

```bash
npm create vite@latest banktopp-test -- --template react-ts
cd banktopp-test
npm install framer-motion sonner zod lucide-react
# Paste banktopp component content into src/App.tsx
npm run dev
```

---

## Code Guidelines

- **Language**: UI text and content are in Norwegian. Use Norwegian for all user-facing strings.
- **Single-file architecture**: All styles and scripts live inside `index.html`. Keep them there unless the project is migrated to a build system.
- **Data changes**: To add, remove, or modify AI tools, edit `tools.json` only. Do not modify the `FALLBACK_TOOLS` array in `index.html` unless also updating `tools.json`.
- **Categories**: Valid values are `tekst`, `bilde`, `video`, `lyd`, `kode`, `web`, `seo`, `analyse`, `automasjon`. Adding a new category requires adding a corresponding `.badge.<category>` CSS rule and a filter button in the HTML.
- **Affiliate disclosures**: Every page must include the disclaimer banner (*"Reklame · Denne siden inneholder affiliate-lenker"*) as required by Norwegian marketing law (`markedsføringsloven`). Replace `"link": "#"` with actual affiliate URLs before going live.
- **Sponsored items first**: `is_sponsored: true` items must appear before non-sponsored items in all lists.
- **No build step**: Do not introduce bundlers, transpilers, or package managers without explicit approval.
- **Accessibility**: Use semantic HTML elements, maintain keyboard navigability, ensure sufficient color contrast (WCAG AA), and respect `prefers-reduced-motion`.

---

## Testing

### AI Super-Portal
Manual browser testing is the primary method (no test framework). Verify:

1. The page loads without a 404 or blank screen.
2. Tool cards render from `tools.json`.
3. Category filter buttons work (click a category; verify cards filter).
4. Search input filters cards by name/description/prompt.
5. "Kopier prompt" buttons copy text and show "Kopiert!" feedback.
6. Fallback tools render if `tools.json` fails to load.
7. Responsive layout works at 375 px, 768 px, and 1280 px.

### Automated Testing
There are no automated tests. If adding tests, prefer a lightweight approach (a simple Node.js script or an HTML-based test page) since the project has no build tooling or package manager.

---

## Cursor Cloud Specific Instructions

### Running the Dev Server

```bash
cd /workspace && python3 -m http.server 8080 &
```

### Manual Testing

After starting the dev server, use the `computerUse` subagent to open `http://localhost:8080` in Chrome and verify the checklist above.

### Additional Notes

- Do **not** run `npm install` at the workspace root — there is no `package.json`; the AI Super-Portal is dependency-free.
- When editing `tools.json`, validate the JSON before committing: `python3 -c "import json; json.load(open('tools.json'))"`.
- To verify Netlify deployment: push to `main` and wait ~60 seconds for the deploy to propagate.

---

## Contact

NorwegianSpark SA · [norwegianspark@gmail.com](mailto:norwegianspark@gmail.com) · +47 99 73 74 67
