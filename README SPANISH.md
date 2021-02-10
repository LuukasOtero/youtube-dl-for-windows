[![Build Status](https://github.com/ytdl-org/youtube-dl/workflows/CI/badge.svg)](https://github.com/ytdl-org/youtube-dl/actions?query=workflow%3ACI)

# YOUTUBE-DL PARA WINDOWS - DESCARGAR CANCIONES DE YOUTUBE.COM

- [DESCRIPCIÓN](#descripción)
- [INSTALACIÓN DE PYTHON](#instalación-de-python)
- [INSTALACIÓN DE FFMPEG](#instalación-de-ffmpeg)
- [INSTALACIÓN DE YOUTUBE-DL](#instalación-de-youtube-dl)
- [CREACIÓN DEL SCRIPT](#creación-del-script)
- [SCRIPT TERMINADO](#script-terminado)
- [COPYRIGHT](#copyright)

# DESCRIPCIÓN

**youtube-dl** es un programa de línea de comandos para descargar videos de YouTube.com. Requiere el intérprete de Python, versión 2.6, 2.7 o 3.2+, y no es específico de la plataforma. Este proyecto está enfocado a Windows, pero en el [GitHub oficial](https://github.com/ytdl-org/youtube-dl), encontrarán para Linux y macOS. Se libera al dominio público, lo que significa que puede modificarlo, redistribuirlo o utilizarlo como desee.

# INSTALACIÓN DE PYTHON

Cómo primer paso instalaremos Python (en lo posible la versión más reciente, de todas formas después veremos como actualizarlo), ya que usaremos el interprete de Python para poder descargar videos de youtube.

Para descargar Python:

    https://www.python.org/downloads/
    
- Instalar Python.
- Verificar que el **PATH** de "Python" se haya ingresado correctamente. Para eso usaremos un shortcut, apretando *"Tecla windows" + "R"*, luego escribir: `"SystemPropertiesAdvanced.exe"`. Apretamos el botón `"Variables de entorno"`, miramos que este correctamente ingresado el **PATH**, de lo contrario agregarlo. Luego, verificar que en *"Variables del sistema"*, en la parte de *"PATHEXT"* esté *".EXE"*, de lo contrario agregarlo.

# Instalación de FFMPEG

Para descargar FFMPEG:

    https://ffmpeg.org/download.html#build-windows

- Recomiendo mover el archivo descargado al disco local `"C"`, pueden crear una carpeta llamada *"FFMPEG"*, por ejemplo.
- Descomprimir el `".rar"` en la carpeta antes mencionada.
- *Recuerden que no deben crear la carpeta en "C:\Windows\System32".*

Una vez realizado los pasos, te quedará algo así: `"C:\<nombreDeLaCarpeta>\ffmpeg\bin"`

# Instalación de Youtube-dl

Para descargar Youtube-dl:

    http://ytdl-org.github.io/youtube-dl/

- Descargar `"youtube-dl"`
- No ejecutarlo.
- Recomiendo moverlo a `"C:\<nombreDeLaCarpeta>\" (son 2 directorios atrás de "\ffmpeg\bin")`

# Creación del Script

- Crear un bloc de notas en `"C:\<nombreDeLaCarpeta>\"`
- Cambiamos su extensión por `".bat"`
- *Click derecho -> editar*. En caso de tener un editor de texto de preferencia también se puede usar.

Los comentarios estarán debajo de cada porción con el fin de dejar el código limpio. Al final, estará el mismo sin comentarios para que puedan copiarlo y pegarlo, creando las modificaciones necesarias.

    @echo off
    title Descargar canciones de Youtube
    color 0A
    
- Título del script y color de las letras (es a gusto, se puede cambiar).

```
    @echo.
    @echo Comprobando actualizaciones de Python y de youtube-dl.
    @echo Pulsa cualquier tecla para continuar...
    pause>nul
    cls
    "c:\python 39\python.exe" -m pip install --upgrade pip
    pip install --upgrade youtube-dl
```

- En caso de necesitar una actualización el interprete de Python, la descargará e instalará. LA RUTA PUEDE CAMBIAR, TODO DEPENDE DE DONDE INSTALASTE PYTHON, EN CASO DE TENER OTRA RUTA, CAMBIARLA.
- También revisará si la aplicación necesita actualizarse.

```
    cd "C:\<nombreDeLaCarpeta>\ffmpeg\bin"
```

- Ingresaremos al directorio dónde tenemos el `"ffmpeg.exe"`. La ruta se puede cambiar, todo depende de donde instalaron el *"FFMPEG"*.

```
    :Reiniciar
    cls
    @echo.
    @echo Ingresar la URL de youtube:
    set c="
    set /p URL=
    youtube-dl -f bestaudio %c%%URL%%c% -x --audio-format mp3 -o C:\<nombreDeLaCarpeta>\<carpetaDeDescargas>\%%(title)s.^%%(ext)s && cls & @echo La descarga se completo exitosamente.
    @echo.
    choice /c SN /n /m "Descargar otra cancion? (S,N)"
    if errorlevel 2 goto Adios
    goto Reiniciar
```

- Crear un bucle, en mi caso `"Reiniciar"`
- Establecer una variable la cuál no se pueda modificar para que contenga unas comillas dobles.
- Establecer una variable la cuál tenga que poner el usuario (URL del video).
- Extraer del video el mejor audio disponible.
- Normalmente los 2 formatos de audios que aparecerán son: `".wbem"` ó `".m4a"`. No importa cuál, serán convertidos a `".mp3"` con el programa *"FFMPEG"*.
- Ingresar la ruta dónde se descargaran las canciones, en mi caso es: `-o C:\<nombreDeLaCarpeta>\<carpetaDeDescargas>\%%(title)s.^%%(ext)s`

# SCRIPT TERMINADO

```
    @echo off
    title Descargar canciones de Youtube
    color 0A
    @echo.
    @echo Comprobando actualizaciones de Python y de youtube-dl.
    @echo Pulsa cualquier tecla para continuar...
    pause>nul
    cls
    "c:\python 39\python.exe" -m pip install --upgrade pip
    pip install --upgrade youtube-dl
    cd "C:\<nombreDeLaCarpeta>\ffmpeg\bin"
    :Reiniciar
    cls
    @echo.
    @echo Ingresar la URL de youtube:
    set c="
    set /p URL=
    youtube-dl -f bestaudio %c%%URL%%c% -x --audio-format mp3 -o C:\<nombreDeLaCarpeta>\<carpetaDeDescargas>\%%(title)s.^%%(ext)s && cls & @echo La descarga se completo exitosamente.
    @echo.
    choice /c SN /n /m "Descargar otra cancion? (S,N)"
    if errorlevel 2 goto Adios
    goto Reiniciar
```

Acuerdense de cambiar las rutas, como por ejemplo: `"C:\<nombreDeLaCarpeta>\ffmpeg\bin"` ó `C:\<nombreDeLaCarpeta>\<carpetaDeDescargas>\%%(title)s.^%%(ext)s`

# COPYRIGHT

*"Youtube-dl" y "FFMPEG" es de dominio público. Encontrarán las páginas oficiales a lo largo del proyecto.*

*Gran parte de la investigación de este README originalmente fue escrito por [Daniel Bolton](https://github.com/dbbolton) y también se libera al dominio público.*
