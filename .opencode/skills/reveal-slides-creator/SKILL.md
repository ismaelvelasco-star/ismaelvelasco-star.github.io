---
name: reveal-slides-creator
description: "Crear presentaciones Reveal.js a partir de documentos de teoría de este repositorio educativo, respetando las reglas de AGENTS.md. Usar cuando se pida generar o actualizar slides (`slides/section*-*/MODULO-UX.Y.-Tema.md` y `.html`) desde archivos de teoría (`docs/section*/uXX/teoria/*.md`), incluyendo formato estricto de slides, notas del presentador y enlazado obligatorio en 4 ubicaciones de `docs`."
---

# Reveal Slides Creator

Generar presentaciones Reveal.js didácticas desde teoría, manteniendo coherencia de
nomenclatura, estructura y enlaces del repositorio.

Consultar reglas detalladas y plantillas en [references/reveal_slides_rules.md](./references/reveal_slides_rules.md).

## Workflow
### 1. Localizar entradas y salidas
- Identificar archivo de teoría origen (`docs/sectionX/uYY/teoria/MODULO-UX.Y.-Tema.md`).
- Determinar módulo de slides:
  - `section1` -> `slides/section1-pr` y prefijo `PR-`
  - `section2` -> `slides/section2-is` y prefijo `IS-`
  - `section3` -> `slides/section3-ed` y prefijo `ED-`
  - `section4` -> `slides/section4-daw` y prefijo `DAW-`
- Mantener nombre base del archivo para `.md` y `.html`.

### 2. Analizar teoría completa
- Leer el documento de teoría completo antes de redactar slides.
- Extraer todos los epígrafes numerados (1, 1.1, 1.1.1, etc.).
- Crear secciones de slides por grandes bloques conceptuales.
- No omitir contenido: cubrir todo el documento origen.
- Hacer una lista de recursos a incorporar en cada punto: imágenes, diagramas, código fuente.
- Si la teoría contiene una imagen que aporta comprensión, copiarla a
  `slides/section*-*/assets/` y enlazarla desde la diapositiva correspondiente.
  No enlazar assets de `docs/` desde las slides ni sustituir una imagen útil por
  una descripción textual.

### 3. Generar archivo de slides Markdown (`.md`)
- Escribir en español de España, tono didáctico y cercano.
- Respetar estas reglas duras:
  - Usar `#` para título principal.
  - Usar `##` para inicio de sección.
  - Usar `###` para cada slide de contenido.
  - Usar `---` solo para separar secciones.
  - Separar slides de la misma sección con exactamente 2 líneas en blanco.
  - No usar `---` ni dobles saltos para otros fines.
  - Limitar a máximo 7 viñetas por slide.
  - Limitar líneas de contenido a 80 caracteres.
- Añadir notas en todas las slides:
  - Dejar una línea en blanco tras contenido.
  - Escribir `Note: ...` compactadas a una sola línea física por slide para que Reveal las interprete bien.
  - Las notas están redactadas como guion de voz docente.
  - Resaltar en las notas aquellas `**ideas clave en negrita**`. 
  - Hacer notas completas para que el profesorado tenga una guía de lo que tiene que decir en cada slide.
- Si un punto necesita varias slides, repetir título con romanos `I`, `II`, `III`.

### 4. Generar HTML Reveal.js (`.html`)
- Basar el HTML en la plantilla Reveal del repositorio.
- Mantener rutas relativas desde carpeta de módulo:
  - `../dist/...`
  - `../plugin/...`
  - `../custom.css`
  - `assets/...` para recursos del propio módulo
- Incluir configuración mínima en `Reveal.initialize()`:
  - `margin: 0.1`
  - `progress: true`
  - `slideNumber: 'c/t'`
  - `showSlideNumber: 'all'`

### 5. Enlazar la presentación en documentación (4 puntos obligatorios)
- Actualizar teoría con sección `## Presentación` entre bibliografía y recursos.
- Actualizar `docs/sectionX/uYY/index.md` en `### Presentaciones`.
- Actualizar `docs/sectionX/index.md` en lista de presentaciones del módulo.
- Actualizar `docs/index.md` en el bloque del módulo y unidad correspondiente.
- Usar siempre URL absoluta:
  - `https://revilofe.github.io/slides/sectionN-xx/MODULO-UX.Y.-Tema.html`

### 6. Validar antes de terminar
- Verificar que existe par `.md` y `.html` con mismo nombre base.
- Verificar reglas de separadores (`---` y dos líneas en blanco).
- Verificar presencia de `Note:` en todas las slides.
- Verificar enlaces en los 4 documentos obligatorios.
- Verificar coherencia de prefijo de módulo (`PR`, `IS`, `ED`, `DAW`).
- Verificar que cada imagen reutilizada desde teoría existe en los assets de
  slides y usa una ruta relativa `assets/...`.

## Definition of Done
- Slides `.md` y `.html` generadas en la carpeta correcta de `slides/`.
- Contenido teórico cubierto sin omisiones.
- Formato Reveal y notas del presentador válidos.
- Enlaces añadidos/actualizados en los 4 puntos de `docs/`.
- Nomenclatura y URLs absolutas correctas.

## Prompt patterns that should trigger this skill
- "Genera slides de la unidad X.Y a partir de este archivo de teoría."
- "Crea la presentación Reveal.js para `docs/section4/u03/teoria/...`."
- "Actualiza la presentación y enlázala en toda la documentación."
