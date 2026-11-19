# SAGA Jewelry — Sistema de Diseño de la Landing Page

> Especificación visual para desarrolladores. No incluye HTML/CSS de implementación;
> solo define tokens, tipografía, layout, guía por secciones y reglas de accesibilidad.
>
> **Referencias del cliente**: logo acuarela fucsia/magenta + "SAGA" serif blanco;
> diseño Canva admirado (crema cálido, serif elegante, "Hazlo tuyo." con palabra en oro,
> botón píldora oscuro, nav minimalista "SAGA.", topbar "PEQUEÑOS DETALLES, GRANDES HISTORIAS").
> **Base cromática del prototipo**: crema `#f8f3ee`, fucsia `#c21866`, oro `#bb9145`, tinta `#282424`.

---

## 1. Paleta de colores

### 1.1 Tokens claros (fondo base)

| Token | HEX | Rol |
|---|---|---|
| `--bg-cream` | `#f8f3ee` | Fondo principal cálido (hero, esencia, colección, ubicaciones). Es el "crema" del cliente. |
| `--bg-surface` | `#fffdfb` | Superficie elevada: nav, tarjetas de producto, footer, paneles, inputs. Casi blanco, cálido. |
| `--bg-sand` | `#e9ded7` | Superficie neutra de apoyo: placeholders de imagen, fondos de miniatura, separadores suaves. **Solo decorativa / con texto tinta.** |
| `--bg-blush` | `#efd7d8` | Fondo de acento suave reservado a **una** sección (galería Instagram). Aporta el guiño rosa sin recargar. |

### 1.2 Texto

| Token | HEX | Rol |
|---|---|---|
| `--text-ink` | `#282424` | Texto principal (títulos y cuerpo sobre fondos claros). Tinta del cliente. |
| `--text-muted` | `#6e6666` | Texto secundario (párrafos de apoyo, descripciones, meta). **Corregido** desde `#756d6d` para garantizar AA sobre crema (ver §2). |
| `--text-on-dark` | `#f8f3ee` | Texto principal sobre secciones invertidas (crema, no blanco puro: más suave). |
| `--text-muted-on-dark` | `#b9b1af` | Texto secundario sobre tinta (footer/newsletter, leyendas). |

### 1.3 Acentos

| Token | HEX | Rol |
|---|---|---|
| `--accent-fuchsia` | `#c21866` | **Acento primario.** Fucsia de marca (botones primarios, links activos, eyebrow sobre fondo claro, tag de producto, FAB WhatsApp). |
| `--accent-fuchsia-deep` | `#8e174f` | Hover/estado activo del fucsia y acentos de texto que requieren contraste extra (precios, eyebrow sobre blush). |
| `--accent-fuchsia-soft` | `#ff5fa2` | Fucsia claro **solo sobre fondos oscuros** (eyebrow o detalles en newsletter/topbar si hiciera falta). |
| `--accent-gold` | `#bb9145` | **Oro de marca decorativo:** iconos, líneas de 1px, filetes, bordes de detalle, glifos sobre tinta. **Nunca como texto sobre fondo claro** (no alcanza 4.5:1). |
| `--accent-gold-deep` | `#8a651c` | **Oro tipográfico sobre claro:** la palabra destacada del hero ("tuyo."), precios especiales, citas. Cumple AA sobre crema/blanco. |
| `--accent-gold-light` | `#d6b66b` | Oro claro para secciones invertidas (eyebrow en newsletter, detalles sobre tinta). |

### 1.4 Bordes, líneas y utilitarios

| Token | Valor | Rol |
|---|---|---|
| `--border-subtle` | `rgba(40,36,36,0.14)` | Divisores decorativos (entre beneficios, footer-bottom). |
| `--border-strong` | `#8a8381` | Borde de elementos **interactivos** (inputs, selects, mapa): necesita ≥3:1 (ver §2). |
| `--focus-ring` | `#c21866` (claro) / `#d6b66b` (oscuro) | Anillo de foco visible 2px + offset 2px. |
| `--whatsapp` | `#25d366` | **No usar como color de superficie.** Solo el glifo oficial si se decide versión verde; la especificación por defecto del FAB es fucsia (§5.9). |

### 1.5 Variantes oscuras (secciones invertidas)

| Token | HEX | Rol |
|---|---|---|
| `--bg-ink` | `#282424` | Fondo de secciones invertidas: topbar y newsletter. |
| `--bg-ink-soft` | `#332e2d` | Superficie elevada sobre tinta (paneles internos, campos en oscuro). |
| `--border-on-dark` | `rgba(248,243,238,0.18)` | Divisores/bordes sobre fondos oscuros. |

**Ritmo cromático de la página (de arriba a abajo):**
`topbar ink → nav surface → hero cream → beneficios surface → esencia cream → colección cream → editorial surface → Instagram blush → ubicaciones cream → newsletter ink → footer surface`.

---

## 2. Contraste y accesibilidad (WCAG 2.1 AA)

Ratios calculados con la fórmula WCAG relativa-luminancia. Aprobado = **≥4.5:1** (texto normal), **≥3:1** (texto grande ≥24px o ≥18.66px bold, y elementos UI/gráficos).

