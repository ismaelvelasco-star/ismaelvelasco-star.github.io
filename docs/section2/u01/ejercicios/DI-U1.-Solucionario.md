---
title: "UD 1 - Solucionario: Introducción a la confección de interfaces"
description: Soluciones comentadas de los ejercicios de la unidad 1, con el enunciado de cada ejercicio.
summary: "Solucionario completo de los ejercicios de la unidad 1: cada solución va precedida de su enunciado y seguida de un comentario didáctico."
authors:
    - Ismael Velasco
date: 2026-09-25
icon: "material/file-document-edit"
permalink: /di/unidad1/solucionario
categories:
    - DI
tags:
    - DI
    - Solucionario
    - Android Studio
    - Kotlin
    - Jetpack Compose
---

# Solucionario de la Unidad 1

Cada solución va precedida de su **enunciado** (en cita) para que el documento se pueda leer solo. Si tu solución difiere pero funciona y está razonada, también vale.

## Bloque A — Conceptos del tema

### A1

> **Enunciado.** Clasifica los siguientes lenguajes en imperativo o declarativo: SQL, Kotlin, HTML, CSS, Java, Python.

**Solución.** Imperativos: **Kotlin, Java, Python** (describen pasos: estructuras de control, asignaciones, bucles). Declarativos: **SQL, HTML, CSS** (describen el resultado: "qué datos quiero", "cómo se ve", sin indicar cómo conseguirlo).

### A2

> **Enunciado.** Explica con una frase cada uno de los tres modelos clave para interfaces: orientado a objetos, basado en eventos y basado en componentes.

**Solución.**

- **POO**: el programa se estructura en objetos (entidades con atributos, propiedades y métodos) que interactúan entre sí.
- **Eventos**: el flujo del programa lo determinan acciones externas (como la pulsación de un botón), a las que el código responde con manejadores.
- **Componentes**: se construye reutilizando módulos de software visuales ya desarrollados y empaquetados, en lugar de programar cada pantalla desde cero.

### A3

> **Enunciado.** Di si cada afirmación es verdadera o falsa, corrigiendo las falsas:
> 1. Kotlin es un lenguaje de bajo nivel porque controla el hardware directamente.
> 2. En el modelo declarativo se describe el problema (el resultado), no los pasos.
> 3. Una función `@Composable` es un componente reutilizable que describe un trozo de interfaz.
> 4. En Jetpack Compose, la vista *Design* genera código que no se puede editar a mano.

**Solución.**

1. **Falsa.** Kotlin es de **alto nivel**: se escribe con reglas cercanas al lenguaje natural y es el compilador quien lo traduce a bytecode (bajo nivel) ejecutable por la máquina.
2. **Verdadera.** Es la definición del modelo declarativo.
3. **Verdadera.** Se define una vez y se reutiliza en cualquier pantalla: el modelo de componentes aplicado a la UI.
4. **Falsa.** El código generado sí se puede editar a mano: es Kotlin normal. De hecho, las dos vistas (*Code* y *Design/Split*) son dos espejos del mismo código, y editarlo directamente es la práctica habitual.

### A4

> **Enunciado.** Completa la tabla con el elemento adecuado de nuestro entorno de trabajo.

**Solución.**

| Necesidad | Elemento |
|-----------|----------|
| Mostrar un texto en pantalla | `Text` |
| Botón con acción al pulsarlo | `Button` |
| Colocar elementos en horizontal | `Row` |
| Librería de interfaces que usamos | Jetpack Compose (Material 3) |
| IDE que usamos en el módulo | Android Studio |

### A5

> **Enunciado.** Según la tabla comparativa del tema (apartado 4), indica la licencia de Visual Studio, Glade y Android Studio, y el enlace de descarga de Android Studio.

**Solución.** MonoDevelop: **libre**. Glade: **libre**. Android Studio: **libre**. Descarga de Android Studio: <https://developer.android.com/studio>.

## Bloque B — El entorno

### B1

> **Enunciado.** Enumera los tres pasos imprescindibles de la instalación de Android Studio según el tema y di qué dos componentes NO hay que instalar aparte (a diferencia de lo que ocurría con Eclipse y el JDK).

**Solución.** Pasos: (1) descargar el instalador desde <https://developer.android.com/studio> según el sistema operativo y ejecutarlo; (2) seguir el asistente con las opciones por defecto (instalación *Standard*, que instala el SDK de Android y las herramientas de emulador); (3) en el primer arranque, dejar que el asistente de configuración descargue los componentes restantes.

Componentes que NO hay que instalar aparte: el **JDK** (Android Studio incluye uno embebido) y la **librería de interfaces** (el asistente de proyectos añade Jetpack Compose automáticamente). Con Eclipse, en cambio, había que instalar el JDK desde la web de Oracle y el diseñador de interfaces vía *Install New Software*.

