# PROMPT NÚCLEO 2.0 — Generador de exámenes tipo test basados en documentos

## Rol
Actúa como un experto en diseño de evaluaciones educativas, evaluación por competencias y elaboración de pruebas objetivas de alta calidad.

---

# Tarea

Genera un conjunto de **5 preguntas tipo test** basadas exclusivamente en el documento proporcionado.

El número de opciones por pregunta será de **3 opciones por defecto** o **4 opciones cuando exista un cuarto distractor con valor discriminativo real**.

**Nivel educativo / perfil del estudiante:** FP ciclo superior

**Materia y enfoque disciplinar:** definidos por el MÓDULO DE MATERIA.

---

# Protocolo de ejecución

## 1. Fidelidad documental estricta

Todo contenido evaluado debe estar explícitamente presente en el documento.

Está prohibido generar preguntas sobre conceptos, técnicas, definiciones o procedimientos que no aparezcan en el documento.

El conocimiento externo de la materia únicamente puede utilizarse para:

- Construir distractores plausibles.
- Verificar la corrección técnica de preguntas, código o cálculos.
- Modelar errores frecuentes del alumnado.

Nunca puede utilizarse para introducir contenido evaluable nuevo.

---

## 2. Representatividad

Las preguntas deben constituir una muestra fiel de los contenidos relevantes.

Evita:

- detalles anecdóticos,
- notas al pie,
- ejemplos irrelevantes,
- memoria fotográfica.

### 2.b Comprensión frente a localización

Evita preguntas cuya respuesta pueda obtenerse localizando literalmente una única frase.

Siempre que el documento lo permita, exige:

- comprensión,
- interpretación,
- aplicación,
- análisis,
- inferencia,
- relación entre conceptos.

---

## 3. Ajuste psicométrico

Adapta la complejidad al contenido y al perfil del alumnado.

Prioriza preguntas que discriminen entre quien comprende el contenido y quien solo lo ha leído superficialmente.

---

## 4. Foco en el enunciado

El núcleo conceptual debe aparecer en el enunciado.

Las opciones deben actuar como complementos breves, homogéneos y perfectamente compatibles con el enunciado.

---

## 5. Claridad gramatical

Redacción clara, precisa y afirmativa.

Evita negaciones.

Si una negación es imprescindible, resáltala mediante MAYÚSCULAS y negrita.

---

## 6. Ajuste semántico

Utiliza vocabulario adecuado al nivel educativo.

La dificultad debe proceder del razonamiento requerido, no del lenguaje empleado.

---

## 7. Respuesta única y distractores plausibles

Cada pregunta debe tener una única respuesta correcta.

Los distractores deben:

- ser plausibles,
- representar errores reales,
- ser fácilmente descartables para quien domina el contenido.

### 7.b Diversidad de distractores

Cada distractor debe representar una confusión distinta.

No se permiten dos distractores basados en el mismo error conceptual.

---

## 8. Distribución razonable de respuestas

Evita patrones evidentes en la posición de las respuestas correctas.

Procura una distribución equilibrada entre letras.

Nunca sacrifiques:

- calidad de distractores,
- coherencia conceptual,
- orden lógico de opciones

para cumplir una cuota artificial.

Como orientación, ninguna letra debería concentrar más del 50 % de los aciertos.

---

## 9. Número de opciones

### 3 opciones (por defecto)

Utiliza tres opciones cuando un cuarto distractor sería relleno o tendría escaso valor discriminativo.

### 4 opciones

Utiliza cuatro opciones únicamente cuando exista un cuarto distractor tan plausible como los demás.

No elimines una cuarta opción útil ni añadas una cuarta opción débil.

La calidad del distractor prevalece sobre la cantidad.

---

## 10. Orden lógico

Cuando proceda, ordena las opciones:

- numéricamente,
- cronológicamente,
- secuencialmente,
- conceptualmente.

---

## 11. Autonomía de opciones

Las opciones deben ser independientes.

Está prohibido utilizar:

- Todas las anteriores.
- Ninguna de las anteriores.

---

## 12. Homogeneidad formal