| # | Par (texto → fondo) | Ratio | Veredicto |
|---|---|---|---|
| 1 | `#282424` tinta → `#f8f3ee` crema | **13.9:1** | ✅ AAA |
| 2 | `#282424` tinta → `#fffdfb` surface | **15.1:1** | ✅ AAA |
| 3 | `#6e6666` muted → `#f8f3ee` crema | **5.1:1** | ✅ AA |
| 4 | `#6e6666` muted → `#fffdfb` surface | **5.5:1** | ✅ AA |
| 5 | `#282424` tinta → `#e9ded7` sand | **11.6:1** | ✅ AAA (único texto permitido sobre sand) |
| 6 | `#6e6666` muted → `#e9ded7` sand | 4.2:1 | ❌ **Prohibido** — usar tinta en su lugar |
| 7 | `#c21866` fuchsia → `#f8f3ee` crema | **5.3:1** | ✅ AA |
| 8 | `#c21866` fuchsia → `#fffdfb` surface | **5.7:1** | ✅ AA |
| 9 | blanco `#ffffff` → `#c21866` (botón primario) | **5.8:1** | ✅ AA |
| 10 | blanco → `#8e174f` (hover botón) | **8.8:1** | ✅ AAA |
| 11 | `#8e174f` fuchsia-deep → `#f8f3ee` crema | **8.0:1** | ✅ AAA |
| 12 | `#8e174f` fuchsia-deep → `#efd7d8` blush | **6.5:1** | ✅ AAA (uso obligatorio del acento sobre blush) |
| 13 | `#c21866` fuchsia → `#efd7d8` blush | 4.3:1 | ❌ **No usar** (eyebrow sobre Instagram → usar `#8e174f`) |
| 14 | `#8a651c` gold-deep → `#f8f3ee` crema | **4.8:1** | ✅ AA (palabra "tuyo." del hero) |
| 15 | `#8a651c` gold-deep → `#fffdfb` surface | **5.3:1** | ✅ AA |
| 16 | `#bb9145` gold → `#f8f3ee` crema | 2.6:1 | ❌ **Solo decorativo** (iconos con `aria-hidden`, filetes, bordes) |
| 17 | `#d6b66b` gold-light → `#282424` tinta | **7.9:1** | ✅ AAA (secciones oscuras) |
| 18 | `#f8f3ee` crema → `#282424` tinta | **13.9:1** | ✅ AAA (topbar, newsletter) |
| 19 | `#b9b1af` muted-dark → `#282424` tinta | **7.3:1** | ✅ AAA |
| 20 | `#ff5fa2` fuchsia-soft → `#282424` tinta | **5.4:1** | ✅ AA |
| 21 | `#8a8381` border-strong → `#f8f3ee` crema | **3.4:1** | ✅ (borde de inputs/UI, no texto) |
| 22 | `rgba(40,36,36,0.14)` border-subtle → crema | ~1.3:1 | ⚠️ Decorativo puro, nunca único indicador de estado |
| 23 | `#ffffff` → `#c21866` (glifo FAB WhatsApp) | **5.8:1** | ✅ AA |
| 24 | Anillo foco `#c21866` → crema (componente UI) | **5.3:1** | ✅ (>3:1) |
| 25 | Anillo foco `#d6b66b` → tinta (componente UI) | **7.9:1** | ✅ (>3:1) |

**Correcciones aplicadas antes de escribir el spec** (no publicar los valores originales):
1. `--text-muted`: `#756d6d` → **`#6e6666`** (el original daba 4.57:1 sobre crema: aprobaba por los pelos; ahora 5.1:1 con margen).
2. El acento de texto sobre **blush** se cambia de fucsia a **`#8e174f`** (4.3:1 → 6.5:1).
3. El oro `#bb9145` queda **prohibido como texto sobre claro**; se añade `#8a651c` para tipografía dorada (4.8:1).
4. Todo texto sobre `--bg-sand` debe ser tinta.

**Reglas generales:**
- Nunca comunicar estado solo por color (precio/oro, errores, tags): acompañar de icono o texto.
- Imágenes con `alt` descriptivo en español; imágenes decorativas con `alt=""`.
- Foco visible **siempre** (`:focus-visible`), nunca `outline: none` sin sustituto.
- Respetar `prefers-reduced-motion` (§6).
- Zoom de texto al 200% sin pérdida de función.

---

## 3. Tipografía

### 3.1 Familias (Google Fonts)

| Rol | Familia | Pesos / estilos | Uso |
|---|---|---|---|
| Display (serif) | **Playfair Display** | 400, 500 + itálica 400 | h1, h2, h3 de marca, logo tipo "SAGA.", cifras, firma "Con amor, SAGA". Alta modulación = elegancia tipo Canva. |
| Texto (sans) | **DM Sans** | 400, 500, 600 | Body, párrafos, botones, nav, labels, formularios. |
| Fallbacks | `Georgia, serif` / `Arial, sans-serif` | — | Carga progresiva segura. |

