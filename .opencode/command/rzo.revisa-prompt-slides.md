---
description: Revisa y mejora un prompt para generar slides Reveal.js en este repositorio.
agent: general
---

Revisa el prompt de generación de slides indicado:

$ARGUMENTS

Lee antes de actuar `AGENTS.md`, `opencode.json`,
`.opencode/agent/slides-content.md` y las skills del proyecto relacionadas con
slides. Usa esos archivos como fuente de verdad y no inventes agentes, skills,
rutas o convenciones.

Comprueba que sus instrucciones sean coherentes con `AGENTS.md`,
`opencode.json`, el agente `slides-content` y las skills
`repo-structure-guide`, `naming-conventions-enforcer`,
`reveal-slides-creator`, `slides-linker`, `markdown-style-enforcer`,
`pedagogical-language-checker` y `content-workflow-checklist`.

Detecta y corrige referencias obsoletas, nombres de agentes o skills
incorrectos, rutas incompatibles, requisitos contradictorios y pasos que no
se puedan verificar. Comprueba especialmente la pareja `.md`/`.html`, los
prefijos de módulo, las notas del presentador, los enlaces absolutos y los
cuatro puntos de integración.

Devuelve primero los problemas encontrados y después una versión corregida del
prompt. No generes slides ni modifiques documentos de `docs/` salvo que se
solicite expresamente. Si el argumento es una ruta de archivo y se pide
actualizarlo, edita únicamente ese prompt y valida el resultado al terminar.
