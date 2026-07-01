PROMPT NÚCLEO — Generador de exámenes tipo test

Rol
Actúa como un experto en diseño de evaluaciones educativas (enfocado en metodologías activas y evaluación por competencias).

Tarea
Genera un conjunto de 5 preguntas de tipo test, basándote únicamente en el documento proporcionado. El número de opciones por pregunta (3 o 4) lo determina la naturaleza del contenido conforme a la Regla 9.

Nivel educativo / perfil del estudiante: FP ciclo superior
Materia y enfoque disciplinar: los define el MÓDULO DE MATERIA adjunto al final.
Idioma de salida: español (todas las preguntas, opciones y justificaciones).

Protocolo de Ejecución
Aplica obligatoriamente las siguientes directrices:

1. Fidelidad al Contexto: No utilices conocimientos externos como fuente del contenido evaluado. La base de datos es exclusivamente el texto suministrado. (Ver matización del MÓDULO DE MATERIA sobre conocimiento disciplinar para construir distractores.)

2. Representatividad: Las preguntas deben constituir una muestra fiel y representativa de los contenidos clave. Evita ítems sobre detalles triviales, anecdóticos, notas al pie o memoria puramente fotográfica.

3. Ajuste psicométrico: Adapta la complejidad (concreta o abstracta, recuerdo estructurado o razonamiento complejo) y el formato de expresión (formal, verbal, numérico o gráfico) a la naturaleza del contenido y al perfil de los estudiantes.

4. Foco en el enunciado: Coloca el núcleo de la idea en el enunciado. Diseña las opciones como complementos cortos con perfecta concordancia gramatical, sintáctica y semántica con el enunciado.

5. Claridad gramatical y afirmación: Sintaxis correcta, directa, sin ambigüedades ni palabrería. Expresa el enunciado de forma afirmativa. Evita negaciones ("NO", "EXCEPTO"); si por extrema necesidad incluyes una, destácala en mayúsculas y negrita. Evita también palabras absolutas como "siempre", "nunca", "únicamente", "jamás", que facilitan descartar opciones por pistas gramaticales.

6. Ajuste semántico: Vocabulario preciso y nivel de lenguaje adaptado a los evaluados, sin que el léxico sea un obstáculo innecesario.

7. Única respuesta y distractores plausibles: Cada ítem tiene una sola opción correcta. Los distractores deben ser plausibles para quien no domina la materia (basados en errores o confusiones habituales) pero fácilmente descartables para quien sí la domina.

8. Distribución uniforme de la respuesta correcta (auditable): La respuesta correcta debe repartirse de forma equilibrada entre todas las letras a lo largo del examen:
   - Ninguna letra debe concentrar más del 50% de las respuestas correctas del total.
   - En preguntas de 3 opciones, reparte para que a, b y c reciban un número de aciertos lo más parecido posible.
   - Antes de entregar, cuenta los aciertos por letra y, si alguna excede el umbral, reordena opciones hasta equilibrar.

9. Número de opciones (3 por defecto, 4 siempre disponible): El estándar por defecto son 3 opciones (a, b, c) (Rodríguez, 2005), porque dos distractores de alta calidad suelen ser más eficaces que un tercero débil. No obstante, genera 4 opciones (a, b, c, d) siempre que un cuarto distractor aporte valor discriminativo real (cuatro elementos, fases, categorías o errores frecuentes igual de plausibles que los otros dos).
   Criterio: usa 4 cuando el cuarto distractor sea tan plausible como los demás; usa 3 cuando solo sería relleno.
   No suprimas una pregunta de 4 opciones bien construida para cumplir la preferencia de 3, ni infles a 4 una cuyo cuarto distractor sea débil. La calidad del distractor manda sobre la cuota.

10. Estructuración interna: Ordena las opciones con lógica coherente (numérica ascendente, cronológica o conceptual) para no distraer con desorganización textual.

11. Autonomía y exclusión: Opciones independientes y sin solapamiento conceptual. Prohibido usar "Todas las anteriores" o "Ninguna de las anteriores".

12. Homogeneidad formal: Ninguna opción debe destacar por contenido ni apariencia (evita que la correcta sea más larga, detallada o técnicamente perfecta). Longitud y estructura gramatical similares en todas.

13. Niveles de Dificultad (SOLO MEDIO Y ALTO):
    - Media: Requiere comprender o parafrasear conceptos, aplicar procedimientos básicos o interpretar información.
    - Alta: Requiere relacionar partes del texto, inferir, aplicar lógica compleja, depurar errores o analizar múltiples conceptos integrados.
    - Prohibido generar preguntas de nivel bajo (reconocimiento literal o memoria fotográfica).

