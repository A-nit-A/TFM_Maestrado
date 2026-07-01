# Listas en Python (Lists)

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

Python tiene un excelente tipo de lista incorporado llamado "list". Los literales de lista se escriben entre corchetes \[ \]. Las listas funcionan de manera similar a las cadenas: utiliza la función len() y los corchetes \[ \] para acceder a los datos, con el primer elemento en el índice 0. (Consulta la [documentación oficial de listas de python.org](https://docs.python.org/3/library/stdtypes.html#typesseq-list)).

```python
  colors = ['red', 'blue', 'green']
  print(colors[0])    ## red
  print(colors[2])    ## green
  print(colors[0])    ## red
  print(colors[2])    ## green
  print(len(colors))  ## 3
```

![lista de cadenas 'red' 'blue' 'green'](https://developers.google.com/static/edu/python/images/list1.png)

La asignación con un = en las listas no realiza una copia. En su lugar, la asignación hace que las dos variables apunten a la misma lista en memoria.

```python
  b = colors   ## Does not copy the list
```

![tanto colors como b apuntan a la misma lista](https://developers.google.com/static/edu/python/images/list2.png)

La "lista vacía" es simplemente un par de corchetes vacíos \[ \]. El '+' sirve para añadir una lista a otra, por lo que \[1, 2\] + \[3, 4\] produce \[1, 2, 3, 4\] (esto es exactamente igual que el + con las cadenas).

## FOR e IN

Las construcciones \*for\* e \*in\* de Python son sumamente útiles, y el primer uso que veremos de ellas es con listas. La construcción \*for\* (`for var in list`) es una forma sencilla de recorrer cada elemento de una lista (u otra colección). No agregues ni elimines elementos de la lista durante la iteración.

```python
  squares = [1, 4, 9, 16]
  sum = 0
  for num in squares:
    sum += num
  print(sum)  ## 30
```

Si sabes qué tipo de elementos hay en la lista, utiliza un nombre de variable en el bucle que capture esa información, como "num", "name" o "url". Dado que el código Python no tiene otra sintaxis que recuerde los tipos, los nombres de tus variables son una herramienta fundamental para tener claro qué está ocurriendo en cada momento.
(Esto puede ser un poco confuso. A medida que te familiarices más con Python, verás referencias a las [indicaciones de tipo (type hints)](https://docs.python.org/3/library/typing.html), que te permiten añadir información de tipado a tus definiciones de funciones. Python no utiliza estas indicaciones de tipo al ejecutar tus programas. Son utilizadas por otros programas como los IDEs (entornos de desarrollo integrados) y herramientas de análisis estático como linters o comprobadores de tipos para validar si tus funciones se llaman con argumentos compatibles).

La construcción \*in\* por sí sola es una manera fácil de verificar si un elemento aparece en una lista (u otra colección) — `value in collection` comprueba si el valor está en la colección y devuelve True/False.

```python
  list = ['larry', 'curly', 'moe']
  if 'curly' in list:
    print('yay') ## yay
```

Las construcciones for/in se utilizan de forma muy común en el código de Python y funcionan con tipos de datos distintos a las listas, por lo que simplemente deberías memorizar su sintaxis. Es posible que tengas hábitos de otros lenguajes en los que comienzas a iterar manualmente sobre una colección, pero en Python deberías usar simplemente for/in.

También puedes usar for/in para trabajar sobre una cadena. La cadena actúa como una lista de sus caracteres, por lo que `for ch in s: print(ch)` imprime todos los caracteres de una cadena.

### Range

La función range(n) genera los números 0, 1, ... n-1, y range(a, b) devuelve a, a+1, ... b-1 (es decir, hasta pero sin incluir el último número). La combinación del bucle for y la función range() te permite construir un bucle for numérico tradicional:

```python
  ## print the numbers from 0 through 99
  for i in range(100):
    print(i)
```

Existe una variante llamada xrange() que evita el costo de construir la lista completa para casos sensibles al rendimiento (en Python 3, range() tendrá el comportamiento de buen rendimiento y te puedes olvidar de xrange()).

### Bucle While

Python también cuenta con el bucle while estándar, y las sentencias \*break\* y \*continue\* funcionan igual que en C++ y Java, alterando el flujo del bucle más interno. Los bucles for/in anteriores resuelven el caso común de iterar sobre cada elemento de una lista, pero el bucle while te otorga un control total sobre los números de índice. Aquí tienes un bucle while que accede a cada tercer elemento de una lista:

```python
  ## Access every 3rd element in a list
  i = 0
  while i < len(a):
    print(a[i])
    i = i + 3
```

### Métodos de lista (List Methods)

Aquí tienes algunos otros métodos de lista comunes:

- list.append(elem) — añade un único elemento al final de la lista. Error común: no devuelve la nueva lista, sino que modifica la original.
- list.insert(index, elem) — inserta el elemento en el índice dado, desplazando los elementos a la derecha.
- list.extend(list2) — añade los elementos de list2 al final de la lista. El uso de + o += en una lista es similar a usar extend().
- list.index(elem) — busca el elemento dado desde el inicio de la lista y devuelve su índice. Lanza un ValueError si el elemento no aparece (usa "in" para verificar sin generar un ValueError).
- list.remove(elem) — busca la primera aparición del elemento dado y lo elimina (lanza ValueError si no está presente).
- list.sort() — ordena la lista en el lugar (no la devuelve). (Es preferible usar la función sorted(), que se muestra más adelante).
- list.reverse() — invierte la lista en el lugar (no la devuelve).
- list.pop(index) — elimina y devuelve el elemento en el índice dado. Devuelve el elemento situado más a la derecha si se omite el índice (aproximadamente lo contrario de append()).

Ten en cuenta que estos son \*métodos\* de un objeto lista, mientras que len() es una función que toma la lista (o cadena o lo que sea) como argumento.

```python
  list = ['larry', 'curly', 'moe']
  list.append('shemp')         ## append elem at end
  list.insert(0, 'xxx')        ## insert elem at index 0
  list.extend(['yyy', 'zzz'])  ## add list of elems at end
  print(list)  ## ['xxx', 'larry', 'curly', 'moe', 'shemp', 'yyy', 'zzz']
  print(list.index('curly'))    ## 2

  list.remove('curly')         ## search and remove that element
  list.pop(1)                  ## removes and returns 'larry'
  print(list)  ## ['xxx', 'moe', 'shemp', 'yyy', 'zzz']
```

Error común: ten en cuenta que los métodos anteriores no \*devuelven\* la lista modificada, simplemente modifican la lista original.

```python
  list = [1, 2, 3]
  print(list.append(4))   ## NO, does not work, append() returns None
  ## Correct pattern:
  list.append(4)
  print(list)  ## [1, 2, 3, 4]
```

### Construcción de listas (List Build Up)

Un patrón común consiste en iniciar una lista como una lista vacía \[\], y luego utilizar append() o extend() para agregarle elementos:

```python
  list = []          ## Start as the empty list
  list.append('a')   ## Use append() to add elements
  list.append('b')
```

### Rebanadas de listas (List Slices)

Las rebanadas (slices) funcionan en las listas igual que con las cadenas, y también se pueden utilizar para cambiar subpartes de la lista.

```python
  list = ['a', 'b', 'c', 'd']
  print(list[1:-1])   ## ['b', 'c']
  list[0:2] = 'z'    ## replace ['a', 'b'] with ['z']
  print(list)         ## ['z', 'c', 'd']
```

## Ejercicio: list1.py

Para practicar el material de esta sección, prueba los problemas de **list1.py** que no utilicen ordenamiento (en los [Ejercicios Básicos](https://developers.google.com/edu/python/exercises/basic)).
