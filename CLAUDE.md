# Foil Engineering - Marketing Site

## Tech Stack
- **Framework**: Astro (static site generator)
- **Styling**: Vanilla CSS (no framework)
- **Deployment**: Vercel (auto-deploys on push to `master`)
- **Domain**: https://www.foil.engineering

## Architecture
- Single-page site (`src/pages/index.astro`) with section anchors
- Sections: Hero, Services (accordion cards), Projects, About, Contact
- Services use collapsible accordion pattern with CSS grid-template-rows animation
- JS for accordions lives in `<script>` block at bottom of `index.astro`
- Layout: `src/layouts/BaseLayout.astro`

## Key Files
- `src/pages/index.astro` - Main page with all sections
- `src/components/Header.astro` - Navigation header
- `src/layouts/BaseLayout.astro` - Base HTML layout
- `src/styles/global.css` - Global styles
- `public/images/` - Static assets (headshot, project screenshots)
- `vercel.json` - Vercel deployment config

## Deployment
- **Vercel project**: `foil-industries`
- **GitHub repo**: `WatsonMulkey/foil-industries`
- **Deploy branch**: `master` (auto-deploys on push)
- **Local path**: `C:\Users\watso\Dev\foil-industries-v2`
- **IMPORTANT**: This directory has its own git repo separate from the parent Dev workspace

## Dev Commands
```bash
npm run dev       # Start dev server (localhost:4321)
npm run build     # Production build to dist/
npm run preview   # Preview production build
```

## Current Status
- Site is live with Services (3 accordion cards), Projects (The Number showcase), About, Contact sections
- Curtis Park proposal drafted but not yet sent
- Services: Product Management, Service Design, Bespoke Tooling
