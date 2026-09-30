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

**B2.** En el análisis del entorno de diseño (apartado 8 del tema), explica para qué sirven: la *Toolbar*, la vista *Split*, el autocompletado (*Ctrl+Espacio*) y el *Component Tree*.

**B3.** ¿Qué diferencia hay entre una **actividad** (`ComponentActivity`) y una **función composable**? ¿Cuál de las dos "monta" a la otra y con qué sentencia?

**B4.** ¿Qué hay que escribir para importar en Kotlin solo el componente `Button` de Material 3? ¿Y para importar toda la librería Material 3?

## Bloque C — Primer proyecto multiplataforma (nivel: medio)

!!! warning "Norma de nombrado obligatoria (anti-copypaste)"
    Todo proyecto que crees en este módulo llevará **tu nombre y tu apellido** delante del nombre del ejercicio, todo junto y sin espacios ni tildes: `NombreApellido` + `NombreDelProyecto`.

    Ejemplo: una alumna llamada Ana García llamaría a su primer proyecto `AnaGarciaMiPrimeraInterfaz`.

    Así cada captura de pantalla, cada preview y cada APK quedan marcados con el nombre de su autor o autora: una entrega prestada delata sola al compañero.

**C1.** Entra en el asistente de Kotlin Multiplatform de JetBrains ([kmp.jetbrains.com](https://kmp.jetbrains.com/)), marca las plataformas **Android** y **Desktop** y genera un proyecto llamado `TuNombreTuApellidoMiPrimeraInterfaz` (por ejemplo `AnaGarciaMiPrimeraInterfaz`, según la norma de nombrado del bloque). Descárgalo, ábrelo en Android Studio y espera la sincronización de Gradle. Captura la pantalla del asistente con tu nombre escrito y la estructura de módulos del panel *Project*.

**C2.** El proyecto multiplataforma no es una carpeta única: es **tres módulos** con misiones distintas. Localiza `core` (lógica compartida), `app/shared` (interfaz compartida con Compose) y `app androidApp` (la actividad Android), y dentro de `shared` el archivo `App.kt`, donde vive la interfaz que se ve en **todas** las plataformas. Haz capturas del panel *Project* con los tres módulos y de `App.kt` abierto en el editor.

**C3.** Ejecuta la app **dos veces**: primero en el emulador Android (*Run ▶* con la configuración `androidApp`) y luego en escritorio (la tarea `run` del módulo `desktopApp`). Debes ver la **misma interfaz** en las dos plataformas: eso es Compose Multiplatform. Captura ambas ejecuciones. Después, modifica el composable compartido `App()` para que muestre tu nombre y tu ciclo en dos `Text`, centrados en pantalla (la misma idea del caso práctico 1 del tema), y vuelve a ejecutar en las dos plataformas para comprobar que el cambio se refleja en ambas.

**C4.** Sustituye el contenido de `App()` por una fila (`Row`) con dos botones **Aceptar** y **Cancelar** (la idea del caso práctico 2 del tema). Escríbelo a mano en el editor con ayuda del autocompletado (**Ctrl+Espacio**) y observa la vista *Split* mientras escribes. Comenta qué ocurre en la preview en cada paso.

**C5.** Añade una función `@Preview` para tu composable y comprueba que la previsualización aparece sin ejecutar la app. Ojo a la regla KMP: el `@Preview` **no puede vivir en `shared`** (ese módulo también compila para escritorio, donde la previsualización de Android no existe); créala en `app androidApp`, en un archivo propio (por ejemplo `Previews.kt`), importando el composable desde `shared`. ¿Qué ventaja tiene la preview respecto a ejecutar el emulador para cada cambio?

## Entrega

- Bloques A y B: respuestas en un documento.
- Bloque C: capturas y proyecto Android Studio comprimido (sin carpetas `build/` ni `.gradle/`) o enlace al repositorio de GitHub.
- Plazo y canal: el que indique la programación de aula.
