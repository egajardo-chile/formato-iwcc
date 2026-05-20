# Handoff: IWCC · Reunión Área Técnica · 21 Abril 2026

## Overview

A 20-slide editorial-style presentation deck for **IWCC (Wine Company Chile)** used for an internal "Reunión Área Técnica" meeting. The deck reviews:

- Roadmap 2026–2027 by category (wine, grapes, services, packaging, marketing, etc.)
- Organizational chart of the Enology area
- Brazil and Chile market sales data + variation YoY
- Strategic recommendation around BeLight 8.5%, UK/LATAM, China, SCC 0,0% premium
- Hoja de ruta (roadmap to launch)
- Tasación comparativa (wine valuation)
- Móvil costo vino / inventory & demand
- Initiatives for the wine plan 2026
- Closing / next steps

The visual language is editorial-magazine: large display serif numbers, copper accents on cream/paper background, hairline rules, italic captions, and full-bleed photography on section dividers.

## About the Design Files

The files in this bundle are **design references created in HTML** — high-fidelity prototypes showing the intended look, layout and pagination, **not production code to copy directly**.

The implementer's task is to **recreate these designs in the target codebase's existing environment** (React, Vue, native slide tool, PPTX template, etc.) using its established components, patterns, and design tokens. If no environment exists yet, choose the most appropriate framework for the team and rebuild the deck there.

> The HTML deck is a fixed 1920×1080 canvas wrapped in a `<deck-stage>` custom element that handles slide navigation, scaling, and print-to-PDF. If the destination is PowerPoint / Keynote / Google Slides, treat each `<section>` as one 16:9 slide.

## Fidelity

**High-fidelity (hifi).** Exact colors, typography scale, spacing, and slide compositions are final. Reproduce pixel-perfectly using the codebase's existing libraries and patterns. The brand palette, type ramp, and slide grid (110px horizontal padding × 90px vertical) should be honored.

## Slide Inventory

Slides are 1920×1080. Each `<section>` inside `<deck-stage>` is one slide. The `data-label` attribute is the human label shown in the deck-stage overlay.

| #  | Label                          | Purpose                                                                                                            |
|----|--------------------------------|--------------------------------------------------------------------------------------------------------------------|
| 01 | Portada                        | Cover. Full-bleed autumn vineyard photo + dark scrim + large display title.                                         |
| 02 | Agenda                         | 6-item agenda grid with italic copper numerals, serif headlines, sans-serif subcopy.                                |
| 03 | Sección Timeline               | Section divider with giant copper "02" and editorial title; right pane is full-bleed photo of winery.               |
| 04 | Roadmap 2026–2027              | Horizontal multi-row timeline by category × quarter; sticky left labels, copper / good / warn cell coloring.        |
| 05 | Sección Organigrama            | Section divider "03 · Enología" with photo right pane.                                                              |
| 06 | Organigrama Enología           | Embedded org-chart image with eyebrow + lede + 31-person caption.                                                   |
| 07 | Sección Brasil                 | Dark section divider with green-toned dusk photo.                                                                   |
| 08 | Brasil Datos                   | Title + table of ventas Brasil (mercado, marca, vol/valor, var %); copper KPIs flanking; mini bar chart row.        |
| 09 | Sección Chile                  | Light section divider with warm aerial winery photo.                                                                |
| 10 | Chile Datos                    | Similar to Brasil with data tables, mega stat callout, recommendation pill at base.                                 |
| 11 | Recomendación Estratégica      | 2×2 matriz (matriz de oportunidad) + recommendation strip pill at bottom.                                           |
| 12 | Hoja de Ruta                   | Cream-background launch timeline; circular dot row of milestones with italic copper "when" labels and slate notes.  |
| 13 | Sección Tasación               | Dark section divider.                                                                                               |
| 14 | Tasación Comparativo           | Comparative valuation table with tasación cards (featured card filled copper) + photo pane right.                   |
| 15 | Sección Móvil Costo Vino       | Light section divider.                                                                                              |
| 16 | Móvil Granel Marzo             | "Big stat" mega numeral (copper) + serif value caption, photo pane right.                                           |
| 17 | Móvil Granel Tabla             | Detailed data table.                                                                                                |
| 18 | Iniciativas Vino 2026          | Cream-background grid of initiatives, each numbered (copper serif), with bullet list.                               |
| 19 | Sección Varios                 | Dark section divider with fog photo.                                                                                |
| 20 | Cierre                         | 2-pane closing: dark "Gracias" mega serif left; copper "Próximos pasos" right with serif blocks.                    |

