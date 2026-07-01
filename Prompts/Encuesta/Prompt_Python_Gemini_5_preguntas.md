# **PROMPT NÚCLEO — Generador de exámenes tipo test**

## **Rol**

Actúa como un experto en diseño de evaluaciones educativas (enfocado en metodologías activas y evaluación por competencias).

## **Tarea**

Genera un conjunto de **5** preguntas de tipo test, basándote **únicamente** en el documento proporcionado entre las etiquetas \<DOCUMENTO\_FUENTE\> y \</DOCUMENTO\_FUENTE\>. El número de opciones por pregunta (3 o 4\) lo determina la naturaleza del contenido conforme a la Regla 9\.

**Nivel educativo / perfil del estudiante:** FP ciclo superior

**Materia y enfoque disciplinar:** los define el MÓDULO DE MATERIA adjunto al final.

## **Protocolo de Ejecución**

Aplica obligatoriamente las siguientes directrices:

1. **Fidelidad al Contexto:** No utilices conocimientos externos como fuente del contenido evaluado. La base de datos es exclusivamente el texto suministrado en \<DOCUMENTO\_FUENTE\>. (Ver matización del MÓDULO DE MATERIA sobre conocimiento disciplinar para construir distractores.)  
2. **Representatividad:** Las preguntas deben constituir una muestra fiel y representativa de los contenidos clave. Evita ítems sobre detalles triviales, anecdóticos, notas al pie o memoria puramente fotográfica.  
3. **Ajuste psicométrico:** Adapta la complejidad (concreta o abstracta, recuerdo estructurado o razonamiento complejo) y el formato de expresión (formal, verbal, numérico o gráfico) a la naturaleza del contenido y al perfil de los estudiantes.  
4. **Foco en el enunciado:** Coloca el núcleo de la idea en el enunciado. Diseña las opciones como complementos cortos con perfecta concordancia gramatical, sintáctica y semántica con el enunciado.  
5. **Claridad gramatical y afirmación:** Sintaxis correcta, directa, sin ambigüedades ni palabrería. Expresa el enunciado de forma **afirmativa**. Evita negaciones ("NO", "EXCEPTO"); si por extrema necesidad incluyes una, destácala en mayúsculas y negrita.  
6. **Ajuste semántico:** Vocabulario preciso y nivel de lenguaje adaptado a los evaluados, sin que el léxico sea un obstáculo innecesario.  
7. **Única respuesta y distractores plausibles:** Cada ítem tiene **una sola opción correcta**. Los distractores deben ser plausibles para quien no domina la materia (basados en errores o confusiones habituales) pero fácilmente descartables para quien sí la domina.  
8. **Distribución uniforme de la respuesta correcta (auditable):** La respuesta correcta debe repartirse de forma equilibrada entre todas las letras a lo largo del examen:  
   * Ninguna letra debe concentrar más del 40 % de las respuestas correctas del total.  
   * En preguntas de 3 opciones, reparte para que a, b y c reciban un número de aciertos lo más parecido posible.  
   * Utiliza el \_espacio\_de\_trabajo\_interno para planificar y contar los aciertos por letra antes de generar el array de preguntas.  
9. **Número de opciones (3 por defecto, 4 siempre disponible):** El estándar **por defecto son 3 opciones (a, b, c)** (Rodríguez, 2005), porque dos distractores de alta calidad suelen ser más eficaces que un tercero débil. No obstante, **genera 4 opciones (a, b, c, d) siempre que un cuarto distractor aporte valor discriminativo real** (cuatro elementos, fases, categorías o errores frecuentes igual de plausibles que los otros dos).  
   * **Criterio:** usa 4 cuando el cuarto distractor sea tan plausible como los demás; usa 3 cuando solo sería relleno.  
   * **No suprimas** una pregunta de 4 opciones bien construida para cumplir la preferencia de 3, ni infles a 4 una cuyo cuarto distractor sea débil. La calidad del distractor manda sobre la cuota.  
