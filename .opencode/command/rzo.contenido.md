---
description: Ejecuta el flujo editorial completo para una tarea de contenido.
agent: editorial-workflow
---

Coordina esta tarea editorial:

$ARGUMENTS

Lee antes de actuar `AGENTS.md`, `opencode.json` y
`.opencode/agent/editorial-workflow.md`. Usa las skills y los agentes que ese
flujo indique como fuente de verdad para la estructura, la nomenclatura, los
metadatos, el estilo y las validaciones.

Determina si la tarea afecta a teoría, prácticas, slides, GIFT o a una unidad
completa. Revisa también la integración con `mkdocs.yml`, los enlaces, los
assets, la normativa y los RA/CE cuando corresponda. No hagas migraciones
implícitas y termina con `content-workflow-checklist`.
