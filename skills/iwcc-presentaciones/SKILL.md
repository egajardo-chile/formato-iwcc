---
name: iwcc-presentaciones
description: >
  Genera presentaciones y decks en el formato editorial corporativo de IWCC
  (Wine Company Chile): deck HTML 1920x1080, paleta cobre/crema/tinta, tipografia
  Cormorant Garamond + IBM Plex Sans, fotografia full-bleed en divisores, tablas
  con semaforo, KPIs y matrices estrategicas. Usa esta skill SIEMPRE que el usuario
  pida una presentacion, deck, slides, reunion, directorio, reporte ejecutivo o
  diga "hazme una pres", "arma slides", "genera un deck", "presentacion para la
  reunion", para IWCC o cualquier contexto corporativo. No esperes que lo pidan
  explicitamente como template.
---

# IWCC Presentaciones — Template editorial

Genera decks `.html` (1920×1080, una página por slide, print-to-PDF) en el sistema
de diseño editorial de IWCC. El template de referencia y todos los assets viven en
este plugin.

## Archivos del plugin

```
${CLAUDE_PLUGIN_ROOT}/
├── template/
│   ├── deck-template.html   # Deck de referencia — 20 slides reales (clónalo y edítalo)
│   ├── deck-stage.js        # Web component <deck-stage>: navegación, escala, print
│   ├── image-slot.js        # Placeholder drag-drop de imágenes
│   ├── photos/              # 8 fotografías (viñedo, bodega, niebla, etc.)
│   └── images/              # gráficos (organigrama)
└── DESIGN_TOKENS.md         # Spec completa: colores, tipografía, componentes, slides
```

## Flujo

### 1. Entender el pedido
Recopila (si no está en el mensaje del usuario):
- **Título / reunión** y fecha
- **Secciones** (cada bloque temático → un divisor + slides de contenido)
- **Datos**: tablas, KPIs, series, matrices
- **Audiencia / contexto** (directorio, área técnica, comercial, etc.)

Si hay contexto suficiente, genera directamente sin preguntar.

### 2. Partir del template
Copia el deck de referencia a la carpeta de trabajo del usuario y renómbralo:

```bash
mkdir -p ~/Downloads/<nombre-reunion>
cp -R "${CLAUDE_PLUGIN_ROOT}/template/." ~/Downloads/<nombre-reunion>/
mv ~/Downloads/<nombre-reunion>/deck-template.html ~/Downloads/<nombre-reunion>/<nombre-reunion>.html
```

`deck-stage.js`, `image-slot.js`, `photos/` e `images/` deben quedar junto al HTML
(las rutas son relativas).

### 3. Editar slide por slide
Cada slide es un `<section data-label="…">` dentro de `<deck-stage>`. Edita el contenido
respetando los componentes y tokens. **Lee `DESIGN_TOKENS.md` para los valores exactos.**

Reglas no negociables del formato IWCC:
1. **El título de cada slide es el insight**, no una etiqueta. ✗ "Ventas Brasil" → ✓ "Brasil crece +12%; Chile requiere acción correctiva".
2. **Un mensaje por slide.**
3. **Paleta**: cobre `#AE5F00` sobre crema/papel `#F8F4EF`; tinta `#1A1A1A` para texto y fondos oscuros.
4. **Tipografía**: serif Cormorant Garamond para display/numerales/itálicas; IBM Plex Sans para cuerpo/labels; IBM Plex Mono para números de página.
5. **Numeración española (es-CL)**: coma decimal, punto miles (`1.240`, `$ 186.000`).
6. **Copy en español** salvo que se pida otro idioma.
7. **Fotos full-bleed** en portada y divisores de sección (usa las de `photos/` o descarga otras y guárdalas ahí).
8. Padding de slide `110px` horizontal × `90px` vertical; no agregues drop-shadows a las cards.

### 4. Tipos de slide disponibles (en el template)
| Slide | Uso |
|-------|-----|
| Portada (`cover-full`) | Foto full-bleed + scrim + título display. Siempre primera. |
| Agenda | Grid de 6 ítems con numerales itálicos cobre. |
| Divisor de sección | 2 paneles 50/50: numeral 280px + título; foto full-bleed a la derecha. |
| Contenido (`cap` + body) | Eyebrow + título + bullets/argumentos. |
| Tabla (`table.data`) | Datos con semáforo `cell-good`/`cell-warn`/`cell-bad` + KPIs. |
| Mega stat (`megastat`) | Un numeral gigante (320px cobre) + caption. |
| Matriz 2×2 | Matriz de oportunidad estratégica + pill de recomendación. |
| Hoja de ruta (timeline) | Hitos en fila con dots cobre/good/slate. |
| Iniciativas | Grid numerado con bullets. |
| Cierre (`end-pane`) | 2 paneles: "Gracias" tinta + "Próximos pasos" cobre. |

### 5. Verificar y entregar
- Abre el HTML en el navegador para revisar.
- Navegación: `←`/`→` o click en los costados.
- PDF: `Ctrl/Cmd + P` → una página por slide (16:9 landscape); `deck-stage.js` ya lo configura.

```bash
open ~/Downloads/<nombre-reunion>/<nombre-reunion>.html
```

## Notas
- No reduzcas el tamaño del canvas: `<deck-stage>` escala solo. El atributo `noscale`
  desactiva la escala (lo usa el exportador a PPTX).
- Cormorant Garamond y las itálicas serif son carga visual del formato — no las sustituyas
  por una serif genérica.
- Si el usuario quiere `.pptx` en vez de HTML, trata cada `<section>` como una slide 16:9
  y reproduce el layout en PowerPoint respetando los mismos tokens.
