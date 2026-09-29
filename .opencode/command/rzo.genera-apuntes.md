---
description: Genera un documento nuevo de teoría siguiendo las convenciones del repositorio.
agent: theory-content
---

Genera apuntes nuevos sobre el tema indicado:

$ARGUMENTS

Lee antes de actuar `AGENTS.md`, `opencode.json`,
`.opencode/agent/theory-content.md` y las skills que ese agente utiliza. No
supongas rutas, prefijos ni metadatos: confirma la configuración en esos
documentos y en los archivos vecinos de la unidad.

Antes de editar, confirma o deduce de forma segura el módulo, la sección, la
unidad, el punto, la ruta de destino y el material reutilizable. Si falta
información imprescindible, pregunta antes de crear archivos. Durante la regeneración, no pierdas contenidos salvo que se indique explícitamente, o consideres que existe un error, o está duplicado. 

Sigue el flujo del agente `theory-content`:

- Localiza la estructura con `repo-structure-guide`.
- Valida nombres con `naming-conventions-enforcer`.
- Redacta con `theory-content-writer`.
- Revisa frontmatter con `frontmatter-metadata-enforcer`.
- Aplica `markdown-style-enforcer` y `pedagogical-language-checker`.
- Usa `mermaid-diagram-creator` cuando aporte valor.
- Valora slides y GIFT asociados, enlazando las slides con `slides-linker` si
  se crean.
- Termina con `content-workflow-checklist`.

Redacta en español de España, con progresión de lo sencillo a lo complejo,
objetivos claros, ejemplos técnicos y una conclusión. Relaciona el tema con
RA y CE cuando exista normativa aplicable. Indica al final qué materiales
asociados conviene generar.
