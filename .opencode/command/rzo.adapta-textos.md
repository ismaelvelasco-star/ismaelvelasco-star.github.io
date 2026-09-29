---
description: Adapta o revisa un texto técnico como teoría didáctica del repositorio.
agent: theory-content
---

Adapta o revisa el texto o archivo indicado como material docente para
alumnado de FP técnica:

$ARGUMENTS

Lee antes de actuar `AGENTS.md`, `opencode.json`,
`.opencode/agent/theory-content.md` y las skills del proyecto que dicho agente
indique. Esas instrucciones son la fuente de verdad para rutas, nombres,
metadatos y validaciones.

Antes de redactar, lee íntegramente
`.opencode/skills/theory-content-writer/templates/theory-document-template.md`
y `.opencode/skills/theory-content-writer/references/theory_rules.md`. Para
una teoría nueva o una reescritura completa, convierte la plantilla en una
lista de comprobación del documento: idea principal, contexto, RA/CE,
objetivos, desarrollo, ejemplos, buenas prácticas, errores frecuentes,
resumen, idea clave, práctica posterior, fuentes y presentación. No omitas
ninguna sección sin una justificación didáctica concreta.

Lee el material completo antes de reescribirlo. Identifica la idea principal,
el objetivo de aprendizaje y los conceptos que necesitan contexto. Conserva el
rigor técnico y el contenido (no pierdas contenido), pero mejora la progresión, la claridad, la narrativa y la
orientación práctica.

Aplica el flujo del agente `theory-content` y utiliza, cuando corresponda,
`repo-structure-guide`, `naming-conventions-enforcer`,
`frontmatter-metadata-enforcer`, `markdown-style-enforcer`,
`pedagogical-language-checker` y `content-workflow-checklist`.

Incluye ejemplos, bloques de código, admonitions o diagramas Mermaid solo
cuando mejoren la comprensión. Comprueba la estructura de teoría, la tabla de
RA y CE según la normativa disponible, las fuentes y los enlaces a slides si
existen. Pregunta por el módulo, unidad, punto o fuente si faltan datos
imprescindibles.

Antes de terminar, contrasta el archivo final sección por sección con la
plantilla. En el cierre, enumera las secciones incluidas y las omitidas; para
cada omisión, explica su justificación didáctica. "Si aplica" no es una
justificación suficiente.
