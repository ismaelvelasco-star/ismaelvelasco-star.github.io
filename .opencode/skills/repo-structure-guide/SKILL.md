---
name: repo-structure-guide
description: "Ubicar correctamente archivos, carpetas, assets y recursos dentro de este repositorio educativo MkDocs + Reveal.js. Usar cuando haya que decidir dónde crear o mover teoría, prácticas, gifts, slides, assets, soluciones, recursos de unidad o cambios en `mkdocs.yml`."
---

# Repo Structure Guide

Determinar la ubicación correcta del contenido antes de escribir nada.

Consultar el mapa y las excepciones del repositorio en
[references/structure_map.md](./references/structure_map.md).

## Workflow
### 1. Identificar tipo de contenido
- Distinguir entre teoría, práctica, gift, slides, assets o recurso auxiliar.
- Distinguir si la acción afecta a una unidad, a un módulo o al índice general.

### 2. Localizar módulo y unidad
- Mapear `section1` a Programación.
- Mapear `section2` a Incidentes de seguridad.
- Mapear `section3` a Entornos de desarrollo.
- Mapear `section4` a Despliegue de aplicaciones web.
- Si la tarea es por unidad, usar siempre `uXX`.

### 3. Resolver destino exacto
- Teoría: `docs/sectionX/uXX/teoria/`.
- Práctica: `docs/sectionX/uXX/practica/`.
- GIFT: `docs/sectionX/uXX/gift/`.
- Slides: `slides/sectionY-zz/`.
- Assets de teoría o práctica: carpeta `assets/` del propio contenido.
- Recursos auxiliares: carpeta `OtrosRecursos/` del bloque correspondiente.

### 4. Verificar impactos laterales
- Si se crea teoría nueva, revisar si hay que añadir práctica, slides y gift.
- Si se crea slide nueva, revisar enlazado en `docs/`.
- Si se crea contenido navegable, revisar `mkdocs.yml`.

## Rules
- Preservar la estructura real del repositorio por encima de recomendaciones
  genéricas.
- No inventar carpetas nuevas si ya existe una convención local válida.
- Mantener `assets/` y `OtrosRecursos/` junto al contenido que los usa.
- Mantener independencia por módulo en `slides/section*-*/assets/`.

## Prompt patterns
- "¿Dónde debería ir este archivo?"
- "Crea la estructura de una unidad nueva."
- "Localiza donde va esta práctica."
- "Añade assets y recursos a la unidad correcta."
