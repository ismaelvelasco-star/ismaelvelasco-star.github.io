---
title: "UD 2 - Ejercicios: Clases y componentes"
description: "Relación de ejercicios del tema 2, de menor a mayor dificultad: Bloque A (conceptos, pocos), Bloque B (componentes sueltos) y Bloque C (mini-proyectos completos)."
authors:
    - Ismael Velasco
date: 2026-09-26
icon: "material/puzzle"
permalink: /di/unidad2/ejercicios
categories:
    - DI
tags:
    - DI
    - Kotlin
    - Jetpack Compose
---

# Ejercicios UD 2 — Clases y componentes

La mayoría de los ejercicios son de **práctica**: créate un proyecto `EjerciciosUD2` con plantilla Empty Activity y ve añadiendo cada ejercicio en su propia función componible. Ejecuta en el emulador (o mira la preview con `@Preview`) tras cada uno.

## Bloque A — Conceptos (calentamiento)

**A1.** Explica con tus palabras la diferencia entre un **Checkbox** y un **RadioButton**, y pon un ejemplo real de interfaz donde usarías cada uno.

**A2.** En Compose, ¿por qué `TextField` necesita obligatoriamente los parámetros `value` y `onValueChange` en pareja? ¿Qué pasaría si falta el segundo?

**A3.** ¿Qué significa que un diálogo es **modal**? Pon un ejemplo de app real donde sea necesario ese comportamiento.

**A4.** Une con flechas cada necesidad con su contenedor: ordenar un formulario en vertical · poner un texto sobre una foto · una fila de botones Aceptar/Cancelar · una cuadrícula de iconos. (Contenedores: Box, Row, LazyVerticalGrid, Column.)

## Bloque B — Componentes sueltos (práctica guiada)

**B1. Tarjeta de presentación.** Crea un componible `MiTarjeta` que muestre tu nombre con `titleLarge` en negrita, tu ciclo con `bodyMedium` y tu instituto con `labelSmall` en gris. Apílalos en un `Column` centrado con `spacedBy(4.dp)`.

**B2. Los tres botones.** En una `Row` centrada con `spacedBy(12.dp)`, coloca los tres niveles de botón: `Button` ("Guardar"), `OutlinedButton` ("Cancelar") y `TextButton` ("Saltar"). Debajo, con otro `Text`, haz que el texto cambie al nombre del último botón pulsado (pista: `var ultimo by remember { mutableStateOf("ninguno") }` y en cada `onClick` actualizarlo).

**B3. Formulario con validación.** Un `Column` con dos `OutlinedTextField` (email y teléfono) y un botón "Enviar" que solo haga algo si el email contiene una `@` y el teléfono tiene 9 caracteres; si no, muestra `supportingText` en rojo con `isError = true` en el campo incorrecto.

**B4. Encuesta con checkboxes.** La lista "¿Qué usas para programar?" con 5 opciones (PC de sobremesa, portátil, móvil, tablet, otro). Cada opción es un `Checkbox` en una `Row`. Abajo, un `Text` que cuente en vivo cuántas hay marcadas (pista: `mutableStateListOf` como en la teoría).

**B5. Talla con radio buttons.** Tres `RadioButton` (S, M, L) **excluyentes** compartiendo la misma variable de estado. Debajo un `Text` que diga "Talla elegida: X". Comprueba que marcar una desmarca la anterior.

**B6. Selector de ciclo.** Un `ExposedDropdownMenuBox` con los cuatro ciclos (DAM, DAW, ASIR, SMR) y un `Text` debajo que muestre el elegido. El valor inicial debe ser DAM.

**B7. Confirmación de borrado.** Un `Button` "Borrar todo" que abra un `AlertDialog` modal con título "¿Borrar todo?", texto de apoyo, botón Aceptar (rojo) y Cancelar. Al aceptar, un contador visible en pantalla vuelve a 0 (pista: el contador suma +1 con otro botón "Añadir").

## Bloque C — Mini-proyectos (integración)

**C1. Formulario de registro completo.** Pantalla única con: nombre de usuario, correo, contraseña (con `PasswordVisualTransformation`), checkbox "Acepto los términos" y botón "Registrarse" **deshabilitado** hasta que el checkbox esté marcado y los tres campos tengan contenido (`enabled = acepta && usuario.isNotBlank() && ...`). Al pulsar, se muestra un `Text` grande "¡Registro completado!".

**C2. Conversor sencillo.** Un campo numérico (`KeyboardType.Number`), un `RadioButton` para elegir dirección (Euros→Dólares o Dólares→Euros) y un `Text` con el resultado que se actualiza al escribir (recuerda `toFloatOrNull()` por si el campo está vacío).

**C3. Login con navegación.** Reproduce el caso práctico 1 completo: pantalla de login (usuario/contraseña con admin/1234) que **navega** a una pantalla de bienvenida "¡Hola, [usuario]!" con un botón "Cerrar sesión" que hace `popBackStack()`. Añade la dependencia de Navigation. *(Sube de dificultad: pasa el nombre de usuario a la pantalla de bienvenida como argumento de ruta.)*

**C4. Reproductor de música.** Reproduce el caso práctico 2 con `LazyVerticalGrid` de 3 columnas y los 9 controles. *(Sube de dificultad: añade un `TopAppBar` con Scaffold y el título "Mi reproductor", y que el botón STOP abra un diálogo modal de confirmación.)*

**C5. La butaca del teatro.** Con `LazyVerticalGrid` de 10 columnas, pinta 30 butacas (3 filas) como `Checkbox` pequeños. Un `Text` debe contar en vivo las butacas seleccionadas y su precio total (12 € cada una). *(Sube de dificultad: marca 3 butacas como "no disponibles" con `enabled = false` desde el inicio.)*
