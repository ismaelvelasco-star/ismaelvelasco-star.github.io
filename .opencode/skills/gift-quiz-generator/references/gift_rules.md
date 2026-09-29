# Reglas para archivos GIFT

## Requisitos mínimos

- Si no te indican el número, crear al menos 15 preguntas por tema.
- Usar 4 opciones y una sola correcta. La primera será la correcta. 
- Redactar en español de España.
- Basar las preguntas en la teoría asociada.
- Priorizar escenarios prácticos y realistas. Supuestos prácticos.
- Caracteres que deben ser escapados si alguno aparece en una pregunta o en una respuesta: [:, {, }, #, ~, =, %]
- Las respuestas incorrectas restán -33.3333%

## Estructura base

```gift
::RA_X.CE_Y. Descripción breve sobre la tematica de la pregunta::
Pregunta o supuesto práctico {
=Respuesta correcta #Feedback correcto.
~%-33.3333%Distractor 1 #Feedback incorrecto.
~%-33.3333%Distractor 2 #Feedback incorrecto.
~%-33.3333%Distractor 3 #Feedback incorrecto.
}
```

## Reglas duras

- Los distractores deben parecer razonables.
- El feedback debe explicar por qué cada opción es correcta o incorrecta.
- Escapar como literales los caracteres conflictivos si aparecen dentro del
  contenido textual.
- Guardar en `docs/sectionX/uXX/gift/` con el mismo nombre base de la teoría.

### Reglas sobre distractores
Cada distractor debe cumplir TODAS estas reglas:

#### 1. VEROSIMILITUD MÁXIMA
   - Debe sonar técnicamente correcto para alguien con conocimiento superficial
   - Usa terminología real del dominio, no términos inventados
   - Basa los distractores en errores conceptuales REALES que cometen profesionales
   - Incluye al menos un distractor que sea "parcialmente cierto pero incompleto"

#### 2. LONGITUD Y ESTRUCTURA SIMILAR
   - Todas las opciones deben tener longitud parecida (±5 palabras)
   - Misma estructura gramatical (todas empiezan con verbo, o todas con sustantivo)
   - Evita que la correcta sea notablemente más larga o detallada

#### 3. EVITA PATRONES DELATORES
   - NO uses "todas las anteriores" o "ninguna de las anteriores"
   - NO hagas la correcta más específica o matizada que las otras
   - NO uses lenguaje absoluto ("siempre", "nunca", "completamente") solo en distractores
   - NO hagas que un distractor sea obviamente absurdo o cómico

#### 4. TIPOS DE DISTRACORES A INCLUIR
Crea 3 distractores, cada uno basado en un error diferente:
   - **Distractor A - Error de confusión conceptual:**
      - Confunde conceptos relacionados pero distintos (ej: táctica vs técnica, detección vs prevención)
   - **Distractor B - Verdad parcial:**
      - Contiene información correcta pero aplicada al contexto equivocado o incompleta
   - **Distractor C - Solución plausible pero incorrecta:**
      - Una medida que tendría sentido en otro contexto pero no responde a ESTA pregunta específica

#### 5. FEEDBACK FORMATIVO
Cada opción (correcta e incorrectas) debe incluir feedback que:
   - Explique POR QUÉ es correcta/incorrecta
   - Mencione el concepto clave que la invalida (si es incorrecta)
   - Sea específico, no genérico ("Incorrecto porque X es Y" no "Incorrecto, revisa el tema")

### Estructura de la pregunta
      
1. **Enunciado:** Supuesto práctico realista (2-4 líneas) que requiera aplicar conocimiento, no solo recordar
2. **Opción correcta:** Debe ser claramente la MEJOR respuesta, no solo "una respuesta correcta"
3. **3 Distractores:** Siguiendo las reglas anteriores
4. **Feedback:** Para cada opción

:, {, }, #, ~, =, %, 
## Referencia de pregunta y distractores 

Aquí tienes un ejemplo de pregunta con distractores de élite, aplicando
todas las reglas del prompt:

    ---

      ::Grupo4-Metodologia. ContencionEvidencias. RansomwareActivo:: 
        Durante la investigación de un incidente de ransomware, el equipo 
        detecta cifrado activo en un servidor de ficheros crítico con 50TB 
        de datos. Un analista junior propone apagar inmediatamente el 
        servidor para detener el cifrado. Simultáneamente, otro analista 
        sugiere aislar la VLAN completa manteniendo los sistemas encendidos.
        El CISO pregunta qué enfoque preserva mejor la capacidad de 
        investigación mientras limita el daño. ¿Qué respuesta es 
        técnicamente más precisa? {
          =Aislar la VLAN completa mantiene evidencias en memoria volátil,
        permite captura de tráfico C2 y evita mecanismos destructivos que 
        algunos ransomware activan al detectar pérdida de conectividad.
          #Correcto. El aislamiento de red contiene el ataque preservando 
        memoria (procesos, claves, conexiones), tráfico para análisis y 
        evita triggers destructivos por pérdida de conexión.
          ~%-33.3333%Apagar inmediatamente el servidor porque el cifrado 
        de 50TB causará más daño operacional que perder evidencias en 
        memoria, priorizando continuidad de negocio sobre investigación 
        forense.
          #Incorrecto. Aunque la continuidad es importante, apagar 
        destruye evidencias críticas (memoria volátil con procesos, 
        conexiones activas, posibles claves de cifrado); el aislamiento 
        contiene SIN destruir evidencias.
          ~%-33.3333%Aislar la VLAN es correcto pero solo si previamente 
        se ha configurado mirror de puertos en los switches para capturar 
        todo el tráfico antes de que el atacante detecte el aislamiento y 
        active contramedidas.
          #Incorrecto. El mirror de puertos es útil pero NO es requisito 
        previo para aislar; esperar a configurar mirror da tiempo al 
        atacante para propagarse o exfiltrar; el aislamiento inmediato es 
        prioritario.
          ~%-33.3333%Apagar el servidor es preferible porque el ransomware
        moderno cifra tan rápidamente que incluso aislar la VLAN permite 
        varios gigabytes de cifrado adicional durante el tiempo de 
        propagación de la configuración de red.
          #Incorrecto. Aunque el cifrado es rápido, la propagación de 
        reglas de aislamiento en switches modernos toma segundos; el daño 
        adicional es mínimo comparado con el valor de preservar memoria y tr
        áfico para investigación.
      }

    ---

  Análisis de por qué estos distractores son de élite:

  Distractor 1 - Error de prioridad (Continuidad vs Forense)
   - ✅ Suena razonable: priorizar negocio sobre investigación es argumento válido en otros contextos
   - ✅ Usa terminología real: "daño operacional", "continuidad de negocio", "investigación forense"
   - ✅ Error sutil: presenta falso dilema cuando hay opción que preserva AMBOS objetivos
   - ❌ Pero es incorrecto: el aislamiento logra contención SIN sacrificar evidencias

  Distractor 2 - Verdad parcial (Mirror de puertos)
   - ✅ Contiene verdad técnica: mirror de puertos SÍ es útil para capturar tráfico
   - ✅ Suena experto: menciona configuración específica de switches
   - ✅ Error sutil: convierte condición útil en requisito obligatorio
   - ❌ Pero es incorrecto: el mirror es opcional, el aislamiento es prioritario e inmediato

  Distractor 3 - Exageración técnica (Velocidad de cifrado)
   - ✅ Usa dato real: ransomware moderno cifra rápidamente
   - ✅ Parece conocimiento actualizado: "gigabytes de cifrado adicional"
   - ✅ Error sutil: exagera tiempos reales de propagación de aislamiento
   - ❌ Pero es incorrecto: switches modernos propagan ACLs en segundos, mucho más rápido que cifrado de 50TB


## Referencia real del repositorio

- `docs/section2/u02/gift/IS-U2.4.1.-DocumentacionDeIncidentes.gift`
