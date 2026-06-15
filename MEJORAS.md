# Ronda de mejoras — Landing Lune Nails

Instrucciones para Claude Code. Aplicar todos los cambios manteniendo las
restricciones del SPEC original (vanilla HTML/CSS/JS, mobile-first, sin frameworks,
paleta y tipografías intactas).

---

## 1. PRIORITARIO — Arreglar el scroll del formulario Tally

El iframe de Tally muestra un scroll interno (doble scroll) en móvil, lo que
perjudica la usabilidad. Objetivo: que el formulario se vea completo sin scroll
dentro del recuadro.

Implementación recomendada: usar el script de redimensionado automático de Tally,
que ajusta la altura del iframe al contenido real.

- Asegurar que el iframe NO tiene un `height` fijo pequeño.
- Usar el embed con auto-resize de Tally. El script `https://tally.so/widgets/embed.js`
  ya detecta el iframe con atributo `data-tally-src` y ajusta la altura
  automáticamente si el iframe tiene `data-tally-src` (no `src` directo).
- Verificar que el atributo es `data-tally-src` y que el script de embed está
  cargado al final del body.
- Como fallback, si el auto-resize no dispara, fijar una altura mínima generosa
  (`min-height: 650px` en móvil) para que no aparezca scroll interno con los
  5 campos del formulario.

Criterio: en móvil de 375px, el formulario completo (5 campos + botón) es visible
haciendo solo scroll de la página, nunca scroll dentro del recuadro.

---

## 2. Imágenes (de Unsplash/Pexels, optimizadas)

Añadir imágenes reales de calidad, pocas y bien elegidas. NO llenar la página.
Todas en formato WebP, comprimidas, con `loading="lazy"` excepto la del hero.
Todas con `alt` descriptivo.

### 2.1 Hero
Añadir UNA imagen de fondo o lateral en el hero:
- En móvil: imagen sutil de fondo con overlay claro (`--blanco` al 75-85% de opacidad)
  para que el texto del H1 siga siendo perfectamente legible. El texto manda,
  la imagen acompaña.
- En desktop: imagen a un lado (split hero) o de fondo con el mismo overlay.
- Temática: manicura elegante, manos cuidadas, tonos neutros que combinen con
  la paleta (nada de colores chillones que choquen con el tostado `--acento`).
- Buscar en Unsplash términos como "manicure neutral", "nails minimal",
  "manicure hands beige". Elegir una que tenga tonos arena/neutros, NO rosa fuerte.

### 2.2 Sección servicios
Opcional y solo si queda elegante: una imagen pequeña por encima del título
"Servicios" como banda separadora, o ninguna. Si genera ruido visual, omitir.
Prioridad baja.

### 2.3 Footer o sección "cómo funciona"
NO añadir imágenes aquí. Mantener limpio.

> IMPORTANTE: descargar las imágenes y servirlas desde el propio proyecto
> (carpeta `/img`), NO enlazar en caliente a Unsplash (puede caerse o cambiar).
> Convertir a WebP y comprimir para mantener el peso total < 600 KB.

---

## 3. Retoques visuales

### 3.1 Header (desktop)
En desktop hay demasiado espacio vacío entre el logo y el botón "Reservar".
Aplicar un `max-width` al contenido del header (ej. 1100px) centrado, con
`justify-content: space-between`, para que no se separen tanto en pantallas anchas.

### 3.2 Hero (desktop)
Reducir el padding inferior del hero o subir la siguiente sección: ahora mismo
queda demasiado espacio en blanco bajo los badges antes de la sección de servicios.
En móvil está bien, ajustar solo desktop.

### 3.3 Espaciado general
Revisar que el espaciado vertical entre secciones sea consistente (mismo padding
arriba/abajo en todas). Que respire pero sin huecos enormes.

### 3.4 Tarjetas de servicios
Verificar que en móvil las 6 tarjetas tienen separación suficiente entre ellas
y que el precio queda bien alineado a la derecha sin pegarse al borde.

---

## 4. Verificación final (mismos criterios del SPEC)

1. Móvil 375px: sin scroll horizontal en ninguna sección.
2. Formulario visible sin scroll interno del iframe.
3. Botón "Reservar cita" del hero above the fold en móvil.
4. Peso total < 600 KB (subió el límite por las imágenes).
5. Lighthouse móvil: Performance ≥ 85, Accessibility ≥ 90.
6. El texto del hero sigue siendo perfectamente legible sobre la imagen.

Al terminar: commit y push a GitHub (se redespliega solo).
