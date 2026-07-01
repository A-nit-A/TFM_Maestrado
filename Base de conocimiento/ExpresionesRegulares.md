# Expresiones Regulares en Python

## Contexto Curricular
- **Etapa:** [FP]

- **Competencias Específica:** 
Reconocer la estructura de un programa.
Escribir y probar programas sencillos.
Realizar operaciones de entrada/salida.
Manipular información con tipos avanzados de datos.

- **Criterios de Avaliación:** 

CA1.1 - Identificáronse as características principais das contornas de aplicación.
CA2.1 - Definíronse os aspectos fundamentais da programación de alto nivel.
básicas, e verifica os seus resultados
CA5.2 - Aprendéronse e distinguíronse os tipos de operadores.
CA5.4 - Distinguíronse e utilizáronse os distintos tipos de datos.

## Saberes Básicos
- Sistema de Archivos
- Ejecución de Procesos Externos
- Excepciones
- urllib y urlparse

## Contenido (Base para los ítems)

Las expresiones regulares son un lenguaje potente para hacer coincidir patrones de texto. Esta página ofrece una introducción básica a las expresiones regulares propiamente dichas, suficiente para nuestros ejercicios de Python, y muestra cómo funcionan las expresiones regulares en Python. El módulo "re" de Python proporciona soporte para expresiones regulares.

En Python, una búsqueda de expresión regular normalmente se escribe como:

```python
match = re.search(pat, str)
```

El método re.search() toma un patrón de expresión regular y una cadena, y busca ese patrón dentro de la cadena. Si la búsqueda tiene éxito, search() devuelve un objeto de coincidencia (match) o None en caso contrario. Por lo tanto, la búsqueda suele ir seguida inmediatamente de una sentencia if para comprobar si la búsqueda tuvo éxito, como se muestra en el siguiente ejemplo que busca el patrón 'word:' seguido de una palabra de 3 letras (detalles a continuación):

```python
import re

str = 'an example word:cat!!'
match = re.search(r'word:\w\w\w', str)
# If-statement after search() tests if it succeeded
if match:
  print('found', match.group()) ## 'found word:cat'
else:
  print('did not find')
```

El código `match = re.search(pat, str)` almacena el resultado de la búsqueda en una variable llamada "match". Luego, la sentencia if comprueba la coincidencia: si es verdadera, la búsqueda tuvo éxito y match.group() es el texto coincidente (por ejemplo, 'word:cat'). De lo contrario, si la coincidencia es falsa (None para ser más específicos), entonces la búsqueda no tuvo éxito y no hay texto coincidente.

La 'r' al inicio de la cadena del patrón designa una cadena "cruda" (raw) de Python que transmite las barras invertidas sin modificarlas, lo cual es muy útil para las expresiones regulares (¡Java necesita urgentemente esta característica!). Recomiendo que siempre escribas las cadenas de patrón con la 'r' por simple costumbre.

## Patrones Básicos

El poder de las expresiones regulares reside en que pueden especificar patrones, no solo caracteres fijos. Aquí tienes los patrones más básicos que coinciden con caracteres individuales:

- a, X, 9, < -- los caracteres ordinarios simplemente coinciden exactamente consigo mismos. Los metacaracteres que no coinciden consigo mismos porque tienen significados especiales son: . ^ $ * + ? { [ ] \ | ( ) (detalles a continuación)
- . (un punto) -- coincide con cualquier carácter individual excepto el salto de línea '\n'
- \w -- (w minúscula) coincide con un carácter de "palabra": una letra, dígito o guion bajo [a-zA-Z0-9_]. Ten en cuenta que, aunque "palabra" (word) es la regla nemotécnica para esto, solo coincide con un único carácter de palabra, no con una palabra entera. \W (W mayúscula) coincide con cualquier carácter que no sea de palabra.
- \b -- límite (límite de palabra) entre un carácter de palabra y uno que no lo es
- \s -- (s minúscula) coincide con un único carácter de espacio en blanco: espacio, salto de línea, retorno de carro, tabulación, salto de página [ \n\r\t\f]. \S (S mayúscula) coincide con cualquier carácter que no sea un espacio en blanco.
- \t, \n, \r -- tabulación, salto de línea, retorno de carro
- \d -- dígito decimal [0-9] (algunas utilidades de expresiones regulares más antiguas no admiten \d, pero todas admiten \w y \s)
- ^ = inicio, $ = fin -- coinciden con el inicio o el final de la cadena
- \ -- inhibe el carácter "especial" de un símbolo. Por lo tanto, por ejemplo, usa \. para coincidir con un punto o \\ para coincidir con una barra diagonal. Si no estás seguro de si un carácter tiene un significado especial, como '@', puedes intentar poner una barra diagonal delante, \@. Si no es una secuencia de escape válida, como \c, tu programa de Python se detendrá con un error.

## Ejemplos Básicos

Chiste: ¿cómo llamas a un cerdo con tres ojos? ¡ceeerdo! (piiig!)

Las reglas básicas de búsqueda de expresiones regulares para un patrón dentro de una cadena son:

- La búsqueda avanza a través de la cadena de principio a fin, deteniéndose en la primera coincidencia encontrada
- Se debe hacer coincidir todo el patrón, pero no necesariamente toda la cadena
- Si `match = re.search(pat, str)` tiene éxito, match no es None y, en particular, match.group() es el texto coincidente

```python
  ## Search for pattern 'iii' in string 'piiig'.
  ## All of the pattern must match, but it may appear anywhere.
  ## On success, match.group() is matched text.
  match = re.search(r'iii', 'piiig') # found, match.group() == "iii"
  match = re.search(r'igs', 'piiig') # not found, match == None

  ## . = any char but \n
  match = re.search(r'..g', 'piiig') # found, match.group() == "iig"

  ## \d = digit char, \w = word char
  match = re.search(r'\d\d\d', 'p123g') # found, match.group() == "123"
  match = re.search(r'\w\w\w', '@@abcd!!') # found, match.group() == "abc"
```

## Repetición

Las cosas se vuelven más interesantes cuando utilizas + y * para especificar la repetición en el patrón

- + -- 1 o más ocurrencias del patrón a su izquierda, por ejemplo, 'i+' = una o más i
- * -- 0 o más ocurrencias del patrón a su izquierda
- ? -- coincide con 0 o 1 ocurrencia del patrón a su izquierda

### Más a la Izquierda y Más Grande (Leftmost & Largest)

En primer lugar, la búsqueda encuentra la coincidencia más a la izquierda para el patrón y, en segundo lugar, intenta consumir la mayor cantidad posible de la cadena; es decir, + y * van tan lejos como sea posible (se dice que + y * son "codiciosos" o "greedy").

## Ejemplos de Repetición

```python
  ## i+ = one or more i's, as many as possible.
  match = re.search(r'pi+', 'piiig') # found, match.group() == "piii"

  ## Finds the first/leftmost solution, and within it drives the +
  ## as far as possible (aka 'leftmost and largest').
  ## In this example, note that it does not get to the second set of i's.
  match = re.search(r'i+', 'piigiiii') # found, match.group() == "ii"

  ## \s* = zero or more whitespace chars
  ## Here look for 3 digits, possibly separated by whitespace.
  match = re.search(r'\d\s*\d\s*\d', 'xx1 2   3xx') # found, match.group() == "1 2   3"
  match = re.search(r'\d\s*\d\s*\d', 'xx12  3xx') # found, match.group() == "12  3"
  match = re.search(r'\d\s*\d\s*\d', 'xx123xx') # found, match.group() == "123"

  ## ^ = matches the start of string, so this fails:
  match = re.search(r'^b\w+', 'foobar') # not found, match == None
  ## but without the ^ it succeeds:
  match = re.search(r'b\w+', 'foobar') # found, match.group() == "bar"
```

## Ejemplo de Correos Electrónicos

Supongamos que deseas encontrar la dirección de correo electrónico dentro de la cadena 'xyz alice-b@google.com purple monkey'. Utilizaremos esto como un ejemplo continuo para demostrar más características de las expresiones regulares. Aquí hay un intento utilizando el patrón r'\w+@\w+':

```python
  str = 'purple alice-b@google.com monkey dishwasher'
  match = re.search(r'\w+@\w+', str)
  if match:
    print(match.group())  ## 'b@google'
```

La búsqueda no obtiene la dirección de correo electrónico completa en este caso porque \w no coincide con '-' o '.' en la dirección. Corregiremos esto utilizando las funciones de expresión regular a continuación.

### Corchetes

Los corchetes se pueden utilizar para indicar un conjunto de caracteres, por lo que [abc] coincide con 'a', 'b' o 'c'. Los códigos \w, \s, etc., también funcionan dentro de los corchetes, con la única excepción de que el punto (.) simplemente significa un punto literal. Para el problema de los correos electrónicos, los corchetes son una forma sencilla de añadir '.' y '-' al conjunto de caracteres que pueden aparecer alrededor del @ con el patrón r'[\w.-]+@[\w.-]+' para obtener la dirección de correo electrónico completa:

```python
  match = re.search(r'[\w.-]+@[\w.-]+', str)
  if match:
    print(match.group())  ## 'alice-b@google.com'
```
(Más características de los corchetes) También puedes usar un guion para indicar un rango, por lo que [a-z] coincide con todas las letras minúsculas. Para usar un guion sin indicar un rango, coloca el guion al final, por ejemplo, [abc-]. Un acento circunflejo (^) al principio de un conjunto entre corchetes lo invierte, por lo que [^ab] significa cualquier carácter excepto 'a' o 'b'.

## Extracción de Grupos

La función de "grupo" de una expresión regular te permite extraer partes del texto coincidente. Supongamos que para el problema de los correos electrónicos queremos extraer el nombre de usuario y el host por separado. Para hacer esto, añade paréntesis ( ) alrededor del nombre de usuario y del host en el patrón, así: r'([\w.-]+)@([\w.-]+)'. En este caso, los paréntesis no cambian lo que el patrón coincidirá, sino que establecen "grupos" lógicos dentro del texto coincidente. En una búsqueda exitosa, match.group(1) es el texto coincidente correspondiente al primer paréntesis izquierdo, y match.group(2) es el texto correspondiente al segundo paréntesis izquierdo. El match.group() simple sigue siendo todo el texto coincidente como de costumbre.

```python
  str = 'purple alice-b@google.com monkey dishwasher'
  match = re.search(r'([\w.-]+)@([\w.-]+)', str)
  if match:
    print(match.group())   ## 'alice-b@google.com' (the whole match)
    print(match.group(1))  ## 'alice-b' (the username, group 1)
    print(match.group(2))  ## 'google.com' (the host, group 2)
```

Un flujo de trabajo común con expresiones regulares consiste en escribir un patrón para lo que estás buscando, añadiendo grupos de paréntesis para extraer las partes que deseas.

## findall

findall() es probablemente la función más potente del módulo re. Anteriormente utilizamos re.search() para encontrar la primera coincidencia de un patrón. findall() encuentra *todas* las coincidencias y las devuelve como una lista de cadenas, representando cada cadena una coincidencia.

```python
  ## Suppose we have a text with many email addresses
  str = 'purple alice@google.com, blah monkey bob@abc.com blah dishwasher'

  ## Here re.findall() returns a list of all the found email strings
  emails = re.findall(r'[\w\.-]+@[\w\.-]+', str) ## ['alice@google.com', 'bob@abc.com']
  for email in emails:
    # do something with each found email string
    print(email)
```

## findall con Archivos

Para los archivos, es posible que tengas la costumbre de escribir un bucle para iterar sobre las líneas del archivo, y luego llamar a findall() en cada línea. En su lugar, ¡deja que findall() haga la iteración por ti, lo cual es mucho mejor! Simplemente proporciona todo el texto del archivo a findall() y deja que devuelva una lista de todas las coincidencias en un solo paso (recuerda que f.read() devuelve todo el texto de un archivo en una sola cadena):

```python
  # Open file
  f = open('test.txt', encoding='utf-8')
  # Feed the file text into findall(); it returns a list of all the found strings
  strings = re.findall(r'some pattern', f.read())
```

## findall y Grupos

El mecanismo de grupo de paréntesis ( ) se puede combinar con findall(). Si el patrón incluye 2 o más grupos de paréntesis, entonces en lugar de devolver una lista de cadenas, findall() devuelve una lista de *tuplas*. Cada tupla representa una coincidencia del patrón, y dentro de la tupla se encuentran los datos de group(1), group(2), etc. Por lo tanto, si se añaden 2 grupos de paréntesis al patrón de correo electrónico, findall() devuelve una lista de tuplas, cada una de longitud 2 que contiene el nombre de usuario y el host, por ejemplo, ('alice', 'google.com').

```python
  str = 'purple alice@google.com, blah monkey bob@abc.com blah dishwasher'
  tuples = re.findall(r'([\w\.-]+)@([\w\.-]+)', str)
  print(tuples)  ## [('alice', 'google.com'), ('bob', 'abc.com')]
  for tuple in tuples:
    print(tuple[0])  ## username
    print(tuple[1])  ## host
```

Una vez que tengas la lista de tuplas, puedes recorrerla en un bucle para realizar algún cálculo para cada tupla. Si el patrón no incluye paréntesis, findall() devuelve una lista de cadenas encontradas como en los ejemplos anteriores. Si el patrón incluye un único conjunto de paréntesis, findall() devuelve una lista de cadenas correspondientes a ese único grupo. (Característica opcional poco conocida: a veces tienes agrupaciones de paréntesis ( ) en el patrón, pero que no deseas extraer. En ese caso, escribe los paréntesis con un ?: al principio, por ejemplo (?: ) y ese paréntesis izquierdo no contará como resultado de grupo).

## Flujo de Trabajo y Depuración de Expresiones Regulares

Los patrones de expresiones regulares concentran mucho significado en solo unos pocos caracteres, pero al ser tan densos, puedes pasar mucho tiempo depurando tus patrones. Configura tu entorno de ejecución de manera que puedas probar un patrón e imprimir lo que coincide fácilmente, por ejemplo, ejecutándolo en un pequeño texto de prueba e imprimiendo el resultado de findall(). Si el patrón no coincide con nada, intenta debilitar el patrón eliminando partes del mismo de modo que obtengas demasiadas coincidencias. Cuando no coincide con nada, no puedes avanzar ya que no hay nada concreto que examinar. Una vez que coincida con demasiadas cosas, puedes trabajar para ajustarlo de forma incremental hasta lograr exactamente lo que deseas.

## Opciones

Las funciones de re toman opciones para modificar el comportamiento de la coincidencia del patrón. La bandera de opción se añade como un argumento adicional a search() o findall(), etc., por ejemplo, re.search(pat, str, re.IGNORECASE).

- IGNORECASE -- ignora las diferencias entre mayúsculas y minúsculas para la coincidencia, por lo que 'a' coincide tanto con 'a' como con 'A'.
- DOTALL -- permite que el punto (.) coincida con el salto de línea (normalmente coincide con cualquier cosa excepto con el salto de línea). Esto puede confundirte: crees que .* coincide con todo, pero por defecto no va más allá del final de una línea. Ten en cuenta que \s (espacio en blanco) incluye los saltos de línea, por lo que si deseas coincidir con una secuencia de espacios en blanco que pueda incluir un salto de línea, simplemente puedes usar \s*
- MULTILINE -- dentro de una cadena compuesta por muchas líneas, permite que ^ y $ coincidan con el inicio y el final de cada línea. Normalmente, ^/$ solo coincidirían con el inicio y el final de toda la cadena.

## Codicioso vs. No Codicioso (Greedy vs. Non-Greedy) (opcional)

Esta es una sección opcional que muestra una técnica de expresiones regulares más avanzada que no es necesaria para los ejercicios.

Supongamos que tienes un texto con etiquetas: <b>foo</b> e <i>y así sucesivamente</i>

Supongamos que estás intentando coincidir con cada etiqueta con el patrón '(<.*>)' -- ¿con qué coincide primero?

El resultado es un poco sorprendente, pero el aspecto codicioso de .* hace que coincida con todo el texto '<b>foo</b> e <i>y así sucesivamente</i>' como una sola coincidencia grande. El problema es que .* va tan lejos como puede, en lugar de detenerse en el primer > (es decir, es "codicioso").

Existe una extensión para las expresiones regulares en la que se añade un ? al final, como .*? o .+?, cambiándolos a no codiciosos. Ahora se detienen tan pronto como pueden. Así, el patrón '(<.*?>)' obtendrá solo '<b>' como la primera coincidencia, y '</b>' como la segunda coincidencia, y así sucesivamente obteniendo cada par <..> a su vez. El estilo suele ser usar un .*? seguido inmediatamente por algún marcador concreto (> en este caso) al cual la secuencia .*? se ve obligada a extenderse.

La extensión *? se originó en Perl, y las expresiones regulares que incluyen las extensiones de Perl se conocen como Expresiones Regulares Compatibles con Perl (PCRE). Python incluye compatibilidad con PCRE. Muchas utilidades de línea de comandos, etc., tienen una opción donde aceptan patrones PCRE.

Una técnica más antigua pero ampliamente utilizada para codificar esta idea de "todos estos caracteres excepto detenerse en X" utiliza el estilo de corchetes. Para lo anterior, podrías escribir el patrón, pero en lugar de .* para obtener todos los caracteres, usa [^>]* que se salta todos los caracteres que no son > (el ^ inicial "invierte" el conjunto de corchetes, por lo que coincide con cualquier carácter que no esté en los corchetes).

## Sustitución (opcional)

La función re.sub(pat, replacement, str) busca todas las instancias del patrón en la cadena dada y las reemplaza. La cadena de reemplazo puede incluir '\1', '\2' que se refieren al texto del group(1), group(2), etc., del texto coincidente original.

Aquí hay un ejemplo que busca todas las direcciones de correo electrónico y las cambia para mantener el usuario (\1) pero tener yo-yo-dyne.com como host.

```python
  str = 'purple alice@google.com, blah monkey bob@abc.com blah dishwasher'
  ## re.sub(pat, replacement, str) -- returns new string with all replacements,
  ## \1 is group(1), \2 group(2) in the replacement
  print(re.sub(r'([\w\.-]+)@([\w\.-]+)', r'\1@yo-yo-dyne.com', str))
  ## purple alice@yo-yo-dyne.com, blah monkey bob@yo-yo-dyne.com blah dishwasher
```