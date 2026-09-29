---
title: "UD 1 - Ejercicios: Introducción a la confección de interfaces"
description: Ejercicios graduados de menor a mayor dificultad sobre el entorno Android Studio, Kotlin y Jetpack Compose.
summary: Lista de ejercicios de la unidad 1 ordenados por dificultad, de los conceptos del tema a la primera interfaz propia.
authors:
    - Ismael Velasco
date: 2026-09-25
icon: "material/file-document-edit"
permalink: /di/unidad1/ejercicios
categories:
    - DI
tags:
    - DI
    - Ejercicios
    - Android Studio
    - Kotlin
    - Jetpack Compose
---

# Ejercicios de la Unidad 1

Ejercicios ordenados **de menor a mayor dificultad**. Los bloques A y B son individuales y cortos; el C monta el primer proyecto. El solucionario está en [`DI-U1.-Solucionario.md`](DI-U1.-Solucionario.md) — intenta cada ejercicio antes de mirarlo.

## Bloque A — Conceptos del tema (nivel: calentamiento)

**A1.** Clasifica los siguientes lenguajes en imperativo o declarativo: SQL, Kotlin, HTML, CSS, Java, Python.

**A2.** Explica con una frase cada uno de los tres modelos clave para interfaces: orientado a objetos, basado en eventos y basado en componentes.

**A3.** Di si cada afirmación es verdadera o falsa, corrigiendo las falsas:

1. Kotlin es un lenguaje de bajo nivel porque controla el hardware directamente.
2. En el modelo declarativo se describe el problema (el resultado), no los pasos.
3. Una función `@Composable` es un componente reutilizable que describe un trozo de interfaz.
4. En Jetpack Compose, la vista *Design* genera código que no se puede editar a mano.

**A4.** Completa la tabla con el elemento adecuado de nuestro entorno de trabajo:

| Necesidad | Elemento |
|-----------|----------|
| Mostrar un texto en pantalla | |
| Botón con acción al pulsarlo | |
| Colocar elementos en horizontal | |
| Librería de interfaces que usamos | |
| IDE que usamos en el módulo | |

**A5.** Según la tabla comparativa del tema (apartado 4), indica la licencia de MonoDevelop, Glade y Android Studio, y el enlace de descarga de Android Studio.

## Bloque B — El entorno (nivel: medio-bajo)

**B1.** Enumera los tres pasos imprescindibles de la instalación de Android Studio según el tema y di qué dos componentes NO hay que instalar aparte (a diferencia de lo que ocurría con Eclipse y el JDK).

**B2.** En el análisis del entorno de diseño (apartado 8 del tema), explica para qué sirven: la *Toolbar*, la vista *Split*, la *Palette* y el *Component Tree*.

**B3.** ¿Qué diferencia hay entre una **actividad** (`ComponentActivity`) y una **función composable**? ¿Cuál de las dos "monta" a la otra y con qué sentencia?

**B4.** ¿Qué hay que escribir para importar en Kotlin solo el componente `Button` de Material 3? ¿Y para importar toda la librería Material 3?

## Bloque C — Primer proyecto (nivel: medio)

**C1.** Instala Android Studio (si no lo tienes ya) siguiendo los pasos del apartado 6 del tema, captura la pantalla de bienvenida y crea un proyecto nuevo *Empty Activity* llamado `MiPrimeraInterfaz`.

**C2.** Localiza en el proyecto generado el archivo donde vive la interfaz (`MainActivity.kt`) y las tres vistas del editor (*Code*, *Split*, *Design*). Haz una captura de cada modo.

**C3.** Modifica el composable de ejemplo para que, en lugar del saludo por defecto, muestre tu nombre y tu ciclo en dos `Text`, centrados en pantalla (como el caso práctico 1 del tema). Ejecuta en el emulador y comprueba el resultado.

**C4.** Sustituye el contenido por una fila con dos botones **Aceptar** y **Cancelar** (como el caso práctico 2 del tema). Hazlo primero desde la vista *Code* y luego prueba a arrastrar un componente desde la paleta en la vista *Design*. Comenta qué observas.

**C5.** Añade una función `@Preview` a tu composable y comprueba que la previsualización aparece sin ejecutar la app. ¿Qué ventaja tiene respecto a ejecutar el emulador para cada cambio?

## Entrega

- Bloques A y B: respuestas en un documento.
- Bloque C: capturas y proyecto Android Studio comprimido (sin carpetas `build/` ni `.gradle/`) o enlace al repositorio de GitHub.
- Plazo y canal: el que indique la programación de aula.
