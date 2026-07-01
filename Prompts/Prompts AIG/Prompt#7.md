# Instrucciones de Generación de Evaluación

**Rol:** Actúa como un experto en diseño de evaluaciones educativas (enfocado en metodologías activas y evaluación por competencias).
**Tarea:** Generar un conjunto de [NÚMERO] preguntas de tipo test, basándote **únicamente** en el documento proporcionado. El número de opciones por pregunta (3 o 4) lo determina la naturaleza del contenido conforme a la Regla 9.
**Nivel educativo / perfil del estudiante:** [INDICA AQUÍ EL NIVEL]

## Protocolo de Ejecución
Para construir cada una de las preguntas, debes aplicar obligatoriamente las siguientes directrices:

1. **Fidelidad al Contexto:** No utilices conocimientos externos como fuente del contenido evaluado. La base de datos es exclusivamente el texto suministrado. (Ver matización en la Regla 16 sobre conocimiento disciplinar para construir distractores.)
2. **Representatividad:** Asegúrate de que las preguntas constituyan una muestra fiel y representativa de los contenidos clave e importantes de la materia. Evita estrictamente generar ítems sobre detalles triviales, anecdóticos, notas al pie o memoria puramente fotográfica.
3. **Ajuste psicométrico:** Adapta la complejidad de la pregunta (si debe ser concreta o abstracta, de recuerdo memorístico estructurado o de razonamiento complejo) y su formato de expresión (formal, verbal, numérico o gráfico) a la naturaleza del contenido evaluado y al perfil de los estudiantes.
4. **Foco en el enunciado:** Coloca el núcleo central de la idea y de la información en el enunciado de la pregunta. Diseña las opciones de respuesta como complementos cortos que guarden una perfecta concordancia gramatical, sintáctica y semántica con dicho enunciado.
5. **Claridad gramatical y afirmación:** Redacta con una sintaxis correcta, directa, sin ambigüedades ni palabrería excesiva. Expresa el enunciado de forma **afirmativa**. Evita el uso de negaciones (como "NO" o "EXCEPTO"); si por extrema necesidad incluyes una negación, destácala claramente en mayúsculas y negrita.
6. **Ajuste semántico:** Utiliza un vocabulario preciso y un nivel de lenguaje perfectamente adaptado al nivel de los evaluados, impidiendo que el léxico actúe como un obstáculo innecesario para comprender lo que se pregunta.
7. **Única respuesta y distractores plausibles:** Cada ítem debe tener **únicamente una opción correcta**. El resto de opciones (distractores) deben ser plausibles y lógicas para quien no domina la materia (por ejemplo, basadas en errores o confusiones habituales de los alumnos), pero fácilmente descartables para el estudiante que sí la conoce.
8. **Distribución uniforme de la respuesta correcta (regla auditable):** Para evitar sesgos de posición, la respuesta correcta debe repartirse de forma equilibrada entre todas las letras a lo largo del examen. Aplica el siguiente criterio verificable:
   - Ninguna letra (a, b, c y, cuando exista, d) debe concentrar más del 40 % de las respuestas correctas del total del examen.
   - En preguntas de 3 opciones, reparte de modo que a, b y c reciban un número de respuestas correctas lo más parecido posible.
   - Antes de entregar, **cuenta** cuántas respuestas correctas hay en cada letra y, si alguna excede el umbral, reubica respuestas correctas (reordenando las opciones) hasta equilibrar.
9. **Número de opciones (3 por defecto, 4 siempre disponible):** El estándar **por defecto son 3 opciones (a, b, c)**, conforme a la evidencia psicométrica (Rodríguez, 2005), porque construir dos distractores de alta calidad suele ser más eficaz que forzar un tercero débil. No obstante, **genera 4 opciones (a, b, c, d) siempre que un cuarto distractor aporte valor discriminativo real**: por ejemplo, cuando el concepto del documento presenta cuatro elementos, fases, categorías o clasificaciones naturales, o cuando existe un cuarto error frecuente lo bastante plausible como para discriminar a quien no domina la materia.
   - **Criterio de decisión:** usa 4 opciones cuando el cuarto distractor sea tan plausible como los otros dos; usa 3 cuando el cuarto solo serviría de relleno.
   - **No suprimas** una pregunta de 4 opciones bien construida para cumplir la preferencia de 3, ni infles a 4 una pregunta cuyo cuarto distractor sea débil. La calidad del distractor manda sobre la cuota.
10. **Estructuración interna:** Ordena las opciones de respuesta de cada pregunta siguiendo una lógica coherente (por ejemplo, orden numérico ascendente, orden cronológico o una estructura conceptual limpia) para no distraer al alumno con desorganizaciones textuales.
11. **Autonomía y exclusión:** Las opciones deben ser independientes entre sí y no solaparse conceptualmente. Queda estrictamente **prohibido** utilizar las opciones "Todas las anteriores" o "Ninguna de las anteriores".
12. **Homogeneidad formal:** Ninguna opción debe destacar sobre las demás ni por su contenido ni por su apariencia (evita que la opción correcta sea significativamente más larga, detallada o técnicamente perfecta). Mantén una longitud y estructura gramatical similar en todas las alternativas.
13. **Niveles de Dificultad:** Clasifica cada pregunta según los siguientes criterios:
    * **Baja:** Reconocimiento literal de términos o datos explícitos.
    * **Media:** Requiere comprender o parafrasear conceptos.
    * **Alta:** Requiere relacionar diferentes partes del texto, realizar inferencias o aplicar la lógica sobre la información dada.
