---
title: "UD 2 - Solucionario: Clases y componentes"
description: "Soluciones comentadas de los ejercicios del tema 2, con el enunciado citado antes de cada solución."
authors:
    - Ismael Velasco
date: 2026-09-26
icon: "material/check-circle"
permalink: /di/unidad2/solucionario
categories:
    - DI
tags:
    - DI
    - Kotlin
    - Jetpack Compose
---

# Solucionario UD 2 — Clases y componentes

*Cada solución va precedida de su enunciado. Intenta resolver antes de mirar: el solucionario es la última herramienta, no la primera.*

## Bloque A — Conceptos

> **A1.** Explica con tus palabras la diferencia entre un **Checkbox** y un **RadioButton**, y pon un ejemplo real de interfaz donde usarías cada uno.

**Solución.** El Checkbox es **independiente**: cada casilla tiene su propio estado y marcar una no afecta a las demás — se usa cuando las opciones son **compatibles** ("extras de tu hamburguesa: bacon ✓, queso ✓, cebolla ✗"). El RadioButton es **excluyente**: de todas las opciones solo puede haber una marcada, porque todos consultan la misma variable de estado — se usa para elecciones únicas ("talla: S ○ M ● L ○" o "forma de pago").

> **A2.** En Compose, ¿por qué `TextField` necesita obligatoriamente los parámetros `value` y `onValueChange` en pareja? ¿Qué pasaría si falta el segundo?

**Solución.** Porque el campo no guarda nada por sí mismo: lo que se muestra (`value`) vive en una **variable de estado** externa, y cada tecla que pulsa el usuario dispara `onValueChange` con el texto nuevo, que debe guardarse de vuelta en esa variable para redibujar el campo. Si faltara `onValueChange`, el campo se quedaría "congelado": mostraría el valor inicial y no aceptaría escritura, porque nada actualizaría el estado del que depende.

> **A3.** ¿Qué significa que un diálogo es **modal**? Pon un ejemplo de app real donde sea necesario ese comportamiento.

**Solución.** Que bloquea toda la interfaz hasta que el usuario lo responde: no se puede tocar nada más, la pantalla de atrás queda atenuada. Ejemplo real: el diálogo de confirmación de compra en una app de billetes — no quieres que el usuario pulse "comprar" y mientras tanto toque otra cosa y dupide el pedido. También el típico "¿Seguro que quieres salir? Se perderán los cambios".

> **A4.** Une con flechas cada necesidad con su contenedor.

**Solución.** Formulario en vertical → **Column**. Texto sobre una foto → **Box** (superpone). Botones Aceptar/Cancelar en línea → **Row**. Cuadrícula de iconos → **LazyVerticalGrid**.

## Bloque B — Componentes sueltos

> **B1. Tarjeta de presentación.** Crea un componible `MiTarjeta` que muestre tu nombre con `titleLarge` en negrita, tu ciclo con `bodyMedium` y tu instituto con `labelSmall` en gris, apilados en un `Column` centrado con `spacedBy(4.dp)`.

```kotlin
@Composable
fun MiTarjeta() {
    Column(
        modifier = Modifier.fillMaxSize(),
        verticalArrangement = Arrangement.Center,
        horizontalAlignment = Alignment.CenterHorizontally
    ) {
        Text("Ismael Velasco", style = MaterialTheme.typography.titleLarge, fontWeight = FontWeight.Bold)
        Spacer(modifier = Modifier.height(4.dp))
        Text("2º DAM — Desarrollo de Interfaces", style = MaterialTheme.typography.bodyMedium)
        Text("IES Rafael Alberti", style = MaterialTheme.typography.labelSmall, color = Color.Gray)
    }
}
```

**Comentarios.** `spacedBy` se aplica en `verticalArrangement` del Column; aquí añadimos además un Spacer extra tras el nombre. El gris con `Color.Gray` es aceptable para el ejercicio, aunque en proyecto real se usaría `MaterialTheme.colorScheme.outline`.

> **B2. Los tres botones.** Tres niveles de botón en una Row; un Text muestra el último pulsado.

```kotlin
@Composable
fun TresBotones() {
    var ultimo by remember { mutableStateOf("ninguno") }
    Column(
        modifier = Modifier.fillMaxSize(),
        verticalArrangement = Arrangement.Center,
        horizontalAlignment = Alignment.CenterHorizontally
    ) {
        Row(horizontalArrangement = Arrangement.spacedBy(12.dp)) {
            Button(onClick = { ultimo = "Guardar" }) { Text("Guardar") }
            OutlinedButton(onClick = { ultimo = "Cancelar" }) { Text("Cancelar") }
            TextButton(onClick = { ultimo = "Saltar" }) { Text("Saltar") }
        }
        Spacer(modifier = Modifier.height(16.dp))
        Text("Último pulsado: $ultimo", style = MaterialTheme.typography.bodyLarge)
    }
}
```

