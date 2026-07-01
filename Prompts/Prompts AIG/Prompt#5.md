# Instrucciones de Generación de Evaluación

**Rol:** Actúa como un experto en diseño de evaluaciones educativas (enfocado en metodologías activas, evaluación por competencias y psicometría aplicada).
**Tarea:** Generar un conjunto de [NÚMERO] preguntas de tipo test basándote **únicamente** en el documento proporcionado.
**Nivel educativo / perfil del estudiante:** [INDICA AQUÍ EL NIVEL]
**Materia/Asignatura:** [INDICA AQUÍ LA MATERIA, EJ: PROGRAMACIÓN PYTHON, HISTORIA, MATEMÁTICAS]

## Protocolo de Ejecución
Para construir cada una de las preguntas, debes aplicar obligatoriamente las siguientes directrices:

1. **Fidelidad al Contexto:** No utilices conocimientos externos. La base de datos es exclusivamente el texto suministrado.
2. **Representatividad:** Asegúrate de que las preguntas constituyan una muestra fiel y representativa de los contenidos clave de la materia. Evita estrictamente generar ítems sobre detalles triviales, anecdóticos, notas al pie o memoria puramente fotográfica.
3. **Ajuste psicométrico y técnico:** Adapta la complejidad de la pregunta y su formato de expresión (formal, verbal, numérico, gráfico o código) a la naturaleza de la materia. 
   * *Para Ciencias/Programación:* Si el enunciado o las opciones contienen fragmentos de código, expresiones matemáticas o fórmulas, debes asegurarte de que estén correctamente formateados y perfectamente escapados para no romper la sintaxis JSON (utiliza `\n` para saltos de línea y escapa las comillas internas `\"` si es necesario).
4. **Foco en el enunciado:** Coloca el núcleo central de la idea y de la información en el enunciado de la pregunta. Diseña las opciones de respuesta como complementos cortos que guarden una perfecta concordancia gramatical, sintáctica y semántica con dicho enunciado.
5. **Claridad gramatical y afirmación:** Redacta con una sintaxis correcta, directa, sin ambigüedades. Expresa el enunciado de forma **afirmativa**. Evita el uso de negaciones (como "NO" o "EXCEPTO"); si por extrema necesidad incluyes una negación, destácala claramente en MAYÚSCULAS y **NEGRITA**.
6. **Ajuste semántico:** Utiliza un vocabulario preciso y un nivel de lenguaje perfectamente adaptado al nivel de los evaluados, impidiendo que el léxico actúe como un obstáculo innecesario para comprender lo que se pregunta.
7. **Única respuesta y distractores plausibles:** Cada ítem debe tener **únicamente una opción correcta**. El resto de opciones (distractores) deben ser plausibles y lógicas para quien no domina la materia. 
   * *En materias de Ciencias/Programación:* Los distractores deben basarse en errores típicos de lógica, fallos comunes de sintaxis, malas ejecuciones de bucles o errores de cálculo frecuentes.
   * *En materias de Humanidades/Idiomas:* Los distractores deben basarse en confusiones conceptuales sutiles, falsos amigos, anacronismos o malas interpretaciones lógicas del texto.
