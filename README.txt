Este repositorio contiene el código para generar la web estática
http://procedimientoslibres.es.

Para la generación se utiliza Pyll: https://github.com/arthurk/pyll

Pyll es un generador de webs estáticas. Usted escribe plantillas de
jinja2 o archivos en formato rst (restructured text) y pyll los
transforma en archivos html listos para ser servidos desde un servidor
web.

Instalación
===========

Es muy recomendable hacer uso de virtualenvwrapper [1] y trabajar
sobre entornos virtuales para Python:

Creamos un entorno virtual específico para pyll:

  $ mkvirtualenv --no-site-packages pyll

Instalamos pyll:

  $ pip install https://github.com/arthurk/pyll/archive/master.tar.gz

Instalamos las fuentes de procedimientoslibres.es:

  $ git clone https://github.com/jdelacueva/web-procedimientoslibres.es.git

Sitúese en el directorio de las fuentes y ejecute el comando pyll:

  $ cd web-procedimientoslibres.es
  $ pyll

Se generará el directorio _output donde encontrará el código de la web
estática. Para consultarlo, es útil ejecutar un servidor local

  $ pyll --server

Podrá acceder a la web en http://localhost:8000/

Incorporación de un nuevo procedimiento
=======================================

El trabajo para modificar la web lo hemos de hacer en los archivos
situados en el directorio web-procedimientoslibres.es/_input.

Para incorporar un nuevo procedimiento deberemos tener en cuenta las
siguientes cuestiones:

1. Modificar la portada de la web. Se trata del archivo
   _input/index.html donde deberá escribir el nombre del procedimiento
   y enlazarlo.

2. Crear un directorio con el nombre del archivo dentro del directorio
   _input/procedimientos. El nombre elegido del directorio
   corresponderá a la url de la web. Así, por ejemplo, si el
   directorio creado se denomina suspension-desahucio, la URL de
   acceso será http://example.com/procedimientos/suspension-desahucio.

   En la elección del nombre del directorio no utilice espacios,
   mayúsculas, caracteres acentuados o con diéresis ni letras tales
   como ñ, ç.

3. Utilice como guía los archivos situados en otros directorios de
   _input/procedimientos para crear los archivos de su procedimiento.
   Tenga en cuenta que cada archivo será transformado en una página
   web.

4. Las primeras líneas de cada archivo contienen metadatos. Existen
   algunos definidos, como 'template:' o 'date:' pero puede utilizar
   cualquiera que tenga por conveniente para su uso en la plantilla
   jinja2. Por ejemplo, si utiliza 'autor:fulano', en la plantilla
   utilizada puede usar el campo {{ page.autor }} que será sustituida
   por el valor 'fulano'.

5. Deberá crear una plantilla para el menú del procedimiento dentro del
   directorio _templates. Esta plantilla debe ser la utilizada en los
   metadatos de los archivos del nuevo directorio.

[1] http://pypi.python.org/pypi/virtualenvwrapper