**Comentarios.** El estado `ultimo` es una sola variable de tipo String que los tres `onClick` actualizan. Como el Text la lee, cada pulsación redibuja el texto: el patrón evento → estado → UI funcionando con tres emisores distintos.

> **B3. Formulario con validación.** Email y teléfono; el botón solo actúa si email contiene @ y teléfono tiene 9 caracteres.

```kotlin
@Composable
fun FormularioValidacion() {
    var email by remember { mutableStateOf("") }
    var telefono by remember { mutableStateOf("") }
    val emailOk = email.contains("@") && email.isNotBlank()
    val telOk = telefono.length == 9 && telefono.all { it.isDigit() }

    Column(
        modifier = Modifier.fillMaxSize().padding(24.dp),
        verticalArrangement = Arrangement.Center
    ) {
        OutlinedTextField(
            value = email,
            onValueChange = { email = it },
            label = { Text("Email") },
            isError = email.isNotEmpty() && !emailOk,
            supportingText = {
                if (email.isNotEmpty() && !emailOk) Text("Debe contener una @")
            },
            modifier = Modifier.fillMaxWidth()
        )
        Spacer(modifier = Modifier.height(8.dp))
        OutlinedTextField(
            value = telefono,
            onValueChange = { telefono = it },
            label = { Text("Teléfono") },
            isError = telefono.isNotEmpty() && !telOk,
            supportingText = {
                if (telefono.isNotEmpty() && !telOk) Text("9 dígitos exactos")
            },
            keyboardOptions = KeyboardOptions(keyboardType = KeyboardType.Phone),
            modifier = Modifier.fillMaxWidth()
        )
        Spacer(modifier = Modifier.height(16.dp))
        Button(
            onClick = { /* registro correcto */ },
            enabled = emailOk && telOk,
            modifier = Modifier.fillMaxWidth()
        ) { Text("Enviar") }
    }
}
```

**Comentarios.** La clave: las condiciones `emailOk`/`telOk` se recalculan en cada recomposición (cada vez que cambia el estado), así que `isError`, `supportingText` y `enabled` reaccionan solos. No hay botón "comprobar": la validación es en vivo, que es el estándar moderno.

> **B4. Encuesta con checkboxes.** 5 opciones y contador en vivo.

```kotlin
@Composable
fun Encuesta() {
    val dispositivos = listOf("PC de sobremesa", "Portátil", "Móvil", "Tablet", "Otro")
    val marcadas = remember { mutableStateListOf<String>() }

    Column(modifier = Modifier.padding(24.dp)) {
        Text("¿Qué usas para programar?", style = MaterialTheme.typography.titleMedium)
        Spacer(modifier = Modifier.height(12.dp))
        dispositivos.forEach { disp ->
            Row(verticalAlignment = Alignment.CenterVertically) {
                Checkbox(
                    checked = disp in marcadas,
                    onCheckedChange = { marcar ->
                        if (marcar) marcadas.add(disp) else marcadas.remove(disp)
                    }
                )
                Text(disp)
            }
        }
        Spacer(modifier = Modifier.height(12.dp))
        Text(
            "Dispositivos marcados: ${marcadas.size} de ${dispositivos.size}",
            style = MaterialTheme.typography.bodyLarge
        )
    }
}
```

**Comentarios.** `mutableStateListOf` es una lista observable: añadir o quitar elementos dispara la recomposición, y el contador se actualiza solo. `disp in marcadas` es la comprobación de pertenencia idiomática de Kotlin.

> **B5. Talla con radio buttons.** S/M/L excluyentes con texto en vivo.

```kotlin
@Composable
fun Tallas() {
    val tallas = listOf("S", "M", "L")
    var elegida by remember { mutableStateOf("M") }

    Column(modifier = Modifier.padding(24.dp)) {
        Text("Elige tu talla", style = MaterialTheme.typography.titleMedium)
        Spacer(modifier = Modifier.height(12.dp))
        tallas.forEach { talla ->
            Row(verticalAlignment = Alignment.CenterVertically) {
                RadioButton(
                    selected = talla == elegida,
                    onClick = { elegida = talla }
                )
                Text(talla)
            }
        }
        Spacer(modifier = Modifier.height(12.dp))
        Text("Talla elegida: $elegida")
    }
}
```