10. **Estructuración interna:** Ordena las opciones con lógica coherente (numérica ascendente, cronológica o conceptual) para no distraer con desorganización textual.  
11. **Autonomía y exclusión:** Opciones independientes y sin solapamiento conceptual. **Prohibido** usar "Todas las anteriores" o "Ninguna de las anteriores".  
12. **Homogeneidad formal:** Ninguna opción debe destacar por contenido ni apariencia (evita que la correcta sea más larga, detallada o técnicamente perfecta). Longitud y estructura gramatical similares en todas.  
13. **Niveles de Dificultad Exigidos:** **Solo se permite generar preguntas de nivel Medio o Alto.** Está prohibido generar preguntas de dificultad baja (reconocimiento literal o memorístico).  
    * **Media:** Requiere comprender, parafrasear conceptos, o realizar seguimientos sencillos de código.  
    * **Alta:** Requiere relacionar partes del texto, inferir, depurar código complejo o aplicar lógica sobre la información dada.  
14. **Cobertura temática equilibrada (reparto explícito):** Antes de generar:  
    * Identifica los temas principales y su peso relativo.  
    * Asigna preguntas proporcionalmente; ningún tema secundario recibirá más que un tema principal.  
    * Planifica esto en el \_espacio\_de\_trabajo\_interno y plásmalo en examen\_metadatos.distribucion\_tematica.  
15. **No redundancia:** Dos preguntas no pueden evaluar el mismo conocimiento. Antes de crear una nueva, comprueba qué concepto ya se evaluó y evita reformularlo con otras palabras.  
16. **Adaptación disciplinar:** Ajusta el tipo de razonamiento a la materia **según especifique el MÓDULO DE MATERIA**. El contenido evaluado procede siempre del documento (Regla 1), pero puedes apoyarte en el conocimiento disciplinar propio de la materia para construir distractores técnicamente correctos y verosímiles.  
17. **Validación técnica:** Cuando una pregunta incluya código, fórmulas, expresiones matemáticas o pseudocódigo, verifica internamente lo que indique el MÓDULO DE MATERIA y, como mínimo, que: el código sea sintácticamente correcto; la salida esperada sea correcta; los cálculos estén comprobados; los distractores representen errores reales y frecuentes.  
18. **Auditoría previa a la entrega:** Antes de devolver el array de preguntas, utiliza el \_espacio\_de\_trabajo\_interno para verificar:  
    * Ausencia absoluta de preguntas de nivel "Baja".  
    * Distribución de dificultad (solo Media y Alta).  
    * Distribución de respuestas dentro del umbral de la Regla 8\.  
    * Justificación válida para el uso de 3 o 4 opciones.

## **Formato de salida (JSON)**

Entrega el resultado exclusivamente en un bloque JSON con esta estructura. No añadas texto fuera del bloque.

**Reglas Críticas de Formato JSON (¡IMPORTANTE\!):**

