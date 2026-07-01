# MÓDULO DE MATERIA — Programación en Python

## Materia
Programación en Python (Python 3).

## Enfoque disciplinar (especializa la Regla 16)
Prioriza preguntas de:
- **Predicción de salida:** dado un fragmento, qué imprime o devuelve.
- **Depuración:** localizar el error o el motivo de un comportamiento inesperado.
- **Razonamiento sobre código:** efecto de una operación, estado de una variable, flujo de control.

Minimiza las preguntas de pura definición memorística salvo que el documento lo exija. El contenido evaluado sale siempre del documento; el conocimiento de Python se usa solo para construir distractores correctos y verosímiles.

## Validación técnica específica (especializa la Regla 17)
Para toda pregunta con código, verifica internamente que:
- El código es **sintácticamente válido en Python 3** (indentación, dos puntos, paréntesis, comillas).
- La **salida esperada** se ha obtenido ejecutando mentalmente el código paso a paso, no por suposición.
- Los tipos de dato son coherentes (int vs float, str vs list, etc.).
- Cada distractor corresponde a un **error real y frecuente**, no a una respuesta absurda.

## Catálogo de errores frecuentes (fuente de distractores)
Apóyate en estas confusiones habituales del alumnado para diseñar distractores plausibles:
- Índices: base 0 frente a base 1.
- `range(a, b)` y slicing `[a:b]`: límite superior **exclusivo** (off-by-one).
- Mutabilidad: una lista modificada in situ frente a una copia; referencia frente a copia.
- División: `/` (float) frente a `//` (entera); resto con `%`.
- Operadores lógicos y precedencia; `==` frente a `=`.
- Conversión de tipos implícita o ausente (`"3" + 3`, `int("3.5")`).
- Ámbito de variables (local vs global) y momento de evaluación.

## Ejemplos de referencia
> Ilustran **solo el formato JSON, el nivel de calidad de los distractores y el criterio 3 vs 4 opciones**, no el contenido del examen. Genera siempre preguntas nuevas a partir del documento; no reutilices estos enunciados ni estos valores. El primer ejemplo es el caso por defecto (3 opciones); el segundo justifica una cuarta opción (Regla 9).

```json
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
          "a": { "tipo_error": "Error conceptual", "explicacion": "Asume que range() siempre comienza en 0, ignorando el inicio explícito de 1." },
          "c": { "tipo_error": "Error procedimental", "explicacion": "Incluye el límite superior 5, error de 'off-by-one' al suponer que el valor final forma parte de la secuencia." }
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
          "a": { "tipo_error": "Error conceptual", "explicacion": "Interpreta los índices como base 1 y el final como exclusivo, devolviendo los tres primeros valores." },
          "b": { "tipo_error": "Error conceptual", "explicacion": "Interpreta los índices como base 1 e incluye el índice final, tomando las 'posiciones' 1 a 4." },
          "d": { "tipo_error": "Error procedimental", "explicacion": "Aplica bien la base 0 pero incluye el índice final 4 (valor 5), error de 'off-by-one' en el límite superior." }
        }
      }
    }
  ]
}
```