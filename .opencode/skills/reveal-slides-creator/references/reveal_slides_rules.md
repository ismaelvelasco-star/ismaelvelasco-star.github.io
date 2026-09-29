# Reglas y plantillas rápidas para Reveal.js

## Mapeo de módulos y rutas

| Docs       | Slides                | Prefijo |
|------------|-----------------------|---------|
| `section1` | `slides/section1-pr`  | `PR`    |
| `section2` | `slides/section2-is`  | `IS`    |
| `section3` | `slides/section3-ed`  | `ED`    |
| `section4` | `slides/section4-daw` | `DAW`   |

## Plantilla de referencia mínima de slides Markdown

```markdown
# MODULO-UX.Y - Título

---

## 1. Sección

Note: Introducir la sección y el objetivo de lo que se va a tratar. 

### 1.1. Concepto I

* Punto clave 1
* Punto clave 2
* Punto clave 3

Note: {En este punto vamos a explicar **conceptos clave** del punto, matices y ejemplo práctico. Tiene que ser una guía para el profesor sobre lo que tiene que hablar en la slide. Un texto que el profesor podria leer directamente, tienes que estár redactadas como guion de voz docente}


### 1.2. Concepto II

* Punto clave 1
* Punto clave 2

Note: {Ampliar con caso de uso real y errores frecuentes. Igualmente tiene que guiar al profesor. Un texto que el profesor podria leer directamente. Tiene que estár redactadas como guion de voz docente}

---
```
## Reglas sobre Note

Las notas deben ser un **guion de aula de voz docente**, con conceptos en negrita y cursiva para las ideas clave, y redactadas como si el profesor las fuera a leer directamente. No como
instrucciones internas para el docente o para el agente. Tampoco deben ser un texto técnico, sino una explicación clara y didáctica de lo que el profesor debe decir en cada slide.

Las notas `Note:` deben redactarse como **guion de aula**, deben poder leerse directamente en clase y seguir la línea argumental de la presentación.

Cada nota debe:

- explicar lo más importante de la slide;
- destacar lo que realmente sobresale de la slide;
- conectar con lo visto antes y preparar la idea siguiente;
- usar tono docente, directo y natural;
- evitar fórmulas como:
  - "Explica que...";
  - "Recalca...";
  - "Introduce...";
  - "Indica...";
  - "Usa esta slide para...".

Formato de énfasis:
- usar `**negrita**` para conceptos importantes;
- usar `_cursiva_` para ideas clave, énfasis o mensajes que deben quedar claros;
- no abusar del resaltado: solo marcar lo que ayude a guiar la explicación.

Ejemplo recomendado:

```markdown
Note: Como estamos viendo, en una crisis se necesita _simplicidad y disciplina_. Las acciones de la slide ayudan a no perder el control cuando el incidente escala. Por ejemplo, **registrar hechos y decisiones** permite dejar constancia de información que podría olvidarse en un momento de presión. También es importante **preservar evidencias**, porque permitirá investigar después con más detalle y sin perder datos relevantes.
```

Ejemplo no recomendado:

```markdown
Note: Explica que en una crisis se necesita simplicidad y disciplina. Recalca que registrar hechos y preservar evidencias es importante.
```

## Reglas duras
- `---` solo separa secciones.
- 2 líneas en blanco solo separan slides dentro de una sección.
- Todas las slides llevan `Note:`.
- Las notas deben estar en una única linea, con las ideas claves en negrita y estár redactadas como guion de voz docente.
- Máximo 7 viñetas por slide.
- Longitud objetivo por línea: <= 80 caracteres.
- Incorporar recursos didácticos siempre que aporten comprensión. Si la teoría
  contiene imágenes aclaratorias, copiarlas obligatoriamente a `assets/` de la
  carpeta de slides y enlazarlas con `assets/nombre-del-recurso.ext`. Nunca
  enlazar desde una slide un asset ubicado en `docs/`.
- Para adaptar tamaño de las imágenes: añadir seguido EN LA MISMA LINEA de la URL lo siguiente `<!-- .element: style="max-width: 50%;" -->`
- Para adaptar el tamaño de las tablas: añadir justo debajo de la tabla `<!-- .element.table: style="font-size:70%;" -->`
- Numeración:
   - Usar `# Titulo ` para título principal.
   - Usar `## X. Titulo` para inicio de sección. Punto X 
   - Usar `### X.Y. Titulo` para cada slide de contenido. Punto X.Y