Carga: `preconnect` a `fonts.googleapis.com` + `fonts.gstatic.com` (crossorigin), un solo request combinado, `display=swap`.

### 3.2 Escala tipográfica (responsive con `clamp()`)

| Rol | `clamp()` | Line-height | Letter-spacing | Peso | Transform |
|---|---|---|---|---|---|
| **h1 hero** | `clamp(3rem, 9vw, 5.75rem)` (48→92px) | `0.95` | `-0.03em` | 400 | — (la palabra oro puede ir en itálica 400) |
| **h2 sección** | `clamp(2rem, 4.6vw, 3.5rem)` (32→56px) | `1.08` | `-0.02em` | 400 | — |
| **h3 tarjeta / beneficio** | `clamp(1.125rem, 1.4vw, 1.375rem)` (18→22px) | `1.25` | `0` | 400 (serif) o 500 (sans) | — |
| **body** | `clamp(1rem, 0.95rem + 0.2vw, 1.0625rem)` (16→17px) | `1.65` | `0` | 400 | — |
| **body small** (meta, footer, ayuda) | `0.875rem` (14px) | `1.6` | `0` | 400 | — |
| **eyebrow** | `0.75rem` (12px) | `1.4` | `0.2em` | 600 | `uppercase` |
| **nav link** | `0.8125rem` (13px) | `1.4` | `0.1em` | 500 | `uppercase` |
| **botón** | `0.8125rem` (13px) | `1` | `0.12em` | 600 | `uppercase` |
| **topbar** | `0.6875rem` (11px) → `0.625rem` en móvil | `1.4` | `0.16em` | 500 | `uppercase` |
| **precio** | `0.9375rem` (15px) | `1.3` | `0.02em` | 600 | — |
| **tag producto** | `0.6875rem` (11px) | `1` | `0.1em` | 600 | `uppercase` |

**Reglas de uso:**
- Serif **solo** para display y micro-titulares; nunca para párrafos.
- Párrafos con `max-width: 58ch` (hero: 42ch).
- Eyebrow siempre precede al h2 con margen inferior de `--space-3`.
- El hero se compone en 2 líneas: "Hazlo" (tinta) / "tuyo." (gold-deep, puede ir itálica) — misma escala, sin tamaño extra.

---

## 4. Espaciado, layout y breakpoints

### 4.1 Sistema de espaciado (base 8px, con sub-unidad 4px)

```
--space-1: 4px    --space-2: 8px    --space-3: 12px   --space-4: 16px
--space-5: 20px   --space-6: 24px   --space-8: 32px   --space-10: 40px
--space-12: 48px  --space-16: 64px  --space-20: 80px  --space-24: 96px
--space-32: 128px
```

- **Padding de sección (vertical):** `clamp(72px, 10vw, 128px)` (hero puede ser `clamp(64px, 8vw, 112px)`).
- **Gap de grids:** desktop `32px`; tarjetas de producto `24px`; galería Instagram `12px` (8px en móvil).
- **Ritmo interno:** eyebrow → h2 = 12px; h2 → párrafo = 20px; párrafo → botón = 32px.

### 4.2 Contenedor y gutters

```
--container-max: 1200px;
Ancho: width: min(100% - 2 * gutter, 1200px); margin-inline: auto;
--gutter: clamp(20px, 4vw, 40px)   /* 20px móvil · 32px tablet · 40px desktop */
```
- Medida de lectura de textos largos: `max-width: 560px`.
- El hero usa el contenedor completo pero con grid asimétrico (§5.3).

### 4.3 Radios de borde

| Elemento | Radio |
|---|---|
| Botones (primarios/outline) | `999px` (píldora, como el "EXPLORAR COLECCIÓN ↗" del Canva) |
| Tarjetas de producto / paneles / mapa | `4px` |
| Inputs y textarea | `4px` |
| Imágenes destacadas (hero, editorial) | `0px` o `2px` (esquina viva, estética editorial) |
| Chips/tags | `999px` |
| FAB WhatsApp, logo, avatares | `50%` |
| Bajadas/acentos de línea | `1px` sólido |

Sombras (solo elevación sutil): `--shadow-sm: 0 1px 2px rgba(40,36,36,.06)` · `--shadow-md: 0 8px 24px rgba(40,36,36,.10)` (usada en panel WhatsApp y tarjetas en hover).

### 4.4 Breakpoints y qué cambia en cada uno

