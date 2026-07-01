# PROMPT NÚCLEO — Generador de exámenes tipo test

## Rol
Actúa como un experto en diseño de evaluaciones educativas (enfocado en metodologías activas y evaluación por competencias).

## Tarea
Genera un conjunto de **[NÚMERO]** preguntas de tipo test, basándote **únicamente** en el documento proporcionado. El número de opciones por pregunta (3 o 4) lo determina la naturaleza del contenido conforme a la Regla 9.

**Nivel educativo / perfil del estudiante:** [NIVEL]
**Materia y enfoque disciplinar:** los define el MÓDULO DE MATERIA adjunto al final.

## Protocolo de Ejecución
Aplica obligatoriamente las siguientes directrices:

1. **Fidelidad al Contexto:** No utilices conocimientos externos como fuente del contenido evaluado. La base de datos es exclusivamente el texto suministrado. (Ver matización del MÓDULO DE MATERIA sobre conocimiento disciplinar para construir distractores.)
2. **Representatividad:** Las preguntas deben constituir una muestra fiel y representativa de los contenidos clave. Evita ítems sobre detalles triviales, anecdóticos, notas al pie o memoria puramente fotográfica.
3. **Ajuste psicométrico:** Adapta la complejidad (concreta o abstracta, recuerdo estructurado o razonamiento complejo) y el formato de expresión (formal, verbal, numérico o gráfico) a la naturaleza del contenido y al perfil de los estudiantes.
4. **Foco en el enunciado:** Coloca el núcleo de la idea en el enunciado. Diseña las opciones como complementos cortos con perfecta concordancia gramatical, sintáctica y semántica con el enunciado.
5. **Claridad gramatical y afirmación:** Sintaxis correcta, directa, sin ambigüedades ni palabrería. Expresa el enunciado de forma **afirmativa**. Evita negaciones ("NO", "EXCEPTO"); si por extrema necesidad incluyes una, destácala en mayúsculas y negrita.
6. **Ajuste semántico:** Vocabulario preciso y nivel de lenguaje adaptado a los evaluados, sin que el léxico sea un obstáculo innecesario.
7. **Única respuesta y distractores plausibles:** Cada ítem tiene **una sola opción correcta**. Los distractores deben ser plausibles para quien no domina la materia (basados en errores o confusiones habituales) pero fácilmente descartables para quien sí la domina.
8. **Distribución uniforme de la respuesta correcta (auditable):** La respuesta correcta debe repartirse de forma equilibrada entre todas las letras a lo largo del examen:
   - Ninguna letra debe concentrar más del 40 % de las respuestas correctas del total.
   - En preguntas de 3 opciones, reparte para que a, b y c reciban un número de aciertos lo más parecido posible.
   - Antes de entregar, **cuenta** los aciertos por letra y, si alguna excede el umbral, reordena opciones hasta equilibrar.
9. **Número de opciones (3 por defecto, 4 siempre disponible):** El estándar **por defecto son 3 opciones (a, b, c)** (Rodríguez, 2005), porque dos distractores de alta calidad suelen ser más eficaces que un tercero débil. No obstante, **genera 4 opciones (a, b, c, d) siempre que un cuarto distractor aporte valor discriminativo real** (cuatro elementos, fases, categorías o errores frecuentes igual de plausibles que los otros dos).
   - **Criterio:** usa 4 cuando el cuarto distractor sea tan plausible como los demás; usa 3 cuando solo sería relleno.
   - **No suprimas** una pregunta de 4 opciones bien construida para cumplir la preferencia de 3, ni infles a 4 una cuyo cuarto distractor sea débil. La calidad del distractor manda sobre la cuota.
10. **Estructuración interna:** Ordena las opciones con lógica coherente (numérica ascendente, cronológica o conceptual) para no distraer con desorganización textual.
11. **Autonomía y exclusión:** Opciones independientes y sin solapamiento conceptual. **Prohibido** usar "Todas las anteriores" o "Ninguna de las anteriores".
12. **Homogeneidad formal:** Ninguna opción debe destacar por contenido ni apariencia (evita que la correcta sea más larga, detallada o técnicamente perfecta). Longitud y estructura gramatical similares en todas.
13. **Niveles de Dificultad:**
    * **Baja:** Reconocimiento literal de términos o datos explícitos.
    * **Media:** Requiere comprender o parafrasear conceptos.
    * **Alta:** Requiere relacionar partes del texto, inferir o aplicar lógica sobre la información dada.