### B2

> **Enunciado.** En el análisis del entorno de diseño (apartado 8 del tema), explica para qué sirven: la *Toolbar*, la vista *Split*, la *Palette* y el *Component Tree*.

**Solución.**

- **Toolbar**: barra de herramientas con las acciones genéricas: crear proyectos y archivos, sincronizar Gradle, gestor de SDK, emulador y, especialmente, el botón **Run** (▶) para ejecutar la app en el dispositivo elegido.
- **Vista *Split***: muestra a la vez el código Kotlin y la previsualización en vivo de la interfaz (`@Preview`), permitiendo diseñar viendo el resultado sin ejecutar la app.
- ***Autocompletado (Ctrl+Espacio)***: el "catálogo" de composables de Compose: al escribir las primeras letras de un componente, Android Studio ofrece la función completa con sus parámetros y documentación. Sustituye a la paleta de arrastre de los editores clásicos (que no existe en Compose).
- ***Component Tree***: árbol que resume todos los componentes colocados en el diseño, como un explorador de la jerarquía de la interfaz.

### B3

> **Enunciado.** ¿Qué diferencia hay entre una **actividad** (`ComponentActivity`) y una **función composable**? ¿Cuál de las dos "monta" a la otra y con qué sentencia?

**Solución.** La **actividad** es la pantalla del sistema operativo que aloja la interfaz; la **función composable** es la que describe el contenido de esa interfaz. La actividad "monta" al composable mediante la sentencia **`setContent { ... }`** dentro de `onCreate`, como una ventana que contiene el diseño.

### B4

> **Enunciado.** ¿Qué hay que escribir para importar en Kotlin solo el componente `Button` de Material 3? ¿Y para importar toda la librería Material 3?

**Solución.**

```kotlin
import androidx.compose.material3.Button   // solo Button
import androidx.compose.material3.*        // toda la librería Material 3
```

La importación se escribe justo después de la declaración del paquete (si existe), y en la práctica el IDE la añade automáticamente con Alt+Intro sobre el elemento en rojo.

## Bloque C — Primer proyecto

### C1

