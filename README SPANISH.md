[![Build Status](https://github.com/ytdl-org/youtube-dl/workflows/CI/badge.svg)](https://github.com/ytdl-org/youtube-dl/actions?query=workflow%3ACI)

# YOUTUBE-DL PARA WINDOWS - DESCARGAR CANCIONES DE YOUTUBE.COM

- [DESCRIPCIÓN](#descripción)
- [INSTALACIÓN DE PYTHON](#instalación-de-python)
- [INSTALACIÓN DE FFMPEG](#instalación-de-ffmpeg)
- [INSTALACIÓN DE YOUTUBE-DL](#instalación-de-youtube-dl)
- [SCRIPT](#script)
- [COPYRIGHT](#copyright)

# DESCRIPCIÓN

**youtube-dl** es un programa de línea de comandos para descargar videos de YouTube.com. Requiere el intérprete de Python, versión 2.6, 2.7 o 3.2+, y no es específico de la plataforma. Este proyecto está enfocado a Windows, pero en el [GitHub oficial](https://github.com/ytdl-org/youtube-dl), encontrarán para Linux y macOS. Se libera al dominio público, lo que significa que puede modificarlo, redistribuirlo o utilizarlo como desee.

# INSTALACIÓN DE PYTHON

### Para descargar Python: *[Python](https://www.python.org/downloads/)*
    
- Instalar Python.
- Verificar que el **PATH** de "Python" se haya ingresado correctamente. Para eso usaremos un shortcut, apretando *"Win" + "R"*, luego escribir: `"SystemPropertiesAdvanced.exe"`. Apretamos el botón `"Variables de entorno"`, miramos que este correctamente ingresado el **PATH**, de lo contrario agregarlo. Luego, verificar que en *"Variables del sistema"*, en la parte de *"PATHEXT"* esté *".EXE"*, de lo contrario agregarlo.

# Instalación de FFMPEG

### Para descargar FFMPEG: *[FFMPEG](https://ffmpeg.org/download.html#build-windows)*

- Recomiendo mover el archivo descargado al disco local `"C"`, pueden crear una carpeta llamada *"FFMPEG"*, por ejemplo.
- Descomprimir el `".rar"` en la carpeta antes mencionada.
- *Recuerden que no deben crear la carpeta en "C:\Windows\System32".*

Una vez realizado los pasos, te quedará algo así: `"C:\<nombreDeLaCarpeta>\ffmpeg\bin"`

# Instalación de Youtube-dl

### Para descargar Youtube-dl: *[Youtube-dl](http://ytdl-org.github.io/youtube-dl/)*

- Descargar `"youtube-dl"`
- No ejecutarlo.
- Recomiendo moverlo a `"C:\<nombreDeLaCarpeta>\" (son 2 directorios atrás de "\ffmpeg\bin")`

# SCRIPT

Las lineas que tienen `::` estan comentadas y no tienen nigun efecto en el script.

```
@echo off
title Descargar canciones de Youtube
color 0A
::Comprobando actualizaciones de Python and Youtube-dl.
::Cambiar la ruta de Python.
"c:\python 39\python.exe" -m pip install --upgrade pip
pip install --upgrade youtube-dl
::Cambiar <nombreDeLaCarpeta>
cd "C:\<nombreDeLaCarpeta>\ffmpeg\bin"
:Reiniciar
cls
@echo.
@echo Ingresar el LINK de youtube:
set c="
set /p LINK=
::Cambiar <nombreDeLaCarpeta> y <carpetaDeDescargas>
youtube-dl -f bestaudio %c%%LINK%%c% -x --audio-format mp3 -o C:\<nombreDeLaCarpeta>\<carpetaDeDescargas>\%%(title)s.^%%(ext)s && cls & @echo La descarga se completo exitosamente.
@echo.
choice /c SN /n /m "Descargar otra cancion? (S,N)"
if errorlevel 2 goto Adios
goto Reiniciar
```

Acuerdense de cambiar las rutas, como por ejemplo: `"C:\<nombreDeLaCarpeta>\ffmpeg\bin"` ó `C:\<nombreDeLaCarpeta>\<carpetaDeDescargas>\%%(title)s.^%%(ext)s`

# COPYRIGHT

*"Youtube-dl" y "FFMPEG" es de dominio público. Encontrarán las páginas oficiales a lo largo del proyecto.*

*Gran parte de la investigación de este README originalmente fue escrito por [Daniel Bolton](https://github.com/dbbolton) y también se libera al dominio público.*
