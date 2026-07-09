## VISTA ONLINE
https://chat.mistral.ai/work/fbf9a532-08c5-400d-9bf8-a3858bb8ed25

## USER

evalua este prompt pensado para hacer preguntas tipo test a partir de un documento. 

## MISTRAL



Evaluación del Prompt para Generación de Exámenes Tipo Test en Python

📌 Resumen Ejecutivo
Calificación: 9.5/10 (Excelente, con ajustes menores para optimizar claridad y flexibilidad).
El prompt es extremadamente robusto, cubre todos los aspectos críticos para generar preguntas de alta calidad psicométrica y pedagógica, y está especialmente bien adaptado a la evaluación de programación en Python. Su estructura es clara, sus reglas son específicas, y el formato de salida (JSON) es impecable. Es uno de los prompts más completos que he evaluado para este propósito.

✅ Puntos Fuertes
1. Estructura y Claridad

Jerarquía lógica: Separación clara entre rol, tarea, protocolo de ejecución, módulo de materia y formato de salida.
Secciones bien definidas: Cada regla (1–18) aborda un aspecto concreto (ej: fidelidad documental, distractores, nivel cognitivo).
Ejemplos prácticos: Los ejemplos en JSON ilustran el formato, la calidad de los distractores y el criterio para 3 vs. 4 opciones.

2. Cobertura de Criterios Pedagógicos


  
    
      Criterio
      ¿Está cubierto?
      Detalle
    
  
  
    
      Fidelidad documental
      ✅ Sí
      Regla 1: Prohíbe introducir contenido externo. Exige evidencia documental en la justificación.
    
    
      Nivel cognitivo
      ✅ Sí (destacado)
      Regla 13: Prohíbe preguntas literales. Prioriza Aplicar (40–60%), Analizar (20–40%), Evaluar (0–20%).
    
    
      Calidad de distractores
      ✅ Sí
      Reglas 7–9: Exige plausibilidad, diversidad y valor discriminativo. Prohíbe "Todas/Ninguna".
    
    
      Distribución de respuestas
      ✅ Sí
      Regla 8: Evita patrones (ej: no más del 50% en una letra).
    
    
      Validación técnica
      ✅ Sí
      Reglas 17–18: Verifica sintaxis Python, resultados, coherencia de tipos y código ejecutable.
    
    
      Cobertura temática
      ✅ Sí
      Regla 14: Exige identificar temas principales y distribuir preguntas proporcionalmente.
    
  




3. Adaptación a Programación en Python
El MÓDULO DE MATERIA es excelente:

Prioridades claras: Enfocado en ejecución mental de código, predicción de salidas, análisis de flujo, identificación de errores y razonamiento sobre estructuras de datos.
Errores frecuentes para distractores:

Índices base 0 vs. base 1.
range() y slicing con límite exclusivo.
Referencia vs. copia / mutabilidad.
/ vs. //, == vs. =, ámbito de variables, precedencia de operadores.
→ Cubre los errores más comunes en Python, lo que garantiza distractores realistas y útiles.

Validación específica:

Sintaxis Python 3 válida.
Resultados correctos y coherencia de tipos.
Razonamiento paso a paso.


4. Formato de Salida (JSON)

Estructura impecable: Incluye metadatos (distribución temática, respuestas), justificación detallada (evidencia documental, análisis de distractores) y campos para confianza y nivel Bloom.
Ejemplos útiles: Muestran cómo aplicar el formato en casos concretos (3 vs. 4 opciones).
Flexibilidad: Permite registrar confianza documental (Alta/Media) y evidencia estructurada (texto + sección).

5. Enfoque en Calidad Psicométrica

Regla 3: Adapta la complejidad al contenido y perfil del alumnado (FP ciclo superior).
Regla 12: Homogeneidad formal en opciones (evita que una opción destaque por longitud o tecnicismo).
Regla 15: Prohíbe redundancia conceptual (no evaluar el mismo conocimiento con redacciones distintas).

⚠️ Áreas de Mejora (Menores)
1. Longitud y Complejidad

Problema: El prompt es muy largo (18 reglas + módulo de materia). Podría abrumar a usuarios menos experimentados.
Solución:

Agrupar reglas relacionadas: Por ejemplo, fusionar las reglas 7, 7b, 9 y 11 en una sección única sobre distractores.
Incluir un resumen ejecutivo al inicio con los principios clave (ej: "1. Fidelidad documental absoluta. 2. Prioriza aplicación/análisis. 3. Distractores plausibles y diversos.").


2. Flexibilidad para Otros Lenguajes o Materias

