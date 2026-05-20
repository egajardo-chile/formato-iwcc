# Formato IWCC — Presentaciones

Template editorial **y** skill instalable de Claude para generar todas las
presentaciones de **IWCC (Wine Company Chile)** en el mismo formato: deck HTML
1920×1080, paleta cobre / crema / tinta, tipografía Cormorant Garamond + IBM Plex,
fotografía full-bleed en divisores, tablas con semáforo, KPIs y matrices estratégicas.

## Qué hay aquí

```
.
├── .claude-plugin/
│   ├── plugin.json          # define el plugin "iwcc-presentaciones"
│   └── marketplace.json     # permite instalarlo como marketplace
├── skills/
│   └── iwcc-presentaciones/
│       └── SKILL.md         # instruye a Claude a usar el template
├── template/
│   ├── deck-template.html   # deck de referencia (20 slides reales)
│   ├── deck-stage.js        # <deck-stage>: navegación, escala, print-to-PDF
│   ├── image-slot.js        # placeholder drag-drop de imágenes
│   ├── photos/              # 8 fotografías del deck
│   └── images/              # gráficos (organigrama)
├── DESIGN_TOKENS.md         # spec completa: colores, tipografía, componentes, slides
└── README.md
```

## Usar como template (manual)

1. Abre `template/deck-template.html` en cualquier navegador moderno.
2. Navega con `←` / `→` o click en los costados.
3. Duplica el HTML, renómbralo a tu reunión y edita cada `<section data-label="…">`.
4. Para PDF: `Ctrl/Cmd + P` (una página por slide, 16:9 landscape).
5. Reemplaza fotos en `photos/` manteniendo nombres, o actualiza los `src=`.

## Instalar como skill en Claude Code

```
/plugin marketplace add egajardo-chile/formato-iwcc
/plugin install iwcc-presentaciones@iwcc
```

Después, pídele a Claude "hazme una presentación para la reunión de …" y usará el
template automáticamente.

## Instalar en Claude Cowork

El mismo marketplace queda disponible en Cowork una vez agregado a tu cuenta: agrega
`egajardo-chile/formato-iwcc` como marketplace e instala `iwcc-presentaciones`. La
skill aparecerá en el selector de skills para presentaciones.

## Tokens de diseño (resumen)

| Token | Valor |
|-------|-------|
| `--ink` | `#1A1A1A` |
| `--copper` | `#AE5F00` |
| `--copper-tint` | `#C87A26` |
| `--paper` | `#F8F4EF` |
| `--cream` | `#E0D5C8` |
| `--good` | `#2F7D4F` |
| `--serif` | Cormorant Garamond |
| `--sans` | IBM Plex Sans |
| `--mono` | IBM Plex Mono |

Padding de slide: `110px` × `90px`. Detalle completo en [`DESIGN_TOKENS.md`](DESIGN_TOKENS.md).

## Licencia

Uso interno IWCC.