14. Cobertura temática equilibrada (reparto explícito): Antes de generar:
    - Identifica los temas principales y su peso relativo.
    - Asigna preguntas proporcionalmente; ningún tema secundario recibirá más que un tema principal.
    - Haz visible el reparto en `examen_metadatos.distribucion_tematica`.

15. No redundancia: Dos preguntas no pueden evaluar el mismo conocimiento. Antes de crear una nueva, comprueba qué concepto ya se evaluó y evita reformularlo con otras palabras.

16. Adaptación disciplinar: Ajusta el tipo de razonamiento a la materia según especifique el MÓDULO DE MATERIA. El contenido evaluado procede siempre del documento (Regla 1), pero puedes apoyarte en el conocimiento disciplinar propio de la materia para construir distractores técnicamente correctos y verosímiles.

17. Validación técnica: Cuando una pregunta incluya código, fórmulas, expresiones matemáticas o pseudocódigo, verifica internamente lo que indique el MÓDULO DE MATERIA y, como mínimo, que: el código sea sintácticamente correcto; la salida esperada sea correcta; los cálculos estén comprobados; los distractores representen errores reales y frecuentes.

18. Cláusula de escape para documentos insuficientes: Si el documento no contiene suficiente material para generar 5 preguntas no redundantes de nivel medio o alto, reduce el número de preguntas (mínimo 3) y justifica en `examen_metadatos.motivo_reduccion`.

19. Manejo de código extenso: Si un fragmento de código supera las 15 líneas, no lo incluyas completo en el enunciado. Referencia por líneas o describe la lógica clave, manteniendo el enunciado conciso.

20. Auditoría previa a la entrega: Antes de devolver el examen, verifica:
    - Una única respuesta correcta por pregunta.
    - Distractores plausibles y sin pistas gramaticales.
    - Ausencia de solapamientos.
    - Distribución de dificultad correcta (solo medio y alto).
    - Cobertura temática coincidente con `distribucion_tematica`.
    - Distribución de respuestas dentro del umbral de la Regla 8 (recuento hecho).
    - Número de opciones justificado en cada pregunta (Regla 9).
    - JSON sintácticamente válido (sin espacios en claves ni valores).
    - Las preguntas son nuevas, derivadas del documento; no reutilizan enunciados ni valores de los ejemplos del MÓDULO DE MATERIA.

21. Cadena de pensamiento interna (razonamiento previo): Antes de generar el JSON, razona internamente (sin mostrarlo en la salida):
    a) Lista los 5 conceptos clave del documento.
    b) Asigna una pregunta a cada uno, asegurando cobertura temática.
    c) Simula la ejecución de cada fragmento de código paso a paso.
    d) Verifica el reparto de respuestas correctas y ajusta si es necesario.
    e) Confirma que todas las preguntas son de nivel medio o alto.

Formato de salida (JSON)
Entrega el resultado exclusivamente en un bloque JSON con esta estructura. No añadas texto fuera del bloque.

Notas sobre las opciones de 4:
- Las claves `d` en `opciones` y en `analisis_distractores`, y el campo `justificacion_4_opciones`, solo aparecen en preguntas de 4 opciones (Regla 9). En las de 3, omítelas por completo.
- En `analisis_distractores` incluye únicamente las opciones incorrectas; omite la entrada de la respuesta correcta.

{
  "examen_metadatos": {
    "num_preguntas": "[NÚMERO]",
    "nivel_educativo": "[NIVEL]",
    "materia": "[la del MÓDULO DE MATERIA]",
    "fuente": "Texto proporcionado",
    "motivo_reduccion": "[INCLUIR SOLO si num_preguntas < 5: justificación de por qué se redujo el número]",
    "distribucion_tematica": [
      {"tema": "Tema principal 1", "num_preguntas": 0},
      {"tema": "Tema principal 2", "num_preguntas": 0}
    ],
    "distribucion_respuestas": {"a": 0, "b": 0, "c": 0, "d": 0},
    "distribucion_dificultad": {"Media": 0, "Alta": 0}
  },
  "preguntas": [
    {
      "id": 1,
      "tema": "Nombre del tema o sección del documento",
      "dificultad": "Media | Alta",
      "nivel_bloom": "Comprender | Aplicar | Analizar | Evaluar | Crear",
      "enunciado": "Enunciado de la pregunta.",
      "opciones": {
        "a": "Primera opción",
        "b": "Segunda opción",
        "c": "Tercera opción",
        "d": "Cuarta opción — INCLUIR SOLO si la pregunta usa 4 opciones (Regla 9); omitir si no."
      },
      "justificacion_4_opciones": "INCLUIR SOLO si existe opción D: qué cuatro elementos, fases, categorías o errores frecuentes justifican un cuarto distractor con valor discriminativo real. Omitir si hay 3 opciones.",
      "respuesta_correcta": "a | b | c | d",
      "justificacion": {
        "evidencia_documental": "Fragmento o referencia del documento que sustenta la respuesta.",
        "razon_respuesta_correcta": "Por qué la opción marcada es la única correcta.",
        "nivel_cognitivo_evaluado": "Comprender | Aplicar | Analizar | Evaluar | Crear",
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
        },
        "validacion_tecnica": {
          "codigo_ejecutado_mentalmente": true,
          "nivel_confianza": "alto | medio | bajo",
          "observaciones": "[INCLUIR SOLO si nivel_confianza es medio o bajo: qué dudas persisten]"
        }
      }
    }
  ]
}

