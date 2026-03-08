# AI Affiliate Portal

En komplett AI affiliate-side med verktøyoversikt, prompts og kopier-knapper. Bygget for SEO og konvertering.

## ✨ Funksjoner

- **Widget-basert** – Legg til nye verktøy ved å legge én linje i `tools.json`
- **Søk** – Søk på verktøynavn, beskrivelse eller prompt
- **Filter** – Filtrer på kategori (Tekst, Bilde, Video, Lyd, Kode, Web, SEO, etc.)
- **Kopier prompt** – Brukere kan kopiere prompts med ett klikk
- **Provisjonsinfo** – Viser affiliate-provisjon per verktøy
- **Mobilvennlig** – Responsivt design
- **SEO-klar** – Meta-tagger og semantisk HTML

## 🚀 Kom i gang

### Lokal utvikling

```bash
# Med Python 3
python -m http.server 8080

# Eller med Node.js (npx)
npx serve .
```

Åpne http://localhost:8080 i nettleseren.

### Legg til affiliate-lenker

1. Registrer deg på [PartnerStack](https://partnerstack.com) eller tilsvarende
2. Søk om godkjenning for hvert verktøy (Jasper, Copy.ai, Leonardo.ai, etc.)
3. Erstatt `"link": "#"` med dine affiliate-URL-er i `tools.json`

### Legg til nye verktøy

Åpne `tools.json` og legg til et nytt objekt:

```json
{
  "name": "Synthesia",
  "category": "video",
  "desc": "AI video avatar generator",
  "prompt": "Create a video presenter explaining AI",
  "link": "https://din-affiliate-lenke.com",
  "commission": "20-25% Fast"
}
```

Kategorier: `tekst`, `bilde`, `video`, `lyd`, `kode`, `web`, `seo`, `analyse`, `automasjon`

## 📁 Filstruktur

```
├── index.html      # Hovedside
├── tools.json     # Verktøydata (enkel å utvide)
└── README.md
```

## 📋 Juridisk

I henhold til norsk markedsføringslov må du:
- Merke siden tydelig med "Reklame" eller "Inneholder affiliate-lenker"
- Ikke skjule at du tjener penger på lenker

Disclaimeren er allerede inkludert øverst på siden.

## 🔗 SEO-struktur (anbefalt)

For mer trafikk, lag undersider som:
- `/best-ai-writing-tools`
- `/best-ai-image-generators`
- `/best-ai-video-tools`
- `/ai-prompts`

## Lisens

MIT
