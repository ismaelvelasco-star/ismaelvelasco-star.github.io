---
title: "UD 1 - P2, Emuladores y perfiles de dispositivo"
description: Configurar AVD con distintos perfiles de hardware y comprobar cómo una misma app se comporta en cada uno.
summary: Creación y configuración de emuladores Android (AVD) para gama baja, gama media, tablet y plegable, analizando limitaciones y adaptación de la interfaz.
authors:
    - Ismael Velasco
date: 2026-09-22
icon: "material/file-document-edit"
permalink: /pmdm/unidad1/p2
categories:
    - PMDM
tags:
    - PMDM
    - Emuladores
    - AVD
    - Ejercicios

# Relacionado con la tabla de contenidos
toc: true
toc_label: "Contenido"
toc_icon: "file-code"
---

# Práctica 1.2: Emuladores y perfiles de dispositivo

Los emuladores permiten ejecutar y depurar apps sin dispositivo físico, variando tamaño de pantalla, versión del SO, sensores y condiciones de red. En esta práctica vamos a montar un parque de dispositivos virtual y a ponerlo a prueba con la misma aplicación.

**Duración estimada:** 2 horas de aula (media sesión del jueves).

### 1. Objetivos

- Crear y configurar Android Virtual Devices (AVD) con distintos perfiles (CE 1.d).
- Identificar configuraciones que clasifican los dispositivos según sus características (CE 1.d).
- Reconocer las limitaciones técnicas de los perfiles de gama baja (CE 1.f).
- Simular condiciones de red y sensores desde el emulador (CE 1.a).

### 2. Pasos a seguir

1. **Crea el AVD de gama media (el de referencia).** En *Tools → Device Manager → Create Device*, elige un teléfono reciente (por ejemplo Pixel 7) con la API actual. Anota su configuración: RAM, almacenamiento, resolución y densidad.

2. **Crea el AVD de gama baja.** Define un perfil personalizado (*New Hardware Profile*) con 2 GB de RAM, pantalla de 5 pulgadas y una API dos versiones anterior a la actual (API n−2). Es el perfil "abuela": el que más limitaciones va a descubrir.

3. **Crea un AVD de pantalla grande.** Tableta de 10-12 pulgadas para comprobar layouts adaptativos.

4. **Crea (o activa) un AVD plegable.** Si tu imagen del sistema lo permite, define un dispositivo foldable y prueba a plegar y desplegar durante la ejecución.

5. **Instala la misma app en los cuatro.** Usa el proyecto *Basic Views Activity* de la práctica anterior (o cualquier plantilla con navegación) y ejecútalo en cada AVD.

6. **Fuerza condiciones adversas en el de gama media.** Con la app en marcha, abre los controles extendidos del emulador y prueba: cambiar el nivel de batería, inyectar una ubicación GPS distinta, y simular red 3G con pérdida de paquetes.

### 3. Ejercicios

**Ejercicio 1 — Ficha técnica comparativa (obligatorio).** Rellena una tabla con los cuatro perfiles creados: nombre, API, RAM, pulgadas y densidad. Añade una columna final: "¿la app se ve correcta?" con Sí/No y una línea explicando el problema si lo hay (elementos cortados, texto demasiado pequeño, navegación incómoda...).

**Ejercicio 2 — El laboratorio de la abuela (obligatorio).** En el AVD de gama baja, activa en *Settings → Developer options* la opción *Don't keep activities*, lanza la app, navega a una pantalla interior, pulsa Inicio y vuelve a la app. Describe qué ha pasado con el estado (¿recuerda dónde estabas?) y relaciónalo con el ciclo de vida de la teoría: qué callback se ejecutó y qué debería hacer la app para no perder el estado.

**Ejercicio 3 — Simulación de red (ampliación).** Con los controles extendidos, configura *Cellular network type: 3G* con la pérdida de paquetes al máximo, y navega por una app que cargue contenido (por ejemplo el navegador del emulador). Cronometra aproximadamente cuánto tarda y describe qué estrategias debería aplicar una app real en esa situación (caché, avisos, reintento...). Conclusión de tres líneas: ¿por qué "en mi móvil va fino" no es un argumento válido de pruebas?

### Criterios de entrega

- Documento con la tabla comparativa de los 4 perfiles.
- Respuestas a los ejercicios 2 y 3 con capturas de los emuladores en cada situación.
- Sube el documento a la plataforma del curso.
