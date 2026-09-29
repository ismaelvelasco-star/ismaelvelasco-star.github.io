---
name: practice-content-writer
description: "Crear o reescribir prácticas de unidad en `docs/section*/uXX/practica*/` con objetivos, pasos, ejercicios y, cuando proceda, solución asociada. Usar cuando se pida redactar una práctica nueva, transformar un enunciado en actividad guiada o completar material práctico existente."
---

# Practice Content Writer

Redactar prácticas accionables y evaluables, alineadas con la teoría del módulo.

Consultar plantilla y reglas en
[references/practice_rules.md](./references/practice_rules.md).

## Workflow
### 1. Preparar la actividad
- Identificar módulo, unidad y alcance de la práctica.
- Verificar si la carpeta real de la sección es `practica/` o `practicas/`.
- Revisar teoría asociada para alinear objetivos y ejercicios.

### 2. Crear el frontmatter
- Incluir `title`, `summary`, `description`, `authors`, `date`, `icon`,
  `permalink`, `categories` y `tags`.
- Usar `icon: "material/file-document-edit"`.

### 3. Redactar la práctica
- Incluir introducción breve y orientada a la tarea.
- Añadir sección de objetivos claros.
- Describir pasos de forma secuencial y verificable.
- Añadir ejercicios finales o ampliaciones cuando tenga sentido.
- Incluir capturas, tablas o código si mejoran la comprensión.

### 4. Preparar materiales asociados
- Si hay plantilla, dataset o recurso auxiliar, guardarlo en `OtrosRecursos/`.
- Si procede, crear un fichero solución con sufijo `-solucion.md` o seguir la
  convención local ya existente.
- Mantener assets visuales en la carpeta `assets/` de la práctica.

## Rules
- La práctica no usa numeración de tema `X.Y` en el nombre del archivo.
- El contenido debe ser operativo, no solo descriptivo.
- Incluir criterios claros para que el alumnado sepa cuándo ha terminado.
- Mantener tono didáctico y lenguaje inclusivo.

## Prompt patterns
- "Crea la práctica de esta unidad."
- "Transforma este enunciado en una práctica guiada."
- "Añade una solución y recursos a esta práctica."