- La estructura será:
   - slide del título.
   - slide del logo [Logo Alberti]
   - slides del índice.
   - slides del contexto y objetivo de la unidad.
   - slides del contenido.
   - slides resumen, ideas clave y conclusion.
- Las notas (`Note:`) deben ser un guion de voz docente, con las ideas clave en negrita, y redactadas como si el profesor las fuera a leer directamente.

## Esqueleto HTML Reveal.js

```html
<!doctype html>
<html lang="es">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>MODULO-UX.Y.-Tema</title>
  <link rel="stylesheet" href="../dist/reset.css">
  <link rel="stylesheet" href="../dist/reveal.css">
  <link rel="stylesheet" href="../dist/theme/black.css" id="theme">
  <link rel="stylesheet" href="../plugin/highlight/monokai.css">
  <link rel="stylesheet" href="../custom.css">
</head>
<body>
  <div class="reveal">
    <div class="slides">
      <!-- secciones/diapositivas -->
    </div>
  </div>
  <script src="../dist/reveal.js"></script>
  <script src="../plugin/notes/notes.js"></script>
  <script src="../plugin/markdown/markdown.js"></script>
  <script src="../plugin/highlight/highlight.js"></script>
  <script>
    Reveal.initialize({
      margin: 0.1,
      progress: true,
      slideNumber: 'c/t',
      showSlideNumber: 'all',
      hash: true,
      plugins: [ RevealMarkdown, RevealHighlight, RevealNotes ]
    });
  </script>
</body>
</html>
```

## Checklist de enlazado en documentación

1. `docs/sectionX/uYY/teoria/MODULO-UX.Y.-Tema.md`
2. `docs/sectionX/uYY/index.md`
3. `docs/sectionX/index.md`
4. `docs/index.md`

Formato de URL:
- `https://revilofe.github.io/slides/section1-pr/PR-UX.Y.-Tema.html`
- `https://revilofe.github.io/slides/section2-is/IS-UX.Y.-Tema.html`
- `https://revilofe.github.io/slides/section3-ed/ED-UX.Y.-Tema.html`
- `https://revilofe.github.io/slides/section4-daw/DAW-UX.Y.-Tema.html`


## Ejemplo de referencia directo 

Sigue este formato de ejemplo como plantilla: 