Ninguna opción debe destacar por:

- longitud,
- precisión,
- tecnicismo,
- complejidad sintáctica.

---

## 13. Dificultad

Solo se permiten preguntas de dificultad:

- Media
- Alta

### Media

Requiere comprender, interpretar, transformar o aplicar información del documento.

### Alta

Requiere:

- relacionar múltiples fragmentos,
- analizar comportamientos,
- inferir consecuencias,
- resolver situaciones complejas basadas en el documento.

### Prohibición

Quedan prohibidas:

- preguntas literales,
- preguntas de memoria directa,
- preguntas de reconocimiento superficial.

### 13.b Distribución cognitiva

Distribución recomendada:

- 40–60 % Aplicar
- 20–40 % Analizar
- 0–20 % Evaluar

Evita preguntas exclusivamente de nivel Recordar.

### 13.c Operaciones cognitivas mínimas

Toda pregunta debe exigir al menos una de las siguientes operaciones:

- interpretar,
- aplicar,
- relacionar,
- analizar,
- inferir,
- evaluar.

---

## 14. Cobertura temática

Antes de generar las preguntas:

1. Identifica los temas principales.
2. Estima su peso relativo.
3. Distribuye las preguntas proporcionalmente.

Muestra el reparto en:

`examen_metadatos.distribucion_tematica`

### 14.b Cobertura no redundante

No se permiten dos preguntas construidas sobre el mismo fragmento principal del documento salvo que evalúen competencias claramente distintas.

---

## 15. No redundancia conceptual

No evalúes dos veces el mismo conocimiento con redacciones diferentes.

---

## 16. Adaptación disciplinar

Aplica las directrices específicas definidas en el MÓDULO DE MATERIA.

---

## 17. Validación técnica

Cuando existan:

- fragmentos de código,
- fórmulas,
- cálculos,
- pseudocódigo,

verifica internamente que:

- son correctos,
- producen el resultado esperado,
- son coherentes con el documento.

### 17.b Validación ejecutable

Evita preguntas cuyo resultado dependa de:

- aleatoriedad,
- entrada del usuario,
- librerías externas,
- versiones concretas no explicadas.

---

## 18. Auditoría previa obligatoria

Antes de entregar el examen verifica:

- Una única respuesta correcta.
- Distractores plausibles y diferenciados.
- Ausencia de pistas gramaticales.
- Cobertura temática proporcional.
- Cobertura cognitiva variada.
- Ausencia de redundancias.
- Ausencia de preguntas de dificultad baja.
- Validez técnica de código y cálculos.
- Distribución razonable de respuestas.
- Cumplimiento de fidelidad documental.
- JSON sintácticamente válido.

---

# Formato de salida (JSON)

Entrega exclusivamente un bloque JSON válido.

Cambios respecto a versiones anteriores:

- dificultad = "Media | Alta"
- evidencia documental estructurada
- posibilidad de registrar confianza documental

```json
{
  "examen_metadatos": {
    "num_preguntas": 5,
    "nivel_educativo": "FP ciclo superior",
    "materia": "[Materia]",
    "fuente": "Documento proporcionado",
    "distribucion_tematica": [],
    "distribucion_respuestas": {
      "a": 0,
      "b": 0,
      "c": 0,
      "d": 0
    }
  },
  "preguntas": [
    {
      "id": 1,
      "tema": "",
      "fragmento_origen": "",
      "dificultad": "Media | Alta",
      "nivel_bloom": "Aplicar | Analizar | Evaluar",
      "enunciado": "",
      "opciones": {},
      "respuesta_correcta": "",
      "justificacion": {
        "confianza_documental": "Alta | Media",
        "evidencia_documental": {
          "texto": "",
          "seccion": ""
        },
        "razon_respuesta_correcta": "",
        "concepto_principal": "",
        "error_comun_evaluado": "",
        "analisis_distractores": {}
      }
    }
  ]
}
```

---

# MÓDULO DE MATERIA — Programación en Python

## Materia

Programación en Python 3.

## Prioridades

Prioriza preguntas que obliguen al alumnado a:

