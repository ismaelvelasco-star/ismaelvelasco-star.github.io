---
title: "UD {{unidad}} - {{codigo_apartado}} {{titulo}}"
description: "{{descripcion_breve}}"
summary: "{{resumen_didactico}}"
authors:
    - {{autor}}
date: {{fecha_yyyy_mm_dd}}
icon: "material/file-document-outline"
permalink: /{{modulo_slug}}/unidad-{{unidad}}/{{permalink_slug}}
categories:
    - "{{categoria}}"
tags:
    - "{{tag_principal}}"
    - "{{tag_secundario}}"
---

## {{codigo_apartado}}. {{titulo}}

!!! abstract "Idea principal"
    {{idea_principal_en_2_o_3_lineas}}

{{introduccion_contextual}}

El objetivo de este tema no es memorizar definiciones aisladas, sino entender
{{proposito_de_aprendizaje}} y saber aplicarlo en situaciones cercanas al
trabajo real.

| Codigo | Descripcion |
|--------|-------------|
| {{RA}} | {{descriptor_RA}} |
| {{CE}} | {{descriptor_CE}} |

!!! info "Que deberias saber al terminar"
    Al acabar este tema deberias poder:

    - {{resultado_aprendizaje_1}};
    - {{resultado_aprendizaje_2}};
    - {{resultado_aprendizaje_3}}.

!!! tip "Mapa del tema"
    En este documento vamos a seguir esta secuencia:

    1. {{bloque_1}};
    2. {{bloque_2}};
    3. {{bloque_3}};
    4. {{bloque_4}}.

### 1. {{primer_concepto_o_contexto}}

{{explicacion_progresiva_del_primer_bloque}}

!!! definition "Definicion"
    {{definicion_clara_y_breve}}

{{desarrollo_con_ejemplo_cercano}}

!!! example "Ejemplo"
    {{ejemplo_aplicado}}

### 2. {{segundo_bloque}}

{{explicacion_del_segundo_bloque}}

| Concepto | Para que sirve | Ejemplo |
|----------|----------------|---------|
| {{concepto_1}} | {{uso_1}} | {{ejemplo_1}} |
| {{concepto_2}} | {{uso_2}} | {{ejemplo_2}} |
| {{concepto_3}} | {{uso_3}} | {{ejemplo_3}} |

!!! note "Aclaracion"
    {{matiz_importante_para_evitar_confusiones}}

### 3. {{tercer_bloque}}

{{explicacion_del_tercer_bloque}}

```{{lenguaje_opcional}}
{{ejemplo_codigo_comando_configuracion_o_pseudocodigo}}
```

{{explicacion_del_ejemplo}}

### 4. {{cuarto_bloque_o_aplicacion_practica}}

{{explicacion_aplicada}}

!!! warning "Atencion"
    {{error_frecuente_o_riesgo_que_el_alumnado_debe_evitar}}

<figure markdown="span">
  ![{{texto_alternativo}}](assets/{{nombre_asset}})
  <figcaption>{{pie_de_figura}}</figcaption>
</figure>

### 5. {{quinto_bloque_o_aplicacion_practica}}

{{Lista de pasos, instrucciones o recomendaciones para aplicar el concepto}}

1. {{nombre_del_paso_1}}: {{explicacion_del_paso_1}}

    ```java
    {{codigo_fuente_java}}
   
    ```

2. {{nombre_del_paso_2}}: {{explicacion_del_paso_2}}

    ```bash
    {{codigo_bash}}
    
    ```

3. {{nombre_del_paso_3}}: {{explicacion_del_paso_3}}

    ```r
    {{codigo_bytecode}}
       
    ```

4. {{nombre_del_paso_4}}: {{explicacion_del_paso_4}}

    ```python
    {{codigo_python}}
   
    ```
{{Cierre_del_bloque_5_con_recomendaciones_o_instrucciones}}

### 6. Buenas prácticas

Para trabajar este contenido con criterio, conviene aplicar estas buenas
practicas:

- **{{buena_practica_1}}**: {{explicacion_1}}.
- **{{buena_practica_2}}**: {{explicacion_2}}.
- **{{buena_practica_3}}**: {{explicacion_3}}.

### 7. Errores frecuentes

| Error frecuente | Por que ocurre | Como evitarlo |
|-----------------|----------------|---------------|
| {{error_1}} | {{causa_1}} | {{prevencion_1}} |
| {{error_2}} | {{causa_2}} | {{prevencion_2}} |
| {{error_3}} | {{causa_3}} | {{prevencion_3}} |

### 8. Resumen

En este tema has aprendido que:

- {{resumen_1}};
- {{resumen_2}};
- {{resumen_3}}.

!!! success "Idea clave"
    {{mensaje_final_que_conecta_con_el_RA_y_el_CE}}

### 9. Para seguir practicando

- {{actividad_o_practica_relacionada_1}}
- {{actividad_o_practica_relacionada_2}}
- {{actividad_o_practica_relacionada_3}}

## Bibliografia y fuentes

- {{fuente_1}}
- {{fuente_2}}
- {{fuente_3}}

<!--
Checklist para theory-content-writer:

- Confirmar ruta con repo-structure-guide.
- Confirmar nombre con naming-conventions-enforcer.
- Consultar docs/sectionX/recursos/{{normativa}} para asociar RA y CE reales.
- Mantener frontmatter compatible con MkDocs Material.
- Usar espanol de Espana y lenguaje inclusivo.
- Mantener una progresion: contexto -> definicion -> ejemplo -> aplicacion -> resumen.
- Usar admonitions solo cuando aporten valor didactico.
- Si hay imagenes, guardarlas en assets/ y usar alt text y figcaption.
- Si el tema requiere slides, GIFT o entrada en mkdocs.yml, indicarlo en el cierre del flujo.
- Revisar con frontmatter-metadata-enforcer, markdown-style-enforcer,
  pedagogical-language-checker y content-workflow-checklist.
-->