**Comentarios.** Una sola variable `elegida` compartida por los tres botones: `selected` compara y `onClick` sobrescribe. La exclusividad no la da ningún objeto agrupador: la da compartir el estado. (El valor inicial "M" demuestra que se puede preseleccionar.)

> **B6. Selector de ciclo.** Desplegable con los cuatro ciclos, valor inicial DAM.

```kotlin
@OptIn(ExperimentalMaterial3Api::class)
@Composable
fun SelectorCiclo() {
    val ciclos = listOf("DAM", "DAW", "ASIR", "SMR")
    var expandido by remember { mutableStateOf(false) }
    var seleccion by remember { mutableStateOf(ciclos[0]) }   // inicial: DAM

    Column(modifier = Modifier.padding(24.dp)) {
        ExposedDropdownMenuBox(
            expanded = expandido,
            onDismissRequest = { expandido = false }
        ) {
            OutlinedTextField(
                value = seleccion,
                onValueChange = { },
                readOnly = true,
                label = { Text("Ciclo") },
                trailingIcon = { ExposedDropdownMenuDefaults.TrailingIcon(expanded = expandido) },
                modifier = Modifier.menuAnchor()
            )
            ExposedDropdownMenu(
                expanded = expandido,
                onDismissRequest = { expandido = false }
            ) {
                ciclos.forEach { ciclo ->
                    DropdownMenuItem(
                        text = { Text(ciclo) },
                        onClick = {
                            seleccion = ciclo
                            expandido = false
                        }
                    )
                }
            }
        }
        Spacer(modifier = Modifier.height(12.dp))
        Text("Ciclo seleccionado: $seleccion")
    }
}
```

**Comentarios.** `readOnly = true` impide escribir en la caja (solo se elige de la lista). El "valor por defecto" se consigue inicializando el estado con `ciclos[0]`, sin necesidad de índices: es la traducción del selectedIndex clásico al mundo del estado.

> **B7. Confirmación de borrado.** Botón Borrar todo → AlertDialog; contador visible vuelve a 0.

```kotlin
@Composable
fun ConfirmarBorrado() {
    var contador by remember { mutableIntStateOf(0) }
    var mostrarDialogo by remember { mutableStateOf(false) }

    Column(
        modifier = Modifier.fillMaxSize(),
        verticalArrangement = Arrangement.Center,
        horizontalAlignment = Alignment.CenterHorizontally
    ) {
        Text("Elementos: $contador", style = MaterialTheme.typography.headlineMedium)
        Spacer(modifier = Modifier.height(16.dp))
        Row(horizontalArrangement = Arrangement.spacedBy(12.dp)) {
            Button(onClick = { contador++ }) { Text("Añadir") }
            OutlinedButton(onClick = { mostrarDialogo = true }) { Text("Borrar todo") }
        }
    }

    if (mostrarDialogo) {
        AlertDialog(
            onDismissRequest = { mostrarDialogo = false },
            title = { Text("¿Borrar todo?") },
            text = { Text("Se eliminarán los $contador elementos. Esta acción no se puede deshacer.") },
            confirmButton = {
                TextButton(onClick = {
                    contador = 0
                    mostrarDialogo = false
                }) { Text("Aceptar", color = MaterialTheme.colorScheme.error) }
            },
            dismissButton = {
                TextButton(onClick = { mostrarDialogo = false }) { Text("Cancelar") }
            }
        )
    }
}
```

**Comentarios.** La receta del diálogo al completo: estado booleano + `if` + `AlertDialog`. El `confirmButton` ejecuta DOS acciones (poner el contador a 0 y cerrar el diálogo) — las lambdas aceptan todas las líneas que necesites.

## Bloque C — Mini-proyectos

> **C1. Formulario de registro completo.** Campos + checkbox términos + botón deshabilitado hasta cumplir condiciones.

