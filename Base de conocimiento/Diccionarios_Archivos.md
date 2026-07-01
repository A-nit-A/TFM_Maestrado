# Diccionarios y Archivos en Python

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

## Tabla Hash de Diccionarios (Dict)

La estructura de tabla hash eficiente de clave/valor de Python se llama "dict" (diccionario). El contenido de un dicc se puede escribir como una serie de pares clave:valor entre llaves { }, por ejemplo, dict = {clave1:valor1, clave2:valor2, ... }. El "diccionario vacío" es simplemente un par de llaves vacías {}.

Buscar o establecer un valor en un diccionario utiliza corchetes, por ejemplo, dict['foo'] busca el valor bajo la clave 'foo'. Las cadenas, los números y las tuplas funcionan como claves, y cualquier tipo puede ser un valor. Otros tipos pueden o no funcionar correctamente como claves (las cadenas y las tuplas funcionan perfectamente ya que son inmutables). Buscar un valor que no está en el diccionario lanza un KeyError; utiliza "in" para comprobar si la clave está en el diccionario, o utiliza dict.get(key) que devuelve el valor o None si la clave no está presente (o get(key, not-found) te permite especificar qué valor devolver en el caso de no encontrarse).

```python
  ## Can build up a dict by starting with the empty dict {}
  ## and storing key/value pairs into the dict like this:
  ## dict[key] = value-for-that-key
  dict = {}
  dict['a'] = 'alpha'
  dict['g'] = 'gamma'
  dict['o'] = 'omega'

  print(dict) ## {'a': 'alpha', 'o': 'omega', 'g': 'gamma'}

  print(dict['a'])     ## Simple lookup, returns 'alpha'
  dict['a'] = 6       ## Put new key/value into dict
  'a' in dict         ## True
  ## print(dict['z'])                  ## Throws KeyError
  if 'z' in dict: print(dict['z'])     ## Avoid KeyError
  print(dict.get('z'))  ## None (instead of KeyError)
```