## Design Tokens

All tokens live as CSS variables on `:root` in the deck HTML. Lift these into your codebase's token system (Tailwind config, design-tokens.js, theme.ts, etc.).

### Colors

| Token             | Hex                       | Use                                       |
|-------------------|---------------------------|-------------------------------------------|
| `--ink`           | `#1A1A1A`                 | Primary text, dark backgrounds            |
| `--ink-soft`      | `#2A2A2A`                 | Slightly softer body                      |
| `--copper`        | `#AE5F00`                 | Brand accent, eyebrows, large numerals    |
| `--copper-deep`   | `#8A4A00`                 | Deeper copper                             |
| `--copper-tint`   | `#C87A26`                 | Lighter copper for dark backgrounds       |
| `--cream`         | `#E0D5C8`                 | Cream surface                             |
| `--cream-soft`    | `#EBE2D6`                 | Softer cream surface                      |
| `--paper`         | `#F8F4EF`                 | Default slide background                  |
| `--slate`         | `#36454F`                 | Slate accents                             |
| `--slate-soft`    | `#5A6772`                 | Captions, footer text                     |
| `--white`         | `#FFFFFF`                 |                                           |
| `--good`          | `#2F7D4F`                 | Positive (table cells, milestone dots)    |
| `--warn`          | `#C8941A`                 | Warning                                   |
| `--bad`           | `#B43E2E`                 | Negative                                  |
| `--rule`          | `rgba(26,26,26,0.12)`     | Hairline rules                            |

### Typography

| Token              | Stack                                                   | Use                       |
|--------------------|---------------------------------------------------------|---------------------------|
| `--serif`          | `"Cormorant Garamond", "Calisto MT", Georgia, serif`    | Display, numerals, italic |
| `--sans`           | `"IBM Plex Sans", system-ui, sans-serif`                | Body, labels, eyebrows    |
| `--mono`           | `"IBM Plex Mono", ui-monospace, monospace`              | Page numbers, tabular nums |

### Type scale (px @ 1920×1080)

| Token              | Size  | Use example                          |
|--------------------|-------|--------------------------------------|
| `--type-display`   | 132px | Cover-level display (not all slides) |
| `--type-mega`      | 104px | Mega stat (e.g. 320px in megastat)   |
| `--type-title`     | 72px  | Section h1                           |
| `--type-subtitle`  | 44px  | Subtitle                             |
| `--type-body`      | 30px  | Body                                 |
| `--type-small`     | 26px  | Small body                           |
| `--type-label`     | 24px  | Labels                               |
| `--type-micro`     | 22px  | Foot row / brand row                 |

Special hand-tuned sizes used in-line (not via tokens):

- Cover title (`.cover-full .ct`): **170px**, serif 500, line-height 0.92, letter-spacing −0.018em
- Cover when (`.cover-full .when`): **64px**, serif 600
- Section divider big num (`.section-divider .big-num`): **280px**, serif 500
- Section divider h2 (`.section-divider h2`): **88px**, serif 500, line-height 0.98
- Captions h1 (`.cap h1`): **76px**, serif 500
- Stat key (`.stat .k`): **84px**, serif 600
- Mega stat key (`.megastat .k`): **320px**, serif 500
- Mega stat value (`.megastat .v`): **56px**, serif 500
- End-pane h1 (`.end-pane h1`): **220px**, serif 500

Letter-spacing conventions:
- Eyebrows/labels: `0.22–0.32em`, uppercase
- IWCC wordmark: `0.36em` serif 600
- Brand-row sub-line: `0.42em` sans 500 12px
- Display serif: `-0.012em` to `-0.025em`

### Spacing

