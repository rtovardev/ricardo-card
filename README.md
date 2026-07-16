# Ricardo Tovar — Tarjeta digital (Perfil Oportunidad)

Landing mobile-first para la tarjeta NFC / QR de Ricardo Tovar, co-fundador de MART Automations. Plantilla clonada de la tarjeta de Álvaro Monagas; mismo look, datos propios.

- **Stack:** HTML + CSS + JS puro. Sin build, sin backend.
- **Deploy target:** Vercel (static).
- **Tamaño hero:** columna 440px en mobile, centrada con sombra en desktop.
- **Idiomas:** ES (default) / EN (toggle arriba a la derecha, persistido en `localStorage`).

## Estructura

```
.
├── index.html         # Página única
├── assets/
│   ├── ricardo.jpg    # Foto hero (1000×1500, ~330KB)
│   └── mart-logo.png  # Logo footer (607×452, transparente)
├── vercel.json        # Cache de assets + headers de seguridad
└── .gitignore
```

## Personalizar

Toda la info editable está en el bloque `PROFILE` y `I18N` dentro de `<script>` en `index.html`. Una sola fuente de verdad que alimenta la página, los botones y el `.vcf` que se descarga al tocar **Guardar contacto**.

### Cambiar la foto del hero
1. Optimiza la nueva imagen: vertical 3:4 (ej. 1000×1500), JPEG q≈80, ≤500KB.
   ```bash
   sips -s format jpeg -s formatOptions 80 -Z 1500 ruta/a/nueva.jpg --out assets/ricardo.jpg
   ```
2. Commit + push. Vercel redespliega automático.

### Cambiar datos de contacto
Edita el objeto `PROFILE` en `index.html`:
- `email` → aparece en el botón Email y en el vCard
- `phone` → solo dígitos con código de país, sin `+` (ej. `"50762428646"`)
- `linkedin`, `github`, `website`

### Cambiar la bio
Edita los campos `bio` dentro de `I18N.es` y `I18N.en` en el mismo `<script>`.

## Deploy en Vercel

### Opción A — Dashboard (recomendado, 1 minuto)
1. Ir a [vercel.com/new](https://vercel.com/new).
2. **Import Git Repository** → seleccionar `rtovardev/ricardo-card`.
3. Framework Preset: **Other**. Build command: vacío. Output directory: vacío (raíz).
4. Click **Deploy**. URL por defecto: `https://ricardo-card.vercel.app`.
5. (Opcional) **Settings → Domains** para conectar `ricardotovar.com` o un subdominio custom.

### Opción B — CLI
```bash
npm i -g vercel
cd ~/ricardo-card
vercel login     # una sola vez
vercel --prod    # primer deploy
```

## Características

- ✅ Mobile-first, 100vh hero, scroll suave a la sección de contacto.
- ✅ Botón **Guardar contacto** descarga un `.vcf` con todos los datos (compatible con iOS/Android).
- ✅ Botones directos: WhatsApp, Email, Llamar.
- ✅ Links: LinkedIn, GitHub, sitio de MART.
- ✅ Toggle ES/EN con detección automática del idioma del navegador y memoria en `localStorage`.
- ✅ Reveal animations + shimmer del nombre (respeta `prefers-reduced-motion`).
- ✅ Open Graph + theme color + favicon SVG inline.
- ✅ Headers de seguridad y cache de assets vía `vercel.json`.

## Licencia

Privado — uso personal de Ricardo Tovar / MART Automations.
