# Template de diapositivas AEPD

Capa visual AEPD construida sobre `template-diapositivas`.

## Responsabilidad de este repositorio

Este repositorio contiene **solo lo que añade la identidad AEPD al motor común**:

- paleta y tokens visuales;
- tipografía y jerarquía;
- cabecera y logotipo;
- márgenes y composición del lienzo;
- layouts AEPD reutilizables;
- ejemplos visuales para crear nuevos decks.

El motor común —Reveal, Notes, Speaker View, contador, galería, lienzo fijo y política de publicación— pertenece a `template-diapositivas` y se copia aquí de forma deliberada para mantener el repositorio autocontenido.

## Estructura

- `index.html`: catálogo de layouts AEPD de ejemplo.
- `style.css`: sistema visual AEPD.
- `assets/aepd-logo.svg`: logotipo local.
- `speaker-gallery.js` y `vendor/reveal/`: copia del motor común.
- `REGRESSIONS.md`: únicamente regresiones específicas de esta capa.

## Uso

1. Crear un repositorio desde este template.
2. Cambiar título y metadatos.
3. Conservar `section.slide-page > .slide-inner`.
4. Elegir solo los layouts necesarios y sustituir su contenido.
5. Añadir notas con `<aside class="notes">...</aside>`.
6. Publicar GitHub Pages desde `main` y `/(root)`.

Las slides de ejemplo son un catálogo, no una obligación. No crear JavaScript para un layout que pueda expresarse con HTML y CSS.

## Identidad visual

Los colores se definen como variables CSS al principio de `style.css`; reutilizar tokens antes de introducir valores sueltos.

El logotipo se sirve localmente desde `assets/aepd-logo.svg`. No depender de recursos remotos para elementos necesarios en presentación.

## Contrato AEPD

- lienzo fijo 1600 × 900;
- una idea dominante por diapositiva;
- texto visible como apoyo, no como sustituto del discurso;
- no convertir las slides en páginas responsive;
- preferir HTML y CSS antes que añadir JavaScript.

## Herencia

Las mejoras del motor genérico se diseñan primero en `template-diapositivas` y, cuando son aplicables, se copian aquí y se validan de nuevo.

Las presentaciones creadas desde esta plantilla son instantáneas autocontenidas: no se actualizan automáticamente cuando cambia el template.

Para regresiones del motor común, consultar `antoniorani/template-diapositivas/REGRESSIONS.md`.