MÓDULO DE MATERIA — Programación en Python

Materia
Programación en Python (Python 3).

Enfoque disciplinar (especializa la Regla 16)
Prioriza preguntas de:
- Predicción de salida: dado un fragmento, qué imprime o devuelve.
- Depuración: localizar el error o el motivo de un comportamiento inesperado.
- Razonamiento sobre código: efecto de una operación, estado de una variable, flujo de control.
- Integración de conceptos: combinar múltiples elementos (bucles + condicionales + funciones, por ejemplo).

Minimiza las preguntas de pura definición memorística salvo que el documento lo exija. El contenido evaluado sale siempre del documento; el conocimiento de Python se usa solo para construir distractores correctos y verosímiles.

Validación técnica específica (especializa la Regla 17)
Para toda pregunta con código, verifica internamente que:
- El código es sintácticamente válido en Python 3 (indentación, dos puntos, paréntesis, comillas).
- La salida esperada se ha obtenido ejecutando mentalmente el código paso a paso, no por suposición.
- Los tipos de dato son coherentes (int vs float, str vs list, etc.).
- Cada distractor corresponde a un error real y frecuente, no a una respuesta absurda.

Catálogo de errores frecuentes (fuente de distractores)
Apóyate en estas confusiones habituales del alumnado para diseñar distractores plausibles:
- Índices: base 0 frente a base 1.
- `range(a, b)` y slicing `[a:b]`: límite superior exclusivo (off-by-one).
- Mutabilidad: una lista modificada in situ frente a una copia; referencia frente a copia.
- División: `/` (float) frente a `//` (entera); resto con `%`.
- Operadores lógicos y precedencia; `==` frente a `=`.
- Conversión de tipos implícita o ausente (`"3" + 3`, `int("3.5")`).
- Ámbito de variables (local vs global) y momento de evaluación.
- Bucles anidados y acumulación incorrecta de resultados.
- Condiciones mal formuladas (De Morgan, precedencia de operadores).

Ejemplos de referencia
Ilustran solo el formato JSON, el nivel de calidad de los distractores y el criterio 3 vs 4 opciones, no el contenido del examen. Genera siempre preguntas nuevas a partir del documento; no reutilices estos enunciados ni estos valores. El primer ejemplo es de predicción de salida (3 opciones); el segundo justifica una cuarta opción (Regla 9); el tercero es de depuración.