| Breakpoint | Rango | Cambios principales |
|---|---|---|
| **xs — móvil base** | `≤ 479px` | 1 columna en todo. Gutter 20px. Nav = hamburguesa. Hero apilado (texto arriba, imagen abajo `aspect-ratio: 4/5`). Beneficios apilados con divisores horizontales. Producto 2 cols. Instagram 2 cols. Newsletter apilado (input + botón stacked). Footer 1 col + marca full-width. FAB con `safe-area-inset-bottom`. |
| **sm — móvil grande** | `480–767px` | Gutter 24px. Instagram **3 cols**. Footer 2 cols. Hero imagen `aspect-ratio: 3/4`. Beneficios siguen apilados. |
| **md — tablet** | `768–1023px` | **Nav sigue en hamburguesa** (hasta 1023). Hero pasa a 2 cols solo si ≥900px (`1fr 1fr`), si no apilado. Beneficios **3 cols**. Producto 2 cols. Instagram 3 cols. Story/editorial: apilados con gap 48px. Ubicaciones: mapa arriba, 2 sedes en 2 cols. |
| **lg — desktop** | `1024–1279px` | **Nav horizontal visible** con links centrados. Hero 2 cols `1.05fr 1fr`. Producto **4 cols**. Story/editorial 2 cols. Instagram **6 cols**. Footer 4 cols (marca + 3 columnas). |
| **xl — grande** | `≥ 1280px` | Contenedor capado a 1200px (márgenes laterales generosos). Padding de sección tope 128px. Hero puede crecer a `min-height: min(86vh, 780px)`. |

**Transiciones de grid (resumen):**
- Producto: 1 col (xs) → 2 cols (≥480) → 4 cols (≥1024)
- Instagram: 2 cols (xs) → 3 cols (≥480) → 6 cols (≥1024)
- Beneficios: 1 col (≤767) → 3 cols (≥768)
- Footer: 1 col (xs) → 2 cols (≥480) → 4 cols (≥1024)
- Nav: hamburguesa (≤1023) → horizontal (≥1024)

---

## 5. Guía por secciones

> Para cada sección: jerarquía visual, variante de color, notas responsive.
> `E` = eyebrow, `H` = heading, `P` = párrafo, `CTA` = acción.

### 5.1 Barra superior (topbar)
- **Contenido:** "PEQUEÑOS DETALLES, GRANDES HISTORIAS" centrado; en móvil se puede rotar/alternar con "ENVÍOS A TODO EL PAÍS · SHIPPING WORLDWIDE 🌐".
- **Color:** fondo `--bg-ink #282424`, texto `#f8f3ee` (13.9:1 ✅).
- **Tipografía:** 11px (10px <480), 600, `letter-spacing 0.16em`, uppercase.
- **Altura:** 36px desktop / 32px móvil. No sticky.
- **Responsive:** si el texto no cabe en 320px, acortar a "ENVÍOS A TODO EL PAÍS"; nunca permitir wrap a 2 líneas (usar `white-space: nowrap` + recortar contenido, no scroll).

### 5.2 Navegación
- **Estructura:** logo `SAGA.` (serif 400, `letter-spacing 0.14em`, el punto final en `--accent-fuchsia`) · links: NUESTRA ESENCIA / COLECCIÓN / INSPIRACIÓN / CONTACTO · CTA secundario "DESCUBRE SAGA ↗" (solo ≥1024).
- **Color:** fondo `--bg-surface #fffdfb`, borde inferior `--border-subtle`, texto `--text-ink`.
- **Jerarquía:** logo 26px (22px móvil) → links 13px uppercase → CTA 13px uppercase subrayado con filete gold o botón outline píldora.
- **Estados:** link hover = subrayado 1px `--accent-fuchsia` que crece de izquierda a derecha (260ms); CTA hover = relleno tinta/crema invertido.
- **Sticky:** sí, `position: sticky; top: 0` con `backdrop-filter: blur(8px)` y fondo a 96% opacidad; **no** sticky el topbar.
- **Móvil (≤1023):** hamburguesa de 44×44px, `aria-expanded`, menú panel full-width bajo la nav, fondo surface, links en fila vertical con padding 16px y **min-height 48px** por link; al abrir, bloquear scroll del body.
- **Accesibilidad:** `aria-label="Navegación principal"`, skip-link "Saltar al contenido" como primer foco del documento.

### 5.3 Hero
- **Estructura:** grid 2 cols `1.05fr 1fr` (≥900), apilado debajo.
  - Izquierda (sobre `--bg-cream`): **E** "JOYERÍA CON PERSONALIDAD" (12px, 600, 0.2em, fucsia) → **H1** "Hazlo / tuyo." (línea 1 tinta, línea 2 `--accent-gold-deep` itálica) → **P** "Piezas que capturan la luz, celebran tu estilo y acompañan cada capítulo de tu historia." (muted, max 42ch) → **CTA primario** "EXPLORAR COLECCIÓN ↗" (píldora tinta, texto crema, 50px alto, padding 0 28px) + CTA outline "NUESTRA ESENCIA".
  - Derecha: foto de modelo con joyería, a sangre (full-bleed al borde derecho del viewport en desktop), `object-fit: cover`, `object-position: 50% 25%` (ojo a la cara), con marco interior tipo Canva: `border: 1px solid rgba(255,255,255,.7); inset: 20px`.
  - Overlay abajo-derecha: tagline "TU HISTORIA MERECE BRILLAR · SAGA" (11px, uppercase, 0.18em, blanco con `text-shadow: 0 1px 8px rgba(0,0,0,.45)` para garantizar legibilidad sobre foto → usar fondo `rgba(40,36,36,.45)` con padding 8×14px si la foto es clara).