```
--pad-x: 110px;         /* slide horizontal padding */
--pad-y: 90px;          /* slide vertical padding   */
--gap-section: 56px;
--gap-item: 28px;
```

Helper classes:
- `.gap-s` 16px, `.gap-m` 28px, `.gap-l` 48px, `.gap-xl` 72px

### Rules / borders

- Hairline: 1px `var(--rule)` (rgba(26,26,26,0.12))
- Copper rule: 2px `var(--copper)`
- Stat card left bar: 4px `var(--copper)` absolute left edge

### Shadows

Used sparingly. The cover title has a layered text-shadow for legibility on photo:
```
text-shadow: 0 6px 36px rgba(0,0,0,0.7), 0 2px 12px rgba(0,0,0,0.55);
```
The cover when has `0 2px 14px rgba(0,0,0,0.4)`.

No drop-shadows on cards.

## Repeating Components

These appear across multiple slides. In a component-based codebase, build each once and reuse.

### `BrandRow` (top header)
Absolute top: 48px; left/right: `var(--pad-x)`. Flex between.
- Left: `IWCC` wordmark — serif 28px, letter-spacing 0.36em, weight 600. Underline-small: `WINE COMPANY CHILE` sans 12px, letter-spacing 0.42em.
- Right: contextual title in uppercase tracked label style (22px, 0.2em, slate-soft).

### `FootRow` (bottom footer)
Absolute bottom: 46px; same horizontal padding. Flex between.
- Left: slide number + slide name (uppercase tracked 0.18em).
- Right: meeting context. Copper 6×6 dot used as separator.

### `Eyebrow`
Inline flex, gap 18px. Copper, 24px sans 500, 0.24em letter-spacing, uppercase. Prefixed with a 56×2 copper bar.

### `Cap` (page heading block)
```
.cap h1   → serif 76px / 500, line-height 1.02
.cap .lede → 30px slate / max-width ~1300px
```

### `Stat` card
Vertical flex. Copper 4px left edge (absolute).
- `.k` 84px serif 600
- `.v` 22px slate-soft

### `MegaStat`
- `.k` 320px serif 500 copper (em can be italic for unit)
- `.v` 56px serif 500 ink, max-width 1100px

### `AgendaItem`
- `.num` 64px serif italic copper (with implicit "/" pattern)
- `h3` 36px serif 500
- `p` body text

### `SectionDivider`
Two-pane 50/50 layout.
- Left pane: cream or paper or dark background. Holds eyebrow + h2 (88px serif) + 280px big copper numeral.
- Right pane: full-bleed `<img class="photo">` + dark `.veil` overlay + `.corner-mark` italic 28px label bottom-left.

### `IwccMark`
Stacked serif "IWCC" 60px + small uppercase "WINE COMPANY CHILE" 14px / 0.42em.

### `Pageno`
Bottom-right, mono 16px, 0.2em.

### `Pill`
Small uppercase chip. `.pill.copper` variant filled copper with paper text — used on the recommendation strip.

