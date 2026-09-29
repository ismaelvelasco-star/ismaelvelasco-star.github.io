---
name: naming-conventions-enforcer
description: "Validar y corregir nombres de archivos, carpetas y prefijos del repositorio educativo. Usar cuando se creen o renombren documentos de teoría, práctica, GIFT, slides, assets o rutas de unidad y haya que comprobar que siguen la convención real del proyecto."
---

# Naming Conventions Enforcer

Evitar incoherencias de nombres antes de crear o enlazar contenido.

Consultar el detalle en
[references/naming_rules.md](./references/naming_rules.md).

## Workflow
### 1. Identificar familia de archivos
- Teoría
- Práctica
- GIFT
- Slides
- Carpetas de unidad o recursos

### 2. Aplicar prefijo correcto
- Usar el prefijo real del módulo en `docs/`.
- Usar el prefijo real del módulo en `slides/`.
- Si hay discrepancia histórica, seguir el patrón ya usado en esa carpeta.

### 3. Validar forma del nombre
- Teoría: `MODULO-UX.Y.-Tema.md`
- Práctica: `MODULO-UX.-PracticaYYY.md`
- GIFT: mismo nombre base que la teoría
- Slides: mismo nombre base en `.md` y `.html`

### 4. Validar carpeta
- Unidad como `uXX`
- Teoría en `teoria/`
- Práctica en `practica/` o `practicas/`
- Recursos en `OtrosRecursos/`
- Assets en `assets/`

## Prompt patterns
- "¿Este nombre es correcto?"
- "Renombra estos archivos según la convención."
- "Comprueba la nomenclatura de esta unidad."
