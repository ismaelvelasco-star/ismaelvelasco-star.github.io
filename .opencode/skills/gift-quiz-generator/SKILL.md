---
name: gift-quiz-generator
description: "Generar bancos de preguntas en formato GIFT a partir de documentos de teoría de este repositorio. Usar cuando se pida crear o actualizar archivos `docs/section*/uXX/gift/*.gift` con preguntas de opción múltiple, feedback formativo y orientación práctica."
---

# Gift Quiz Generator

Convertir teoría en cuestionarios GIFT pedagógicos y técnicamente válidos, como un experto en diseño de evaluaciones con 20 años de experiencia creando preguntas para certificaciones internacionales en la temática a la que va orientada los test, con distractores "imposibles de descartar" 

Consultar y seguir las reglas y plantilla en
[references/gift_rules.md](./references/gift_rules.md).

## Workflow
### 1. Analizar la teoría
- Leer el archivo o archivos de teoría completos.
- Identificar conceptos clave, definiciones y situaciones prácticas basadas en supuestos prácticos realistas.
- Cubrir el contenido sin dejar bloques importantes fuera.

### 2. Diseñar el banco de preguntas
- Crear al menos 15 preguntas por archivo, salvo que se indique el número de preguntas a generar. 
- Priorizar supuestos prácticos y aplicación real del contenido.
- Añadir una parte menor de preguntas de definición teórica solo si aportan valor.

### 3. Redactar en formato GIFT
- Usar 4 opciones y una sola correcta que deberá ser la primera.
- Hacer que las respuestas incorrectas (distractores) sean plausibles.
- Añadir feedback formativo y específico en todas las opciones.
- Mantener tono claro, cercano y formalmente correcto.

### 4. Validar sintaxis
- Conservar la sintaxis estructural de GIFT.
- Escapar como literales los caracteres conflictivos dentro de textos y feedback cuando proceda.
- Guardar el archivo en `gift/` con el mismo nombre base que la teoría.

## Prompt patterns
- "Genera el GIFT de este tema."
- "Crea un cuestionario de 15 preguntas a partir de esta teoría."
- "Actualiza este banco GIFT con mejores distractores."
