---
description: Genera o revisa preguntas GIFT con distractores plausibles y feedback formativo.
agent: gift-quiz-content
---

Genera o revisa un cuestionario GIFT a partir de la teoría indicada:

$ARGUMENTS

Lee antes de actuar `AGENTS.md`, `opencode.json`,
`.opencode/agent/gift-quiz-content.md` y las skills que ese agente utiliza.
Lee la teoría completa y aplica el flujo del agente `gift-quiz-content`.
Usa `repo-structure-guide` y `naming-conventions-enforcer` para localizar y
nombrar el archivo, y `gift-quiz-generator` para elaborar las preguntas.
Termina con `markdown-style-enforcer` y `content-workflow-checklist`.

Las preguntas deben estar en español de España, tener dificultad media-alta
para FP de especialización y evaluar comprensión o aplicación, no solo
memoria. Formula tres distractores plausibles basados en errores habituales,
sin pistas formales ni respuestas absurdas. Incluye feedback formativo para la
respuesta correcta y para cada distractor, y verifica que el formato GIFT sea
válido y que las respuestas estén justificadas por la teoría.
