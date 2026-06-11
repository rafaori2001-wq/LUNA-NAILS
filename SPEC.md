# SPEC — Landing "Lune Nails · Cádiz"

Especificación para construir una landing de demostración de un sistema de reservas
con confirmación automática por WhatsApp. Negocio ficticio (nail studio).
Esta página es una herramienta de venta: se enseñará en vivo desde el móvil
de una clienta potencial (dueña de nail studio). Debe parecer real y profesional.

---

## 1. Objetivo de la página

Un único trabajo: **que la visitante reserve una cita**.
Todo lo demás (servicios, horario, ubicación) existe solo para dar confianza
antes de reservar.

Audiencia real de la demo: dueñas de nail studios y centros de estética en Cádiz.
La página debe parecer la web de un negocio real del sector, no una plantilla.

---

## 2. Restricciones técnicas (NO negociables)

- **HTML + CSS + JavaScript vanilla.** Sin frameworks, sin build step, sin npm.
- Máximo 3 ficheros: `index.html`, `styles.css`, `script.js`.
  Si cabe limpio en un solo `index.html`, mejor.
- **Mobile-first.** Se diseña primero para 375px. El desktop es la adaptación.
  La demo se hará siempre desde un móvil.
- Peso total < 500 KB. Sin imágenes externas pesadas: usar fondos CSS,
  gradientes suaves y SVG inline.
- Tipografías de Google Fonts: máximo 2 familias, con `display=swap`.
- Sin cookies, sin analytics, sin banners de consentimiento.
- Accesibilidad mínima: contraste AA, focus visible, `prefers-reduced-motion`
  respetado.
- Debe funcionar abriendo `index.html` en local Y desplegada en Cloudflare Pages
  sin cambios.

---

## 3. Identidad y dirección de diseño

**Concepto:** nail studio gaditano contemporáneo. Limpio, luminoso, con un punto
de distinción que no caiga en el rosa-chicle genérico del sector.
Referencia estética: estudio de fotografía minimalista, no spa de lujo ni
salón de uñas americano.

### Paleta (usar exactamente estos valores)

| Token            | Hex       | Uso                                                        |
|------------------|-----------|------------------------------------------------------------|
| `--blanco`       | `#FAFAF8` | Fondo principal (blanco cálido, no frío)                   |
| `--negro-suave`  | `#1A1A1A` | Texto principal                                            |
| `--arena`        | `#E8E0D5` | Fondo de secciones alternas, tarjetas                      |
| `--acento`       | `#B8956A` | Acento ÚNICO: botones CTA, detalles, líneas. Usar con moderación. Tostado cálido, no dorado ni rosa. |
| `--gris-texto`   | `#6B6B6B` | Texto secundario, precios en tarjetas                      |

Prohibido: fondo rosa, lila, o cualquier color típico de "spa".
El acento `--acento` es el único color que no es neutro: usarlo solo en CTAs,
un detalle decorativo y hover de enlaces. En ningún sitio más.

### Tipografía

- **Display (titulares):** "Cormorant Garamond" (Google Fonts), peso 500-600,
  con tracking normal-amplio. Solo para H1, H2 y el logo. Da elegancia sin
  ser recargado.
- **Cuerpo y UI:** "DM Sans", pesos 400 y 500. Limpio, moderno, legible en móvil.
- Escala: H1 ~clamp(2.4rem, 9vw, 4.2rem); cuerpo 1rem/1.7.

### Elemento firma

Un **punto lunar**: un círculo perfecto pequeño (~8px) en `--acento` que aparece
junto al logo y se repite como separador entre secciones (en lugar de líneas
horizontales). Es el único elemento decorativo recurrente. Simple, coherente,
y nada que ver con lo que haría una plantilla genérica.

---

## 4. Estructura y contenido (textos definitivos, usar tal cual)

