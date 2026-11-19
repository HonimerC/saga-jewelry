# SAGA Jewelry — Página de inicio

Landing page responsiva para **SAGA Jewelry** (joyería contemporánea de Maturín, Venezuela).

- **Stack:** HTML + CSS + JavaScript puro (sin dependencias ni build)
- **Tipografías:** Playfair Display + DM Sans (Google Fonts)
- **Imágenes:** WebP optimizado (activos ~890 KB en total)
- **Diseño:** sistema de diseño propio en [`diseno-spec.md`](diseno-spec.md)

## Estructura

```
index.html        ← la página completa (CSS y JS incluidos)
assets/           ← imágenes WebP + favicon
diseno-spec.md    ← paleta, tipografía, breakpoints y reglas de accesibilidad
```

## Funcionalidades

- Menú móvil accesible (hamburguesa, Escape, foco gestionado)
- Botón flotante de WhatsApp con los dos números de las sedes
- Dos sedes con mapa (Google Maps): C.C. Servimas Monterrey y Sector Centro
- Modal "Catálogo en construcción"
- Animaciones de entrada y aparición al hacer scroll (respetan `prefers-reduced-motion`)
- Accesibilidad: contraste WCAG AA, skip-link, ARIA, navegación por teclado

## Ver localmente

```bash
python -m http.server 8080
# abrir http://127.0.0.1:8080
```

## Publicar

GitHub Pages: *Settings → Pages → Source: rama `main`, carpeta `/`*.