Problema: El MÓDULO DE MATERIA está hardcodeado para Python. Si se quiere reutilizar el prompt para Java, C++ o Matemáticas, habría que reescribirlo.
Solución:

Separar el núcleo genérico (reglas 1–18) del módulo específico.
Añadir un placeholder para el módulo de materia:
markdown
Copy

## MÓDULO DE MATERIA — [NOMBRE]
**Materia**: [Ej: Programación en Python 3, Álgebra Lineal, etc.]
**Prioridades**: [Describir enfoque disciplinar]
**Errores frecuentes para distractores**: [Lista específica]
**Validación específica**: [Criterios técnicos]






3. Manejo de Documentos Ambiguos o con Errores

Problema: No se especifica cómo actuar si el documento:

Tiene errores técnicos (ej: código Python incorrecto).
Es ambiguo (ej: definiciones contradictorias).
No contiene suficiente información para generar 5 preguntas de calidad.

Solución:

Añadir una regla 19:

"19. Manejo de documentos problemáticos

Si el documento contiene errores técnicos, no generes preguntas basadas en ellos. Ignóralos o corrígelos internamente (y documéntalo en justificacion.confianza_documental = 'Media').
Si el documento es ambiguo, evita preguntas sobre los fragmentos ambiguos o reformúlalas para que la respuesta correcta sea inequívoca.
Si no hay suficiente contenido relevante, genera menos de 5 preguntas y justifícalo en examen_metadatos.notas."




4. Validación de Ejecutabilidad en Python

Problema: La Regla 17b prohíbe preguntas que dependan de aleatoriedad, entrada de usuario o librerías externas. Sin embargo, no se aclara si se permite:

Uso de librerías estándar de Python (ej: math, random si se fija una semilla).
Código que modifica variables globales (ej: global x).

Solución:

Especificar:

"17b. Validación ejecutable (ampliado)

Permitido: Uso de librerías estándar de Python (ej: math, os) si están mencionadas en el documento.
Prohibido: Dependencia de:

Aleatoriedad sin semilla fija (ej: random.randint() sin random.seed(42)).
Entrada de usuario (input()).
Librerías externas no estándar (ej: numpy, pandas).
Versiones específicas de Python no explicadas."





5. Distribución Cognitiva (Regla 13b)

Problema: La distribución recomendada (40–60% Aplicar, 20–40% Analizar, 0–20% Evaluar) es fija. En algunos documentos, podría ser más adecuado priorizar Analizar sobre Aplicar.
Solución:

Hacerla flexible:

"13b. Distribución cognitiva (recomendación)

Por defecto: 40–60% Aplicar, 20–40% Analizar, 0–20% Evaluar.
Ajustable: Si el documento lo justifica (ej: enfoque teórico), prioriza Analizar o Evaluar según el contenido."




6. Formato de Salida: Campos Opcionales

Problema: El JSON incluye campos como justificacion_4_opciones (solo en el ejemplo 2), pero no se aclara si es obligatorio o opcional.
Solución:

Especificar en el formato de salida:

"Campos opcionales:

justificacion_4_opciones: Solo incluir si se usan 4 opciones y se justifica su valor discriminativo (Regla 9).
examen_metadatos.notas: Para observaciones adicionales (ej: 'Documento con errores menores en la sección X')."




🔍 Comparación con Estándares de Buenas Prácticas


  
    
      Criterio
      Prompt Actual
      Estándar Ideal
      Diferencia
    
  
  
    
      Fidelidad documental
      ✅ Excelente
      ✅ Excelente
      -
    
    
      Nivel cognitivo
      ✅ Excelente
      ✅ Excelente
      -
    
    
      Calidad de distractores
      ✅ Excelente
      ✅ Excelente
      -
    
    
      Adaptación a Python
      ✅ Excelente
      ✅ Excelente
      -
    
    
      Manejo de ambigüedades
      ❌ No cubierto
      ✅ Recomendado
      Falta regla
    
    
      Flexibilidad
      ⚠️ Limitada
      ✅ Alta
      Hardcodeado a Python
    
    
      Longitud
      ⚠️ Muy largo
      ✅ Conciso
      Podría resumirse
    
  




📝 Recomendaciones Finales
1. Para Uso Inmediato (Python)

Aplica el prompt tal cual. Es excelente para generar exámenes de Python basados en documentos.
Añade la Regla 19 (manejo de documentos problemáticos) para mayor robustez.
2. Para Reutilización en Otras Materias

Modulariza el prompt:

Núcleo genérico: Reglas 1–18 (universales para cualquier materia).
Módulo específico: Adaptable a Python, Java, Matemáticas, etc.

3. Para Mejorar la Claridad

