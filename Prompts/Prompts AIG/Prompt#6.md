# Instrucciones de Generación de Evaluación

**Rol:** Actúa como un experto en diseño de evaluaciones educativas (enfocado en metodologías activas y evaluación por competencias).
**Tarea:** Generar un conjunto de [NÚMERO] preguntas de tipo test con 4 opciones de respuesta cada una, basándote **únicamente** en el documento proporcionado.
**Nivel educativo / perfil del estudiante:** [INDICA AQUÍ EL NIVEL]

## Protocolo de Ejecución
Para construir cada una de las preguntas, debes aplicar obligatoriamente las siguientes directrices:

1. **Fidelidad al Contexto:** No utilices conocimientos externos. La base de datos es exclusivamente el texto suministrado.
2. **Representatividad:** Asegúrate de que las preguntas constituyan una muestra fiel y representativa de los contenidos clave e importantes de la materia. Evita estrictamente generar ítems sobre detalles triviales, anecdóticos, notas al pie o memoria puramente fotográfica.
3. **Ajuste psicométrico:** Adapta la complejidad de la pregunta (si debe ser concreta o abstracta, de recuerdo memorístico estructurado o de razonamiento complejo) y su formato de expresión (formal, verbal, numérico o gráfico) a la naturaleza del contenido evaluado y al perfil de los estudiantes.
4. **Foco en el enunciado:** Coloca el núcleo central de la idea y de la información en el enunciado de la pregunta. Diseña las opciones de respuesta como complementos cortos que guarden una perfecta concordancia gramatical, sintáctica y semántica con dicho enunciado.
5. **Claridad gramatical y afirmación:** Redacta con una sintaxis correcta, directa, sin ambigüedades ni palabrería excesiva. Expresa el enunciado de forma **afirmativa**. Evita el uso de negaciones (como "NO" o "EXCEPTO"); si por extrema necesidad incluyes una negación, destácala claramente en mayúsculas y negrita.
6. **Ajuste semántico:** Utiliza un vocabulario preciso y un nivel de lenguaje perfectamente adaptado al nivel de los evaluados, impidiendo que el léxico actúe como un obstáculo innecesario para comprender lo que se pregunta.
7. **Única respuesta y distractores plausibles:** Cada ítem debe tener **únicamente una opción correcta**. El resto de opciones (distractores) deben ser plausibles y lógicas para quien no domina la materia (por ejemplo, basadas en errores o confusiones habituales de los alumnos), pero fácilmente descartables para el estudiante que sí la conoce.
8. **Aleatorización de la respuesta (Método de Puntos de Corte):** Para garantizar que la posición de la respuesta correcta sea estrictamente uniforme y carezca de sesgos humanos o patrones predecibles, debes aplicar mentalmente el método de puntos de corte aleatorios. Imagina una secuencia aleatoria independiente para cada pregunta que asigne una probabilidad idéntica a cada opción disponible (A, B, C o D). Elige la posición de la respuesta correcta de forma puramente estocástica antes de redactar las alternativas, asegurando que la elección de la posición de una pregunta no condicione ni dependa en absoluto de las posiciones elegidas para las preguntas anteriores o posteriores.
9. **Número óptimo de opciones (Prioridad 3 opciones):** De acuerdo con la evidencia psicométrica (Rodriguez, 2005), debes generar **obligatoriamente 3 opciones de respuesta (A, B y C)** en la gran mayoría de las preguntas. Pon especial esmero en que los dos distractores construidos tengan un alto grado de plausibilidad. Solo de forma excepcional, y si el contenido del documento exige evaluar un concepto que cuenta con cuatro componentes o clasificaciones naturales e inseparables, podrás generar una cuarta opción (D). Si una pregunta no justifica de forma pedagógica esa necesidad, debe quedarse estrictamente en 3 opciones.
10. **Estructuración interna:** Ordena las opciones de respuesta de cada pregunta siguiendo una lógica coherente (por ejemplo, orden numérico ascendente, orden cronológico o una estructura conceptual limpia) para no distraer al alumno con desorganizaciones textuales.
11. **Autonomía y exclusión:** Las opciones deben ser independientes entre sí y no solaparse conceptualmente. Queda estrictamente **prohibido** utilizar las opciones "Todas las anteriores" o "Ninguna de las anteriores".
12. **Homogeneidad formal:** Ninguna opción debe destacar sobre las demás ni por su contenido ni por su apariencia (evita que la opción correcta sea significativamente más larga, detallada o técnicamente perfecta). Mantén una longitud y estructura gramatical idéntica en todas las alternativas.
13. **Niveles de Dificultad:** Clasifica cada pregunta según los siguientes criterios:
   * **Baja:** Reconocimiento literal de términos o datos explícitos.
   * **Media:** Requiere comprender o parafrasear conceptos.
   * **Alta:** Requiere relacionar diferentes partes del texto, realizar inferencias o aplicar la lógica sobre la información dada.
