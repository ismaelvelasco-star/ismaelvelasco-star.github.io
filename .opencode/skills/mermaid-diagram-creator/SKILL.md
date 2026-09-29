---
name: mermaid-diagram-creator
description: "Crear diagramas Mermaid didácticos y válidos para teoría, prácticas y slides de este repositorio, incluyendo diagramas UML y diagramas explicativos. Usar cuando haya que representar flujos, clases, secuencias, estados, relaciones o procesos en documentos de Programación, Entornos de desarrollo y módulos afines."
---

# Mermaid Diagram Creator

Generar diagramas Mermaid claros, robustos y compatibles con MkDocs Material.

Consultar reglas, sintaxis segura y plantillas en
[references/mermaid_rules.md](./references/mermaid_rules.md).

## Workflow
### 1. Elegir el tipo de diagrama
- `flowchart` para procesos, decisiones y explicaciones paso a paso.
- `classDiagram` para UML de clases y relaciones estructurales.
- `sequenceDiagram` para interacción temporal entre actores u objetos.
- `stateDiagram-v2` para estados y transiciones.
- Otros tipos solo si aportan claridad y el repositorio ya los soporta.

### 2. Diseñar el contenido
- Reducir el diagrama a las relaciones o pasos clave.
- Evitar saturar un único diagrama con demasiada información.
- Usar texto breve y pedagógico en nodos y relaciones.
- Si el contenido es complejo, dividirlo en dos diagramas.

### 3. Redactar en Mermaid seguro
- Usar siempre bloques ` ```mermaid `.
- Poner etiquetas entre comillas si contienen caracteres problemáticos.
- No usar `\n` dentro de etiquetas.
- Usar `<br/>` para saltos de línea dentro de nodos.
- En aristas con texto, preferir `-->|Sí|` y `-->|No|`.

### 4. Adaptar al contexto educativo
- En teoría, usar diagramas para ejemplificar conceptos y relaciones.
- En prácticas, usar diagramas para apoyar el análisis o el enunciado.
- En slides, simplificar al máximo para que se lean en proyección.
- En UML, priorizar claridad sobre exhaustividad formal si el objetivo es
  didáctico.

## Rules
- Mantener el diagrama autocontenido y entendible sin leer todo el tema.
- Nombrar actores, clases o estados con términos del propio módulo.
- Evitar etiquetas largas sin necesidad.
- Si Mermaid falla con `Syntax error in text`, revisar primero comillas y
  saltos de línea.

## Coordination
- Usar `markdown-style-enforcer` para revisar el bloque Markdown final.
- Usar `theory-content-writer` o `reveal-slides-creator` para integrar el
  diagrama dentro del contenido.

## Prompt patterns
- "Crea un diagrama Mermaid para explicar este proceso."
- "Genera un UML de clases en Mermaid para este ejemplo."
- "Necesito un diagrama de secuencia o de estados para esta explicación."
