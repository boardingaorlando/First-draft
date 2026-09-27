# Boarding a Orlando — sitio web

Sitio estático: se publica tal cual, sin instalar nada.

```
index.html    el sitio completo (todas las solapas)
styles.css    estilos
assets/       logo, íconos y fotos
CNAME         dominio boardingaorlando.com
.nojekyll     necesario para GitHub Pages
```

## Publicar en GitHub Pages
1. Subí TODO el contenido de esta carpeta a la raíz del repo (index.html tiene que quedar en la raíz, no dentro de otra carpeta).
2. Settings → Pages → Source: Deploy from a branch → main / (root).
3. Custom domain: boardingaorlando.com.
4. DNS del dominio: registros A → 185.199.108.153, 185.199.109.153, 185.199.110.153, 185.199.111.153 · CNAME de www → <tu-usuario>.github.io
5. Marcá Enforce HTTPS cuando aparezca.

Nota: con el plan gratis de GitHub, Pages solo funciona si el repo es público. Para repo privado necesitás GitHub Pro.

## Fotos pendientes
Subilas a assets/ con el nombre exacto (minúsculas, .jpg; logos .png transparente). Si falta una, se ve el fondo de color.
- Portadas: hero.jpg ✓, grupales.jpg, cruceros.jpg
- inicio/: paquetes, grupales, cruceros, combinados
- instagram/: perfil, 1 a 6
- nosotros/: historia-caro, historia-nacho, orlando, california, paris, tokio, osaka, singapur
- agentes-1.jpg, agentes-2.jpg
- testimonios/: 1 a 3
- grupales/: salida-1, salida-2
- cruceros/: clasico, caribe, halloween, navidad, marvel, galeria-1 a galeria-8
- proveedores/: disney, universal, disney-cruise-line, civitatis, aerolinea-1 a aerolinea-3 (.png)

## Formulario
Conectado a Google Apps Script (Sheets + mail) y protegido con Cloudflare Turnstile. La Secret Key vive solo en Apps Script, nunca en este repo.
