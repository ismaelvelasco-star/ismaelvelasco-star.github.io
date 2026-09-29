---
name: theory-content-writer
description: "Crear o reescribir documentos de teoría en `docs/section*/uXX/teoria/*.md` para este repositorio educativo. Usar cuando se pida redactar teoría nueva, ampliar una unidad, adaptar apuntes externos al formato MkDocs o convertir borradores en material didáctico para alumnado."
---

# Theory Content Writer

Redactar teoría clara, progresiva y alineada con la estructura real del
repositorio.

Consultar plantilla y reglas detalladas en
- [Plantilla base para documentos de teoría](./templates/theory-document-template.md).
- [References/theory_rules.md](./references/theory_rules.md).

Usa `./templates/theory-document-template.md` como esqueleto base
para nuevas teorías o reescrituras completas. Antes de editar, compárala con
el documento y prepara una lista de las secciones que se incluirán. La
plantilla puede adaptarse cuando el tema, el módulo o la progresión didáctica
lo requieran, pero no se puede omitir una sección sin una justificación
didáctica concreta registrada en el cierre.

## Workflow
### 1. Preparar contexto
- Identificar módulo, unidad y tema.
- Revisar teoría vecina de la misma unidad para mantener continuidad.
- Si existe normativa o recurso base del módulo, usarlo como marco de contenido.
- hacer referencia literal a normativa relacionada en la introducción y dejar constancia del RA y CE trabajados en formato tabla.

### 2. Crear el frontmatter
- Incluir siempre `title`, `description`, `summary`, `authors`, `date`,
  `icon`, `permalink`, `categories` y `tags`.
- Usar `icon: "material/file-document-outline"`.
- Mantener categorías y permalink coherentes con el módulo.

### 3. Redactar el cuerpo
- Abrir con una introducción que explique contexto y objetivo.
- Identificar Resultado de aprendizaje y criterios de evaluación trabajados y dejar constancia.
- Desarrollar de lo simple a lo complejo.
- Incluir ejemplos, imágenes, definiciones y bloques de código cuando aporten
  valor.
- Mantener jerarquía de encabezados coherente con el documento existente.
- Evitar separadores `---` dentro de teoría.
- En reescrituras completas, incluir las secciones de **Buenas prácticas** y
  **Errores frecuentes** cuando el contenido técnico presente decisiones,
  riesgos o confusiones previsibles. Si no aplican, justificarlo expresamente
  en el cierre.
- Incluir **Para seguir practicando** cuando exista una práctica, actividad o
  recurso relacionado. Si no existe o no procede, indicarlo en el cierre.

### 4. Añadir elementos didácticos
- Usar admonitions para resaltar ideas clave.
- Incluir listas con indentación limpia de 4 espacios al anidar.
- Añadir figuras con `<figure markdown>` y `figcaption` cuando haya apoyo
  visual.
- Introducir ejemplos prácticos orientados a alumnado de FP, con código o casos reales.

### 5. Integrar el documento
- Si ya existe slide asociada, añadir sección `## Presentación`.
- Si no existe, valorar si hay que crearla con `reveal-slides-creator`.
- Revisar navegación y enlaces internos si el documento es nuevo.

## Coordination
- Usar `frontmatter-metadata-enforcer` para validar YAML final.
- Usar `markdown-style-enforcer` para ajustar sintaxis MkDocs.
- Usar `pedagogical-language-checker` para revisar tono y claridad.

## Prompt patterns
- "Crea el tema de teoría de la unidad."
- "Convierte estos apuntes en un documento MkDocs."
- "Amplía este archivo de teoría con ejemplos y mejor estructura."

## Checklist 
- Confirmar ruta con repo-structure-guide.
- Confirmar nombre con naming-conventions-enforcer.
- Consultar docs/sectionX/recursos/{{normativa}} para asociar RA y CE reales.
- Mantener frontmatter compatible con MkDocs Material.
- Usar español de España y lenguaje inclusivo.
- Mantener una progresión: contexto -> definición -> ejemplo -> aplicación -> resumen.
- Antes de cerrar, contrastar el documento final con
  `templates/theory-document-template.md`, sección por sección.
- Confirmar de forma explícita: idea principal, contexto, RA/CE, objetivos,
  desarrollo, ejemplos, buenas prácticas, errores frecuentes, resumen, idea
  clave, práctica posterior, fuentes y presentación.
- Documentar en el cierre toda sección de plantilla omitida y su justificación
  didáctica; no usar "si aplica" como motivo suficiente.
- Usar admonitions solo cuando aporten valor didáctico.
- Si hay imágenes, guardarlas en assets/ y usar alt text y figcaption.
- Si el tema requiere slides, GIFT o entrada en mkdocs.yml, indicarlo en el cierre del flujo.