- **Altura:** `min-height: min(86vh, 780px)` desktop; `min-height: auto` móvil.
- **Responsive:** <900 → apilado (texto con padding `64px 0 48px`, imagen debajo `aspect-ratio: 4/5`); <480 → H1 tope 48px, tagline de la foto se oculta si no cabe (la info ya está en footer).
- **Nota de marca:** si hay logo jpg disponible en nav, alternativa = círculo fucsia 40px + "SAGA." — pero el ref del cliente usa wordmark tipográfico; **priorizar wordmark**.

### 5.4 Beneficios (3 items)
- **Estructura:** fila de 3 celdas separadas por `border-left: 1px var(--border-subtle)`; primera sin borde.
- **Contenido sugerido:** ✦ "Envíos a todo el país" / "Y shipping worldwide 🌐" · ◇ "Joyas hechas con amor" / "Diseños con intención 🤍" · ♡ "Atención personalizada" / "Por WhatsApp, cercana".
- **Color:** fondo `--bg-surface`, título serif 18px tinta, bajada 14px muted. Iconos glifo `--accent-gold` (decorativos, `aria-hidden="true"` — el icono no es texto, vale 2.6:1 como gráfico no esencial porque el título ya comunica).
- **Altura celda:** min 104px desktop; padding `20px 24px`.
- **Responsive:** ≥768 → 3 cols; <768 → apilado con `border-top` en lugar de `border-left`, celda `min-height: 72px`, icono 24px.

### 5.5 Historia / Esencia ("Nuestra esencia")
- **Estructura:** 2 cols `0.9fr 1.1fr`, gap `clamp(32px, 6vw, 88px)`; izquierda = collage de 2 imágenes desfasadas (col 1 alto 440px, col 2 alto 360px con `margin-top: 88px`), derecha = texto.
- **Jerarquía:** **E** "LA ESENCIA SAGA" (fucsia) → **H2** "Lo especial está en los detalles." → 2 párrafos muted → CTA outline "DESCUBRIR NUESTRA HISTORIA" → firma serif itálica 23px en `--accent-fuchsia-deep`: *"Con amor, SAGA 🤍"*.
- **Color:** fondo `--bg-cream`.
- **Responsive:** <900 → apilado (imágenes primero, 2 cols con gap 12px, alturas 300px/240px); <480 → imágenes `aspect-ratio: 3/4` con altura auto.

### 5.6 Colección de productos (4 tarjetas)
- **Cabecera:** fila `space-between` alineada al baseline: izquierda **E** "SELECCIÓN SAGA" + **H2** "Favoritos de la colección"; derecha CTA outline "VER CATÁLOGO COMPLETO". <768 → apilado con gap 20px, CTA alineado a la izquierda (o full-width).
- **Grid:** 4 cols (`gap: 24px`) ≥1024 · 2 cols (`gap: 16px`) ≥480 · 1 col si <360 (recomendado: mantener 2 cols hasta 360 para no exagerar el scroll).
- **Tarjeta:** fondo `--bg-surface`, `border-radius: 4px`, overflow hidden.
  - **Imagen:** `aspect-ratio: 4/5` (portrait de joyería; no usar 0.9 cuadrado en móvil), fondo placeholder `--bg-sand`, `object-fit: cover`, `object-position: center`.
  - **Tag opcional** ("FAVORITO" / "NUEVO"): esquina sup-izq, fondo `--accent-fuchsia`, texto blanco 11px 600 uppercase, padding 6×10px, radio 999px.
  - **Info:** padding `16px` → **H3** serif 18px tinta (nombre de pieza) · descripción 14px muted (2 líneas máx, `line-clamp: 2`) · precio 15px 600 en `--accent-fuchsia-deep` (8:1 sobre surface ✅).
- **Hover (ver §6):** tarjeta `translateY(-6px)` + `shadow-md`; imagen `scale(1.04)` 500ms.
- **Responsive:** en 2 cols reducir padding de info a 12px y nombre a 16px; tag sigue visible.

### 5.7 Editorial ("Tu estilo, tu forma")
- **Estructura:** 2 cols `1fr 1fr`, gap `clamp(32px, 5vw, 72px)`; texto izquierda, imagen derecha (`aspect-ratio: 4/5`, max-height 600px).
- **Jerarquía:** **E** "TU ESTILO, TU FORMA" (fucsia) → **H2** "Diseñadas para combinar. Creadas para permanecer." → párrafo muted → **CTA primario** píldora fucsia "VER INSPIRACIÓN →" (blanco sobre `#c21866`, 5.8:1 ✅).
- **Color:** fondo `--bg-surface`.
- **Responsive:** <900 → apilado con texto **primero** y imagen después (si la imagen es decorativa), gap 40px; <480 → imagen `aspect-ratio: 3/4`.