Añade un resumen inicial con los 5 principios clave.
Simplifica la redacción de algunas reglas (ej: la Regla 13c podría ser más concisa).

🎯 Veredicto
✅ Aprobado con honores.
Este prompt es de los mejores que he visto para generar preguntas tipo test de programación. Con los ajustes menores sugeridos (especialmente la Regla 19 y la modularización), sería perfecto.

¿Necesitas ayuda para implementar alguno de los ajustes o adaptarlo a otro lenguaje? 🛠️

## USER

añade las mejoras propuestas y ajusta para que solo cree preguntas de dificultad media y alta

## MISTRAL

# PROMPT NÚCLEO 3.0 — Generador de exámenes tipo test basados en documentos (SOLO DIFICULTAD MEDIA/ALTA)

---
## 📌 RESUMEN EJECUTIVO
1. **Fidelidad absoluta**: Solo contenido explícito en el documento.
2. **Dificultad**: **Únicamente Media o Alta** (prohibidas preguntas literales o de memoria).
3. **Enfoque cognitivo**: Prioriza **Aplicar (40–60%)**, **Analizar (20–40%)**, **Evaluar (0–20%)**.
4. **Distractores**: Plausibles, diversos y con valor discriminativo real.
5. **Validación**: Código, fórmulas y cálculos deben ser técnicamente correctos.

---

---

# Rol
Actúa como un **experto en diseño de evaluaciones educativas**, especializado en **elaboración de pruebas objetivas de alta calidad psicométrica** para formación profesional (FP ciclo superior).

---

# Tarea
Genera un conjunto de **5 preguntas tipo test** basadas **exclusivamente** en el documento proporcionado, con las siguientes restricciones:
- **Dificultad**: **Solo "Media" o "Alta"**. Prohibidas preguntas de dificultad baja (literales, memoria directa o reconocimiento superficial).
- **Número de opciones**: **3 por defecto** o **4 cuando exista un cuarto distractor con valor discriminativo real**.
- **Nivel educativo**: FP ciclo superior.
- **Materia**: Definida por el **MÓDULO DE MATERIA** (adaptable a cualquier disciplina).

---

---

# 📜 Protocolo de Ejecución

## 1. Fidelidad Documental Estricta
- **Todo el contenido evaluable debe aparecer explícitamente en el documento**.
- **Prohibido**: Generar preguntas sobre conceptos, técnicas o definiciones no presentes.
- **Permitido usar conocimiento externo solo para**:
  - Construir distractores plausibles.
  - Verificar corrección técnica (código, cálculos).
  - Modelar errores frecuentes del alumnado.

---

## 2. Representatividad
- Las preguntas deben ser una **muestra fiel de los contenidos relevantes**.
- **Evita**: Detalles anecdóticos, notas al pie, ejemplos irrelevantes o memoria fotográfica.

---
### 2.b Comprensión frente a Localización
- **Prohibido**: Preguntas cuya respuesta se obtenga localizando literalmente una frase.
- **Exige siempre**:
  - Comprensión.
  - Interpretación.
  - Aplicación.
  - Análisis.
  - Inferencia.
  - Relación entre conceptos.

---

## 3. Ajuste Psicométrico
- Adapta la complejidad al contenido y al perfil del alumnado (FP ciclo superior).
- **Prioriza**: Preguntas que discriminen entre quien **comprende** el contenido y quien solo lo ha leído superficialmente.

---

## 4. Foco en el Enunciado
- El **núcleo conceptual debe aparecer en el enunciado**.
- Las opciones deben ser **complementos breves, homogéneos y compatibles** con el enunciado.

---
## 5. Claridad Gramatical
- Redacción **clara, precisa y afirmativa**.
- **Evita negaciones**. Si son imprescindibles, resáltalas: **NO** o **NUNCA**.

---
## 6. Ajuste Semántico
- Usa vocabulario adecuado al nivel educativo (FP ciclo superior).
- La dificultad debe provenir del **razonamiento requerido**, no del lenguaje.

---
## 7. Distractores y Opciones
### 7.a Requisitos de Distractores
- Cada pregunta tiene **una única respuesta correcta**.
- Los distractores deben:
  - Ser **plausibles**.
  - Representar **errores reales y distintos** (no dos distractores basados en el mismo error conceptual).
  - Ser **fácilmente descartables** para quien domina el contenido.

### 7.b Número de Opciones
- **3 opciones**: Por defecto.
- **4 opciones**: Solo si el cuarto distractor tiene **valor discriminativo real** (ej: modelos mentales distintos sobre el mismo concepto).
  - **Nunca** añadas una cuarta opción débil ni elimines una útil.

