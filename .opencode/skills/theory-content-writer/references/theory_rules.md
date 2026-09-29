# Reglas para documentos de teoría

## Frontmatter obligatorio

```yaml
---
title: "UD X - X.Y Título del tema"
description: Breve descripción
summary: Resumen corto
authors:
    - Eduardo Fdez
date: YYYY-MM-DD
icon: "material/file-document-outline"
permalink: /modulo/unidadX/X.Y
categories:
    - MODULO
tags:
    - Tag1
    - Tag2
---
```
## Estructura recomendada

- Introducción breve con contexto y objetivo.
- Desarrollo en secciones y subsecciones numeradas.
- Los bloques con pasos numerados deben ser claros y concisos, con ejemplos prácticos y código cuando sea relevante. El código irá identado y en bloque, con el lenguaje de programación indicado.
- Ejemplos prácticos, definiciones y código cuando ayuden.
- Resumen, idea clave, buenas prácticas, errores frecuentes y práctica
  posterior cuando exista material relacionado.
- Cierre con bibliografía, presentación y recursos si aplica.

## Auditoría obligatoria de plantilla

En toda teoría nueva o reescritura completa, revisar
`templates/theory-document-template.md` antes de editar y contrastar el
resultado final con ella antes de cerrar. Deben constar explícitamente estas
comprobaciones: idea principal, contexto, RA/CE, objetivos, desarrollo,
ejemplos, buenas prácticas, errores frecuentes, resumen, idea clave, para
seguir practicando, fuentes y presentación.

Una sección solo puede omitirse si existe una justificación didáctica concreta.
Registrar esa justificación en el cierre de la tarea. La expresión "si aplica"
no basta por sí sola para omitirla.

## Referencia a normativa

Durante la introducción, hacer una introdución y luego referencia a la normativa que esta relacionada con el contenido del documento.

La referencia literal a la normativa se hará en formato tabla, e incluirá el resultado de aprendizaje y los criterios de evaluación trabajados el contenido del documento.

```markdown
---

| Código | Descripción                                     |
|--------|-------------------------------------------------|
| RAX    | {Descripción del resultado de aprendizaje X}    |
| CE y   | {Descripción del criterio de evaluación y}      |
| CE y   | {Descripción del criterio de evaluación z}      |

```

## Reglas duras

- No usar `---` para separar bloques de teoría.
- Mantener indentación de 4 espacios en listas anidadas.
- Usar admonitions MkDocs para resaltar información importante.
- Usar figuras con `figcaption` para imágenes relevantes.
- Redactar en español de España, tono didáctico e inclusivo.

## Referencia a plantilla 

Usa la siguiente plantilla como esqueleto base para nuevas teorías o reescrituras completas. La plantilla orienta la estructura común del repositorio, pero no es un formato rígido: puede adaptarse cuando el tema, el módulo o la progresión didáctica lo requieran.

[theory-document-template.md](../templates/theory-document-template.md)