### 4.1 Header (fijo, compacto)
- Logo texto: "LUNE" en display + "· nails cádiz" en DM Sans pequeño al lado.
- Punto lunar junto al logo.
- Botón-enlace a la derecha: **"Reservar"** (ancla a #reservar).
- Fondo: `--blanco` con sombra muy sutil al hacer scroll.

### 4.2 Hero
- Fondo `--blanco`.
- H1: **"Uñas que duran. Cita en un minuto."**
- Subtítulo: "Reserva el servicio que quieras y recibe la confirmación
  en tu WhatsApp al instante. Sin llamadas, sin esperas."
- Botón primario (relleno `--acento`): **"Reservar cita"** → ancla a #reservar.
- Botón secundario (solo borde, color `--negro-suave`): **"Ver servicios"**
  → ancla a #servicios.
- Debajo, tres micro-badges en línea (icono check + texto pequeño):
  - "Confirmación por WhatsApp"
  - "Recordatorio el día antes"
  - "Sin necesidad de llamar"

### 4.3 Servicios (#servicios) — fondo `--arena`
Título de sección: **"Servicios"**

Seis tarjetas simples (nombre, duración, precio):

| Servicio               | Duración | Precio |
|------------------------|----------|--------|
| Manicura gel           | 60 min   | 28 €   |
| Pedicura gel           | 75 min   | 32 €   |
| Uñas acrílicas         | 90 min   | 45 €   |
| Nail art (diseño)      | 30 min   | 15 €   |
| Retirada de gel        | 30 min   | 12 €   |
| Manicura express       | 30 min   | 14 €   |

Cada tarjeta lleva un botón/enlace "Reservar" que ancla a #reservar.

### 4.4 Cómo funciona — fondo `--blanco`
Título: **"Reservar es muy sencillo"**

Tres pasos en horizontal (vertical en móvil). Numerados porque es una
secuencia real:

1. **Elige tu servicio** — "Selecciona el servicio, el día y la hora que
   mejor te vienen."
2. **WhatsApp al instante** — "En menos de un minuto recibes la confirmación
   directamente en tu WhatsApp."
3. **Te avisamos el día antes** — "Te enviamos un recordatorio automático
   24 h antes de tu cita para que no se te pase."

En el paso 2, incluir un mock minimalista de burbuja de chat en CSS puro
(fondo `--arena`, texto en `--negro-suave`, sin logos oficiales de WhatsApp):
> "✓✓ Hola Lucía, tu cita en Lune Nails está confirmada para el viernes
> 14 a las 17:00. ¡Te esperamos 🤍"

### 4.5 Reserva (#reservar) — fondo `--arena`
Título: **"Reserva tu cita"**
Subtítulo: "Recibirás la confirmación en tu WhatsApp en menos de un minuto."

Formulario Tally embebido:

```html
<iframe data-tally-src="https://tally.so/embed/XXXXXX?hideTitle=1&transparentBackground=1"
        loading="lazy" width="100%" height="500" frameborder="0"
        title="Reserva tu cita en Lune Nails"></iframe>
<script src="https://tally.so/widgets/embed.js" async></script>
```

> NOTA: usar el placeholder `XXXXXX`. El ID real se sustituirá después.
> Altura suficiente para evitar doble scroll en móvil.

### 4.6 Ubicación y horario — fondo `--blanco`
- Dirección ficticia: "Calle Ancha, 24 · 11001 Cádiz"
- En lugar de mapa embebido: botón "Cómo llegar" que abre
  `https://maps.google.com/?q=Calle+Ancha+24+Cádiz`
- Horario:
  - Lunes a viernes: 10:00 – 14:00 / 16:30 – 20:00
  - Sábado: 10:00 – 15:00
  - Domingo: Cerrado
- Instagram ficticio: "@lunenails.cadiz" (enlace a `https://instagram.com`,
  sin ancla real).

### 4.7 Footer — fondo `--negro-suave`
- "Lune Nails · Cádiz" en blanco + botón "Reservar cita".
- Texto pequeño en `--gris-texto` claro:
  "Página de demostración — sistema de reservas con confirmación automática
  por WhatsApp."

---

## 5. Comportamiento

- Scroll suave en todos los enlaces ancla.
- Header fijo que añade sombra suave al hacer scroll (JS, degradable:
  si no hay JS las anclas funcionan igualmente).
- Sin parallax, sin animaciones de scroll, sin efectos por sección.
- Transiciones de hover: 150ms ease en botones y tarjetas. Nada más.
- La página debe ser completamente funcional sin JavaScript.

---

## 6. Criterios de aceptación

1. En móvil de 375px no hay scroll horizontal en ninguna sección.
2. El botón "Reservar cita" del hero es visible sin hacer scroll (above the fold)
   en móvil.
3. Lighthouse móvil: Performance ≥ 90, Accessibility ≥ 90.
4. Funciona sin JavaScript (anclas y formulario operativos, solo se pierden
   header dinámico y micro-animaciones).
5. Todos los textos son exactamente los de esta especificación. Cero lorem ipsum.
6. Peso total < 500 KB. Carga < 2 s en conexión 4G simulada.
7. El mock de burbuja WhatsApp no incluye ningún logo oficial de WhatsApp
   (solo texto y estilo CSS).

---

## 7. Despliegue

1. Repositorio Git con commit inicial al terminar.
2. Push a GitHub (rama `main`).
3. Conectar repo a Cloudflare Pages: build command vacío, output directorio raíz.
4. Verificar la URL `*.pages.dev` en un móvil real.
