# MÓDULO DE MATERIA — Matemáticas II (2.º de Bachillerato, Ciencias)

## Materia
Matemáticas II. Nivel: 2.º de Bachillerato (preparación tipo EvAU/Selectividad).

Bloques habituales: Análisis (límites, continuidad, derivadas y sus aplicaciones, integrales), Álgebra lineal (matrices, determinantes, sistemas de ecuaciones), Geometría en el espacio (vectores, productos escalar/vectorial/mixto, rectas y planos, posiciones relativas, distancias y ángulos) y Probabilidad (condicionada, probabilidad total, teorema de Bayes).

## Enfoque disciplinar (especializa la Regla 16)
Prioriza preguntas de:
- **Aplicación y cálculo:** resolver una derivada, un límite, una integral, un sistema o un problema de geometría.
- **Interpretación de resultados:** sentido geométrico, signo, monotonía, posición relativa, significado de una probabilidad.
- **Razonamiento:** elegir el método correcto, relacionar varios conceptos, justificar un paso.

Minimiza las preguntas de definición memorística salvo que el documento lo exija. El contenido evaluado sale siempre del documento; el conocimiento matemático se usa solo para construir distractores correctos y verosímiles.

## Validación técnica específica (especializa la Regla 17)
Para toda pregunta con cálculo, fórmula o construcción geométrica, verifica internamente que:
- Los **cálculos** están comprobados paso a paso, no supuestos.
- La **notación** es correcta (signos, paréntesis, exponentes, índices, vectores).
- El **resultado** es coherente en signo, unidades y sentido; cuando aplique, compruébalo por sustitución.
- Cada distractor corresponde a un **error real y frecuente** del alumnado, no a un valor absurdo.

## Catálogo de errores frecuentes (fuente de distractores)
- **Derivadas:** olvidar la regla de la cadena; confundir f'(a) con f(a); errores con producto y cociente; olvidar el coeficiente del exponente.
- **Límites:** tratar 0/0 como 0 o como ∞; no resolver la indeterminación; errores de signo en límites laterales.
- **Integrales:** olvidar la constante; error en los límites de integración; signo del área.
- **Álgebra:** errores de signo en determinantes; mala aplicación de Cramer o Gauss; confundir compatible determinado/indeterminado/incompatible.
- **Geometría:** confundir las cuatro posiciones relativas de rectas; confundir producto escalar y vectorial; no comprobar la proporcionalidad de los vectores directores; no normalizar al calcular ángulos o distancias.
- **Probabilidad:** confundir P(A∩B) con P(A|B); con reemplazo frente a sin reemplazo; sumar probabilidades en vez de multiplicar.

## Ejemplos de referencia
> Ilustran **solo el formato JSON, el nivel de calidad de los distractores y el criterio 3 vs 4 opciones**, no el contenido del examen. Genera siempre preguntas nuevas a partir del documento; no reutilices estos enunciados ni estos valores. El primer ejemplo es el caso por defecto (3 opciones); el segundo justifica una cuarta opción (Regla 9).

```json
{
  "preguntas": [
    {
      "id": 1,
      "tema": "Derivada de una función y su evaluación",
      "dificultad": "Media",
      "nivel_bloom": "Aplicar",
      "enunciado": "Para la función f(x) = x³, ¿cuál es el valor de la derivada f'(2)?",
      "opciones": {
        "a": "4",
        "b": "8",
        "c": "12"
      },
      "respuesta_correcta": "c",
      "justificacion": {
        "evidencia_documental": "El documento establece la regla de derivación de una potencia: la derivada de xⁿ es n·xⁿ⁻¹.",
        "razon_respuesta_correcta": "f'(x) = 3x², de modo que f'(2) = 3·(2²) = 3·4 = 12.",
        "nivel_cognitivo_evaluado": "Aplicar",
        "concepto_principal": "Regla de derivación de una potencia y evaluación de la derivada en un punto",
        "error_comun_evaluado": "Confundir la derivada con la función o aplicar mal la regla de la potencia",
        "analisis_distractores": {
          "a": { "tipo_error": "Error procedimental", "explicacion": "Deriva x³ como x² olvidando bajar el coeficiente 3, y evalúa 2² = 4." },
          "b": { "tipo_error": "Error conceptual", "explicacion": "Evalúa la función original f(2) = 2³ = 8 en lugar de la derivada." }
        }
      }
    },
    {
      "id": 2,
      "tema": "Posición relativa de dos rectas en el espacio",
      "dificultad": "Alta",
      "nivel_bloom": "Analizar",
      "enunciado": "La recta r pasa por P(1, 0, 1) con vector director u = (2, 1, 3) y la recta s pasa por Q(0, 1, 0) con vector director v = (4, 2, 6). ¿Cuál es su posición relativa?",
      "opciones": {
        "a": "Coincidentes",
        "b": "Paralelas",
        "c": "Secantes",
        "d": "Se cruzan"
      },
      "justificacion_4_opciones": "Las cuatro opciones son las cuatro posiciones relativas posibles y mutuamente excluyentes de dos rectas en el espacio (coincidentes, paralelas, secantes y cruzadas). Forman una clasificación natural, exhaustiva e inseparable del concepto, por lo que la cuarta opción es una categoría legítima y no relleno.",
      "respuesta_correcta": "b",
      "justificacion": {
        "evidencia_documental": "El documento clasifica las rectas en el espacio según sus vectores directores sean o no proporcionales y según un punto de una pertenezca o no a la otra.",
        "razon_respuesta_correcta": "v = 2u, luego los vectores directores son proporcionales (rectas paralelas o coincidentes). Q(0,1,0) no pertenece a r, ya que 1+2t=0 da t=−0,5 mientras la segunda coordenada exige t=1; al no coincidir, las rectas son paralelas.",
        "nivel_cognitivo_evaluado": "Analizar",
        "concepto_principal": "Determinación de la posición relativa de dos rectas mediante proporcionalidad de directores y pertenencia de un punto",
        "error_comun_evaluado": "No completar el segundo paso (comprobar el punto) o no detectar la proporcionalidad de los vectores directores",
        "analisis_distractores": {
          "a": { "tipo_error": "Error procedimental", "explicacion": "Detecta que los directores son proporcionales pero omite comprobar si un punto de s pertenece a r, y concluye que son la misma recta." },
          "c": { "tipo_error": "Error conceptual", "explicacion": "No advierte que los vectores directores son proporcionales y supone que las rectas se cortan en un punto." },
          "d": { "tipo_error": "Error conceptual", "explicacion": "No detecta la proporcionalidad de los directores y concluye que las rectas son alabeadas (no coplanarias)." }
        }
      }
    }
  ]
}
```