### 7.c Autonomía de Opciones
- **Prohibido**: Usar "Todas las anteriores" o "Ninguna de las anteriores".

### 7.d Homogeneidad Formal
- Ninguna opción debe destacar por:
  - Longitud.
  - Precisión.
  - Tecnicismo.
  - Complejidad sintáctica.

---
## 8. Distribución Razonable de Respuestas
- Evita patrones evidentes en la posición de las respuestas correctas.
- **Orientación**: Ninguna letra (a, b, c, d) debería concentrar más del **50% de los aciertos**.
- **Nunca sacrifiques**:
  - Calidad de distractores.
  - Coherencia conceptual.
  - Orden lógico de opciones.

---
## 9. Orden Lógico
- Cuando proceda, ordena las opciones:
  - Numéricamente.
  - Cronológicamente.
  - Secuencialmente.
  - Conceptualmente.

---
## 10. Dificultad (SOLO MEDIA O ALTA)
### 10.a Niveles Permitidos
   **Dificultad** | **Definición** |
 |----------------|----------------|
 | **Media**      | Requiere comprender, interpretar, transformar o aplicar información del documento. |
 | **Alta**       | Requiere relacionar múltiples fragmentos, analizar comportamientos, inferir consecuencias o resolver situaciones complejas. |

### 10.b Prohibiciones
- **Preguntas literales**.
- **Preguntas de memoria directa**.
- **Preguntas de reconocimiento superficial**.

### 10.c Distribución Cognitiva (Recomendada)
- **Aplicar**: 40–60%.
- **Analizar**: 20–40%.
- **Evaluar**: 0–20%.
- **Flexible**: Ajusta según el contenido del documento.

### 10.d Operaciones Cognitivas Mínimas
- **Toda pregunta debe exigir al menos una** de estas operaciones:
  - Interpretar.
  - Aplicar.
  - Relacionar.
  - Analizar.
  - Inferir.
  - Evaluar.

---
## 11. Cobertura Temática
1. Identifica los **temas principales** del documento.
2. Estima su **peso relativo**.
3. Distribuye las preguntas **proporcionalmente**.
- **Muestra el reparto** en `examen_metadatos.distribucion_tematica`.

---
### 11.b Cobertura No Redundante
- **Prohibido**: Dos preguntas sobre el **mismo fragmento principal** del documento, salvo que evalúen **competencias claramente distintas**.

---
## 12. No Redundancia Conceptual
- **Prohibido**: Evaluar el mismo conocimiento con redacciones diferentes.

---
## 13. Adaptación Disciplinar
- Aplica las **directrices específicas** definidas en el **MÓDULO DE MATERIA**.

---
## 14. Validación Técnica
- Cuando existan **fragmentos de código, fórmulas o cálculos**:
  - Verifica que son **correctos**.
  - Verifica que producen el **resultado esperado**.
  - Verifica que son **coherentes con el documento**.

---
### 14.b Validación Ejecutable (Python)
- **Permitido**:
  - Uso de **librerías estándar de Python** (ej: `math`, `os`) **si están mencionadas en el documento**.
  - Código con **semilla fija** para aleatoriedad (ej: `random.seed(42)`).
- **Prohibido**:
  - Dependencia de **aleatoriedad sin semilla fija**.
  - Entrada de usuario (`input()`).
  - Librerías externas no estándar (ej: `numpy`, `pandas`).
  - Versiones específicas de Python no explicadas.

---
## 15. Manejo de Documentos Problemáticos
- **Si el documento contiene errores técnicos**:
  - **No generes preguntas** basadas en ellos.
  - **Corrige internamente** el error (si es posible) y documéntalo en `justificacion.confianza_documental = "Media"`.
- **Si el documento es ambiguo**:
  - **Evita preguntas** sobre los fragmentos ambiguos.
  - **Reformula** las preguntas para que la respuesta correcta sea inequívoca.
- **Si no hay suficiente contenido relevante**:
  - **Genera menos de 5 preguntas** y justifícalo en `examen_metadatos.notas`.

---
## 16. Auditoría Previa Obligatoria
Antes de entregar el examen, verifica:
1. **Una única respuesta correcta** por pregunta.
2. **Distractores plausibles y diferenciados**.
3. **Ausencia de pistas gramaticales**.
4. **Cobertura temática proporcional**.
5. **Cobertura cognitiva variada**.
6. **Ausencia de redundancias**.
7. **Ausencia de preguntas de dificultad baja**.
8. **Validez técnica** de código y cálculos.
9. **Distribución razonable de respuestas** (ninguna letra >50% aciertos).
10. **Cumplimiento de fidelidad documental**.
11. **JSON sintácticamente válido**.

