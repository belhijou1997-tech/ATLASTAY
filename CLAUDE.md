# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this project is

AtlasStay is a single-page marketing/conversion website for a premium accommodation and experience service based in Marrakech. The entire product is one file: `index.html`. There is no backend, no build system, no package manager, and no framework — all HTML, CSS, and JavaScript live in that single file. Bookings are converted entirely through WhatsApp.

## How to preview

Open `index.html` directly in a browser. No server, no build step required.

```
open index.html          # macOS
xdg-open index.html      # Linux
```

## Architecture

### Single-file structure

Everything is in `index.html` in this order:
1. `<head>` with Google Fonts import (Playfair Display + Inter)
2. `<style>` block — all CSS (~250 lines of custom properties + component styles)
3. HTML body — sections in page order: lang-bar → nav → hero → trust-bar → about → fiducia → proprieta → esperienze → transfer → how → booking → recensioni → faq → contatti → cta-final → footer → wa-sticky
4. `<script>` block at the end — all JavaScript (~80 lines)

### CSS design tokens

All colours are defined as CSS custom properties in `:root`:

```css
--nero: #0B0B0B      /* main background */
--nero-mid: #141414  /* section alternation */
--nero-soft: #1e1e1e /* cards */
--oro: #C9A96E       /* gold accent — primary brand colour */
--oro-light: #dfc08a /* gold hover */
--oro-dim: rgba(201,169,110,0.15)  /* subtle borders */
--bianco: #F5F0E8    /* off-white text */
--grigio: #888       /* muted text */
--verde: #25D366     /* WhatsApp green */
```

Typography: headings use `'Playfair Display', serif`; body uses `'Inter', sans-serif`.  
Responsive breakpoint: `960px` (single media query block at the bottom of `<style>`).

### Multilingual system

Three languages are supported: IT (default), EN, FR.

Every translatable element carries `data-it`, `data-en`, and `data-fr` attributes:
```html
<h1 data-it="Testo italiano" data-en="English text" data-fr="Texte français">Testo italiano</h1>
```

`setLang(l)` in the script block iterates all `[data-it]` elements and sets `innerHTML` (or `textContent` for inputs/options) to the appropriate attribute value. When adding new text, always add all three `data-*` attributes — omitting one silently leaves the element unchanged when the user switches to that language.

### WhatsApp integration

The booking form (`#prenota`) generates a structured WhatsApp message client-side. `updatePreview()` shows a live preview; `sendWA()` opens `wa.me/393881080923` with the message URL-encoded. The message template exists in three language variants inside each function — both functions duplicate this template, so changes to the message format must be made in both `updatePreview()` and `sendWA()`.

All CTA links on the page point to the same WhatsApp number with pre-filled context-specific messages.

### Reveal animations

Elements with class `reveal` are observed by an `IntersectionObserver`. When they enter the viewport, `visible` is added (opacity 0→1, translateY 22px→0). Add `class="reveal"` to any new card or content block to get the staggered entrance effect.

## Key conventions

- **Section alternation**: sections alternate between `var(--nero)` and `var(--nero-mid)` backgrounds to create visual separation without dividers.
- **Dividers**: decorative `<div class="divider">` elements with a `✦` gem appear between select sections.
- **Button variants**: `.btn-primary` (gold), `.btn-ghost` (outlined gold), `.btn-wa` (WhatsApp green), `.btn-sm` (full-width gold for property cards), `.micro-cta` (inline text link with arrow).
- **Section labels**: small uppercase gold labels above headings use class `s-label`; main headings use `s-title` with `<em>` for italic gold emphasis.
- **Responsive**: the 960px breakpoint collapses all multi-column grids to single-column and switches nav to hamburger. Any new multi-column layout needs a corresponding override in the `@media(max-width:960px)` block.

## Reference files

- `Claud.md` — business operating document (service overview, tone, conversion goals, page structure intent). Consult this for brand voice and copy decisions.
- `copy.md` — approved marketing copy for each section. Use as the canonical source for text content.
