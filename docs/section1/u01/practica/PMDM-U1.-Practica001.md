---
title: "UD 1 - P1, Explorando Android Studio y sus plantillas"
description: Crear, ejecutar y comparar los prototipos de proyecto que ofrece Android Studio, en teléfono real o emulador.
summary: Primera toma de contacto con Android Studio creando los cinco primeros tipos de plantilla de proyecto y analizándolos en ejecución.
authors:
    - Ismael Velasco
date: 2026-09-22
icon: "material/file-document-edit"
permalink: /pmdm/unidad1/p1
categories:
    - PMDM
tags:
    - PMDM
    - Android Studio
    - Plantillas
    - Ejercicios

# Relacionado con la tabla de contenidos
toc: true
toc_label: "Contenido"
toc_icon: "file-code"
---

# Práctica 1.1: Explorando Android Studio y sus plantillas

En esta práctica vamos a crear, ejecutar y comparar los prototipos de proyecto que ofrece Android Studio al iniciar un nuevo proyecto. Es la primera toma de contacto con el entorno de desarrollo y con el ciclo completo: crear → ejecutar → observar.

**Duración estimada:** 2 horas de aula (media sesión del jueves). Si se realiza también la parte de ampliación, son 4 horas (sesión completa).

### 1. Objetivos

- Instalar y configurar el entorno de desarrollo Android Studio (CE 1.c).
- Crear proyectos a partir de las plantillas incluidas en Android Studio (CE 1.b).
- Ejecutar aplicaciones en un dispositivo físico o emulador (CE 1.c).
- Identificar los componentes que genera cada plantilla y su propósito (CE 1.e).

### 2. Pasos a seguir

1. **Prepara el entorno.** Abre Android Studio y verifica en *Tools → SDK Manager* que hay una imagen de sistema instalada. Si vas a usar emulador, crea un AVD en *Tools → Device Manager* (por ejemplo, un Pixel de gama media con la API actual).

2. **Crea los prototipos.** Carga en tu teléfono Android (o en el emulador, si tu teléfono usa otro sistema operativo) un prototipo de proyecto de **los 5 primeros tipos** que aparecen al crear un nuevo proyecto en Android Studio:

    1. Empty Activity
    2. Basic Views Activity
    3. Buttons Navigation Views Activity
    4. Empty Views Activity
    5. Navigation Drawer Views Activity

    Para cada uno: *File → New → New Project*, elige la plantilla, ponle un nombre distintivo (por ejemplo `P11Empty`, `P12BasicViews`...), lenguaje **Kotlin** y la API mínima sugerida.

3. **Ejecuta cada proyecto.** Pulsa Run y selecciona tu dispositivo o emulador. Espera a que compile, instale y arranque la app.

4. **Explora la estructura.** Sin modificar nada, abre el panel *Project* y anota qué archivos se abren por defecto: `MainActivity.kt`, el layout o los composables generados, recursos en `res/` y el `AndroidManifest.xml`. Observa qué cambia entre la plantilla *Views* (XML clásico) y las plantillas con Compose.

5. **Interacciona con cada app.** Navega por cada prototipo: en *Basic Views* y *Navigation Drawer* verás navegación entre pantallas; en *Buttons Navigation* una barra inferior. Anota qué componentes de interfaz trae cada uno.

6. **Documenta con capturas.** Realiza pantallazos de estos proyectos en tu teléfono o emulador y adjúntalos en un documento Word/PDF, ordenados por plantilla, con una línea de comentario por cada uno: qué pantalla es y qué componentes destaca.

### 3. Ejercicios

**Ejercicio 1 — Comparativa de plantillas (obligatorio).** Con las cinco apps ejecutadas, completa en tu documento una tabla como esta:

| Plantilla | ¿USA XML o Compose? | Navegación que incluye | Un componente destacado |
|-----------|--------------------|------------------------|-------------------------|
| Empty Activity | | | |
| Basic Views Activity | | | |
| Buttons Navigation Views Activity | | | |
| Empty Views Activity | | | |
| Navigation Drawer Views Activity | | | |

**Ejercicio 2 — Cambio de texto (obligatorio).** En el proyecto *Empty Activity*, localiza el texto "Hello Android!" (o el equivalente que genere tu versión) y cámbialo por tu nombre y el del ciclo. Vuelve a ejecutar y captura el resultado. Explica en dos líneas en qué archivo hiciste el cambio.

**Ejercicio 3 — Ampliación: plantilla Wear OS (opcional, para sesión de 4 horas).** Crea un sexto proyecto con la plantilla de *Wear OS* o, si tu versión no la ofrece, con cualquier plantilla de la sección *Automotive* o *TV*. Ejecútala en el emulador específico (reloj o TV) y compara la experiencia con el móvil: tamaño de pantalla, controles y límites. Añade captura y conclusión de dos líneas: ¿merecería la pena adaptar una app móvil a ese dispositivo?

### Criterios de entrega

- Documento Word o PDF con las capturas de los 5 prototipos (o 6 con la ampliación) corriendo en tu teléfono o emulador.
- Tabla comparativa completada y respuestas a los ejercicios 2 y 3.
- Sube el documento a la plataforma del curso.
