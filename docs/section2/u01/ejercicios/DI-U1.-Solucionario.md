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
- ***Palette***: paleta de composables en la vista *Design* de la que se arrastran los componentes (textos, botones, campos, contenedores) hasta el lienzo.
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

> **Enunciado.** Instala Android Studio (si no lo tienes ya) siguiendo los pasos del apartado 6 del tema, captura la pantalla de bienvenida y crea un proyecto nuevo *Empty Activity* llamado `MiPrimeraInterfaz`.

**Solución.** Tras completar el asistente de instalación y el primer arranque, la pantalla de bienvenida ofrece *New Project* / *Open*. Se elige **New Project → Empty Activity (Compose)**, se escribe el nombre `MiPrimeraInterfaz` y se deja el resto por defecto. La captura debe mostrar el asistente con el nombre escrito y, si se quiere, el proyecto ya abierto con el archivo `MainActivity.kt` visible.

### C2

> **Enunciado.** Localiza en el proyecto generado el archivo donde vive la interfaz (`MainActivity.kt`) y las tres vistas del editor (*Code*, *Split*, *Design*). Haz una captura de cada modo.

**Solución.** El archivo está en `app/src/main/java/<paquete>/MainActivity.kt`. Arriba a la derecha del editor aparecen las tres pestañas: **Code** (solo código Kotlin), **Split** (código + previsualización) y **Design** (solo previsualización). Las capturas deben mostrar la misma función `Greeting` renderizada en los tres modos. Es normal que en *Code* no haya nada visual: la previsualización aparece en cuanto el editor detecta funciones composables (o al añadir `@Preview`, ver C5).

### C3

> **Enunciado.** Modifica el composable de ejemplo para que, en lugar del saludo por defecto, muestre tu nombre y tu ciclo en dos `Text`, centrados en pantalla (como el caso práctico 1 del tema). Ejecuta en el emulador y comprueba el resultado.

**Solución.**

```kotlin
class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContent {
            MiPrimeraInterfaz()
        }
    }
}

@Composable
fun MiPrimeraInterfaz() {
    Column(
        modifier = Modifier.fillMaxSize(),
        verticalArrangement = Arrangement.Center,
        horizontalAlignment = Alignment.CenterHorizontally
    ) {
        Text("Tu Nombre")
        Text("2º DAM · Desarrollo de Interfaces")
    }
}
```

El centrado lo hace el contenedor `Column` con sus parámetros de disposición (`verticalArrangement` y `horizontalAlignment`), no el texto. Al ejecutar (Run ▶ con el emulador arrancado) debe verse la pantalla con los dos textos centrados, ocupando toda la pantalla del dispositivo virtual.

### C4

> **Enunciado.** Sustituye el contenido por una fila con dos botones **Aceptar** y **Cancelar** (como el caso práctico 2 del tema). Hazlo primero desde la vista *Code* y luego prueba a arrastrar un componente desde la paleta en la vista *Design*. Comentario: ¿qué observas?

**Solución.**

```kotlin
@Composable
fun MiPrimeraInterfaz() {
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

**Qué se observa:** al arrastrar un componente desde la paleta en la vista *Design*, Android Studio **escribe el mismo código Kotlin** en la vista *Code*: las dos vistas son espejos de un único código. No hay "doble verdad" como en otros entornos clásicos: lo que arrastras es lo que está en el archivo, y puedes ajustarlo a mano en cualquier momento.

### C5

> **Enunciado.** Añade una función `@Preview` a tu composable y comprueba que la previsualización aparece sin ejecutar la app. ¿Qué ventaja tiene respecto a ejecutar el emulador para cada cambio?

**Solución.**

```kotlin
@Preview(showBackground = true)
@Composable
fun MiPrimeraInterfazPreview() {
    MiPrimeraInterfaz()
}
```

Con solo guardar el archivo, la previsualización aparece en el panel derecho (vista *Split* o *Design*) sin arrancar el emulador. **Ventaja:** el ciclo de cambio→verificación pasa de minutos (arrancar emulador, desplegar APK) a **segundos** (guardar y mirar), lo que acelera enormemente el diseño de interfaces. Además se pueden declarar varias previews con contenidos distintos para ver varios estados de la misma pantalla a la vez.