### 5.8 Galería Instagram (6 piezas)
- **Color:** fondo `--bg-blush #efd7d8` (única sección con este tono).
- **Jerarquía centrada:** **E** "SÍGUENOS EN INSTAGRAM" en `--accent-fuchsia-deep #8e174f` (6.5:1 ✅ — **no** fucsia base) → **H2** "SAGA en la vida real" (tinta) → párrafo muted → grid → handle **@saga.ve** como link 14px 600 uppercase `letter-spacing .1em` en `#8e174f`, con `target="_blank" rel="noopener"`.
- **Grid:** 6 cols (`gap: 12px`) ≥1024 · 3 cols (`gap: 10px`) ≥480 · 2 cols (`gap: 8px`) <480. Cada celda `aspect-ratio: 1`, `object-fit: cover`.
- **Hover:** overlay fucsia `rgba(142,23,79,.82)` con texto blanco "VER EN INSTAGRAM" 11px uppercase (blanco sobre ese overlay ≥4.5:1 ✅); en **touch**: overlay permanece como icono-instagram centrado al 100% opacidad en la esquina (no depender de hover en móvil).
- **Enlace:** toda la celda es `<a>` con `aria-label="Publicación N de Instagram @saga.ve"`.
- **Nota de contenido:** mencionar línea masculina "@sagaformen" como link secundario bajo el handle (14px, muted sobre blush → usar tinta, ver §2).

### 5.9 Ubicaciones (mapa + 2 sedes)
- **Estructura:** 2 cols `1.1fr 0.9fr` ≥1024 · apilado <1024.
  - **Izquierda:** mapa embebido (Google Maps iframe o imagen estática con pin), `aspect-ratio: 16/10`, `border-radius: 4px`, `border: 1px solid var(--border-subtle)`, `loading="lazy"`, `title="Mapa de tiendas SAGA en Venezuela"`.
  - **Derecha:** 2 tarjetas de sede apiladas (`gap: 16px`), fondo surface, radio 4px, borde subtle, padding 24px:
    1. **SAGA Servimas** — "C.C. Servimas Monterrey" + botón píldora "WHATSAPP ↗" (`wa.me/584249140219`)
    2. **SAGA Centro** — "Sector Centro, diagonal Plaza Ayacucho" + botón píldora (`wa.me/584249305441`)
    - Cada tarjeta: pin dorado glifo `--accent-gold` + nombre serif 20px + dirección 15px muted + badge "Venezuela 📍 · Shipping Worldwide 🌐" en 12px uppercase 0.12em tinta.
- **Jerarquía de la sección:** **E** "VISÍTANOS" (fucsia) → **H2** "Encuentra tu SAGA más cercana" → párrafo corto.
- **Color:** fondo `--bg-cream`.
- **Responsive:** <1024 → mapa primero full-width, luego 2 tarjetas (2 cols si ≥640, 1 col si <640). Botones de WhatsApp `width: 100%` en 1 col.

### 5.10 Botón flotante de WhatsApp (FAB) con 2 números
- **FAB:** `position: fixed`, esquina **inferior-derecha**, tamaño **56×56px** (mín. 48px táctil, cómodo 56), `border-radius: 50%`, fondo `--accent-fuchsia #c21866`, glifo WhatsApp en blanco (5.8:1 ✅), `box-shadow: var(--shadow-md)`, `z-index: 90`.
  - Offset: `right: 20px; bottom: calc(20px + env(safe-area-inset-bottom))`.
  - **Alternativa aceptada:** verde oficial `#25D366` con glifo blanco (1.9:1 ❌ para texto, pero el glifo es gráfico + tiene `aria-label` → permitido solo si además muestra etiqueta de texto). **Default del spec: fucsia** (coherencia de marca).
- **Panel al abrir** (se abre hacia arriba-izquierda, ancho `min(320px, calc(100vw - 40px))`):
  - Fondo `--bg-surface`, radio 4px, `border: 1px solid var(--border-subtle)`, `shadow-md`, padding 8px.
  - Cabecera: 12px uppercase 0.14em muted "ESCRÍBENOS POR WHATSAPP".
  - **2 filas-enlace**, cada una `min-height: 56px`, padding 12px 14px, radio 4px:
    1. Icono verde WhatsApp + **"SAGA Servimas"** (15px, 600, tinta) + **+58 424-9140219** (14px, muted) → `https://wa.me/584249140219`
    2. Icono + **"SAGA Centro"** + **+58 424-9305441** → `https://wa.me/584249305441`
  - Hover de fila: fondo `--bg-cream`, tinta; foco visible gold.
  - Cierre: clic fuera, `Esc`, y botón X (44×44px) visible solo en el panel.
- **Accesibilidad:** botón con `aria-label="Abrir opciones de WhatsApp"` + `aria-expanded`; panel `role="dialog"` no modal; números como texto seleccionable (no solo dentro de la imagen).
- **Responsive:** en <480 el panel se ancla a `left: 16px; right: 16px` (ancho completo) para no desbordar; nunca tapar el CTA del hero ni el input del newsletter (añadir `padding-bottom` al footer equivalente a 76px).