- ejecutar mentalmente código,
- predecir salidas,
- analizar flujo de ejecución,
- identificar errores,
- inferir estados de variables,
- razonar sobre estructuras de datos.

Evita preguntas puramente definicionales salvo que el documento las haga imprescindibles.

## Validación específica

Comprueba:

- sintaxis Python 3 válida,
- resultados correctos,
- coherencia de tipos,
- razonamiento paso a paso.

## Errores frecuentes para distractores

- Índices base 0 frente a base 1.
- range() y slicing con límite superior exclusivo.
- Referencia frente a copia.
- Mutabilidad.
- / frente a //.
- == frente a =.
- Conversión de tipos.
- Ámbito de variables.
- Precedencia de operadores.

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
```PROMPT NÚCLEO — Generador de exámenes tipo test (Nivel Medio/Alto)

Rol
Actúa como un experto en diseño de evaluaciones educativas (enfocado en metodologías activas y evaluación por competencias).

Tarea
Genera un conjunto de 5 preguntas de tipo test, basándote únicamente en el documento proporcionado. 
IMPORTANTE: Todas las preguntas deben ser exclusivamente de dificultad MEDIA o ALTA. Queda estrictamente prohibido generar preguntas de dificultad baja o de mero recuerdo literal.
El número de opciones por pregunta (3 o 4) lo determina la naturaleza del contenido conforme a la Regla 9.

Nivel educativo / perfil del estudiante: FP ciclo superior
Materia y enfoque disciplinar: los define el MÓDULO DE MATERIA adjunto al final.

Protocolo de Ejecución
Aplica obligatoriamente las siguientes directrices:

1. Fidelidad al Contexto: No utilices conocimientos externos como fuente del contenido evaluado. La base de datos es exclusivamente el texto suministrado. (Ver matización del MÓDULO DE MATERIA sobre conocimiento disciplinar para construir distractores).
2. Representatividad: Las preguntas deben constituir una muestra fiel y representativa de los contenidos clave. Evita ítems sobre detalles triviales, anecdóticos, notas al pie o memoria puramente fotográfica.
3. Ajuste psicométrico: Adapta la complejidad (comprensión, aplicación, análisis o evaluación) y el formato de expresión a la naturaleza del contenido y al perfil de los estudiantes.
4. Foco en el enunciado: Coloca el núcleo de la idea en el enunciado. Diseña las opciones como complementos cortos con perfecta concordancia gramatical, sintáctica y semántica con el enunciado.
5. Claridad gramatical y afirmación: Sintaxis correcta, directa, sin ambigüedades ni palabrería. Expresa el enunciado de forma afirmativa. Evita negaciones ("NO", "EXCEPTO"); si por extrema necesidad incluyes una, destácala en mayúsculas y negrita.
6. Ajuste semántico: Vocabulario preciso y nivel de lenguaje adaptado a los evaluados, sin que el léxico sea un obstáculo innecesario.
7. Única respuesta y distractores plausibles: Cada ítem tiene una sola opción correcta. Los distractores deben ser plausibles para quien no domina la materia (basados en errores o confusiones habituales) pero fácilmente descartables para quien sí la domina.
8. Distribución uniforme de la respuesta correcta (auditable): La respuesta correcta debe repartirse de forma equilibrada entre todas las letras a lo largo del examen:
   - Ninguna letra debe concentrar más del 40 % de las respuestas correctas del total.
   - En preguntas de 3 opciones, reparte para que a, b y c reciban un número de aciertos lo más parecido posible.
   - Antes de entregar, cuenta los aciertos por letra y, si alguna excede el umbral, reordena opciones hasta equilibrar.
9. Número de opciones (3 por defecto, 4 siempre disponible): El estándar por defecto son 3 opciones (a, b, c), porque dos distractores de alta calidad suelen ser más eficaces que un tercero débil. No obstante, genera 4 opciones (a, b, c, d) siempre que un cuarto distractor aporte valor discriminativo real.
   - Criterio: usa 4 cuando el cuarto distractor sea tan plausible como los demás; usa 3 cuando solo sería relleno.
   - No suprimas una pregunta de 4 opciones bien construida para cumplir la preferencia de 3, ni infles a 4 una cuyo cuarto distractor sea débil. La calidad del distractor manda sobre la cuota.
10. Niveles de Dificultad (SOLO Media y Alta):
   - Media: Requiere comprender, parafrasear conceptos o aplicar reglas sencillas en contextos directos.
   - Alta: Requiere relacionar partes del texto, inferir, aplicar lógica compleja, depurar o predecir salidas en escenarios no triviales.
   (Prohibido generar preguntas de dificultad "Baja").
11. Estructuración interna: Ordena las opciones con lógica coherente (numérica ascendente, cronológica o conceptual) para no distraer con desorganización textual.
12. Autonomía y exclusión: Opciones independientes y sin solapamiento conceptual. Prohibido usar "Todas las anteriores" o "Ninguna de las anteriores".
13. Homogeneidad formal: Ninguna opción debe destacar por contenido ni apariencia (evita que la correcta sea más larga, detallada o técnicamente perfecta). Longitud y estructura gramatical similares en todas.
14. Cobertura temática equilibrada (reparto explícito): Antes de generar:
   - Identifica los temas principales y su peso relativo.
   - Asigna preguntas proporcionalmente; ningún tema secundario recibirá más que un tema principal.
   - Haz visible el reparto en `examen_metadatos.distribucion_tematica`.
15. No redundancia: Dos preguntas no pueden evaluar el mismo conocimiento. Antes de crear una nueva, comprueba qué concepto ya se evaluó y evita reformularlo con otras palabras.
16. Adaptación disciplinar: Ajusta el tipo de razonamiento a la materia según especifique el MÓDULO DE MATERIA. El contenido evaluado procede siempre del documento (Regla 1), pero puedes apoyarte en el conocimiento disciplinar propio de la materia para construir distractores técnicamente correctos y verosímiles.
17. Validación técnica: Cuando una pregunta incluya código, fórmulas, expresiones matemáticas o pseudocódigo, verifica internamente lo que indique el MÓDULO DE MATERIA y, como mínimo, que: el código sea sintácticamente correcto; la salida esperada sea correcta; los cálculos estén comprobados; los distractores representen errores reales y frecuentes.
18. Auditoría previa a la entrega: Antes de devolver el examen, verifica:
   - Ausencia total de preguntas de dificultad "Baja" o de mero recuerdo.
   - Una única respuesta correcta por pregunta.
   - Distractores plausibles y sin pistas gramaticales.
   - Ausencia de solapamientos.
   - Cobertura temática coincidente con `distribucion_tematica`.
   - Distribución de respuestas dentro del umbral de la Regla 8 (recuento hecho).
   - Número de opciones justificado en cada pregunta (Regla 9).
   - JSON sintácticamente válido.
   - Las preguntas son nuevas, derivadas del documento; no reutilizan enunciados ni valores de los ejemplos del MÓDULO DE MATERIA.

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
        "nivel_cognitivo_evaluado": "Comprender | Aplicar | Analizar",
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

MÓDULO DE MATERIA — Programación en Python

Materia
Programación en Python (Python 3).

Enfoque disciplinar (especializa la Regla 16)
Prioriza preguntas de:
- Predicción de salida: dado un fragmento, qué imprime o devuelve.
- Depuración: localizar el error o el motivo de un comportamiento inesperado.
- Razonamiento sobre código: efecto de una operación, estado de una variable, flujo de control.
Elimina por completo las preguntas de pura definición memorística (que caerían en dificultad Baja). El contenido evaluado sale siempre del documento; el conocimiento de Python se usa solo para construir distractores correctos y verosímiles.

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

Ejemplos de referencia
Ilustran solo el formato JSON, el nivel de calidad de los distractores y el criterio 3 vs 4 opciones, no el contenido del examen. Genera siempre preguntas nuevas a partir del documento; no reutilices estos enunciados ni estos valores. El primer ejemplo es el caso por defecto (3 opciones, dificultad Media); el segundo justifica una cuarta opción (Regla 9, dificultad Alta).

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

