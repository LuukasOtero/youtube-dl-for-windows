[![Build Status](https://github.com/ytdl-org/youtube-dl/workflows/CI/badge.svg)](https://github.com/ytdl-org/youtube-dl/actions?query=workflow%3ACI)

# YOUTUBE-DL FOR WINDOWS - TO DOWNLOAD SONGS FROM YOUTUBE.COM

- [DESCRIPTION](#description)
- [PYTHON INSTALLATION](#python-installation)
- [FFMPEG INSTALLATION](#ffmpeg-installation)
- [YOUTUBE-DL INSTALLATION](#youtube-dl-installation)
- [SCRIPT CREATION](#script-creation)
- [FINISHED SCRIPT](#finished-script)
- [COPYRIGHT](#copyright)

# DESCRIPTION

**youtube-dl** is a command-line program for download videos from YouTube.com. It requires the Python interpreter, version 2.6, 2.7, or 3.2+, and it is not platform specific. This project is focused on Windows, but on the [Official GitHub](https://github.com/ytdl-org/youtube-dl), you will find it for Linux and macOS. It is released to the public domain, which means you can modify it, redistribute it or use it however you like.

# PYTHON INSTALLATION

As a first step we will install Python (if possible the most recent version, anyway later we will see how to update it), since we will use the Python interpreter to download videos from YouTube.

To download Python:

    https://www.python.org/downloads/
    
- Ejecutar el instalador de Python e instalarlo correctamente.
- Verificar que el PATH "Python" se haya ingresado bien. Para eso usaremos el shortcut de Windows, apretando "Ctrl" + "R" y escribiendo: "SystemPropertiesAdvanced.exe". Apretamos donde dice "Variables de entorno", miramos que este correctamente ingresado el PATH, de lo contrario agregarlo. Seguido de eso, verificar que en "Variables del sistema", en la parte de "PATHEXT" esté ".EXE", de lo contrario agregarlo.

# FFMPEG INSTALLATION

To download FFMPEG:

    https://ffmpeg.org/download.html#build-windows

- Recomiendo mover el archivo descargado al disco local "C", pueden crear una carpeta llamada "FFMPEG", por ejemplo.
- Descomprimir el ".rar" en la carpeta antes mencionada.
- *Recuerden que no deben crear la carpeta en "C:\Windows\System32".*

Una vez realizado los pasos, te quedará algo así: "C:\<nombreDeLaCarpeta>\ffmpeg\bin".

# YOUTUBE-DL INSTALLATION

To download Youtube-dl:

    http://ytdl-org.github.io/youtube-dl/

- Download "youtube-dl".
- Do not run it.
- I recommend moving it to `"C:\<folderName>\" (are 2 directories behind to "\ffmpeg\bin")`

# SCRIPT CREATION

- Create a notepad in `"C:\<folderName>\"`
- Change its extension to `".bat"`
- Right click -> edit. If you have a preferred text editor you can also use it.

Los comentarios estarán debajo de cada porción con el fin de dejar el código limpio, al final estará el mismo sin comentarios para que puedan copiarlo y pegarlo, creando las modificaciones necesarias.

    @echo off
    title Downloader songs from Youtube
    color 0A
    
- Title of the script and color of the letters (it is to taste, it can be changed).

```
    @echo.
    @echo Python and youtube-dl... Checking updates.
    @echo Press any key to continue...
    pause>nul
    cls
    "c:\python 39\python.exe" -m pip install --upgrade pip
    pip install --upgrade youtube-dl
```

- En caso de necesitar una actualización el interprete de Python, la descargará e instalará. LA RUTA PUEDE CAMBIAR, TODO DEPENDE DE DONDE INSTALASTE PYTHON, EN CASO DE TENER OTRA RUTA, CAMBIARLA.
- También revisará si la aplicación necesita actualizarse.

```
    cd "C:\<folderName>\ffmpeg\bin"
```

- Ingresaremos al directorio dónde tenemos el "ffmpeg.exe". La ruta se puede cambiar, todo depende de donde instalaron el "FFMPEG".

```
    :Reboot
    cls
    @echo.
    @echo Ingresar la URL de youtube:
    set c="
    set /p URL=
    youtube-dl -f bestaudio %c%%URL%%c% -x --audio-format mp3 -o C:\<folderName>\<folderDownloads>\%%(title)s.^%%(ext)s && cls & @echo The download was completed successfully.
    @echo.
    choice /c YN /n /m "Download another song? (Y,N)"
    if errorlevel 2 goto Bye
    goto Reboot
```

- Crear un bucle, en mi caso "Reiniciar"
- Establecer una variable la cuál no se pueda modificar para que contenga unas comillas dobles.
- Establecer una variable la cuál tenga que ponerla el usuario (va a ser la URL del video).
- Extraer del video el mejor audio disponible.
- Normalmente los 2 formatos de audios que aparecerán son: ".wbem" ó ".m4a". No importa cuál, serán convertidos a ".mp3" con el programa "FFMPEG".
- Ingresar la ruta dónde se descargaran las canciones, en mi caso es: `-o C:\<folderName>\<folderDownloads>\%%(title)s.^%%(ext)s`

# FINISHED SCRIPT

```
    @echo off
    title Descargar canciones de youtube
    color 0A
    @echo.
    @echo A continuacion se realizaran chequeos de actualizaciones de Python y de youtube-dl.
    @echo Pulsa cualquier tecla para continuar.
    pause>nul
    cls
    "c:\python 39\python.exe" -m pip install --upgrade pip
    pip install --upgrade youtube-dl
    cd "C:\<nombreDeLaCarpeta>\ffmpeg\bin"
    :Reboot
    cls
    @echo.
    @echo Ingresar la URL de youtube:
    set c="
    set /p URL=
    youtube-dl -f bestaudio %c%%URL%%c% -x --audio-format mp3 -o C:\<nameFolder>\<folderDownloads>\%%(title)s.^%%(ext)s && cls & @echo The download was completed successfully.
    @echo.
    choice /c YN /n /m "Download another song? (Y,N)"
    if errorlevel 2 goto Bye
    goto Reboot
```

Acuerdense de cambiar las rutas, como por ejemplo: `"C:\<folderName>\ffmpeg\bin"` ó `C:\<folderName>\<folderDownloads>\%%(title)s.^%%(ext)s`

# COPYRIGHT

"Youtube-dl" and "FFMPEG" is in the public domain. You will find the official pages throughout the project.

Much of the research for this README was originally written by [Daniel Bolton](https://github.com/dbbolton) and is also released into the public domain.
