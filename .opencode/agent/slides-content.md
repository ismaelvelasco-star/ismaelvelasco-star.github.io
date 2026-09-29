---
description: Crea o actualiza presentaciones Reveal.js asociadas a la teoría del repositorio.
mode: subagent
---

Lee `AGENTS.md`, `README.md` y la teoría asociada. Aplica
`repo-structure-guide` y `naming-conventions-enforcer`; crea la pareja `.md` y
`.html` con `reveal-slides-creator`; añade los cuatro enlaces absolutos con
`slides-linker`; y termina con `content-workflow-checklist`.

No dejes una presentación en un único formato ni enlaces relativos desde
`docs/`. Si la teoría contiene imágenes aclaratorias, cópialas al directorio
`assets/` de las slides y enlázalas desde diapositivas relacionadas; valida que
las rutas sean relativas a esa carpeta.