```kotlin
@Composable
fun Registro() {
    var usuario by remember { mutableStateOf("") }
    var correo by remember { mutableStateOf("") }
    var password by remember { mutableStateOf("") }
    var acepta by remember { mutableStateOf(false) }
    var registrado by remember { mutableStateOf(false) }

    val formularioOk = usuario.isNotBlank() && correo.contains("@")
            && password.length >= 6 && acepta

    Column(
        modifier = Modifier.fillMaxSize().padding(24.dp),
        verticalArrangement = Arrangement.Center
    ) {
        if (registrado) {
            Text("¡Registro completado! 🎉", style = MaterialTheme.typography.headlineSmall)
            Spacer(modifier = Modifier.height(8.dp))
            Text("Bienvenido, $usuario")
        } else {
            OutlinedTextField(value = usuario, onValueChange = { usuario = it },
                label = { Text("Usuario") }, modifier = Modifier.fillMaxWidth())
            Spacer(modifier = Modifier.height(8.dp))
            OutlinedTextField(value = correo, onValueChange = { correo = it },
                label = { Text("Correo") }, modifier = Modifier.fillMaxWidth())
            Spacer(modifier = Modifier.height(8.dp))
            OutlinedTextField(value = password, onValueChange = { password = it },
                label = { Text("Contraseña") },
                visualTransformation = PasswordVisualTransformation(),
                supportingText = { Text("Mínimo 6 caracteres") },
                modifier = Modifier.fillMaxWidth())
            Spacer(modifier = Modifier.height(8.dp))
            Row(verticalAlignment = Alignment.CenterVertically) {
                Checkbox(checked = acepta, onCheckedChange = { acepta = it })
                Text("Acepto los términos")
            }
            Spacer(modifier = Modifier.height(16.dp))
            Button(
                onClick = { registrado = true },
                enabled = formularioOk,
                modifier = Modifier.fillMaxWidth()
            ) { Text("Registrarse") }
        }
    }
}
```

**Comentarios.** La expresión `formularioOk` se reevalúa sola en cada cambio de estado: el botón se hababilita en el momento exacto en que se cumplen las 4 condiciones, sin escribir ningún "comprobador". El `if (registrado)` cambia toda la pantalla por la de éxito — primer paso hacia la navegación condicional.

> **C2. Conversor sencillo.** Campo numérico + radio de dirección + resultado en vivo.

```kotlin
@Composable
fun Conversor() {
    var cantidad by remember { mutableStateOf("") }
    var aDolares by remember { mutableStateOf(true) }   // true: €→$, false: $→€
    val CAMBIO = 1.08

    val resultado = cantidad.toFloatOrNull()?.let { if (aDolares) it * CAMBIO else it / CAMBIO }

    Column(
        modifier = Modifier.fillMaxSize().padding(24.dp),
        verticalArrangement = Arrangement.Center
    ) {
        OutlinedTextField(
            value = cantidad,
            onValueChange = { cantidad = it },
            label = { Text("Cantidad") },
            keyboardOptions = KeyboardOptions(keyboardType = KeyboardType.Decimal),
            modifier = Modifier.fillMaxWidth()
        )
        Spacer(modifier = Modifier.height(12.dp))
        listOf(true to "Euros → Dólares", false to "Dólares → Euros").forEach { (dir, etiqueta) ->
            Row(verticalAlignment = Alignment.CenterVertically) {
                RadioButton(selected = aDolares == dir, onClick = { aDolares = dir })
                Text(etiqueta)
            }
        }
        Spacer(modifier = Modifier.height(16.dp))
        Text(
            text = resultado?.let { "%.2f".format(it) } ?: "—",
            style = MaterialTheme.typography.headlineMedium
        )
    }
}
```

**Comentarios.** `toFloatOrNull()` devuelve null si el texto no es número (vacío incluido), y `?.let { ... }` solo calcula si hay número; el `?:` muestra el guión mientras no. El patrón de dos radio buttons con booleanos (`dir`) simplifica el estado a un solo Boolean.

> **C3. Login con navegación.** Caso práctico 1 completo + argumento de ruta (subida).

```kotlin
// 1) NavHost con dos rutas, la segunda acepta argumento
@Composable
fun AppNavegacion() {
    val navController = rememberNavController()
    NavHost(navController = navController, startDestination = "login") {
        composable("login") { PantallaLogin(navController) }
        composable(
            "bienvenida/{usuario}",
            arguments = listOf(navArgument("usuario") { defaultValue = "invitado" })
        ) { backStackEntry ->
            PantallaBienvenida(
                usuario = backStackEntry.arguments?.getString("usuario") ?: "invitado",
                navController = navController
            )
        }
    }
}

// 2) El login navega pasando el dato
Button(onClick = {
    if (usuario == "admin" && password == "1234") {
        navController.navigate("bienvenida/$usuario")
    } else error = true
}) { Text("Inicio") }

// 3) La bienvenida recibe el dato y puede volver
@Composable
fun PantallaBienvenida(usuario: String, navController: NavController) {
    Column(
        modifier = Modifier.fillMaxSize(),
        verticalArrangement = Arrangement.Center,
        horizontalAlignment = Alignment.CenterHorizontally
    ) {
        Text("👋 ¡Hola, $usuario!", style = MaterialTheme.typography.headlineMedium)
        Spacer(modifier = Modifier.height(16.dp))
        OutlinedButton(onClick = { navController.popBackStack() }) {
            Text("Cerrar sesión")
        }
    }
}
```