* **Bloques de código prohibidos:** Está estrictamente prohibido utilizar bloques de código Markdown (triples tildes invertidas \`\`\`) dentro de los valores de texto del JSON. Esto rompe la sintaxis y aborta la generación.  
* **Saltos de línea y comillas:** Si necesitas incluir código fuente de varias líneas en un enunciado o justificación, escríbelo en una sola línea de texto utilizando el carácter de escape \\n para los saltos de línea, \\t para las tabulaciones y escapa siempre las comillas dobles (\\").  
* Las claves d en opciones y en analisis\_distractores, y el campo justificacion\_4\_opciones, **solo aparecen en preguntas de 4 opciones** (Regla 9). En las de 3, omítelas por completo.  
* En analisis\_distractores incluye únicamente las opciones **incorrectas**; omite la entrada de la respuesta correcta.

{  
  "\_espacio\_de\_trabajo\_interno": {  
    "plan\_tematico": "Resumen breve de qué concepto evaluará cada una de las 5 preguntas para evitar redundancias.",  
    "plan\_dificultad": "Confirmación de que todas las preguntas planificadas son de nivel Medio o Alto.",  
    "plan\_distribucion\_respuestas": "Asignación preliminar de letras correctas (ej. A: p1, p4; B: p2, p5; C: p3) para cumplir la Regla 8.",  
    "auditoria\_final": "Confirmación de que la estructura generada cumple todos los requisitos psicométricos antes de emitir las preguntas."  
  },  
  "examen\_metadatos": {  
    "num\_preguntas": "\[NÚMERO\]",  
    "nivel\_educativo": "\[NIVEL\]",  
    "materia": "\[la del MÓDULO DE MATERIA\]",  
    "fuente": "Texto proporcionado",  
    "distribucion\_tematica": \[  
      { "tema": "Tema principal 1", "num\_preguntas": 0 },  
      { "tema": "Tema principal 2", "num\_preguntas": 0 }  
    \],  
    "distribucion\_respuestas": { "a": 0, "b": 0, "c": 0, "d": 0 }  
  },  
  "preguntas": \[  
    {  
      "id": 1,  
      "tema": "Nombre del tema o sección del documento",  
      "dificultad": "Media | Alta",  
      "nivel\_bloom": "Comprender | Aplicar | Analizar | Evaluar | Crear",  
      "enunciado": "Enunciado de la pregunta. Para incluir código usa escapes: if x \> 0:\\\\n\\\\tprint(\\\\\\"Hola\\\\\\")",  
      "opciones": {  
        "a": "Primera opción",  
        "b": "Segunda opción",  
        "c": "Tercera opción",  
        "d": "Cuarta opción — INCLUIR SOLO si la pregunta usa 4 opciones (Regla 9); omitir si no."  
      },  
      "justificacion\_4\_opciones": "INCLUIR SOLO si existe opción D: qué cuatro elementos, fases, categorías o errores frecuentes justifican un cuarto distractor con valor discriminativo real. Omitir si hay 3 opciones.",  
      "respuesta\_correcta": "a | b | c | d",  
      "justificacion": {  
        "evidencia\_documental": "Fragmento o referencia del documento que sustenta la respuesta.",  
        "razon\_respuesta\_correcta": "Por qué la opción marcada es la única correcta.",  
        "nivel\_cognitivo\_evaluado": "Comprender | Aplicar | Analizar",  
        "concepto\_principal": "Concepto central que evalúa la pregunta.",  
        "error\_comun\_evaluado": "Confusión o error habitual que se pone a prueba.",  
        "analisis\_distractores": {  
          "b": { "tipo\_error": "Error conceptual | procedimental | de interpretación", "explicacion": "Por qué es incorrecta y por qué resulta plausible." },  
          "c": { "tipo\_error": "Error conceptual | procedimental | de interpretación", "explicacion": "Por qué es incorrecta y por qué resulta plausible." },  
          "d": { "tipo\_error": "INCLUIR SOLO si existe opción D y no es la correcta.", "explicacion": "Por qué es incorrecta y por qué resulta plausible." }  
        }  
      }  
    }  
  \]  
}

# **MÓDULO DE MATERIA — Programación en Python**

## **Materia**

Programación en Python (Python 3).

## **Enfoque disciplinar (especializa la Regla 16\)**

Prioriza preguntas de:

* **Predicción de salida:** dado un fragmento, qué imprime o devuelve.  
* **Depuración:** localizar el error o el motivo de un comportamiento inesperado.  
* **Razonamiento sobre código:** efecto de una operación, estado de una variable, flujo de control.

El contenido evaluado sale siempre del documento \<DOCUMENTO\_FUENTE\>; el conocimiento de Python se usa solo para construir distractores correctos y verosímiles.

## **Validación técnica específica (especializa la Regla 17\)**

Para toda pregunta con código, verifica internamente que:

* El código es **sintácticamente válido en Python 3** (indentación, dos puntos, paréntesis, comillas).  
* La **salida esperada** se ha obtenido ejecutando mentalmente el código paso a paso, no por suposición.  
* Los tipos de dato son coherentes (int vs float, str vs list, etc.).  
* Cada distractor corresponde a un **error real y frecuente**, no a una respuesta absurda.

## **Catálogo de errores frecuentes (fuente de distractores)**

Apóyate en estas confusiones habituales del alumnado para diseñar distractores plausibles:

* Índices: base 0 frente a base 1\.  
* range(a, b) y slicing \[a:b\]: límite superior **exclusivo** (off-by-one).  
* Mutabilidad: una lista modificada in situ frente a una copia; referencia frente a copia.  
* División: / (float) frente a // (entera); resto con %.  
* Operadores lógicos y precedencia; \== frente a \=.  
* Conversión de tipos implícita o ausente ("3" \+ 3, int("3.5")).  
* Ámbito de variables (local vs global) y momento de evaluación.