# youtube-dl for windows - download videos from youtube.com

- [ENGLISH](#english)
- [ESPAÑOL](#español)

# ENGLISH

# ESPAÑOL
# Instalación de Python

Cómo primer paso instalaremos Python (en lo posible la versión más reciente, de todas formas después veremos como actualizarlo), ya que usaremos el interprete de Python para poder descargar videos de youtube.

Para descargar Python:

    https://www.python.org/downloads/
    
- Ejecutar el instalador de Python e instalarlo correctamente.
- Verificar que el PATH "Python" se haya ingresado bien. Para eso usaremos el shortcut de Windows, apretando "Ctrl" + "R" y escribiendo: "SystemPropertiesAdvanced.exe". Apretamos donde dice "Variables de entorno", miramos que este correctamente ingresado el PATH, de lo contrario agregarlo. Seguido de eso, verificar que en "Variables del sistema", en la parte de "PATHEXT" esté ".EXE", de lo contrario agregarlo.

# Instalación de Youtube-dl

Para descargar Youtube-dl:

    http://ytdl-org.github.io/youtube-dl/

- Descargar youtube-dl.
- No ejecutarlo.
- Si quiere moverlo, puede hacerlo.

# Creación del Scrip

- Crearemos un bloc de notas y le cambiaremos la extensión ".txt" por ".bat"
- Editamos, en caso de tener un editor de texto de preferencia también se puede usar.

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
d:
cd "D:\LUKAS\THINGS\Canciones\"
:Reiniciar
cls
@echo.
@echo Ingresar la URL de youtube:
set c="
set /p URL=
youtube-dl -f bestaudio %c%%URL%%c%
ren *.webm *.mp3 || ren *.m4a *.mp3
@echo.
choice /c SN /n /m "Descargar otra cancion? (S,N)"
if errorlevel 2 goto Adios
goto Reiniciar

