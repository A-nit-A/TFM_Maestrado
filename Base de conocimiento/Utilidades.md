# Utilidades en Python

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

En esta sección, analizaremos algunos de los muchos módulos de utilidad estándar de Python para resolver problemas comunes.

## Sistema de Archivos -- os, os.path, shutil

Los módulos *os* y *os.path* incluyen muchas funciones para interactuar con el sistema de archivos. El módulo *shutil* puede copiar archivos.

- [os module docs](https://docs.python.org/library/os)
- filenames = os.listdir(dir) -- lista de nombres de archivos en esa ruta de directorio (sin incluir . y ..). Los nombres de archivos son solo los nombres dentro del directorio, no sus rutas absolutas.
- os.path.join(dir, filename) -- a partir de un nombre de archivo de la lista anterior, utilízalo para unir el directorio y el nombre del archivo para formar una ruta.
- os.path.abspath(path) -- a partir de una ruta, devuelve su forma absoluta, por ejemplo, /home/nick/foo/bar.html.
- os.path.dirname(path), os.path.basename(path) -- a partir de dir/foo/bar.html, devuelve el nombre del directorio "dir/foo" y el nombre base "bar.html".
- os.path.exists(path) -- verdadero si existe.
- os.mkdir(dir_path) -- crea un directorio, os.makedirs(dir_path) crea todos los directorios necesarios en esta ruta.
- shutil.copy(source-path, dest-path) -- copia un archivo (los directorios de la ruta de destino deben existir).

```python
## Example pulls filenames from a dir, prints their relative and absolute paths
def printdir(dir):
  filenames = os.listdir(dir)
  for filename in filenames:
    print(filename)  ## foo.txt
    print(os.path.join(dir, filename)) ## dir/foo.txt (relative to current dir)
    print(os.path.abspath(os.path.join(dir, filename))) ## /home/nick/dir/foo.txt
```

Explorar un módulo funciona muy bien con las funciones integradas de Python help() y dir(). En el intérprete, haz un "import os" y luego utiliza estos comandos para ver qué está disponible en el módulo: dir(os), help(os.listdir), dir(os.path), help(os.path.dirname).

## Ejecución de Procesos Externos -- subprocess

El módulo *subprocess* es una forma sencilla de ejecutar un comando externo y capturar su salida.

- [subprocess module docs](https://docs.python.org/3/library/subprocess.html#using-the-subprocess-module)
- output = subprocess.check_output(cmd, stderr=subprocess.STDOUT) -- ejecuta el comando, espera a que finalice y devuelve su texto de salida. El comando se ejecuta con su salida estándar y error estándar combinados en un único texto de salida. Si falla, lanza un CalledProcessError.
- Si deseas más control sobre la ejecución del subproceso, consulta la [clase subprocess.popen](https://docs.python.org/3/library/subprocess.html#popen-objects)
- También existe un simple subprocess.call(cmd) que ejecuta el comando, vuelca su salida en tu salida y devuelve su código de error. Esto es útil si deseas ejecutar el comando pero no necesitas capturar su salida en tus estructuras de datos de Python.

```python
import subprocess

## Given a dir path, run an external 'ls -l' on it --
## shows how to call an external program
def listdir(dir):
  cmd = 'ls -l ' + dir
  print("Command to run:", cmd)   ## good to debug cmd before actually running it
  (status, output) = subprocess.getstatusoutput(cmd)
  if status:    ## Error case, print the command's output to stderr and exit
    sys.stderr.write(output)
    sys.exit(status)
  print(output)  ## Otherwise do something with the command's output
```

## Excepciones

Una excepción representa un error en tiempo de ejecución que detiene la ejecución normal en una línea determinada y transfiere el control al código de manejo de errores. Esta sección solo presenta los usos más básicos de las excepciones. Por ejemplo, un error en tiempo de ejecución podría ser que una variable utilizada en el programa no tenga un valor (ValueError... probablemente ya te hayas topado con este unas cuantas veces), o un error en la operación de apertura de un archivo porque este no existe (IOError). Obtén más información en el [tutorial de excepciones](https://docs.python.org/tutorial/errors) y consulta la [lista completa de excepciones](https://docs.python.org/library/exceptions).

Sin ningún código de manejo de errores (como hemos hecho hasta ahora), una excepción en tiempo de ejecución simplemente detiene el programa con un mensaje de error. Ese es un buen comportamiento por defecto y lo has visto muchas veces. Puedes añadir una estructura "try/except" a tu código para manejar las excepciones, de esta manera:

```python
  try:
    ## Either of these two lines could throw an IOError, say
    ## if the file does not exist or the read() encounters a low level error.
    f = open(filename, 'rb')
    data = f.read()
    f.close()
  except IOError:
    ## Control jumps directly to here if any of the above lines throws IOError.
    sys.stderr.write('problem reading:' + filename)
  ## In any case, the code then continues with the line after the try/except
```

La sección try: incluye el código que podría lanzar una excepción. La sección except: contiene el código a ejecutar si ocurre una excepción. Si no hay excepción, la sección except: se omite (es decir, ese código es solo para el manejo de errores, no para el caso "normal" del código). Puedes obtener un puntero al objeto de excepción en sí con la sintaxis "except IOError as e: ..." (donde e apunta al objeto de excepción).

## HTTP -- urllib y urlparse

El módulo *urllib.request* proporciona la obtención de URLs, haciendo que una URL parezca un archivo del cual se puede leer. El módulo *urlparse* sirve para desglosar y componer URLs.

- [urllib.request module docs](https://docs.python.org/3/library/urllib.request.html#module-urllib.request)
- ufile = urllib.request.urlopen(url) -- devuelve un objeto similar a un archivo para esa URL.
- text = ufile.read() -- se puede leer de él como si fuera un archivo (readlines(), etc., también funcionan).
- info = ufile.info() -- la metainformación de esa solicitud. info.gettype() es el tipo MIME, por ejemplo, 'text/html'.
- baseurl = ufile.geturl() -- obtiene la URL "base" de la solicitud, la cual puede ser diferente de la original debido a redirecciones.
- urllib.request.urlretrieve(url, filename) -- descarga los datos de la URL en la ruta de archivo especificada.
- urllib.parse.urljoin(baseurl, url) -- a partir de una URL que puede o no estar completa y de la baseurl de la página de la que proviene, devuelve una URL completa. Utiliza geturl() arriba para proporcionar la URL base.

Todas las excepciones se encuentran en urllib.error.

```python
from urllib.request import urlopen

## Given a url, try to retrieve it. If it's text/html,
## print its base url and its text.
def wget(url):
  ufile = urlopen(url)  ## get file-like object for url
  info = ufile.info()   ## meta-info about the url content
  if info.get_content_type() == 'text/html':
    print('base url:' + ufile.geturl())
    text = ufile.read()  ## read all its text
    print(text)
```

El código anterior funciona bien, pero no incluye el manejo de errores si una URL no funciona por alguna razón. Aquí tienes una versión de la función que añade lógica try/except para imprimir un mensaje de error si falla la operación de la URL.

Si `urlopen()` parece quedarse colgado, es posible que tu sistema no permita el acceso directo a algunas direcciones HTTP. Puedes verificar esto intentando obtener la misma URL usando `wget` o `curl`. Si estos programas también fallan, deberás obtener el contenido HTTP a través de un servicio proxy. La configuración del acceso proxy no está cubierta por este tutorial.

```python
## Version that uses try/except to print an error message if the
## urlopen() fails.
def wget2(url):
  try:
    ufile = urlopen(url)
    if ufile.info().get_content_type() == 'text/html':
      print(ufile.read())
  except IOError:
    print('problem reading url:', url)
```