14. **Cobertura temática equilibrada (con reparto explícito):** Antes de generar las preguntas:
    - Identifica los temas principales del documento y su peso relativo.
    - Decide cuántas preguntas asignas a cada tema, proporcionalmente a su peso.
    - Ningún tema secundario podrá recibir más preguntas que un tema principal.
    - **Haz visible este reparto** rellenando el campo `examen_metadatos.distribucion_tematica` del JSON con cada tema y su número de preguntas asignado.
15. **No redundancia:** Dos preguntas no pueden evaluar exactamente el mismo conocimiento. Antes de generar una nueva pregunta:
    - Comprueba qué concepto principal ya ha sido evaluado.
    - Evita reformular la misma pregunta con otras palabras.
16. **Adaptación disciplinar y uso del conocimiento técnico:** Ajusta el tipo de razonamiento al área. El **contenido evaluado** procede siempre del documento (Regla 1), pero puedes apoyarte en el conocimiento disciplinar propio de la materia (sintaxis de un lenguaje, reglas matemáticas, convenciones históricas) **para construir distractores técnicamente correctos y verosímiles**.
    - **Ciencias y Matemáticas:** priorizar aplicación, cálculo e interpretación.
    - **Programación:** priorizar predicción de salida, depuración y razonamiento sobre código.
    - **Historia:** priorizar causalidad, contextualización e interpretación.
    - **Lengua:** priorizar análisis sintáctico, semántico y pragmático.
    - **Idiomas:** priorizar uso contextual, comprensión e inferencia.
17. **Validación técnica:** Cuando una pregunta incluya código, fórmulas, expresiones matemáticas o pseudocódigo, verifica internamente que:
    - el código compila o es sintácticamente correcto;
    - la salida esperada es correcta;
    - los cálculos han sido comprobados;
    - los distractores representan errores reales y frecuentes.
18. **Auditoría previa a la entrega:** Antes de devolver el examen, verifica:
    - Una única respuesta correcta por pregunta.
    - Distractores plausibles.
    - Ausencia de pistas gramaticales.
    - Ausencia de solapamientos.
    - Correcta distribución de dificultad.
    - Correcta cobertura temática (coincide con `distribucion_tematica`).
    - Distribución de respuestas dentro del umbral de la Regla 8 (recuento por letra hecho).
    - Número de opciones justificado en cada pregunta conforme a la Regla 9.
    - JSON sintácticamente válido.

## Formato de salida (JSON)

Entrega el resultado exclusivamente en un bloque de código JSON con la siguiente estructura. No añadas texto fuera del bloque JSON.

Notas sobre las opciones de 4:
- Las claves `d` en `opciones` y en `analisis_distractores`, y el campo `justificacion_4_opciones`, **solo aparecen en preguntas que usen 4 opciones** conforme a la Regla 9. En preguntas de 3 opciones, omite esas claves por completo.
- En `analisis_distractores` incluye únicamente las opciones **incorrectas**; omite siempre la entrada correspondiente a la respuesta correcta.

```json
{
  "examen_metadatos": {
    "num_preguntas": "[NÚMERO]",
    "nivel_educativo": "[NIVEL]",
    "fuente": "Texto proporcionado",
    "distribucion_tematica": [
      { "tema": "Nombre del tema principal 1", "num_preguntas": 0 },
      { "tema": "Nombre del tema principal 2", "num_preguntas": 0 }
    ],
    "distribucion_respuestas": { "a": 0, "b": 0, "c": 0, "d": 0 }
  },
  "preguntas": [
    {
      "id": 1,
      "tema": "Nombre del tema o sección del documento",
      "dificultad": "Baja | Media | Alta",
      "nivel_bloom": "Recordar | Comprender | Aplicar | Analizar | Evaluar | Crear",
      "enunciado": "Enunciado de la pregunta.",
      "opciones": {
        "a": "Primera opción",
        "b": "Segunda opción",
        "c": "Tercera opción",
        "d": "Cuarta opción — INCLUIR SOLO si la pregunta usa 4 opciones (Regla 9); omitir esta clave en caso contrario."
      },
      "justificacion_4_opciones": "INCLUIR SOLO si existe opción D: explicación de qué cuatro elementos, fases, categorías o errores frecuentes del documento justifican un cuarto distractor con valor discriminativo real. Omitir esta clave si la pregunta tiene 3 opciones.",
      "respuesta_correcta": "a | b | c | d",
      "justificacion": {
        "evidencia_documental": "Fragmento o referencia del documento que sustenta la respuesta.",
        "razon_respuesta_correcta": "Por qué la opción marcada es la única correcta.",
        "nivel_cognitivo_evaluado": "Comprender",
        "concepto_principal": "Concepto central que evalúa la pregunta.",
        "error_comun_evaluado": "Confusión o error habitual que se pone a prueba.",
        "analisis_distractores": {
          "b": {
            "tipo_error": "Error conceptual | procedimental | de interpretación",
            "explicacion": "Por qué es incorrecta y por qué resulta plausible."
          },
          "c": {
            "tipo_error": "Error conceptual | procedimental | de interpretación",
            "explicacion": "Por qué es incorrecta y por qué resulta plausible."
          },
          "d": {
            "tipo_error": "INCLUIR SOLO si existe opción D y no es la correcta.",
            "explicacion": "Por qué es incorrecta y por qué resulta plausible."
          }
        }
      }
    }
  ]
}
```