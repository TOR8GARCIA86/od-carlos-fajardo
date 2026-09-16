# Entrega Técnica — Sitio Web OD. Carlos Fajardo · Clínica SIMEB

> Documento preparado por Hat Agencia para el programador que tomará el proyecto.
> Fecha: Septiembre 2026

---

## 1. Repositorio y URL

| Item | Valor |
|------|-------|
| **Repositorio GitHub** | `https://github.com/TOR8GARCIA86/od-carlos-fajardo` |
| **GitHub Pages (staging)** | `https://tor8garcia86.github.io/od-carlos-fajardo/` |
| **Dominio final** | `https://odcarlosfajardo.com/` (pendiente apuntar) |
| **Rama principal** | `main` |

---

## 2. Estructura del proyecto

```
od-carlos-fajardo/
├── index.html          ← Sitio completo (todo en un solo archivo HTML/CSS/JS)
├── gracias.html        ← Página de confirmación post-formulario
├── robots.txt          ← SEO: permite todo, apunta al sitemap
├── sitemap.xml         ← SEO: URL canónica del sitio
└── assets/             ← Imágenes (ver sección 4)
```

El sitio **no usa frameworks ni dependencias npm**. Es HTML/CSS/JS puro.
Todo el código está dentro de `index.html`.

---

## 3. Tareas pendientes — OBLIGATORIAS antes de salir a producción

### 3.1 Conectar el formulario de contacto (Web3Forms)