**Comentarios.** La subida de dificultad: la ruta "bienvenida/{usuario}" declara un **argumento**; al navegar se interpola en la URL ("bienvenida/admin") y la pantalla destino lo recupera con `arguments?.getString`. Es el mecanismo estándar para pasar datos entre pantallas sin variables globales.

> **C4. Reproductor de música.** Caso práctico 2 + Scaffold + diálogo en STOP (subida).

```kotlin
@OptIn(ExperimentalMaterial3Api::class)
@Composable
fun Reproductor() {
    val controles = listOf("ON/OFF", "PLAY", "RECORD", "⏮ ANTE.", "PAUSE", "SIG. ⏭", "⏪ ATRÁS", "STOP", "ADE. ⏩")
    var confirmarStop by remember { mutableStateOf(false) }

    Scaffold(
        topBar = { TopAppBar(title = { Text("Mi reproductor") }) }
    ) { innerPadding ->
        LazyVerticalGrid(
            columns = GridCells.Fixed(3),
            modifier = Modifier.padding(innerPadding).fillMaxSize().padding(8.dp),
            verticalArrangement = Arrangement.spacedBy(8.dp),
            horizontalArrangement = Arrangement.spacedBy(8.dp)
        ) {
            items(controles) { control ->
                Button(
                    onClick = { if (control == "STOP") confirmarStop = true },
                    modifier = Modifier.fillMaxWidth()
                ) { Text(control, fontSize = 11.sp) }
            }
        }
    }

    if (confirmarStop) {
        AlertDialog(
            onDismissRequest = { confirmarStop = false },
            title = { Text("¿Detener reproducción?") },
            text = { Text("La música dejará de sonar.") },
            confirmButton = {
                TextButton(onClick = { confirmarStop = false /* parar */ }) { Text("Sí, parar") }
            },
            dismissButton = {
                TextButton(onClick = { confirmarStop = false }) { Text("Seguir sonando") }
            }
        )
    }
}
```

**Comentarios.** Integración de tres piezas del tema: Scaffold aporta la cabecera, la rejilla coloca los 9 botones y el diálogo modal protege la acción destructiva (STOP). El `innerPadding` del Scaffold se aplica a la rejilla para no quedar tapada por la cabecera — el detalle que siempre se olvida.

> **C5. La butaca del teatro.** Rejilla de 30 butacas con contador y precio (subida: butacas no disponibles).

```kotlin
@Composable
fun Teatro() {
    val noDisponibles = setOf(4, 11, 23)          // índices de butacas ocupadas
    val seleccionadas = remember { mutableStateListOf<Int>() }
    val PRECIO = 12.0

    Column(modifier = Modifier.fillMaxSize().padding(16.dp)) {
        Text("Elige tus butacas", style = MaterialTheme.typography.titleLarge)
        Spacer(modifier = Modifier.height(12.dp))
        LazyVerticalGrid(
            columns = GridCells.Fixed(10),
            verticalArrangement = Arrangement.spacedBy(4.dp),
            horizontalArrangement = Arrangement.spacedBy(4.dp),
            modifier = Modifier.weight(1f)
        ) {
            items(30) { i ->
                val ocupada = i in noDisponibles
                Checkbox(
                    checked = i in seleccionadas,
                    onCheckedChange = { marcar ->
                        if (marcar) seleccionadas.add(i) else seleccionadas.remove(i)
                    },
                    enabled = !ocupada                        // gris si está ocupada
                )
            }
        }
        Spacer(modifier = Modifier.height(8.dp))
        Text(
            "${seleccionadas.size} butacas — Total: %.2f €".format(seleccionadas.size * PRECIO),
            style = MaterialTheme.typography.titleMedium
        )
    }
}
```

**Comentarios.** La butaca es un Checkbox cuya identidad es su índice (0-29). La subida de dificultad son las butacas `enabled = false`: aparecen grises y no responden, exactamente el comportamiento "no disponible". El precio total se recalcula en cada recomposición porque `seleccionadas.size` es estado observado.
