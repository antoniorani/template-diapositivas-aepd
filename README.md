# Template de diapositivas AEPD

Plantilla autocontenida para crear presentaciones web con la identidad visual usada en las presentaciones AEPD.

Está construida sobre `template-diapositivas`, pero añade un sistema visual específico: paleta, tipografía, márgenes, cabecera con logotipo, composiciones reutilizables y ejemplos de layouts.

## Principios

- **Lienzo fijo 1600 × 900.** Reveal.js escala la diapositiva completa; el contenido no hace reflow en móvil.
- **Una idea principal por diapositiva.** El diseño favorece mensajes breves y jerarquía visual.
- **Sin build.** No hay npm, bundler ni framework.
- **Dependencias críticas locales.** Reveal.js y Speaker View viven en `vendor/reveal/`.
- **Personalización separada.** La galería del presentador vive en `speaker-gallery.js`; no se modifica `vendor/reveal/notes.js`.
- **Contenido y diseño separados.** `index.html` contiene las slides y `style.css` contiene el lenguaje visual.

## Estructura

- `index.html`: ejemplos de layouts y configuración de Reveal.js.
- `style.css`: tokens visuales y componentes AEPD.
- `speaker-gallery.js`: galería de todas las diapositivas en Speaker View.
- `assets/`: recursos visuales locales, incluido el logotipo AEPD.
- `vendor/reveal/`: Reveal.js 6.0.1 y plugin de notas.
- `REGRESSIONS.md`: fallos reales que no deben repetirse.

## Empezar una nueva presentación

1. Crea un repositorio nuevo a partir de esta plantilla.
2. Cambia título y metadatos en `index.html`.
3. Conserva la estructura exterior de cada slide: `section.slide-page > .slide-inner`.
4. Elige uno de los layouts de ejemplo y sustituye el contenido.
5. Añade las notas dentro de cada slide con `<aside class="notes">...</aside>`.
6. Publica con GitHub Pages.

No es necesario conservar todas las slides de ejemplo. Están aquí como catálogo visual para copiar únicamente las composiciones que hagan falta.

## Layouts incluidos

- **Portada**: título, subtítulo y bloque de contexto.
- **Idea + tres bloques**: mensaje principal con tres fuentes, argumentos o líneas de trabajo.
- **Dato destacado**: cifra o indicador protagonista con explicación.
- **Comparación**: dos bloques paralelos para opciones, entidades o enfoques.
- **Proceso**: cuatro pasos secuenciales.
- **Timeline**: cinco hitos sobre una línea temporal.
- **Decisión / mensaje clave**: llamada principal con contexto y conclusión.
- **Cierre**: slide final sencilla.

Las clases son semánticas y reutilizables; no crees un componente JavaScript para un layout que pueda expresarse con HTML y CSS.

## Speaker View

Pulsa **S** para abrir la vista del presentador en una ventana independiente.

Dentro de Speaker View:

- **G** o **Todas las diapositivas**: abre la galería.
- Flechas: recorrer miniaturas.
- Enter o Espacio: ir a la seleccionada.
- Esc: volver a las notas.

## Contrato de renderizado

La presentación se diseña siempre sobre un lienzo de **1600 × 900**.

La configuración base debe conservar:

```js
width: 1600,
height: 900,
margin: 0,
minScale: 0.1,
maxScale: 10,
scrollActivationWidth: null
```

No uses `@media (max-width: ...)` para reorganizar slides. En una pantalla pequeña debe verse exactamente la misma composición, solo escalada.

Los media queries de accesibilidad como `prefers-reduced-motion` sí son válidos porque no alteran la geometría.

## Identidad visual

Los colores están definidos como variables CSS al principio de `style.css`. Evita introducir colores sueltos si ya existe un token equivalente.

El logotipo AEPD se sirve localmente desde `assets/aepd-logo.svg`, usando el fichero proporcionado para la plantilla. La presentación no depende de la web de AEPD durante su ejecución. Mantén este fichero sin modificaciones visuales y conserva la misma ruta en los decks derivados.

## Antes de simplificar

Consulta `REGRESSIONS.md`. Un despliegue de GitHub Pages correcto no garantiza que la presentación funcione en navegador: cualquier cambio en scripts, CSS, plugins o rutas críticas debe validarse también abriendo la URL publicada.

## Relación con el motor y las presentaciones derivadas

Esta plantilla es una **copia autocontenida** del motor de `template-diapositivas` más el sistema visual AEPD. No existe una dependencia en tiempo de ejecución entre ambos repositorios.

Política de actualización:

1. Las mejoras del motor común —Reveal.js, configuración base, Speaker View, galería o reglas de renderizado— se evalúan primero en `template-diapositivas`.
2. Cuando una mejora del motor sea útil para AEPD, se incorpora aquí de forma deliberada y se valida de nuevo.
3. La identidad visual AEPD —paleta, logo, márgenes, tipografía y layouts— evoluciona en este repositorio.
4. Las nuevas presentaciones AEPD se crean a partir de esta plantilla y quedan como **instantáneas autocontenidas**.
5. Las presentaciones ya creadas no se sincronizan automáticamente con esta plantilla. Solo se trasladan cambios cuando exista una necesidad concreta, especialmente correcciones importantes o de fiabilidad.

No uses submódulos, CDN ni paquetes remotos únicamente para compartir estos archivos. La pequeña duplicación del motor es intencionada: prioriza que cada presentación pueda ejecutarse por sí sola.