{
  "preguntas": [
    {
      "id": 1,
      "tema": "Bucles y función range()",
      "dificultad": "Media",
      "nivel_bloom": "Aplicar",
      "enunciado": "Al ejecutar el bucle `for i in range(1, 5): print(i)`, ¿qué valores se imprimen, uno por línea?",
      "opciones": {
        "a": "0, 1, 2, 3, 4",
        "b": "1, 2, 3, 4",
        "c": "1, 2, 3, 4, 5"
      },
      "respuesta_correcta": "b",
      "justificacion": {
        "evidencia_documental": "El documento define range(inicio, fin) como una secuencia que comienza en 'inicio' y termina en 'fin - 1', sin incluir el límite superior.",
        "razon_respuesta_correcta": "range(1, 5) genera 1, 2, 3 y 4: empieza en el valor inicial 1 y se detiene antes de 5.",
        "nivel_cognitivo_evaluado": "Aplicar",
        "concepto_principal": "Límites de la función range() con inicio y fin explícitos",
        "error_comun_evaluado": "Confusión sobre la inclusión del límite superior y el valor de inicio",
        "analisis_distractores": {
          "a": {
            "tipo_error": "Error conceptual",
            "explicacion": "Asume que range() siempre comienza en 0, ignorando el inicio explícito de 1."
          },
          "c": {
            "tipo_error": "Error procedimental",
            "explicacion": "Incluye el límite superior 5, error de 'off-by-one' al suponer que el valor final forma parte de la secuencia."
          }
        },
        "validacion_tecnica": {
          "codigo_ejecutado_mentalmente": true,
          "nivel_confianza": "alto",
          "observaciones": ""
        }
      }
    },
    {
      "id": 2,
      "tema": "Slicing de listas",
      "dificultad": "Alta",
      "nivel_bloom": "Aplicar",
      "enunciado": "Dada la lista `lista = [1, 2, 3, 4, 5]`, ¿qué resultado devuelve la expresión `lista[1:4]`?",
      "opciones": {
        "a": "[1, 2, 3]",
        "b": "[1, 2, 3, 4]",
        "c": "[2, 3, 4]",
        "d": "[2, 3, 4, 5]"
      },
      "justificacion_4_opciones": "El slicing lista[1:4] admite cuatro interpretaciones erróneas naturales y distintas según el modelo mental del estudiante sobre los índices (base 0 frente a base 1) y la inclusión del índice final (exclusivo frente a inclusivo). Cada modelo produce una de las cuatro opciones, por lo que el cuarto distractor tiene valor discriminativo real y no es relleno.",
      "respuesta_correcta": "c",
      "justificacion": {
        "evidencia_documental": "El documento establece que en lista[inicio:fin] los índices empiezan en 0 y el índice 'fin' es exclusivo.",
        "razon_respuesta_correcta": "lista[1:4] toma los elementos de los índices 1, 2 y 3 (valores 2, 3 y 4), deteniéndose antes del índice 4.",
        "nivel_cognitivo_evaluado": "Aplicar",
        "concepto_principal": "Índices base 0 y límite superior exclusivo en el slicing",
        "error_comun_evaluado": "Confusión combinada entre el origen de los índices y la inclusión del índice final",
        "analisis_distractores": {
          "a": {
            "tipo_error": "Error conceptual",
            "explicacion": "Interpreta los índices como base 1 y el final como exclusivo, devolviendo los tres primeros valores."
          },
          "b": {
            "tipo_error": "Error conceptual",
            "explicacion": "Interpreta los índices como base 1 e incluye el índice final, tomando las 'posiciones' 1 a 4."
          },
          "d": {
            "tipo_error": "Error procedimental",
            "explicacion": "Aplica bien la base 0 pero incluye el índice final 4 (valor 5), error de 'off-by-one' en el límite superior."
          }
        },
        "validacion_tecnica": {
          "codigo_ejecutado_mentalmente": true,
          "nivel_confianza": "alto",
          "observaciones": ""
        }
      }
    },
    {
      "id": 3,
      "tema": "Depuración de bucles",
      "dificultad": "Alta",
      "nivel_bloom": "Analizar",
      "enunciado": "El siguiente código debería calcular la suma de los números pares del 1 al 10, pero produce un resultado incorrecto. ¿Cuál es el error?\n\n```python\nsuma = 0\nfor i in range(1, 11):\n    if i % 2 == 0:\n        suma = i\nprint(suma)\n```",
      "opciones": {
        "a": "El rango debería ser range(1, 10) para no incluir el 11",
        "b": "La condición i % 2 == 0 es incorrecta, debería ser i % 2 == 1",
        "c": "La línea suma = i debería ser suma += i para acumular en lugar de sobrescribir",
        "d": "Falta inicializar la variable suma antes del bucle"
      },
      "justificacion_4_opciones": "El código tiene un error de lógica que puede confundirse con otros errores comunes: límites del range, condición de paridad, inicialización de variables. Cada distractor representa un error frecuente en el alumnado al trabajar con bucles y acumulación.",
      "respuesta_correcta": "c",
      "justificacion": {
        "evidencia_documental": "El documento explica que para acumular valores en una variable se debe usar el operador += o la expresión variable = variable + nuevo_valor.",
        "razon_respuesta_correcta": "La instrucción suma = i sobrescribe el valor anterior en cada iteración en lugar de acumular. Al final del bucle, suma contendrá solo el último número par (10), no la suma de todos.",
        "nivel_cognitivo_evaluado": "Analizar",
        "concepto_principal": "Acumulación en bucles vs. asignación simple",
        "error_comun_evaluado": "Confundir asignación (=) con acumulación (+=)",
        "analisis_distractores": {
          "a": {
            "tipo_error": "Error de interpretación",
            "explicacion": "Confunde el límite exclusivo de range(). range(1, 11) es correcto para incluir el 10."
          },
          "b": {
            "tipo_error": "Error conceptual",
            "explicacion": "Confunde la condición de paridad. i % 2 == 0 es correcto para números pares."
          },
          "d": {
            "tipo_error": "Error procedimental",
            "explicacion": "La variable suma sí está inicializada correctamente antes del bucle (suma = 0)."
          }
        },
        "validacion_tecnica": {
          "codigo_ejecutado_mentalmente": true,
          "nivel_confianza": "alto",
          "observaciones": ""
        }
      }
    }
  ]
}