### `Table.data`
- 22px sans, full width, collapse
- `th` uppercase eyebrow style, color slate
- `td` border-bottom 1px rule
- Cell flags: `.cell-good` (rgba(47,125,79,0.10) bg, green text), `.cell-warn` (rgba(200,148,26,0.14) bg, #8a6510 text), `.cell-bad` red.

### `Matriz` (2×2 strategic matrix)
- Header `th.crit` left-aligned ink
- Body `td.crit` left, serif 24px / weight 500, ink

### `Timeline` (slide 04)
CSS grid with sticky row labels (italic serif 26px + sans uppercase 14px small). Cells have bottom 1px rule and copper/good/warn fills. Designed to read like a horizontal Gantt.

### `RutaStep` (slide 12)
- Circular dot 16px (copper / good / slate variants) with double box-shadow ring (`0 0 0 6px paper, 0 0 0 8px copper`).
- `.when` italic serif 30px copper / good
- Body 18–20px slate

### `Initiative` (slide 18)
- `.num` serif 80px copper 600
- `h3` serif 34px 500 ink
- `ul` 12px gap, custom (no marker)

### `TasacionCard` (slide 14)
- Default: paper background, ink text
- `.featured`: ink fill, paper text, copper-tint accents
- `.name` serif 32px 600
- `.total` serif 72px 600 copper (copper-tint when featured)
- `.breakdown` flex column gap 8px, 18px sans

### `EndPane` (slide 20)
Half-screen vertical-flex pane. Used twice in the cierre slide:
- Left: ink bg, paper text, mega serif `h1` 220px (e.g. "Gracias").
- Right: copper bg, paper text, label + serif 56px copy block.

## Interactions & Behavior

The HTML deck is a static slide presentation; the only "interaction" is **slide navigation**:

- `←`/`→` keys, tap-zones, or `<deck-stage>` API `goTo(n)` navigate.
- Slide index is reflected in the URL hash, so reload returns to the same slide.
- A `noscale` attribute on `<deck-stage>` disables the responsive transform (used by the PPTX exporter).
- `<image-slot>` placeholders accept drag-and-drop user uploads; not currently used.

When recreating in a real app:
- **Static slides only.** No animations or transitions inside slides.
- **No data fetching.** All numbers, tables, and copy are hard-coded.
- Provide standard keyboard arrow navigation, tap/click forward, and a slide counter.
- Optional: print-to-PDF (one page per slide, 1920×1080 landscape).

## State

None. Every value is content-baked. The only state is the current slide index (URL hash).

## Assets

### Photography (`photos/`)

Real photographs used in the deck. Stock photography placeholders — replace with licensed assets for production.

| File                       | Used on             | Treatment                                            |
|----------------------------|---------------------|------------------------------------------------------|
| `autumn-vineyard.jpeg`     | Slide 01 cover      | Full-bleed bg + scrim                                |
| `winery-side.jpeg`         | Slide 03 divider    | Right pane + veil + corner mark                      |
| `workers.jpeg`             | Slide 05 divider    | Right pane + veil                                    |
| `dusk.jpeg`                | Slide 07 divider    | Right pane, green tinted gradient bg                 |
| `winery-aerial.jpeg`       | Slide 09 divider    | Right pane, warm gradient bg                         |
| `pond.jpeg`                | Slide 14            | Right pane                                           |
| `tanks.jpeg`               | Slide 16            | Right pane                                           |
| `fog.jpeg`                 | Slide 19 divider    | Right pane                                           |

### Illustrative graphics (`images/`)

| File          | Used on   | Notes                                       |
|---------------|-----------|---------------------------------------------|
| `image3.png`  | Slide 06  | Organigrama Enología (org chart graphic)    |

### Fonts

Loaded from Google Fonts at build:
- Cormorant Garamond (italic 400/500; roman 400/500/600/700)
- IBM Plex Sans (300/400/500/600/700)
- IBM Plex Mono (400/500/600)

## Files in this bundle

- `Reunión Área Técnica.html` — full HTML source, 20 slides
- `deck-stage.js` — slide host custom element (scaling, nav, print). Drop-in dependency.
- `image-slot.js` — drag-drop image placeholder custom element (used for optional image slots).
- `photos/` — slide photography (only the 8 used in the deck)
- `images/` — organigrama PNG

## Implementation notes

- The HTML uses **CSS variables only** — no Tailwind, no preprocessor. Mapping these to the target system's token primitives is the highest-value first step.
- All slides are **statically authored HTML**. Each `<section>` is independent. If you port to a component framework, keep slide content as data-light declarative markup; the editorial layouts vary enough that "one slide template with props" is the wrong abstraction. Instead, build the **shared atoms** above (`BrandRow`, `FootRow`, `Eyebrow`, `Cap`, `Stat`, `MegaStat`, `SectionDivider`, `Table.data`, etc.) and let each slide arrange them freely.
- Letter-spacing and italic serifs are load-bearing for the editorial feel. Don't substitute Cormorant Garamond for a generic serif without checking the visual rhythm.
- Numbers in tables and KPIs use Spanish locale: `,` decimal, `.` thousands. Preserve.
- Copy is in Spanish (es-CL). Do not translate without sign-off.