1. Ir a **[web3forms.com](https://web3forms.com)**
2. Crear cuenta con el correo: `administracion@odcarlosfajardo.com`
3. Obtener el **Access Key**
4. En `index.html`, buscar la línea:
   ```html
   <input type="hidden" name="access_key" value="WEB3FORMS_ACCESS_KEY">
   ```
5. Reemplazar `WEB3FORMS_ACCESS_KEY` con la clave real

El formulario ya tiene:
- Honeypot antispam (`name="botcheck"`)
- Validación de campos
- Redirección automática a `gracias.html` al enviar
- Evento DataLayer `lead_form_submitted` para GTM

---

### 3.2 Conectar Google Tag Manager

1. Crear (o usar el existente) contenedor en **[tagmanager.google.com](https://tagmanager.google.com)**
2. Copiar el ID del contenedor (formato: `GTM-XXXXXXX`)
3. Buscar y reemplazar **todas** las apariciones de `GTM-XXXXXX` (son 4 en total):
   - `index.html` — 2 apariciones (script head + noscript body)
   - `gracias.html` — 2 apariciones (script head + noscript body)

Con GTM se pueden configurar:
- Google Analytics 4
- Meta Pixel (Facebook Ads)
- Conversiones de Google Ads
- Los eventos ya están disparando desde el código: `lead_form_submitted`, `click_whatsapp`, `gracias_page_view`

---

### 3.3 Apuntar el dominio a GitHub Pages

1. En el panel del registrador de dominio (`odcarlosfajardo.com`), crear registros DNS:
   ```
   A     @    185.199.108.153
   A     @    185.199.109.153
   A     @    185.199.110.153
   A     @    185.199.111.153
   CNAME www  tor8garcia86.github.io
   ```
2. En GitHub → Settings del repo → Pages → Custom domain → escribir `odcarlosfajardo.com`
3. Activar **Enforce HTTPS**

Una vez el dominio esté activo, el `sitemap.xml` ya apunta a `https://odcarlosfajardo.com/` y el `robots.txt` también.

---

### 3.4 Indexación en Google Search Console

1. Ir a **[search.google.com/search-console](https://search.google.com/search-console)**
2. Agregar propiedad con el dominio `odcarlosfajardo.com`
3. Verificar vía DNS (método recomendado con el registrador)
4. Enviar el sitemap: `https://odcarlosfajardo.com/sitemap.xml`

---

## 4. Assets — Mapa de imágenes

### Imágenes activas en el sitio (las que usa `index.html`)

| Archivo en `assets/` | Sección donde se usa |
|----------------------|----------------------|
| `hero-portada-pc.jpg` | Hero desktop |
| `hero-portada-movil.jpg` | Hero móvil |
| `Director.jpg` | Sección Director |
| `Carlos especialista.jpg` | Sección Director |
| `Clinica-fachada.jpeg` | Sección Clínica |
| `Clinica.jpg` | Sección Clínica |
| `P510_Front_PS.jpg` | Galería equipos (Programat P510) |
| `PrograMill-PM7-Ivoclar.jpg` | Galería equipos (PrograMill PM7) |
| `Programat-S2-Ivoclar.jpg` | Galería equipos (Programat S2) |
| `IPS-emax-ceramico.jpg` | Galería equipos (IPS e.max) |
| `IPS-emax-ZirCAD-Prim.jpg` | Galería equipos (IPS e.max ZirCAD) |
| `IPS-emax-ZirCAD-Prime-Esthetic.jpg` | Galería equipos |
| `TRIOS-Core-3Shape.jpg` | Galería equipos (TRIOS 3Shape) |
| `Empress.jpg` | Galería equipos (IPS Empress) |
| `caso1-antes.jpg` | Casos — Caso 1 Antes |
| `caso1-proceso.jpg` | Casos — Caso 1 Proceso |
| `caso1-despues.jpg` | Casos — Caso 1 Después |
| `caso2-antes.jpg` | Casos — Caso 2 Antes |
| `caso2-proceso.jpg` | Casos — Caso 2 Proceso |
| `caso2-despues.jpg` | Casos — Caso 2 Después |
| `LOGO Full blanco.png` | Logo footer |
| `LOGO ODC_blanco.png` | Logo nav |
| `Od Insta.jpg` | Sección Instagram / CTA |

### Archivos en `assets/` que NO están en el sitio (archivos de trabajo / originales)

Estos pueden archivarse o eliminarse cuando el programador lo considere:

- `*.psd` — Archivos fuente de Photoshop (Casos.psd, Director.psd, Galeria.psd, etc.)
- `DirectorV1.jpg` / `DirectorV1.psd` — Versión anterior del Director
- `Dr Fajardo *.jpg` — Versiones anteriores del hero
- `Dr-Fajardo-hero-pc.jpg` / `Dr-Fajardo-hero-movil.jpg` — Hero anterior
- `Caso 1 Antes.png`, `Caso 2 Antes_.png`, etc. — Originales con espacios (las copias renombradas sin espacios son las activas)
- `Foto de portada.jpg` / `Foto de portada.psd` — Original de la foto hero
- `Hero1.png` — Descartado
- `Perfil Carlos F.jpg` — No usado actualmente

---

## 5. Paleta de marca

| Token | Hex | Uso |
|-------|-----|-----|
| `--gold` | `#C4A05B` | Acentos, botones principales, highlights |
| `--black` | `#1D1D1B` | Fondo principal |
| `--cream` | `#F5E3D8` | Secciones claras |
| `--wine` | `#8F1913` | Acentos secundarios, etiqueta "Después" |

---

## 6. Tipografías

Cargadas desde Google Fonts (ya incluidas en el `<head>`):

- **Cormorant Garamond** — Títulos y display (serif elegante)
- **Jost** — Cuerpo de texto, botones, etiquetas (sans-serif limpio)

---

## 7. Contacto del cliente

| | |
|-|-|
| **Clínica** | SIMEB — Salud Integral Médica Estética de Bogotá |
| **Doctor** | OD. Carlos Eduardo Fajardo Escolar |
| **Correo admin** | `administracion@odcarlosfajardo.com` |
| **WhatsApp** | Ya configurado en el botón flotante del sitio |

---

## 8. Notas técnicas importantes

- El sitio **no tiene backend**. El formulario usa Web3Forms (servicio externo gratuito).
- Los eventos de conversión se disparan vía **DataLayer → GTM** (no directamente a GA4 o Meta Pixel; eso se configura dentro de GTM).
- El campo `name="botcheck"` en el formulario es el **honeypot antispam** — no eliminarlo.
- Las imágenes de equipos están en un **filmstrip horizontal con scroll** en móvil.
- El contador de estadísticas usa `IntersectionObserver` con threshold `0.1` para activarse en móvil al hacer scroll.
- El Schema.org (JSON-LD) ya está configurado para Dentist + Person en el `<head>`.
- `gracias.html` tiene `<meta name="robots" content="noindex">` para que Google no la indexe.
