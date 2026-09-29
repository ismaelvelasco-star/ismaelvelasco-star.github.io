---
name: markdown-style-enforcer
description: "Aplicar y verificar las convenciones Markdown y MkDocs Material de este repositorio educativo. Usar cuando haya que corregir jerarquía de encabezados, listas, admonitions, figuras, bloques de código, citas, separadores o consistencia visual de teoría y práctica."
---

# Markdown Style Enforcer

Normalizar la sintaxis Markdown para que el contenido sea consistente y
renderice bien en MkDocs.

Consultar ejemplos y reglas en
[references/markdown_rules.md](./references/markdown_rules.md).

## Workflow
### 1. Detectar el tipo de documento
- Diferenciar entre teoría, práctica y slides.
- Aplicar reglas de teoría/práctica aquí.
- Delegar reglas de slides a `reveal-slides-creator`.

### 2. Revisar estructura
- Verificar encabezados y profundidad.
- Eliminar separadores innecesarios.
- Mantener bloques de contenido legibles y estables.

### 3. Revisar elementos Markdown
- Listas con indentación de 4 espacios al anidar.
- Admonitions bien formadas.
- Figuras con `<figure markdown>` y `figcaption`.
- Bloques de código con lenguaje explícito.
- Citas en bloque cuando resalten ideas clave.
- Revisar numeración de secciones y subsecciones.

### 4. Revisar consistencia
- No usar emoticonos.
- No mezclar estilos incompatibles dentro del mismo documento.
- Mantener referencias a `assets/` y `OtrosRecursos/` correctas.

## Prompt patterns
- "Revisa el Markdown de este archivo."
- "Corrige formato, listas y admonitions."
- "Haz que este documento siga el estilo del repositorio."
