---
title: "UD 1 - P1: Nuestra app en todas las plataformas"
description: Generar ejecutables de un proyecto Compose Multiplatform para escritorio, web y móvil desde Android Studio con tareas Gradle.
summary: "Práctica de empaquetado: del código Kotlin a un .exe de Windows, una web estática y un APK, usando Run → Edit Configurations."
authors:
    - Ismael Velasco
date: 2026-09-29
icon: "material/file-document-edit"
permalink: /di/unidad1/p1
categories:
    - DI
tags:
    - DI
    - Compose Multiplatform
    - Gradle
    - Empaquetado
    - KMP

# Relacionado con la tabla de contenidos
toc: true
toc_label: "Contenido"
toc_icon: "file-code"
---

# Práctica 1: Nuestra app en todas las plataformas

Ya tenemos una interfaz Compose que compila y corre. ¿Y si la queremos **en el escritorio de cualquier Windows, en un navegador y en el móvil**? En esta práctica vamos a convertir el proyecto Compose Multiplatform en productos repartibles: un `.exe` portable, un instalador `.msi`, una web estática y un APK. Todo sin escribir una línea de empaquetado: **las tareas Gradle ya lo saben hacer**.

**Duración estimada:** 2 horas de aula. Con la ampliación, 4 horas.

### 1. Objetivos

- Crear configuraciones de ejecución Gradle personalizadas en Android Studio (*Run → Edit Configurations*).
- Generar un ejecutable de escritorio portátil para Windows (`createDistributable`).
- Generar el instalador del sistema operativo actual (`packageDistributionForCurrentOS`).
- Generar la distribución web del proyecto (`composeCompatibilityBrowserDistribution`) y servirla en local.
- Entender qué plataformas pueden compilarse desde Windows y cuáles exigen otro sistema operativo (iOS → macOS).

### 2. Punto de partida: el proyecto multiplataforma

