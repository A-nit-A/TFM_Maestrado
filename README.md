# TFM_Maestrado
Biblioteca de información con documentos relaccionados con mi TFM del Maestrado Universitario en Profesorado de la Universidade de Vigo

## Base de conocimiento
Aquí se encuentran lo ficheros que se usaron como referencia para la Generación Automática de Ítems que se emplearon como preguntas a evaluar por parte de los docentes en la encuesta de validación del prompt final.
  
Tambén añadimos la programación looifp de la materia Contornas e sintaxe en Python.

## Prompts
En este directorio se encuentran los prompts más relevantes usados para el TFM.

### Chats

**Qwen_EvaluaciónPromptParaTest.md**
Chat con Qwen 3.7 para el ajuste del Prompt para generar items para la encuesta.
Qwen ajusta el Prompt a su gusto para luego poder usarlo a la hora de generar los items que formaron parte de la encuesta al profesorado.

**Dice.md**
Chat para la creación de la aplicación DICE. Esta aplicación crea un fichero Moodle XML que se importa directamente en Moodle (Aula Virtual) a partir del fichero JSON creado con el prompt de Generación Automática de Ítems.

**Excel.md**
Chat para usar comandos de Excel a la hora de organizar las tablas de datos de la encuesta para la creación de las gráficas.

**ProfesoradoEnseñarAprenderAlumnado.md**
Chat para generar un grafico en el que se explica como con el uso de la información guardada como vectores la IA puede relacionar conceptos como: profesorado y  alumnado.

### Encuesta
A partir de **Prompt_Python_Base_5_preguntas.md** que es el prompt final para la generación automática de 5 preguntas sobre la materia Python3 se crean otro 5 prompts uno por cada modelo de IA usado para la encuesta de valoración de la calidad de los ítems.

- **Prompt_Python_ChatGP_5_preguntas.md** ChatGPT 5.5
- **Prompt_Python_Claude_5_preguntas.md** Claude 4.6 Opus
- **Prompt_Python_Gemini_5_preguntas.md** Gemini 3.1 Pro
- **Prompt_Python_Mistral_5_preguntas.md** Mistral 3.5 Medium
- **Prompt_Python_Qwen_5_preguntas.md** Qwen 3.7

### Prompts AIG
Se presenta la evolución del prompt usado para la Generación Automática de Ítems desde el fichero **Prompt#1.md** al **Prompt#8.md**. Este último se convirtió en 2 partes: **Prompt_Kernel.md** y Prompt_Materia_XXXXXXXX.md. El objetivo de esta partición es la de poder generar un prompt específico para cada materia manteniendo el núcleo del prompt final intacto y sin que crezca de forma indefinida al crear nuevas materias. Como ejemplo tenemos en este directorio los prompts: **Prompt_Materia_Matematicas.md** y **Prompt_Materia_Python_3.md**
   
También hay una guía para crear materias nuevas: **GuiaCrearMateria.md**.
