---
name: slides-linker
description: "Añadir o corregir enlaces a una presentación Reveal.js dentro de la documentación del repositorio. Usar cuando exista una slide nueva o modificada y haya que actualizar teoría, índice de unidad, índice de módulo e índice principal con URLs absolutas."
---

# Slides Linker

Actualizar de forma consistente los 4 puntos de acceso a una presentación.

Consultar reglas y ejemplos en
[references/linking_rules.md](./references/linking_rules.md).

## Workflow
### 1. Identificar la presentación
- Confirmar archivo `.html` final y carpeta de `slides/`.
- Derivar la URL absoluta pública correspondiente.

### 2. Actualizar teoría
- Añadir `## Presentación` al final del documento de teoría.
- Insertarla después de `## Referencias y bibliografía` y antes de
  `## Recursos adicionales`.

### 3. Actualizar índices
- Añadir el enlace en `docs/sectionX/uXX/index.md` dentro de
  `### Presentaciones`.
- Añadir el enlace en `docs/sectionX/index.md` dentro del bloque de
  presentaciones del módulo.
- Añadir el enlace en `docs/index.md` dentro del módulo y unidad
  correspondientes.

### 4. Verificar
- Reemplazar `Por definir` si era el marcador anterior.
- Usar siempre URL absoluta.
- Revisar que el texto visible del enlace sea consistente con el título.

## Prompt patterns
- "Enlaza esta presentación en la documentación."
- "Falta añadir la slide en los 4 sitios."
- "Corrige los enlaces de esta presentación."