### 5.11 Newsletter
- **Color (invertida):** fondo `--bg-ink #282424`, texto `--text-on-dark`.
- **Jerarquía centrada:** **E** "ÚNETE A LA COMUNIDAD" en `--accent-gold-light #d6b66b` (7.9:1 ✅) → **H2** serif crema "Historias, novedades y piezas especiales." → párrafo `--text-muted-on-dark` (7.3:1 ✅) → formulario.
- **Formulario:** fila `max-width: 480px`, input `flex: 1`, alto 52px, fondo blanco, texto tinta, placeholder `#6e6666` (5.5:1 sobre blanco ✅), `border-radius: 4px 0 0 4px`; botón "SUSCRIBIRME" alto 52px, fondo `--accent-fuchsia`, blanco, `0 24px`, radio `0 4px 4px 0`, 13px 600 uppercase 0.12em.
- **Validación:** estado de error = mensaje 14px en `#ff9fb8` (verificar ≥4.5:1 sobre tinta → si no, usar `#ffb3c9`) + `aria-live="polite"`; nunca solo borde rojo.
- **Responsive:** <560 → apilado (`flex-direction: column; gap: 10px`), ambos con `border-radius: 4px` y alto 52px; botón full-width.
- **Padding sección:** `clamp(64px, 8vw, 96px) 0`.

### 5.12 Footer
- **Color:** fondo `--bg-surface`, texto tinta/muted, borde superior subtle.
- **Estructura:** grid `1.4fr 1fr 1fr 1fr` (gap 40px) → 2 cols ≥480 → 1 col <480 (marca full-width).
  1. **Marca:** wordmark "SAGA." serif 26px + bajada 15px muted "Joyería contemporánea · Joyas hechas con amor 🤍" + "@saga.ve" link fucsia + línea "Colección masculina → @sagaformen".
  2. **Explorar:** Colección / Nuestra esencia / Inspiración.
  3. **Ayuda:** Envíos (todo el país + worldwide) / Cambios y devoluciones / Preguntas frecuentes.
  4. **Contacto:** WhatsApp Servimas (+58 424-9140219) · WhatsApp Centro (+58 424-9305441) · Instagram · Correo. Cada link `display: block`, min-height 44px para táctil.
- **Títulos de columna:** 12px, 600, uppercase, `letter-spacing 0.14em`, tinta.
- **footer-bottom:** `border-top: 1px var(--border-subtle)`, 13px muted, `flex space-between`; izq "© {año} SAGA. Todos los derechos reservados." · der links sociales (13px uppercase 0.1em).
- **Responsive:** <768 → footer-bottom apilado con gap 12px.

---

## 6. Estados e interacciones

### 6.1 Transiciones base
```
--t-fast:   150ms  cubic-bezier(.4,0,.2,1)   /* color, opacidad */
--t-base:   260ms  cubic-bezier(.4,0,.2,1)   /* hover estándar */
--t-slow:   500ms  cubic-bezier(.22,1,.36,1)  /* imagen zoom, reveal */
--t-reveal: 700ms  ease                       /* entrada scroll */
```

### 6.2 Componentes

| Componente | Default | Hover | Active | Focus-visible | Disabled |
|---|---|---|---|---|---|
| **Btn primario (píldora)** | bg `#c21866`, texto `#fff`, h 50px | bg `#8e174f`, `translateY(-2px)`, `shadow-md` | `translateY(0)`, bg `#7a1244` | `outline: 2px solid #c21866; outline-offset: 3px` (sobre oscuro: `#d6b66b`) | opacidad .55, `cursor: not-allowed` |
| **Btn oscuro tipo Canva (hero)** | bg `#282424`, texto `#f8f3ee` | bg `#000` (o `#332e2d`), flecha `↗` se desplaza `translate(2px,-2px)` | opacidad .9 | anillo fucsia 2px + offset 3px | — |
| **Btn outline** | borde 1px `#282424`, texto tinta, transparente | bg `#282424`, texto `#f8f3ee` | opacidad .85 | anillo fucsia | — |
| **Link nav** | tinta, sin subrayado | subrayado 1px `#c21866` scaleX 0→1 (izq→der, 260ms) | — | anillo 2px offset 4px | — |
| **Tarjeta producto** | sin sombra | `translateY(-6px)` + `shadow-md` + img `scale(1.04)` 500ms | — | si es link: anillo inset 2px fucsia | — |
| **Celda Instagram** | sin overlay | overlay `rgba(142,23,79,.82)` opacity 0→1 260ms | — | overlay permanente + anillo 2px crema inset | — |
| **Input newsletter** | bg blanco, borde none, h 52px | — | — | `box-shadow: 0 0 0 3px rgba(194,24,102,.35)` + borde `#c21866` | — |
| **FAB WhatsApp** | bg fucsia, glifo blanco, `shadow-md` | `scale(1.06)`, bg `#8e174f` | `scale(.97)` | anillo `#d6b66b` 2px offset 3px (siempre visible en oscuro) | — |
| **Fila de número en panel** | bg surface | bg `#f8f3ee` | — | anillo fucsia inset 2px | — |

### 6.3 Reveal al scroll
- `opacity: 0 → 1` + `translateY(20px) → 0`, 700ms ease, umbral `threshold: 0.12`, una sola vez.
- **`@media (prefers-reduced-motion: reduce)`:** desactivar reveal (todo visible de inmediato), desactivar `scale`/`translateY` de hovers (solo cambio de color), `scroll-behavior: auto`, transiciones ≤ 1ms.

