---
title: "UD 1 - P3, ADB y el administrador de aplicaciones"
description: Manejar una app desde la consola con ADB - instalar, arrancar, conceder permisos, leer logs y transferir archivos.
summary: Primer contacto profesional con adb (Android Debug Bridge) como herramienta del administrador de aplicaciones - ciclo completo de una app sin tocar la pantalla.
authors:
    - Ismael Velasco
date: 2026-09-22
icon: "material/file-document-edit"
permalink: /pmdm/unidad1/p3
categories:
    - PMDM
tags:
    - PMDM
    - ADB
    - Administrador de aplicaciones
    - Ejercicios

# Relacionado con la tabla de contenidos
toc: true
toc_label: "Contenido"
toc_icon: "file-code"
---

# Práctica 1.3: ADB y el administrador de aplicaciones

Detrás de cada pantalla de Android hay un administrador de aplicaciones que se puede manejar por consola. En esta práctica vamos a usar `adb` para instalar, arrancar, inspeccionar y desinstalar una aplicación sin tocarla en pantalla: el flujo de trabajo real de desarrollo y pruebas.

**Duración estimada:** 2 horas de aula (media sesión del jueves). Combinada con la práctica 1.2, completa una sesión de 4 horas.

### 1. Objetivos

- Utilizar el entorno de ejecución del administrador de aplicaciones (CE 1.c).
- Instalar, lanzar y desinstalar apps desde la consola con `adb install/uninstall` y `am start` (CE 1.h).
- Conceder y revocar permisos en tiempo de ejecución con `pm grant/revoke` (CE 1.h).
- Leer logs de la aplicación con `logcat` para diagnosticar su comportamiento (CE 1.a).

### 2. Pasos a seguir

1. **Localiza el ejecutable adb.** En Android Studio, abre un terminal (*View → Tool Windows → Terminal*). El ejecutable `adb` vive en `platform-tools` dentro del SDK de Android; puedes usar la ruta completa o añadirlo al PATH. Comprueba la conexión:

    ```bash
    adb devices
    ```

    Debe aparecer tu emulador o teléfono con estado *device*.

2. **Localiza el APK de tu práctica.** El proyecto de la práctica 1.1 genera su APK en `app/build/outputs/apk/debug/app-debug.apk` tras ejecutar *Build → Build Bundle(s)/APK(s) → Build APK(s)*. Anota la ruta.

3. **Instala desde consola.** Con el emulador arrancado:

    ```bash
    adb install ruta/al/app-debug.apk
    adb install -r ruta/al/app-debug.apk    # reemplaza una versión existente
    ```

4. **Lista y arranca la app.** Descubre el nombre de paquete de tus apps y arranca la actividad principal:

    ```bash
    adb shell pm list packages | grep p11
    adb shell am start -n com.example.p11empty/.MainActivity
    ```

5. **Lee los logs en vivo.** Con la app en pantalla, en otro terminal:

    ```bash
    adb logcat *:W
    ```

    Gira el dispositivo o navega por la app y observa qué mensajes aparecen.

6. **Permisos a lo industrial.** Concede y revoca un permiso peligroso y observa el cambio en la app:

    ```bash
    adb shell pm grant com.example.p11empty android.permission.CAMERA
    adb shell pm revoke com.example.p11empty android.permission.CAMERA
    ```

7. **Copia archivos.** Sube y baja un archivo entre el PC y el emulador:

    ```bash
    echo "log de prueba" > prueba.txt
    adb push prueba.txt /sdcard/Download/
    adb pull /sdcard/Download/prueba.txt descargado.txt
    ```

### 3. Ejercicios

**Ejercicio 1 — La hoja de ruta del paquete (obligatorio).** Entrega una secuencia de comandos (copiados de tu terminal, con su salida) que haga: instalar el APK → arrancar la actividad principal → listar el paquete para verificar que está instalado → desinstalarlo → verificar con `pm list packages` que ya no aparece. Marca cada paso con un comentario de una línea explicando qué hace.

**Ejercicio 2 — Caza de logs (obligatorio).** Con `adb logcat` abierto, provoca deliberadamente un error en tu app (por ejemplo, cierra la app desde el selector de recientes y reanúdala con *Don't keep activities* activo, o fuerza un giro de pantalla). Captura las líneas relevantes del log y explica qué estaba pasando en el ciclo de vida de la app en ese momento.

**Ejercicio 3 — Ampliación: batería y diagnóstico.** Usa `adb shell dumpsys batterystats` y `adb shell dumpsys activity processes` con tu app arrancada. Localiza en la salida el nombre de tu paquete y extrae dos datos que llamen tu atención (procesos vivos, tiempo de CPU, consumo...). Explica en tres líneas por qué estas herramientas son la base del trabajo de un equipo de calidad (QA) antes de publicar una app.

### Criterios de entrega

- Documento con las salidas de los comandos de los tres ejercicios (capturas o texto copiado).
- Cada secuencia de comandos comentada línea a línea.
- Sube el documento a la plataforma del curso.
