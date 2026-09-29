---
name: frontmatter-metadata-enforcer
description: "Validar, completar o corregir el frontmatter YAML de documentos educativos de este repositorio. Usar cuando se editen archivos de teoría o práctica y haya que asegurar campos obligatorios, iconos correctos, permalink coherente y metadatos consistentes."
---

# Frontmatter Metadata Enforcer

Garantizar que teoría y práctica tengan metadatos completos y coherentes.

Consultar reglas exactas en
[references/frontmatter_rules.md](./references/frontmatter_rules.md).

## Workflow
### 1. Detectar tipo de documento
- Distinguir entre teoría y práctica.
- Identificar módulo, unidad y tipo de permalink esperado.

### 2. Verificar campos obligatorios
- `title`
- `description`
- `summary`
- `authors`
- `date`
- `icon`
- `permalink`
- `categories`
- `tags`

### 3. Aplicar reglas por tipo
- Teoría: `icon: "material/file-document-outline"`.
- Práctica: `icon: "material/file-document-edit"`.
- `categories` y `tags` deben ser listas YAML válidas.
- `authors` debe mantenerse como lista.

### 4. Validar coherencia
- La fecha debe ir en formato `YYYY-MM-DD`.
- El permalink debe corresponder a módulo, unidad y tipo de documento.
- El título debe reflejar unidad, punto o práctica.

## Prompt patterns
- "Corrige el frontmatter de este archivo."
- "Faltan metadatos en esta teoría."
- "Comprueba si este YAML cumple la convención del repo."