> **Enunciado.** Entra en el asistente de Kotlin Multiplatform de JetBrains ([kmp.jetbrains.com](https://kmp.jetbrains.com/)), marca las plataformas **Android** y **Desktop** y genera un proyecto llamado `TuNombreTuApellidoMiPrimeraInterfaz` (por ejemplo `AnaGarciaMiPrimeraInterfaz`, según la norma de nombrado del bloque). Descárgalo, ábrelo en Android Studio y espera la sincronización de Gradle. Captura la pantalla del asistente con tu nombre escrito y la estructura de módulos del panel *Project*.

**Solución.** En el asistente web se marca el proyecto *Compose Multiplatform* con las casillas **Android** y **Desktop** (JVM), se escribe el nombre del proyecto **con tu nombre y apellido delante** (en el ejemplo, `AnaGarciaMiPrimeraInterfaz`) y se pulsa *Download*. El ZIP resultante se descomprime y se abre en Android Studio (*File → Open*), donde la primera sincronización de Gradle descarga dependencias y puede tardar varios minutos. La captura del panel *Project* (vista *Project*, no *Android*) debe mostrar la estructura en árbol: carpetas `core`, `app` (con `shared`, `androidApp` y `desktopApp` dentro) y los scripts de Gradle. El nombre propio en el proyecto queda así documentado en las capturas, la preview y el APK: cualquier entrega "prestada" se identifica de un vistazo.

### C2

> **Enunciado.** El proyecto multiplataforma no es una carpeta única: es **tres módulos** con misiones distintas. Localiza `core` (lógica compartida), `app/shared` (interfaz compartida con Compose) y `app androidApp` (la actividad Android), y dentro de `shared` el archivo `App.kt`, donde vive la interfaz que se ve en **todas** las plataformas. Haz capturas del panel *Project* con los tres módulos y de `App.kt` abierto en el editor.

**Solución.** El panel *Project* muestra la estructura real del disco. Los tres módulos y su misión:

| Módulo | Misión | Qué contiene |
|--------|--------|--------------|
| `core` | Lógica compartida **pura** (sin interfaz) | Funciones de datos y reglas de negocio; **prohibido** Compose aquí |
| `app/shared` | Interfaz compartida con **Compose Multiplatform** | `App.kt` y el resto de composables; se compila para todas las plataformas marcadas |
| `app/androidApp` | La "puerta" Android | `MainActivity.kt` con `setContent { App() }`; solo existe en Android |

La regla de oro que ya conoces del tema: **todo lo que se ve en pantalla se escribe en `shared`**; `androidApp` se limita a montarlo en la actividad. El archivo clave es `app/shared/src/commonMain/kotlin/.../App.kt`: al abrirlo, su función `App()` muestra el saludo de ejemplo que verás idéntico en Android y en escritorio.

### C3

> **Enunciado.** Ejecuta la app **dos veces**: primero en el emulador Android (*Run ▶* con la configuración `androidApp`) y luego en escritorio (la tarea `run` del módulo `desktopApp`). Debes ver la **misma interfaz** en las dos plataformas: eso es Compose Multiplatform. Captura ambas ejecuciones. Después, modifica el composable compartido `App()` para que muestre tu nombre y tu ciclo en dos `Text`, centrados en pantalla (la misma idea del caso práctico 1 del tema), y vuelve a ejecutar en las dos plataformas para comprobar que el cambio se refleja en ambas.

**Solución.** Primera parte: en el selector de configuraciones (a la izquierda de *Run ▶*) se elige `androidApp` y se ejecuta con el emulador arrancado; después, en el panel *Gradle* se navega hasta `app → desktopApp → Tasks → application → run` (o el botón ▶ de la tarea), y se abre una **ventana de escritorio** con la misma interfaz del emulador.

Segunda parte, el código compartido en `shared/src/commonMain/.../App.kt`:

```kotlin
@Composable
fun App() {
    Column(
        modifier = Modifier.fillMaxSize(),
        verticalArrangement = Arrangement.Center,
        horizontalAlignment = Alignment.CenterHorizontally
    ) {
        Text("Ana García")                       // <- tu nombre real
        Text("2º DAM · Desarrollo de Interfaces") // <- tu ciclo
    }
}
```

Como `App()` vive en `shared`, **una sola edición** sirve para las dos plataformas: al reejecutar `androidApp` en el emulador y `run` en escritorio, los dos textos aparecen centrados en ambos. El centrado lo hace el contenedor `Column` con sus parámetros de disposición (`verticalArrangement` y `horizontalAlignment`), no el texto.

### C4

> **Enunciado.** Sustituye el contenido de `App()` por una fila (`Row`) con dos botones **Aceptar** y **Cancelar** (la idea del caso práctico 2 del tema). Escríbelo a mano en el editor con ayuda del autocompletado (**Ctrl+Espacio**) y observa la vista *Split* mientras escribes. Comenta qué ocurre en la preview en cada paso.

**Solución.**

```kotlin
@Composable
fun App() {
    Row(
        modifier = Modifier.fillMaxSize(),
        horizontalArrangement = Arrangement.Center,
        verticalAlignment = Alignment.CenterVertically
    ) {
        Button(onClick = { }) {
            Text("Aceptar")
        }
        Button(onClick = { }) {
            Text("Cancelar")
        }
    }
}
```

**Qué se observa:** mientras se escribe, la preview de la vista *Split* se redibuja al instante — incluso con el código a medias, mostrando el estado intermedio. La vista *Split* es un espejo en vivo del código: cada carácter escrito se refleja al segundo en la previsualización, sin compilar ni ejecutar nada.

### C5

> **Enunciado.** Añade una función `@Preview` para tu composable y comprueba que la previsualización aparece sin ejecutar la app. Ojo a la regla KMP: el `@Preview` **no puede vivir en `shared`** (ese módulo también compila para escritorio, donde la previsualización de Android no existe); créala en `app androidApp`, en un archivo propio (por ejemplo `Previews.kt`), importando el composable desde `shared`. ¿Qué ventaja tiene la preview respecto a ejecutar el emulador para cada cambio?

**Solución.** En `app/androidApp/src/main/kotlin/.../Previews.kt` (archivo nuevo en el módulo **Android**):

```kotlin
package org.tunombre.apellido.miprimainterfaz   // el paquete de TU androidApp

import androidx.compose.ui.tooling.preview.Preview
import org.tunombre.apellido.MiPrimeraInterfaz.shared.App   // el composable llega desde shared

@Preview(showBackground = true)
@Composable
fun AppPreview() {
    App()
}
```

La importación de `App` resuelve contra el módulo `shared`, que Android Studio ya tiene sincronizado como dependencia de `androidApp`. Con solo guardar el archivo, la previsualización aparece en el panel derecho (vista *Split* o *Design*) **sin arrancar el emulador**. **Ventaja:** el ciclo de cambio→verificación pasa de minutos (arrancar emulador, desplegar APK) a **segundos** (guardar y mirar), lo que acelera enormemente el diseño de interfaces. Además se pueden declarar varias previews con contenidos distintos para ver varios estados de la misma pantalla a la vez.
