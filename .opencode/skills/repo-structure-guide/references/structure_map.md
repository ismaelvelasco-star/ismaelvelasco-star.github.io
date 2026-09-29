# Mapa estructural del repositorio

## Árbol esencial

```text
docs/
  sectionX/
    index.md        # Índice del módulo
    recursos/       # Normativa del módulo
    uXX/
      index.md      # Índice de la unidad
      teoria/       # Teoría de la unidad
      practica/     # Prácticas de la unidad
      gift/         # Exámenes tipo test

slides/
  section1-pr/
  section2-is/
  section3-ed/
  section4-daw/
```

## Reglas de ubicación

- Crear teoría en `docs/sectionX/uXX/teoria/`.
- Crear práctica en la carpeta ya usada por esa sección:
  - `practica/` en la mayoría de módulos.
- Crear GIFT en `docs/sectionX/uXX/gift/`.
- Crear slides en la carpeta de módulo de `slides/`.
- Guardar imágenes y multimedia en `assets/`.
- Guardar plantillas, PDFs y ficheros de apoyo en `OtrosRecursos/`.

## Prefijos reales del repositorio

| Sección | Prefijo en docs | Prefijo en slides |
| --- | --- | --- |
| `section1` | `PROG-` | `PR-` |
| `section2` | `IS-` | `IS-` |
| `section3` | `EDES-` | `ED-` |
| `section4` | `DAW-` | `DAW-` |

## Referencias reales útiles

- Teoría: `docs/section1/u09/teoria/PROG-U9.2.-JDBC-1.md`
- Práctica: `docs/section1/u09/practica/PROG-U9.-Practica001.md`
- Slides: `slides/section2-is/IS-U2.1.1.-TaxonomiaDeIncidentes.md`
- GIFT: `docs/section2/u02/gift/IS-U2.4.1.-DocumentacionDeIncidentes.gift`
