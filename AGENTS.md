# AGENTS.md — Developer & AI Agent Guide

## Project Overview

This repository contains two related web products owned by **NorwegianSpark SA** (`Org no. 834 984 172`):

1. **AI Super-Portal** (`index.html` + `tools.json`) — A Norwegian-language static affiliate site listing AI tools with copyable prompts, category filters, and search. Deployed to Netlify.
2. **Banktopp** (`banktopp.htlm.txt`) — A full-featured React 19 + TypeScript + Tailwind single-file component for a Norwegian bank comparison site. Designed to be deployed via [v0.dev](https://v0.dev) → Vercel.

**Language**: Norwegian (Bokmål) for all user-facing copy. Code comments and variable names may be in English.

---

## File Structure

```
├── index.html          # AI Super-Portal — main page (vanilla HTML/CSS/JS)
├── tools.json          # AI tool data — single source of truth for all cards
├── banktopp.htlm.txt   # Banktopp React/TS component (drag into v0.dev to deploy)
├── images/             # Static image assets
├── README.md           # End-user documentation
├── CONTRIBUTING.md     # Contribution guidelines
└── AGENTS.md           # This file
```

---

## AI Super-Portal (`index.html` + `tools.json`)

### Tech Stack
- Vanilla HTML5, CSS3, JavaScript (ES2020+)
- No build step required
- Fonts: `Outfit` (body), `JetBrains Mono` (code) via Google Fonts

### Design Tokens
| Token | Value |
|---|---|
| `--primary` | `#00d2ff` (cyan) |
| `--secondary` | `#3a7bd5` (blue) |
| `--accent` | `#a855f7` (purple) |
| `--dark` | `#0a0e17` (background) |
| `--card-bg` | `#131a2b` |

### Data Schema (`tools.json`)
Each tool object in the `tools` array:
```json
{
  "name": "string — display name",
  "category": "tekst | bilde | video | lyd | kode | web | seo | analyse | automasjon",
  "desc": "string — short Norwegian description",
  "prompt": "string — example prompt to copy (Norwegian or English)",
  "link": "string — affiliate URL (use '#' as placeholder)",
  "commission": "string — commission info, e.g. '30% Fast'"
}
```

**To add a new tool**: append an object to `tools.json`. The page re-renders dynamically — no code change needed.

### Running Locally
```bash
# Python 3
python -m http.server 8080

# Node.js
npx serve .
```
Open `http://localhost:8080`.

### Deployment
Deployed to **Netlify** (static hosting). Pushing to `main` triggers an automatic deploy. No build command is needed — the publish directory is `/` (root).

If a page returns 404 on Netlify, check:
- The Netlify `_redirects` file or `netlify.toml` for SPA routing rules (not present by default — add if needed)
- That the requested URL path matches an actual file

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

---

## Code Conventions

- **No build step** for the AI Super-Portal — keep it zero-dependency
- **Norwegian user-facing copy** — all text shown to users must be in Norwegian Bokmål
- **Affiliate disclosures** — every page must include the disclaimer: *"Reklame · Denne siden inneholder affiliate-lenker"* as required by Norwegian marketing law (`markedsføringsloven`)
- **Sponsored items first** — `is_sponsored: true` items must appear before non-sponsored items in all lists
- **WCAG AA** — maintain accessible colour contrast ratios and ARIA attributes, especially for Banktopp
- Do not add SVG noise or decorative animations that break `prefers-reduced-motion`

---

## Testing

### AI Super-Portal
Manual browser testing is the primary method (no test framework):

```bash
python -m http.server 8080
# Open http://localhost:8080
```

Verify:
- Cards render from `tools.json`
- Category filter buttons work
- Search filters cards in real time
- "Kopier prompt" button copies text and shows "Kopiert!" feedback
- Fallback tools render if `tools.json` fails to load
- Responsive layout at 375px, 768px, 1280px

### Banktopp
Since this is a single `.tsx` file intended for v0.dev, local testing requires a Vite + React project:

```bash
npm create vite@latest banktopp-test -- --template react-ts
cd banktopp-test
npm install framer-motion sonner zod lucide-react
# Paste banktopp component content into src/App.tsx
npm run dev
```

---

## Cursor Cloud Specific Instructions

- The local dev server for the AI Super-Portal is `python -m http.server 8080`; it starts instantly with no dependencies to install
- When testing UI changes to `index.html`, use the `computerUse` subagent to open `http://localhost:8080` in Chrome
- Do **not** run `npm install` at the workspace root — there is no `package.json`; the AI Super-Portal is dependency-free
- When editing `tools.json`, validate that the JSON is well-formed before committing (`python -c "import json; json.load(open('tools.json'))"`)
- To verify Netlify deployment: check the branch was pushed to `main` and wait ~60 seconds for the deploy to propagate

---

## Contact

NorwegianSpark SA · [norwegianspark@gmail.com](mailto:norwegianspark@gmail.com) · +47 99 73 74 67
