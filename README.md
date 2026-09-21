# Boarding a Orlando — sitio web

Landing estática. Sin build, sin dependencias, sin npm. Se publica tal cual.

```
index.html      la página completa
styles.css      tokens del sistema de diseño + layout + componentes
assets/
  logo-badge.png
  icons/*.svg   36 íconos (Lucide, licencia ISC)
CNAME           dominio personalizado de GitHub Pages
.nojekyll       evita que Pages procese el sitio con Jekyll
```

## Ver en local

Abrí `index.html` en el navegador. O, para que todo cargue igual que en producción:

```bash
python3 -m http.server 8000   # luego http://localhost:8000
```

## Publicar en GitHub Pages

1. Subí estos archivos a la **raíz** del repo (o a `/docs`).
2. Settings → Pages → Source: *Deploy from a branch* → `main` / `/ (root)`.
3. Custom domain: `boardingaorlando.com` (el archivo `CNAME` ya lo declara).
4. En el DNS del dominio, apuntá:
   - `A` → `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - `CNAME` de `www` → `boardingaorlando.github.io`
5. Marcá *Enforce HTTPS* cuando GitHub emita el certificado (puede tardar unos minutos).

## Qué falta reemplazar antes de salir al aire

Está todo marcado con texto visible o comentarios en el HTML.

| Qué | Dónde |
| --- | --- |
| Número de WhatsApp | todos los `href="#cotizar"` → `https://wa.me/598XXXXXXXX?text=Hola,%20quiero%20cotizar%20mi%20viaje%20a%20Orlando` |
| Precios, nombres e inclusiones de paquetes | sección `#paquetes` |
| Estadísticas (+1.200 familias, 9 años, 20+ viajes, 4,9) | sección `#nosotros` |
| Testimonios | sección `#testimonios` — nombres reales solo con permiso |
| Respuestas del FAQ | sección `#faq` — cada cifra la tienen que confirmar Caro y Nacho |
| Contacto, ciudad y redes | `footer` |
| Fotos | cada `.photo-slot` es un degradado con etiqueta; reemplazar por `<img>` o `background-image` |
| Ciudad de salida del itinerario | dice `BOG → MCO`; si los viajeros salen de Uruguay va `MVD → MCO` |

## Formulario

Hoy es **maqueta**: no envía nada, solo muestra el mensaje de éxito. Para activarlo hay tres caminos, de menor a mayor trabajo:

- **WhatsApp** — en el `submit`, armar el texto y abrir `https://wa.me/...?text=...`. Cero backend.
- **Formspree / Basin** — cambiar `<form id="quote-form">` por `<form action="https://formspree.io/f/XXXX" method="POST">` y borrar el `preventDefault`.
- **Google Sheets** — Apps Script publicado como Web App y un `fetch` en el `submit`.

## Tipografías

Baloo 2 y Nunito se cargan desde Google Fonts (el `@import` arriba de `styles.css`). Es la única dependencia externa del sitio. Son **sustitutas**: cuando lleguen las tipografías reales de la marca, se reemplaza ese `@import` por reglas `@font-face` locales y se actualizan `--font-display` y `--font-body`.

## Nota legal

El pie incluye la línea de no afiliación porque el logo lleva imaginería tipo Disney. Conviene que un abogado revise el logo y la redacción antes de operar comercialmente.