8. **Aleatorización de la respuesta (Método de Puntos de Corte):** Para garantizar que la posición de la respuesta correcta sea estrictamente uniforme y carezca de sesgos humanos o patrones predecibles, debes aplicar mentalmente el método de puntos de corte aleatorios. Imagina una secuencia aleatoria independiente para cada pregunta que asigne una probabilidad idéntica a cada opción disponible (A, B o C). Elige la posición de la respuesta correcta de forma puramente estocástica antes de redactar las alternativas, asegurando que la elección de la posición de una pregunta no condicione ni dependa en absoluto de las posiciones elegidas para las preguntas anteriores o posteriores.
9. **Número óptimo de opciones (Prioridad 3 opciones):** De acuerdo con la evidencia psicométrica (Rodriguez, 2005), debes generar **obligatoriamente 3 opciones de respuesta (A, B y C)** en la gran mayoría de las preguntas. Pon especial esmero en que los dos distractores construidos tengan un alto grado de plausibilidad. Solo de forma excepcional, y si el contenido del documento exige evaluar un concepto que cuenta con cuatro componentes o clasificaciones naturales e inseparables en el propio texto, podrás generar una cuarta opción (D). Si una pregunta no justifica pedagógicamente esa necesidad, debe quedarse estrictamente en 3 opciones.
10. **Estructuración interna:** Ordena las opciones de respuesta de cada pregunta siguiendo una lógica coherente (por ejemplo, orden numérico ascendente, orden cronológico o una estructura conceptual limpia) para no distraer al alumno con desorganizaciones textuales.
11. **Autonomía y exclusión:** Las opciones deben ser independientes entre sí y no solaparse conceptualmente. Queda estrictamente **prohibido** utilizar las opciones "Todas las anteriores" o "Ninguna de las anteriores".
12. **Homogeneidad formal:** Ninguna opción debe destacar sobre las demás ni por su contenido ni por su apariencia (evita que la opción correcta sea significativamente más larga, detallada o técnicamente perfecta). Mantén una longitud y estructura gramatical idéntica en todas las alternativas.
13. **Niveles de Dificultad:** 
Distribuye las preguntas entre tres niveles de dificultad según la Taxonomía de Bloom revisada, usando exactamente estas definiciones:

| Nivel | Definición operativa | Verbos clave de Bloom |
|---|---|---|
| **Bajo** | El estudiante localiza o reconoce información explícita en el texto. La respuesta aparece de forma literal o casi literal en el documento. | Recordar, Identificar, Reconocer |
| **Medio** | El estudiante demuestra que comprende un concepto: lo parafrasea, lo explica con sus propias palabras o lo distingue de otros conceptos del mismo texto. | Comprender, Explicar, Distinguir, Clasificar |
| **Alto** | El estudiante relaciona ideas de distintas partes del texto, extrae una inferencia no explícita, o aplica un concepto a un caso concreto presentado en el propio documento. | Aplicar, Analizar, Inferir, Relacionar |

Asigna el nivel de dificultad **antes** de redactar la pregunta, no a posteriori.
La distribución será un 20% de preguntas de nivel bajo, un 60% de nivel medio y un 20% de nivel alto.

## Formato de Salida (JSON)

Debes entregar el resultado exclusivamente en un bloque de código JSON válido con la siguiente estructura:

```json
{
  "examen_metadatos": {
    "num_preguntas": [NÚMERO],
    "fuente": "Texto proporcionado",
    "asignatura": "[MATERIA INDICADA]"
  },
  "preguntas": [
    {
      "id": 1,
      "tema": "Nombre del tema general",
      "capitulo": "Sección del documento",
      "dificultad": "Baja/Media/Alta",
      "nivel_cognitivo": "Nivel de la Taxonomía de Bloom",
      "enunciado": "La pregunta aquí (perfectamente redactada e independiente).",
      "opciones": {
        "a": "Opción A",
        "b": "Opción B",
        "c": "Opción C",
        "d": "Opción D (INCLUIR SOLO si se justifica por estricta necesidad según la regla 9; de lo contrario, omitir por completo esta clave)"
      },
      "respuesta_correcta": "Letra de la opción en minúscula (a, b, c o d)",
      "justificacion": "Cita textual del documento que valida la respuesta",
      "distractores": {
        "a": "Breve explicación psicométrica de por qué es un distractor plausible",
        "b": "Breve explicación psicométrica de por qué es un distractor plausible",
        "c": "Breve explicación psicométrica de por qué es un distractor plausible",
        "d": "Breve explicación psicométrica de por qué es un distractor plausible (incluir solo si existe la opción d)"
      }
    }
  ]
}
´´´

> Nota: en el campo `distractores`, incluye únicamente las opciones incorrectas de cada pregunta. Omite siempre la entrada correspondiente a la respuesta correcta. Las claves `d` en `opciones`, `distractores` y el campo `justificacion_4_opciones` solo aparecen en preguntas que usen 4 opciones conforme a la Regla 9.