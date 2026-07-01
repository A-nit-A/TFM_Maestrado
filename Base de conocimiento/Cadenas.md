# Cadenas en Python (Strings)

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
  
Python tiene una clase de cadena incorporada llamada "str" con muchas características útiles (hay un módulo más antiguo llamado "string" que no debes usar). Los literales de cadena pueden estar delimitados por comillas dobles o simples, aunque las comillas simples se usan más comúnmente. Las secuencias de escape con barra invertida funcionan de la manera habitual tanto dentro de literales con comillas simples como dobles, por ejemplo, \n \' \". Un literal de cadena entre comillas dobles puede contener comillas simples sin ningún problema (por ejemplo, "I didn't do it") y de igual manera una cadena entre comillas simples puede contener comillas dobles. Un literal de cadena puede abarcar varias líneas, pero debe haber una barra invertida \ al final de cada línea para escapar el salto de línea. Los literales de cadena dentro de comillas triples, """ o ''', pueden abarcar varias líneas de texto.

Las cadenas de Python son "inmutables", lo que significa que no se pueden cambiar después de crearse (las cadenas de Java también usan este estilo inmutable). Como las cadenas no se pueden modificar, construimos \*nuevas\* cadenas a medida que avanzamos para representar los valores calculados. Así, por ejemplo, la expresión ('hello' + 'there') toma las 2 cadenas 'hello' y 'there' y construye una nueva cadena 'hellothere'.

Se puede acceder a los caracteres de una cadena utilizando la sintaxis estándar \[ \], y al igual que Java y C++, Python utiliza indexación basada en cero, por lo que si s es 'hello', s\[1\] es 'e'. Si el índice está fuera de los límites de la cadena, Python genera un error. El estilo de Python (a diferencia de Perl) es detenerse si no sabe qué hacer, en lugar de inventar un valor por defecto. La útil sintaxis de "rebanado" (slice) (que se detalla a continuación) también funciona para extraer cualquier subcadena de una cadena. La función len(string) devuelve la longitud de una cadena. La sintaxis \[ \] y la función len() en realidad funcionan en cualquier tipo de secuencia (cadenas, listas, etc.). Python intenta que sus operaciones funcionen de manera consistente en diferentes tipos. Un error típico de los principiantes en Python: no utilices "len" como nombre de variable para evitar bloquear la función len(). El operador '+' puede concatenar dos cadenas. Observa en el código siguiente que las variables no se declaran previamente: simplemente asígnales un valor y continúa.

```python
  s = 'hi'
  print(s[1])          ## i
  print(len(s))        ## 2
  print(s + ' there')  ## hi there
```

A diferencia de Java, el '+' no convierte automáticamente números u otros tipos a formato de cadena. La función str() convierte valores a un formato de cadena para que puedan combinarse con otras cadenas.

```python
  pi = 3.14
  ##text = 'The value of pi is ' + pi      ## NO, does not work
  text = 'The value of pi is '  + str(pi)  ## yes
```

Para los números, los operadores estándar +, /, \* funcionan de la manera habitual. No existe el operador ++, pero funcionan +=, -=, etc. Si deseas una división entera, usa 2 barras diagonales; por ejemplo, 6 // 5 es 1.

La función "print" normalmente imprime uno o más elementos de Python seguidos de un salto de línea. Un literal de cadena "cruda" (raw string) tiene el prefijo 'r' y pasa todos los caracteres directamente sin un tratamiento especial para las barras invertidas, por lo que r'x\nx' se evalúa como la cadena de longitud 4 'x\nx'.
"print" puede recibir varios argumentos para cambiar la forma en que imprime las cosas (consulta la [definición de la función print en python.org](https://docs.python.org/3/library/functions.html#print)) como por ejemplo
establecer "end" en "" para no imprimir más un salto de línea después de terminar de imprimir todos los elementos.

```python
  raw = r'this\t\n and that'

  # this\t\n and that
  print(raw)

  multi = """It was the best of times.
  It was the worst of times."""

  # It was the best of times.
  #   It was the worst of times.
  print(multi)
```

### Métodos de cadena (String Methods)

Estos son algunos de los métodos de cadena más comunes. Un método es similar a una función, pero se ejecuta "sobre" un objeto. Si la variable s es una cadena, entonces el código s.lower() ejecuta el método lower() en ese objeto de cadena y devuelve el resultado (esta idea de un método ejecutándose sobre un objeto es una de las ideas básicas que componen la Programación Orientada a Objetos, POO). Aquí tienes algunos de los métodos de cadena más comunes:

- s.lower(), s.upper() — devuelve la versión en minúsculas o mayúsculas de la cadena.
- s.strip() — devuelve una cadena con los espacios en blanco eliminados del principio y del final.
- s.isalpha()/s.isdigit()/s.isspace()... — comprueba si todos los caracteres de la cadena pertenecen a las diversas clases de caracteres.
- s.startswith('other'), s.endswith('other') — comprueba si la cadena comienza o termina con la otra cadena especificada.
- s.find('other') — busca la otra cadena dada (no es una expresión regular) dentro de s, y devuelve el primer índice donde comienza, o -1 si no la encuentra.
- s.replace('old', 'new') — devuelve una cadena donde todas las apariciones de 'old' han sido reemplazadas por 'new'.
- s.split('delim') — devuelve una lista de subcadenas separadas por el delimitador dado. El delimitador no es una expresión regular, es solo texto. 'aaa,bbb,ccc'.split(',') -\> \['aaa', 'bbb', 'ccc'\]. Como un caso especial y conveniente, s.split() (sin argumentos) divide por todos los caracteres de espacio en blanco.
- s.join(list) — lo contrario de split(), une los elementos de la lista dada utilizando la cadena como delimitador. Por ejemplo, '---'.join(\['aaa', 'bbb', 'ccc'\]) -\> aaa---bbb---ccc

Una búsqueda en Google de "python str" debería llevarte a los [métodos de cadena oficiales en python.org](http://docs.python.org/library/stdtypes.html#string-methods), que enumera todos los métodos de str.

Python no tiene un tipo de carácter separado. En su lugar, una expresión como s\[8\] devuelve una cadena de longitud 1 que contiene el carácter. Con esa cadena de longitud 1, los operadores ==, \<=, ... funcionan todos como cabría esperar, por lo que en su mayoría no necesitas saber que Python no tiene un tipo "char" escalar independiente.

### Rebanadas de cadena (String Slices)

La sintaxis de "rebanado" (slice) es una forma muy práctica de referirse a subpartes de secuencias, normalmente cadenas y listas. La rebanada s\[start:end\] representa los elementos que comienzan en start y se extienden hasta, pero sin incluir, end. Supongamos que tenemos s = "Hello"


![the string 'hello' with letter indexes 0 1 2 3 4](https://developers.google.com/static/edu/python/images/hello.png)

- s\[1:4\] es 'ell' — caracteres que comienzan en el índice 1 y se extienden hasta, pero sin incluir, el índice 4.
- s\[1:\] es 'ello' — al omitir cualquiera de los índices, se toma por defecto el inicio o el final de la cadena.
- s\[:\] es 'Hello' — al omitir ambos, siempre obtenemos una copia de todo el elemento (esta es la forma pitónica de copiar una secuencia como una cadena o lista).
- s\[1:100\] es 'ello' — un índice que es demasiado grande se trunca a la longitud de la cadena.

Los números de índice estándar basados en cero permiten acceder fácilmente a los caracteres cercanos al inicio de la cadena. Como alternativa, Python utiliza números negativos para proporcionar un acceso sencillo a los caracteres situados al final de la cadena: s\[-1\] es el último carácter 'o', s\[-2\] es 'l' el penúlt carácter, y así sucesivamente. Los números de índice negativos cuentan hacia atrás desde el final de la cadena:

- s\[-1\] es 'o' — el último carácter (el primero desde el final).
- s\[-4\] es 'e' — el cuarto desde el final.
- s\[:-3\] es 'He' — yendo hasta, pero sin incluir, los últimos 3 caracteres.
- s\[-3:\] es 'llo' — comenzando con el tercer carácter desde el final y extendiéndose hasta el final de la cadena.

Es una bonita regla de las rebanadas que, para cualquier índice n, `s[:n] + s[n:] == s`. Esto funciona incluso si n es negativo o está fuera de los límites. O dicho de otra forma, s\[:n\] y s\[n:\] siempre dividen la cadena en dos partes, conservando todos los caracteres. Como veremos más adelante en la sección de listas, las rebanadas también funcionan con listas.

### Formateo de cadenas (String formatting)

Una cosa genial que puede hacer Python es convertir automáticamente objetos en una cadena adecuada para imprimir. Dos formas integradas de hacer esto son los literales de cadena formateados, también llamados "f-strings", e invocar a str.format().

#### Literales de cadena formateados (Formatted string literals)

A menudo verás literales de cadena formateados utilizados en situaciones como:

```python
  value = 2.791514
  print(f'approximate value = {value:.2f}')  # approximate value = 2.79

  car = {'tires':4, 'doors':2}
  print(f'car = {car}') # car = {'tires': 4, 'doors': 2}
```

Un literal de cadena formateado lleva el prefijo 'f' (al igual que el prefijo 'r' utilizado para cadenas crudas).
Cualquier texto fuera de las llaves '{}' se imprime directamente. Las expresiones contenidas en '{}' se imprimen utilizando la especificación de formato descrita en [la especificación de formato](https://docs.python.org/3/library/string.html#formatspec).
Hay muchas cosas útiles que se pueden hacer con el formateo, incluyendo el truncamiento, la conversión a notación científica y la alineación a la izquierda/derecha/centro.

Las f-strings son muy útiles cuando deseas imprimir una tabla de objetos y te gustaría que las columnas que representan diferentes atributos de los objetos estuvieran alineadas como:

```python
  address_book = [{'name':'N.X.', 'addr':'15 Jones St', 'bonus': 70},
      {'name':'J.P.', 'addr':'1005 5th St', 'bonus': 400},
      {'name':'A.A.', 'addr':'200001 Bdwy', 'bonus': 5},]

  for person in address_book:
    print(f'{person["name"]:8} || {person["addr"]:20} || {person["bonus"]:>5}')

  # N.X.     || 15 Jones St          ||    70
  # J.P.     || 1005 5th St          ||   400
  # A.A.     || 200001 Bdwy          ||     5
```

### Operador % de cadenas

Python también cuenta con una funcionalidad más antigua de tipo printf() para ensamblar una cadena. El operador % toma una cadena de formato de tipo printf a la izquierda (%d para int, %s para string, %f/%g para punto flotante), y los valores correspondientes en una tupla a la derecha (una tupla está compuesta por valores separados por comas, típicamente agrupados dentro de paréntesis):

```python
  # % operator
  text = "%d little pigs come out, or I'll %s, and I'll %s, and I'll blow your %s down." % (3, 'huff', 'puff', 'house')
```

La línea anterior es algo larga; supón que quieres dividirla en líneas distintas. No puedes simplemente dividir la línea después del '%' como harías en otros lenguajes, ya que por defecto Python trata cada línea como una sentencia separada (como aspecto positivo, por esta razón no necesitamos escribir punto y coma en cada línea). Para solucionar esto, encierra toda la expresión entre un par de paréntesis externos; de esta forma, se permite que la expresión se extienda por varias líneas. Esta técnica de escribir código en varias líneas funciona con las diversas estructuras de agrupación detalladas a continuación: ( ), \[ \], { }.

```python
  # Add parentheses to make the long line work:
  text = (
    "%d little pigs come out, or I'll %s, and I'll %s, and I'll blow your %s down."
    % (3, 'huff', 'puff', 'house'))
```

Eso está mejor, pero la línea sigue siendo un poco larga. Python te permite dividir una línea en fragmentos, que luego concatenará de forma automática. Así que, para hacer esta línea aún más corta, podemos hacer esto:

```python
  # Split the line into chunks, which are concatenated automatically by Python
  text = (
    "%d little pigs come out, "
    "or I'll %s, and I'll %s, "
    "and I'll blow your %s down."
    % (3, 'huff', 'puff', 'house'))
```

### Cadenas (Unicode frente a bytes)

Las cadenas normales de Python son unicode.

Python también admite cadenas compuestas por bytes puros (denotadas por el prefijo 'b' delante de un literal de cadena) como:

```python
> byte_string = b'A byte string'
> byte_string
  b'A byte string'
```

Una cadena unicode es un tipo de objeto diferente a una cadena de bytes, pero diversas bibliotecas, como las expresiones regulares, funcionan correctamente si se les pasa cualquiera de los dos tipos de cadena.

Para convertir una cadena normal de Python en bytes, llama al método encode() de la cadena. En la otra dirección, el método decode() de la cadena de bytes convierte bytes codificados puros en una cadena unicode:

```python
> ustring = 'A unicode \u018e string \xf1'
> b = ustring.encode('utf-8')
> b
b'A unicode \xc6\x8e string \xc3\xb1'  ## bytes of utf-8 encoding. Note the b-prefix.
> t = b.decode('utf-8')                ## Convert bytes back to a unicode string
> t == ustring                         ## It's the same as the original, yay!
True
```

En la sección de lectura de archivos, hay un ejemplo que muestra cómo abrir un archivo de texto con alguna codificación y extraer cadenas unicode.

## Sentencia If

Python no utiliza { } para encerrar bloques de código para if/bucles/funciones, etc. En su lugar, Python utiliza los dos puntos (:) y la sangría/espacio en blanco para agrupar sentencias. La prueba booleana para un if no necesita estar entre paréntesis (gran diferencia con respecto a C++/Java), y puede tener cláusulas \*elif\* y \*else\* (regla nemotécnica: la palabra "elif" tiene la misma longitud que la palabra "else").

Cualquier valor se puede utilizar como una prueba de if. Los valores "cero" cuentan todos como falsos: None, 0, cadena vacía, lista vacía, diccionario vacío. También existe un tipo booleano con dos valores: True y False (convertidos a un entero, estos son 1 y 0). Python tiene las operaciones de comparación habituales: ==, !=, \<, \<=, \>, \>=. A diferencia de Java y C, == está sobrecargado para funcionar correctamente con cadenas. Los operadores booleanos son las palabras escritas \*and\*, \*or\*, \*not\* (Python no utiliza el estilo C \&\& \|\| !). A continuación se muestra cómo podría verse el código para una aplicación de salud que ofrece recomendaciones de bebidas a lo largo del día (observa cómo cada bloque de sentencias then/else comienza con un : y las sentencias se agrupan por su sangría):

```python
  if time_hour >= 0 and time_hour <= 24:
    print('Suggesting a drink option...')
    if mood == 'sleepy' and time_hour < 10:
      print('coffee')
    elif mood == 'thirsty' or time_hour < 2:
      print('lemonade')
    else:
      print('water')
```

Descubro que omitir los ":" es mi error de sintaxis más común al escribir este tipo de código, probablemente porque es algo adicional que escribir en comparación con mis hábitos de C++/Java. Además, no pongas la prueba booleana entre paréntesis; ese es un hábito de C/Java. Si el código is corto, puedes colocar el código en la misma línea después de los ":", de esta manera (esto también se aplica a funciones, bucles, etc.), aunque algunas personas consideran que es más legible espaciar las cosas en líneas separadas.

```python
  if time_hour < 10: print('coffee')
  else: print('water')
```

## Ejercicio: string1.py

Para practicar el material de esta sección, prueba el ejercicio **string1.py** en los [Ejercicios Básicos](https://developers.google.com/edu/python/exercises/basic).