14. **Cobertura temática equilibrada (reparto explícito):** Antes de generar:
    - Identifica los temas principales y su peso relativo.
    - Asigna preguntas proporcionalmente; ningún tema secundario recibirá más que un tema principal.
    - **Haz visible el reparto** en `examen_metadatos.distribucion_tematica`.
15. **No redundancia:** Dos preguntas no pueden evaluar el mismo conocimiento. Antes de crear una nueva, comprueba qué concepto ya se evaluó y evita reformularlo con otras palabras.
16. **Adaptación disciplinar:** Ajusta el tipo de razonamiento a la materia **según especifique el MÓDULO DE MATERIA**. El contenido evaluado procede siempre del documento (Regla 1), pero puedes apoyarte en el conocimiento disciplinar propio de la materia para construir distractores técnicamente correctos y verosímiles.
17. **Validación técnica:** Cuando una pregunta incluya código, fórmulas, expresiones matemáticas o pseudocódigo, verifica internamente lo que indique el MÓDULO DE MATERIA y, como mínimo, que: el código sea sintácticamente correcto; la salida esperada sea correcta; los cálculos estén comprobados; los distractores representen errores reales y frecuentes.
18. **Auditoría previa a la entrega:** Antes de devolver el examen, verifica:
    - Una única respuesta correcta por pregunta.
    - Distractores plausibles y sin pistas gramaticales.
    - Ausencia de solapamientos.
    - Distribución de dificultad correcta.
    - Cobertura temática coincidente con `distribucion_tematica`.
    - Distribución de respuestas dentro del umbral de la Regla 8 (recuento hecho).
    - Número de opciones justificado en cada pregunta (Regla 9).
    - JSON sintácticamente válido.
    - Las preguntas son **nuevas**, derivadas del documento; no reutilizan enunciados ni valores de los ejemplos del MÓDULO DE MATERIA.

## Formato de salida (JSON)
Entrega el resultado exclusivamente en un bloque JSON con esta estructura. No añadas texto fuera del bloque.

Notas sobre las opciones de 4:
- Las claves `d` en `opciones` y en `analisis_distractores`, y el campo `justificacion_4_opciones`, **solo aparecen en preguntas de 4 opciones** (Regla 9). En las de 3, omítelas por completo.
- En `analisis_distractores` incluye únicamente las opciones **incorrectas**; omite la entrada de la respuesta correcta.

```json
{
  "examen_metadatos": {
    "num_preguntas": "[NÚMERO]",
    "nivel_educativo": "[NIVEL]",
    "materia": "[la del MÓDULO DE MATERIA]",
    "fuente": "Texto proporcionado",
    "distribucion_tematica": [
      { "tema": "Tema principal 1", "num_preguntas": 0 },
      { "tema": "Tema principal 2", "num_preguntas": 0 }
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
        "d": "Cuarta opción — INCLUIR SOLO si la pregunta usa 4 opciones (Regla 9); omitir si no."
      },
      "justificacion_4_opciones": "INCLUIR SOLO si existe opción D: qué cuatro elementos, fases, categorías o errores frecuentes justifican un cuarto distractor con valor discriminativo real. Omitir si hay 3 opciones.",
      "respuesta_correcta": "a | b | c | d",
      "justificacion": {
        "evidencia_documental": "Fragmento o referencia del documento que sustenta la respuesta.",
        "razon_respuesta_correcta": "Por qué la opción marcada es la única correcta.",
        "nivel_cognitivo_evaluado": "Comprender",
        "concepto_principal": "Concepto central que evalúa la pregunta.",
        "error_comun_evaluado": "Confusión o error habitual que se pone a prueba.",
        "analisis_distractores": {
          "b": { "tipo_error": "Error conceptual | procedimental | de interpretación", "explicacion": "Por qué es incorrecta y por qué resulta plausible." },
          "c": { "tipo_error": "Error conceptual | procedimental | de interpretación", "explicacion": "Por qué es incorrecta y por qué resulta plausible." },
          "d": { "tipo_error": "INCLUIR SOLO si existe opción D y no es la correcta.", "explicacion": "Por qué es incorrecta y por qué resulta plausible." }
        }
      }
    }
  ]
}
```