Partimos de un proyecto creado con el asistente de [kmp.jetbrains.com](https://kmp.jetbrains.com/), con esta estructura de módulos:

| Módulo | Qué contiene | Producto que genera |
| ------ | ------------ | ------------------- |
| `core` | Lógica pura compartida (sin UI) | Biblioteca usada por los demás |
| `app/shared` | UI Compose compartida | Biblioteca de composables |
| `app/androidApp` | Punto de entrada Android | **APK** (`assembleDebug` / `assembleRelease`) |
| `app/desktopApp` | Punto de entrada escritorio (JVM) | **.exe portable, .msi, .deb, .dmg, uber JAR** |
| `app/webApp` | Punto de entrada navegador (Kotlin/JS + Wasm) | **Web estática** (HTML + JS/Wasm) |
| `app/iosApp` | Punto de entrada iOS | App iOS (**solo desde macOS + Xcode**) |

> **Regla de oro:** cada plataforma se empaqueta DESDE su sistema operativo. Desde Windows podemos generar Android, escritorio y web. iOS exige un Mac. No es una limitación de Kotlin: firmar y compilar para iOS requiere las herramientas de Apple.

### 3. La herramienta estrella: Run → Edit Configurations

Android Studio puede lanzar **cualquier tarea Gradle** con el botón de *Run*, pero hay que enseñársela. Este es el flujo que usaremos toda la práctica (y toda la carrera):

1. Menú **Run → Edit Configurations...**
2. Botón **+** → **Gradle**
3. **Name:** un nombre claro, por ejemplo `Generar EXE`
4. **Run:** la tarea Gradle completa, por ejemplo `:app:desktopApp:createDistributable`
5. **Apply → OK**

Ahora esa tarea aparece en el desplegable de configuraciones (junto al botón ▶) y se ejecuta **con un clic**, igual que una app. Crea una configuración por cada producto de esta práctica: `Generar EXE`, `Generar MSI`, `Generar Web`, `Generar APK`.

### 4. Escritorio: el .exe portable

**Tarea:** `:app:desktopApp:createDistributable`

1. Crea la configuración de ejecución como se explicó arriba y lánzala.
2. La primera ejecución descarga herramientas (WiX Toolset, imagen de runtime). Paciencia: es normal que tarde.
3. Cuando acabe, el producto está en:

```
app/desktopApp/build/compose/binaries/main/app/<tu.paquete>/
```

4. Dentro hay tres piezas: el `.exe` (lanzador), la carpeta `runtime/` (una JVM completa) y `app/` (los jars de tu aplicación).
5. **Copia la carpeta entera** al Escritorio, renómbrala (`MiAppEscritorio`) y haz doble clic en el `.exe`. Tu interfaz Compose corre como programa de Windows, **sin tener Java instalado** en el equipo.

> Tareas hermanas: `run` ejecuta sin empaquetar, `runDistributable` prueba justo lo que acaba de empaquetarse, y `createReleaseDistributable` genera la versión optimizada (con ProGuard, vía `proguardReleaseJars`).

### 5. Escritorio: el instalador .msi

**Tarea:** `:app:desktopApp:packageDistributionForCurrentOS`

Genera el instalador nativo **del sistema operativo en el que compilas**: en Windows, un `.msi` (en Linux un `.deb`, en macOS un `.dmg`). El archivo queda en `app/desktopApp/build/compose/binaries/main/msi/`. Instálalo: tu app aparece en el menú Inicio y en *Aplicaciones instaladas*, con su desinstalador. La diferencia con el portable es exactamente esa: integración con el sistema.

> Las tareas `packageMsi`, `packageDeb` y `packageDmg` existen por separado, pero jpackage solo empaqueta para el SO anfitrión: desde Windows, la válida es `packageMsi`. Otra vez la regla de oro del apartado 2.

### 6. Escritorio: el uber JAR

**Tarea:** `:app:desktopApp:packageUberJarForCurrentOS`

Un único `.jar` con todo dentro (incluida la JVM ahead-of-time del módulo). Es el formato más portable entre máquinas **que ya tienen Java**, pero no es un ejecutable nativo: se lanza con `java -jar MiApp.jar`. Útil para servidores o para llevar tu app en un pen drive a cualquier SO con Java.

### 7. Web: la app en el navegador

**Tarea:** `:app:webApp:composeCompatibilityBrowserDistribution`

Compila la UI compartida a JavaScript + WebAssembly y genera una web estática completa en:

```
app/webApp/build/dist/wasmJs/productionExecutable/
```

Esa carpeta es **una web lista para publicar**: contiene un `index.html` y los bundles. Kotlin genera además la versión JS como *fallback* para navegadores sin Wasm moderno (de ahí lo de *compatibility*). Las variantes finas son `jsBrowserDistribution` (solo JavaScript) y `wasmJsBrowserDistribution` (solo Wasm).

Para probarla en local, desde esa carpeta:

```
python -m http.server 8080
```

y abre `http://localhost:8080` en el navegador. Tu misma interfaz, en una pestaña. Para el desarrollo diario con recarga caliente existen `jsBrowserDevelopmentRun` y `wasmJsBrowserDevelopmentRun`, que arrancan un servidor webpack.

### 8. Android: el APK de toda la vida

**Tarea:** `:app:androidApp:assembleDebug`

Genera el APK en `app/androidApp/build/outputs/apk/debug/`. Se instala con `adb install -r app-debug.apk` (o arrastrándolo al emulador). Para Google Play, la tarea es `assembleRelease` (o `bundleRelease`, que genera el `.aab` que exige la tienda).

### 9. ¿Y iOS?

El módulo `app/iosApp` está listo, pero compilarlo **exige macOS con Xcode**: ni el simulador ni la firma de Apple funcionan desde Windows o Linux. Es la única plataforma que nos queda vetada desde el aula. Cuando la necesites, las opciones reales son un Mac, o un servicio de compilación en la nube (los CI de pago con runners macOS).

### 10. Tabla de referencia

| Configuración (Run) | Tarea Gradle | Producto | Dónde queda |
| ------------------- | ------------ | -------- | ----------- |
| Generar EXE | `:app:desktopApp:createDistributable` | Carpeta portable con `.exe` + runtime | `build/compose/binaries/main/app/` |
| Generar MSI | `:app:desktopApp:packageDistributionForCurrentOS` | Instalador `.msi` del SO actual | `build/compose/binaries/main/msi/` |
| Generar JAR | `:app:desktopApp:packageUberJarForCurrentOS` | Uber JAR ejecutable | `build/compose/binaries/main/uber/` |
| Generar Web | `:app:webApp:composeCompatibilityBrowserDistribution` | Web estática (Wasm + fallback JS) | `build/dist/wasmJs/productionExecutable/` |
| Generar APK | `:app:androidApp:assembleDebug` | APK debug | `build/outputs/apk/debug/` |

### Ejercicios

**Ejercicio 1 — El .exe portable (obligatorio).** Genera el ejecutable de escritorio, copia la carpeta de distribución fuera del proyecto (por ejemplo al Escritorio, con nombre distinto) y demuestra con dos capturas que funciona: una del proceso de compilación terminado en el terminal de Android Studio y otra de la app de escritorio abierta. Explica en dos líneas qué contiene la carpeta generada (exe, runtime, app).

**Ejercicio 2 — La web en el navegador (obligatorio).** Genera la distribución web, sírvela en local con `python -m http.server` y captura la app funcionando en el navegador (se debe ver la URL localhost en la barra de direcciones). Indica el tamaño total de la carpeta generada.

**Ejercicio 3 — Tabla comparativa (obligatorio).** Completa en tu documento esta tabla con los datos REALES de tu proyecto:

| Producto | Tarea | Tamaño en disco | ¿Necesita Java instalado? | Usuario final: cómo lo abre |
| -------- | ----- | --------------- | ------------------------- | --------------------------- |
| .exe portable | | | | |
| .msi | | | | |
| uber JAR | | | | |
| Web | | | | |
| APK | | | | |

**Ejercicio 4 — Ampliación: el instalador (opcional, sesión de 4 horas).** Genera el `.msi`, instala la app, captura el menú Inicio con tu app y la entrada de *Aplicaciones instaladas*, y desinstálala. Añade una reflexión de tres líneas: ¿cuándo repartirías un portable y cuándo un instalador a tus usuarios?

### Criterios de entrega

- Documento con las capturas de los ejercicios obligatorios y la tabla comparativa con datos reales.
- Las capturas deben ser propias (se ve tu usuario, tu nombre de proyecto o tu interfaz).
- Sube el documento a la plataforma del curso.