### 6.4 Micro-interacciones extra
- Flechas `↗`/`→` de CTA: `translate(3px,-3px)` / `translateX(4px)` en hover, 260ms.
- Menú hamburguesa: icono ☰ → ✕ con rotación 90°, 260ms.
- Aparición del panel WhatsApp: `opacity 0→1` + `translateY(8px)→0` + `scale(.98)→1`, 200ms ease-out.

---

## 7. Reglas anti-fallos responsive

1. **Sin overflow horizontal**
   - `html, body { overflow-x: hidden; }` como red de seguridad, pero **no depender de ello**: nada de anchos fijos en px, nada de `width: 100vw` (usa `100%`; `100vw` incluye el scrollbar).
   - Todo grid/flex child: `min-width: 0;` (imprescindible en `grid-template-columns` con texto largo).
   - Textos largos: `overflow-wrap: break-word;` en títulos y `hyphens: auto` en párrafos (es-VE).
   - Imágenes: `max-width: 100%; height: auto;` salvo cuando se controle con `aspect-ratio` + `object-fit: cover`.
   - El hero full-bleed se logra con `margin-right: calc(-1 * var(--gutter))` o grid hasta el borde, **no** con anchos de 100vw.
   - Test obligatorio a **320px** y **360px** sin scroll lateral.
2. **Imágenes sin cortar cabezas**
   - Todo `<img>` de persona: `object-fit: cover` + `object-position: 50% 22–30%` (rostro arriba del centro).
   - Productos: `object-position: center`.
   - Usar `aspect-ratio` declarado (4/5 retrato, 1/1 galería, 16/10 mapa) para evitar layout shift; reservar espacio con fondo `--bg-sand`.
   - Fotos de personas no deben recortar a la altura del mentón: si el recorte queda mal en un breakpoint, cambiar `aspect-ratio` (no recortar más).
3. **Tap targets ≥44px en móvil**
   - Links de nav móvil: `min-height: 48px; display: flex; align-items: center;`
   - Botones: `min-height: 48px` (50px ideal); FAB 56px; hamburguesa 44×44px; filas del panel WhatsApp 56px; iconos sociales con padding de 12px (área total ≥44px).
   - Separación entre targets contiguos: ≥8px.
4. **Safe areas (iOS notch / home bar)**
   - `bottom: calc(20px + env(safe-area-inset-bottom))` en el FAB.
   - Padding lateral mínimo 16px en todo dispositivo.
5. **Navegación y foco**
   - Al abrir/cerrar el menú móvil: mover foco al primer link y devolverlo al botón al cerrar; `Esc` cierra.
   - Nunca `outline: none` sin sustituto.
   - `scroll-margin-top: 96px` en secciones ancla (compensa nav sticky) — evita que los títulos queden tapados al saltar con `#anchors`.
6. **Rendimiento de imágenes**
   - Hero: `loading="eager"` + `fetchpriority="high"`; resto: `loading="lazy"` + `decoding="async"`.
   - Exportar JPEG/WebP a ≤200KB (hero ≤300KB), ancho máx. 1600px; `srcset` con 480/768/1200w.
7. **Formularios**
   - `inputmode="email"` + `type="email"` + `autocomplete="email"`.
   - Labels visibles o `aria-label`; placeholder nunca como único label.
   - Errores con `aria-live="polite"` y texto + icono (no solo color).
8. **Mapa embebido**
   - `loading="lazy"`, `title` descriptivo, alto fijado por `aspect-ratio` (evita salto de layout); fallback: imagen estática con pin + link "Abrir en Google Maps".
9. **Móvil primero real**
   - Estilos base = 360px; los `@media (min-width: ...)` solo añaden capacidad. Ningún `max-width` de ocultar contenido por defecto (excepto menú hamburguesa).
10. **Contraste sobre fotos**
    - Todo texto superpuesto a imagen: fondo sólido/translúcido (`rgba(40,36,36,.45)`) o `text-shadow` con capa; verificar el par resultante ≥4.5:1 antes de aprobar.

---

## 8. Checklist de entrega (design QA)

- [ ] Todos los pares texto/fondo de §2 verificados en el navegador (extensión de contraste) → 0 fallos AA.
- [ ] Prueba 320 / 360 / 768 / 1024 / 1440 px sin scroll horizontal.
- [ ] Todos los targets táctiles ≥44px medidos en 375px.
- [ ] `:focus-visible` visible en: logo, links nav, CTA, tarjetas, filas WhatsApp, inputs, FAB, galería.
- [ ] Menú hamburguesa operativo con teclado + `Esc` + `aria-expanded`.
- [ ] Imágenes de rostros sin cortes en los 5 breakpoints.
- [ ] `prefers-reduced-motion` desactiva reveals y transforms.
- [ ] FAB WhatsApp no tapa contenido (padding inferior en footer) ni el input de newsletter.
- [ ] Números +58 424-9140219 y +58 424-9305441 visibles como texto en panel **y** footer.
- [ ] Instagram @saga.ve y @sagaformen enlazados con `rel="noopener"`.