![dict with keys 'a' 'o' 'g'](https://developers.google.com/static/edu/python/images/dict.png)

Un bucle for en un diccionario itera sobre sus claves por defecto. Las claves aparecerán en un orden arbitrario. Los métodos dict.keys() y dict.values() devuelven listas de las claves o valores explícitamente. También existe un método items() que devuelve una lista de tuplas (clave, valor), que es la forma más eficiente de examinar todos los datos de clave y valor en el diccionario. Todas estas listas se pueden pasar a la función sorted().

```python
  ## By default, iterating over a dict iterates over its keys.
  ## Note that the keys are in a random order.
  for key in dict:
    print(key)
  ## prints a g o

  ## Exactly the same as above
  for key in dict.keys():
    print(key)

  ## Get the .keys() list:
  print(dict.keys())  ## dict_keys(['a', 'o', 'g'])

  ## Likewise, there's a .values() list of values
  print(dict.values())  ## dict_values(['alpha', 'omega', 'gamma'])

  ## Common case -- loop over the keys in sorted order,
  ## accessing each key/value
  for key in sorted(dict.keys()):
    print(key, dict[key])

  ## .items() is the dict expressed as (key, value) tuples
  print(dict.items())  ##  dict_items([('a', 'alpha'), ('o', 'omega'), ('g', 'gamma')])

  ## This loop syntax accesses the whole dict by looping
  ## over the .items() tuple list, accessing one (key, value)
  ## pair on each iteration.
  for k, v in dict.items(): print(k, '>', v)
  ## a > alpha    o > omega     g > gamma
```

Nota de estrategia: desde el punto de vista del rendimiento, el diccionario es una de tus mejores herramientas, y deberías usarlo siempre que puedas como una forma fácil de organizar datos. Por ejemplo, podrías leer un archivo de registro (log) donde cada línea comienza con una dirección IP y almacenar los datos en un diccionario utilizando la dirección IP como clave y la lista de líneas donde aparece como valor. Una vez que hayas leído todo el archivo, podrás buscar cualquier dirección IP y ver instantáneamente su lista de líneas. El diccionario toma datos dispersos y los convierte en algo coherente.

## Formateo de Diccionarios

El operador % funciona convenientemente para sustituir valores de un diccionario en una cadena por su nombre:

```python
  h = {}
  h['word'] = 'garfield'
  h['count'] = 42
  s = 'I want %(count)d copies of %(word)s' % h  # %d for int, %s for string
  # 'I want 42 copies of garfield'

  # You can also use str.format().
  s = 'I want {count:d} copies of {word}'.format(h)
```

## Del

El operador "del" realiza eliminaciones. En el caso más sencillo, puede eliminar la definición de una variable, como si esa variable no se hubiera definido. Del también se puede usar en elementos o rebanadas (slices) de listas para eliminar esa parte de la lista y para eliminar entradas de un diccionario.

```python
  var = 6
  del var  # var no more!

  list = ['a', 'b', 'c', 'd']
  del list[0]     ## Delete first element
  del list[-2:]   ## Delete last two elements
  print(list)      ## ['b']

  dict = {'a':1, 'b':2, 'c':3}
  del dict['b']   ## Delete 'b' entry
  print(dict)      ## {'a':1, 'c':3}
```

## Archivos

La función open() abre y devuelve un manejador de archivo que se puede utilizar para leer o escribir un archivo de la manera habitual. El código f = open('name', 'r') abre el archivo en la variable f, listo para operaciones de lectura, y se usa f.close() cuando se termina. En lugar de 'r', usa 'w' para escribir y 'a' para añadir (append). El bucle for estándar funciona para archivos de texto, iterando a través de las líneas del archivo (esto funciona solo para archivos de texto, no para archivos binarios). La técnica del bucle for es una forma sencilla y eficiente de ver todas las líneas de un archivo de texto:

```python
  # Echo the contents of a text file
  f = open('foo.txt', 'rt', encoding='utf-8')
  for line in f:   ## iterates over the lines of the file
    print(line, end='')    ## end='' so print does not add an end-of-line char
                           ## since 'line' already includes the end-of-line.
  f.close()
```

Leer una línea a la vez tiene la excelente cualidad de que no todo el archivo necesita caber en la memoria al mismo tiempo; es muy útil si deseas examinar cada línea de un archivo de 10 gigabytes sin utilizar 10 gigabytes de memoria. El método f.readlines() lee todo el archivo en la memoria y devuelve su contenido como una lista de sus líneas. El método f.read() lee todo el archivo en una sola cadena, lo cual puede ser una forma práctica de trabajar con todo el texto a la vez, como por ejemplo con las expresiones regulares que veremos más adelante.

Para escribir, el método f.write(string) es la forma más sencilla de escribir datos en un archivo de salida abierto. O también puedes usar "print" con un archivo abierto como "print(string, file=f)".

## Archivos Unicode

Para leer y escribir archivos codificados en unicode, utiliza un modo `'t'` y especifica explícitamente una codificación:

```python
with open('foo.txt', 'rt', encoding='utf-8') as f:
  for line in f:
    # here line is a *unicode* string

with open('write_test', encoding='utf-8', mode='wt') as f:
    f.write('\u20ACunicode\u20AC\n') #  €unicode€
    # AKA print('\u20ACunicode\u20AC', file=f)  ## which auto-adds end='\n'
```

## Ejercicio: Desarrollo incremental

Al construir un programa en Python, no lo escribas todo de una sola vez. En su lugar, identifica un primer hito, por ejemplo, "el primer paso es extraer la lista de palabras". Escribe el código para alcanzar ese hito y simplemente imprime tus estructuras de datos en ese punto; luego puedes ejecutar un sys.exit(0) para que el programa no avance hacia las partes no terminadas. Una vez que el código del hito esté funcionando, puedes trabajar en el código para el siguiente hito. Poder ver la impresión de tus variables en un estado determinado te ayuda a pensar en cómo necesitas transformar esas variables para llegar al siguiente estado. Python es muy rápido con este patrón, lo que te permite hacer un pequeño cambio y ejecutar el programa para ver cómo funciona. Aprovecha ese ciclo rápido de retroalimentación para construir tu programa en pequeños pasos.