---
---
# 🎯 MÓDULO DE MATERIA — [NOMBRE]
**Instrucciones**: Reemplaza este bloque con el módulo específico de la materia. Ejemplo para **Programación en Python 3**:

---
## Materia
Programación en Python 3.

---
## Prioridades
Prioriza preguntas que obliguen al alumnado a:
- Ejecutar mentalmente código.
- Predecir salidas.
- Analizar flujo de ejecución.
- Identificar errores.
- Inferir estados de variables.
- Razonar sobre estructuras de datos.

**Evita**: Preguntas puramente definicionales, salvo que el documento las haga imprescindibles.

---
## Validación Específica
Comprueba:
- Sintaxis Python 3 válida.
- Resultados correctos.
- Coherencia de tipos.
- Razonamiento paso a paso.

---
## Errores Frecuentes para Distractores
 | **Error**                     | **Ejemplo**                          |
 |-------------------------------|--------------------------------------|
 | Índices base 0 vs. base 1     | `lista[1]` vs. `lista[0]`            |
 | `range()` con límite exclusivo | `range(1, 5)` → 1, 2, 3, 4 (no 5)   |
 | Referencia vs. copia          | Modificar una lista dentro de otra   |
 | Mutabilidad                   | Listas vs. tuplas                    |
 | `/` vs. `//`                  | División entera vs. flotante         |
 | `==` vs. `=`                  | Comparación vs. asignación           |
 | Conversión de tipos           | `int("5")` vs. `int("a")`            |
 | Ámbito de variables           | `global` vs. local                   |
 | Precedencia de operadores     | `*` antes que `+`                    |

---
---
# 📤 Formato de Salida (JSON)
Entrega **exclusivamente** un bloque JSON válido.

---
## Estructura Básica
```json
{
  "examen_metadatos": {
    "num_preguntas": 5,
    "nivel_educativo": "FP ciclo superior",
    "materia": "[Materia]",
    "fuente": "Documento proporcionado",
    "distribucion_tematica": [
      {"tema": "Tema 1", "peso": 40, "num_preguntas": 2},
      {"tema": "Tema 2", "peso": 60, "num_preguntas": 3}
    ],
    "distribucion_respuestas": {
      "a": 2,
      "b": 1,
      "c": 1,
      "d": 1
    },
    "notas": "Opcional: Observaciones (ej: 'Documento con errores menores en la sección X')"
  },
  "preguntas": [
    {
      "id": 1,
      "tema": "Bucles y función range()",
      "fragmento_origen": "Sección 2.1, párrafo 3",
      "dificultad": "Media | Alta",
      "nivel_bloom": "Aplicar | Analizar | Evaluar",
      "enunciado": "Pregunta clara y directa...",
      "opciones": {
        "a": "Opción incorrecta 1",
        "b": "Opción correcta",
        "c": "Opción incorrecta 2",
        "d": "Opción incorrecta 3 (opcional)"
      },
      "respuesta_correcta": "b",
      "justificacion": {
        "confianza_documental": "Alta | Media",
        "evidencia_documental": {
          "texto": "Cita textual o referencia al fragmento relevante",
          "seccion": "Sección 2.1"
        },
        "razon_respuesta_correcta": "Explicación breve de por qué es correcta",
        "concepto_principal": "Concepto evaluado (ej: 'Límites de range()')",
        "error_comun_evaluado": "Error que cometen los alumnos (ej: 'Off-by-one en range()')",
        "analisis_distractores": {
          "a": {
            "tipo_error": "Error conceptual | procedimental | sintáctico",
            "explicacion": "Por qué es incorrecta esta opción"
          },
          "c": {
            "tipo_error": "Error conceptual",
            "explicacion": "Por qué es incorrecta esta opción"
          }
        },
        "justificacion_4_opciones": "Opcional: Solo si se usan 4 opciones. Explica por qué el cuarto distractor tiene valor discriminativo real."
      }
    }
  ]
}
```

| Campo | Obligatorio | Notas |
| --- | --- | --- |
| examen_metadatos | ✅ Sí | - |
| distribucion_tematica | ✅ Sí | - |
| distribucion_respuestas | ✅ Sí | - |
| notas | ❌ No | Solo si hay observaciones relevantes |
| justificacion_4_opciones | ❌ No | Solo si se usan 4 opciones y se justifica su valor |
| dificultad | ✅ Sí | Solo "Media" o "Alta" |
| nivel_bloom | ✅ Sí | Solo "Aplicar", "Analizar" o "Evaluar" |
