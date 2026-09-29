# Reglas Markdown del repositorio

## Encabezados

- En teoría y práctica, mantener una jerarquía clara.
- Seguir la estructura ya usada por el archivo vecino cuando exista.
- Usar `###`, `####`, `#####` para secciones internas según profundidad.

## Listas

- Mantener 4 espacios en listas anidadas.
- Dejar líneas en blanco cuando la anidación lo necesite para claridad.
- Evitar anidar más de 3 niveles para no perder legibilidad.
- Usar bullets `-` para listas no numeradas y números `1.` para listas ordenadas.

## Numeración de unidades y secciones, subsecciones 
- Usar `## X.Y Titulo` para el titulo principal del documento.
- Usar `### Z. Punto` para cada sección de contenido. 
- Usar `#### Z.W. Punto` para subsecciones dentro de cada sección de contenido.
- Usar `##### Z.W.V. Punto` para subsecciones dentro de cada subsección de contenido, si es necesario.
- Mantener la numeración coherente con el módulo y la unidad a la que pertenece el documento.
- Usar `##` para  `Fuentes y referencias` y `Presentación` si el documento tiene slide asociada.

## Elementos obligatorios o recomendados

- Admonitions MkDocs:
  - `note`
  - `warning`
  - `tip`
  - `quote`
  - `success`
  - `example`
  - `info`
  - `danger`
  - `question`
  - `abstract`
  - `definition`
- Figuras con `figcaption`.
- Bloques de código con lenguaje explícito.
- Citas en bloque para definiciones o ideas clave.

## Reglas duras

- No usar `---` para separar bloques de teoría o práctica.
- No usar emoticonos.
- Mantener referencias a imágenes con rutas correctas.
- En slides, las reglas de separadores viven en `reveal-slides-creator`.