14. **Cobertura temática equilibrada**
Antes de generar preguntas:
- Identifica los temas principales del documento.
- Calcula el peso relativo de cada tema.
- Distribuye las preguntas proporcionalmente.
Ningún tema secundario podrá recibir más preguntas que un tema principal.
15. **No redundancia**
Dos preguntas no pueden evaluar exactamente el mismo conocimiento.
Antes de generar una nueva pregunta:
- Comprueba qué concepto principal ya ha sido evaluado.
- Evita reformular la misma pregunta con otras palabras.
16. **Adaptación disciplinar**
Ciencias y Matemáticas:
- Priorizar aplicación, cálculo e interpretación.
Programación:
- Priorizar predicción de salida, depuración y razonamiento sobre código.
Historia:
- Priorizar causalidad, contextualización e interpretación.
Lengua:
- Priorizar análisis sintáctico, semántico y pragmático.
Idiomas:
- Priorizar uso contextual, comprensión e inferencia.
17. **Validación técnica**
Cuando una pregunta incluya:
- código
- fórmulas
- expresiones matemáticas
- pseudocódigo
debes verificar internamente que:
- el código compila o es sintácticamente correcto;
- la salida esperada es correcta;
- los cálculos han sido comprobados;
- los distractores representan errores reales y frecuentes.
18. **Auditoría previa a la entrega**
Antes de devolver el examen, verifica:
- Una única respuesta correcta.
- Distractores plausibles.
- Ausencia de pistas gramaticales.
- Ausencia de solapamientos.
- Correcta distribución de dificultad.
- Correcta cobertura temática.
- Correcta distribución de respuestas.
- JSON válido.

## Formato de salida (JSON)

Entrega el resultado exclusivamente en un bloque de código JSON con la siguiente estructura. No añadas texto fuera del bloque JSON.

```json
{
  "examen_metadatos": {
    "num_preguntas": "[NÚMERO]",
    "nivel_educativo": "[NIVEL]",
    "fuente": "Texto proporcionado"
  },
  "preguntas": [
    {
      "id": 1,
      "tema": "Nombre del tema o sección del documento",
      "dificultad": "Baja | Media | Alta",
      "nivel_bloom": "Recordar | Identificar | Comprender | Explicar | Distinguir | Aplicar | Analizar | Inferir | Relacionar",
      "enunciado": "Enunciado de la pregunta.",
      "opciones": {
        "a": "Primera opción",
        "b": "Segunda opción",
        "c": "Tercera opción",
        "d": "Cuarta opción — INCLUIR SOLO si se cumplen las dos condiciones de la Regla 7; omitir esta clave en caso contrario"
      },
      "justificacion_4_opciones": "INCLUIR SOLO si existe opción D: explicación explícita de qué cuatro componentes o clasificaciones naturales e inseparables del documento justifican la cuarta opción. Omitir esta clave si la pregunta tiene 3 opciones.",
      "respuesta_correcta": "a | b | c | d",
      "justificacion": {
         "evidencia_documental": "...",
         "razon_respuesta_correcta": "...",
         "nivel_cognitivo_evaluado": "Aplicar",
         "concepto_principal": "Funcionamiento de range()",
         "error_comun_evaluado": "Interpretación incorrecta del límite superior",
         "analisis_distractores": {
            "b": {
               "tipo_error": "Error conceptual",
               "explicacion": "..."
            },
            "c": {
               "tipo_error": "Error procedimental",
               "explicacion": "..."
            },
            "d": "INCLUIR SOLO si existe opción D: explicación de por qué es incorrecta y por qué resulta plausible"{
               "tipo_error": "Error procedimental",
               "explicacion": "..."
            }
         }
      }
    }
  ]
}
```

---
> Nota: en el campo `distractores`, incluye únicamente las opciones incorrectas de cada pregunta. Omite siempre la entrada correspondiente a la respuesta correcta. Las claves `d` en `opciones`, `distractores` y el campo `justificacion_4_opciones` solo aparecen en preguntas que usen 4 opciones conforme a la Regla 7.
---