```markdown

# DAW-U5.1 - Servidores de aplicaciones

---

![Logo Alberti](assets/logo-iesra.png) <!-- .element height="50%" -->

---

## Índice

Note: En esta presentación vamos a ver, paso a paso, qué es un **servidor de
aplicaciones**, cómo encaja en una arquitectura web, y cómo se **despliegan**
aplicaciones de forma segura. El objetivo es que el alumnado entienda el
enfoque del **RA3**: implantar, configurar con seguridad, probar y documentar.


### Índice I

- 5.1. Servidores de aplicaciones (contexto y objetivo)
- 1. RA3 y criterios de evaluación
- 2. Concepto y papel del servidor de aplicaciones
- 3. Servidor web vs servidor de aplicaciones

Note: En esta primera parte ubicamos el tema: venimos de ver **HTTP** y
**servidores web**, y ahora damos el salto al servidor de aplicaciones. Luego
aterrizamos el **RA3** y pasamos al núcleo: definición, terminología y por qué
se usa. Cerraremos con el flujo de peticiones y la comparación entre capas.


### Índice II

- 4. Despliegue: entornos, proceso y tipos
- 5. Buenas prácticas de despliegue
- 6. Despliegue de aplicaciones Java (WAR, Maven, Gradle)
- 7. Despliegue Node.js con Express (npm)
- 8. CI/CD en el despliegue moderno
- 9. Evidencias típicas para evaluar el RA3

Note: En esta segunda parte conectamos el servidor de aplicaciones con el
trabajo real: **despliegues** por entornos, buenas prácticas y ejemplos en
**Java** y **Node.js**. Terminamos con **CI/CD** para automatizar, y con la
lista de **evidencias** que suelen pedirse para demostrar el RA3.

---

## 5.1. Servidores de aplicaciones

Note: Abrimos la unidad 5.1. Venimos de la unidad 3, donde ya trabajamos la
base de arquitecturas web, **HTTP/HTTPS** y servidores web. Aquí damos un paso
más: el **servidor de aplicaciones** como pieza clave para ejecutar lógica,
aplicar seguridad, gestionar sesiones y desplegar de forma profesional.


### Contexto y objetivo de la unidad

- Partimos de servidores web y HTTP/HTTPS (unidad 3)
- Añadimos el servidor de aplicaciones como capa de negocio
- Enfoque práctico: configuración, seguridad y pruebas
- Meta: servicio estable, seguro y escalable

Note: Esta unidad busca que el alumnado vea el servidor de aplicaciones como
una capa que aporta **servicios comunes**: sesiones, seguridad, recursos,
transacciones o logs. La idea clave es separar responsabilidades: el servidor
web sirve estático y hace de frontal; el servidor de aplicaciones **procesa**
la lógica de negocio y se integra con la base de datos.

---

## 1. Resultado de aprendizaje y criterios de evaluación (RA3)

Note: En esta sección conectamos el temario con la evaluación. El **RA3** pide
que el alumnado sea capaz de **implantar** una aplicación en un servidor de
aplicaciones, **configurar** con seguridad, **probar** y **documentar** el
proceso. Esto guía qué vamos a practicar y qué evidencias se piden.


### RA3: qué se espera del alumnado

- Implantar aplicaciones web en un servidor de aplicaciones
- Configurar el servidor con criterios de **seguridad**
- Ajustar parámetros y verificar el despliegue
- Documentar administración y recomendaciones

Note: Cuando decimos RA3, hablamos de un ciclo completo: no es solo "subir un
archivo". Implica entender componentes del servidor, tocar configuración,
activar medidas de **seguridad**, comprobar que funciona y dejar una
documentación que permita repetir la instalación sin improvisar.


### 1.1. Criterios de evaluación asociados I

- a) Componentes y funcionamiento de servicios
- b) Ficheros de configuración y librerías compartidas
- c) Cooperación con servidor web (proxy / reverse proxy)
- d) Mecanismos de seguridad del servidor de aplicaciones
- e) Componentes web del servidor (contenedor, etc.)

Note: Estos criterios son la "lista de comprobación" del RA3. Primero,
conocemos qué piezas tiene el servidor y cómo funcionan (**a**). Luego, dónde
se configura (**b**), cómo se integra con el servidor web (**c**), y qué
seguridad hay que activar (**d**). También se valora usar correctamente los
componentes web del servidor (**e**).

---

## 2. Concepto y papel del servidor de aplicaciones

Note: Aquí definimos qué es un servidor de aplicaciones y por qué se usa. La
idea principal: es un **middleware** entre el cliente y los datos que aporta
servicios comunes para que la aplicación no los reimplemente una y otra vez.


### 2.1. Definición y ubicación en la arquitectura

- Plataforma software para **ejecutar** aplicaciones web
- Aporta sesiones, seguridad, transacciones, recursos y logs
- Suele ubicarse entre servidor web y base de datos

![Arquitectura](assets/application-server1.webp) <!-- .element: style="max-width: 50%;" -->

Note: Un servidor de aplicaciones es un entorno donde corre nuestra app y que
añade servicios de infraestructura. Se coloca entre el servidor web y la base
de datos para procesar peticiones dinámicas y ejecutar la **lógica de negocio**
de forma controlada. Fijaos en la separación de capas: cada una tiene su rol.


### 2.2. Terminología básica

| Término           | Idea clave               |
|-------------------|--------------------------|
| Servidor web      | Estático + HTTP/HTTPS    |
| Cliente web       | Navegador o app          |
| HTTPS             | Canal cifrado            |
| JSON              | Intercambio de datos     |
| Lógica de negocio | Reglas del dominio       |
| Aplicación        | Presenta y consume datos |
<!-- .element.table: style="font-size:70%;" -->

Note: Esta tabla nos da vocabulario común. **Servidor web** suele servir
estático y actuar como frontal. El **cliente** pide recursos. **HTTPS** es
cifrado y autenticidad del canal. **JSON** es el formato típico en APIs. La
**lógica de negocio** son reglas del dominio. Y la **aplicación** orquesta y
presenta datos al usuario.


---

```

## Ejemplo de referencia 
`slides/section4-daw/DAW-U5.1.-ServidoresAplicaciones.md`
