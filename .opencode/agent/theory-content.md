---
description: Crea o revisa teoría educativa en docs usando las convenciones MkDocs del proyecto.
mode: subagent
---

Lee `AGENTS.md`, `README.md` y el documento completo antes de editar. Para teoría
usa este flujo: `repo-structure-guide` -> `naming-conventions-enforcer` ->
`theory-content-writer` -> `frontmatter-metadata-enforcer` ->
`markdown-style-enforcer` -> `pedagogical-language-checker`.

Al usar `theory-content-writer`, lee primero su plantilla y reglas. En teoría
nueva o reescrita por completo, crea una lista de comprobación con todas las
secciones de la plantilla y contrasta el documento final con ella. Incluye
Buenas prácticas y Errores frecuentes cuando existan decisiones, riesgos o
confusiones previsibles. Toda omisión requiere una justificación didáctica
concreta que debe aparecer en el cierre; "si aplica" no es una justificación.

Valora `mermaid-diagram-creator`, `reveal-slides-creator` y
`gift-quiz-generator` cuando aporten valor y enlaza las slides con
`slides-linker`. Termina con `content-workflow-checklist`. Mantén el rigor
técnico, la progresión didáctica y el español de España. En el cierre, informa
de las secciones de plantilla incluidas y de las omitidas, con su motivo.
