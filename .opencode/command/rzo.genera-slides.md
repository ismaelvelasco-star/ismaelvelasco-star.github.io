---
description: Genera y enlaza una presentación Reveal.js desde una teoría existente.
agent: slides-content
---

Genera o actualiza las slides Reveal.js asociadas a la teoría indicada:

$ARGUMENTS

Lee antes de actuar `AGENTS.md`, `opencode.json`,
`.opencode/agent/slides-content.md` y las skills que ese agente utiliza. La
configuración del proyecto prevalece sobre cualquier supuesto de este prompt.

Lee la teoría completa antes de diseñar la presentación. Aplica el flujo del
agente `slides-content`:

- Usa `repo-structure-guide` y `naming-conventions-enforcer` para localizar y
  nombrar el destino.
- Usa `reveal-slides-creator` para crear la pareja `.md` y `.html` en la ruta
  `slides/section*-*/` correspondiente.
- Mantén los prefijos reales del módulo (`PR-`, `IS-`, `ED-` o `DAW-`).
- Incluye una progresión didáctica, ejemplos, código comentado, cierre de cada
  bloque y notas del presentador (`Note:`).
- No sobrecargues las slides: usa títulos breves, viñetas claras y un máximo
  aproximado de siete elementos por slide.
- Usa `mermaid-diagram-creator` solo si un diagrama mejora la explicación.
- Usa `slides-linker` para insertar enlaces absolutos en los cuatro puntos
  obligatorios de la documentación.
- Termina con `content-workflow-checklist` y revisa formato, enlaces y pareja
  de archivos.

Si faltan la teoría fuente, la unidad o el destino, pregunta antes de crear
archivos. No dejes una presentación únicamente en `.md` o únicamente en
`.html`.
