# Trabajo Individual

Ronal Jancoña Paicho 

GitHub: RonalSinD

## Clase 1 

### ¿Qué es GIT?
Es un Sistema de Control de  Versiones Distribuido (VCS) open source, creado poor Linus Torvalds en 2005.
nos permite guardar archivos y las versiones de estos a lo largo del tiempo de manera local, guarda el historial de cambios de un proyecto, podemos volver atras si algo falla, trabajo en equipo sin perjudicar a ningun integrante ya que cada uno tiene una copia completa del repositorio, mantener diferentes verciones de un mismo proyecto `ramas`.
![Logo de GIT](imagenes/Git_Logo.png)


### ¿Cómo nació GIT?
La creacion de GIT sucedio por varias razones de un mismo problema, porque en ese entonces BITKEEPER dejo de ser gratuito y Linus Torvalds no queria pagar por una licencia por que linux es open source, asi que decidio crear su propio sistema de control de versiones al que llamo GIT, motivado tambien por que estaba cansado de depender de heramientas propietarias que no podia controlar, termino creando una de las herramientas mas importantes para los desarrolladores en todo el mundo.

Creo GIT en 2 a 3 semanas despues...

![Creador de GIT](imagenes/linus_git.webp)


### ¿Cómo instalar GIT?
Para instalar GIT debe de ir a su pagina web [Instalar GitHub](https://git-scm.com/downloads) y seguir los pasos de instalacion de tu Sistema Operativo, Git esta disponible tanto para:

Linux:    [descarga](https://git-scm.com/install/linux)

![Linux](imagenes/linux-logo.webp)

macOS:    [descarga](https://git-scm.com/install/mac)

![macOS](imagenes/macOS-Logo.webp)

Windows:  [descarga](https://git-scm.com/install/windows).

![Windows](imagenes/windows-log.webp)

GIT es multiplataforma, funciona de igual madera en deferentes Sistemas Operativos, lo unoco que cambia es la forma de instalarlo: como tengo Debian lo explicare, en la distro de Debian se deben de ejecutar los comandos:```sudo apt update``` y ```sudo apt install git``` asi de facil, una vez instalado GIT verifica con el comando ```git --version```


### Configuraciones Básicas
Antes de comenzar a usar Git, es recomendable configurar tu nombre de usuario y correo electrónico:
```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tu_correo@gmail.com"
git config --global core.autocrlf true
```
este ultimo es importante porque sirve para manejar automaticamente los saltos de  linea entre distintos Sistemas Operativos, resuelve el problema de:

Windows usa: CRLF(Carriage Return + Line Feed)

Linux/macOS usan: LF (Line Feed)


### Archivos que todo repositorio debería tener
README.md es un archivo  de documentacion en formato Markdown(.md) esto describe tu proyecto, sirve para expllicar que hace tu proyecto, indica como instalarlo o usarlo, muestra ejemplos, documentar dependencias, comandos, estructura, da un contexto a cualquier persona que vea el repositorio.



#### README.md
Es importante porque es lo primero que se ve en la plataforma de GITHUB, permite que otros entiendad tu proyecto sin leer codigo, mejora la presentacion y profecionalismo del repositorio.

![README.md](imagenes/readme-imagen.webp)



#### .gitignore
.gitignore es un archivo que le dice a Git qué archivos o carpetas NO debe rastrear (trackear), sirve para evitar subir cosas innecesarias o sencibles como archivos temporales(`.log`,`.tmp`), dependencias(`node_modules/`), archivos del sistema(.`DS_Store`,`Thumbs.db`), configuraciones locales, claves o contraseñas.

![.gitignore](imagenes/gitignore.webp)

tanto README.md y .gitignore se usan siempre juntos, porque cumple funciones complementarias 

README.md `Explica el proyecto`

.gitignore `Mantener limpio el repositorio`



## Clase 2

### STATES Y COMMITS
Un resumen breve de estos dos conceptos seria que states(estados en Git), son las etapas por las que pasa un archivo de un Git, `Directorio de Trabajo`: La carpeta local, donde estamos trabajando, pero Git aun no lo tiene registrado, `Stage Area`: El area de espera donde todo esta lsito para guardarse, `Repositorio local`: archivo guardado en el historial del repositorio.

Commit(buenas practicas) seria un modo convencional para escribir mensajes de commit claros, estructurados y consistentes, de modo que el historial del proyecto sea facil de entender y automatizar.


![Ciclo de GIT](imagenes/Git-Life-Cycle.webp)

```Bash
Directorio de Trabajo: 
  ⮟
  Creo,modifico o elimino los ficheros
  ⮟
  Preparo los cambios que quiero grabar
  ⮟
Area Temporal Transitoria(Stage Area)
  ⮟
  Confirmo los cambios y los grabo en el repositorio
  ⮟
Repositorio Local
  ⮟
  Sincronizo los cambios con el repositorio en el servidor
  ⮟
Repositorio Remoto
```
### DIRECTORIO DE TRABAJO (MODIFICADO)
Es smplemente una carpeta comun, con la unica diferencia que Git observa tus archivos, y los cataloga en:

`Untracked`: Archivo nuevo de Git o esta en seguimiento

`Modified`: Archivo que ya existe en Git, pero fue modificado

cuando un archivo no esta en el `.gitignore` pasa automaticamente a uno de estos estados

#### git restore archivo
Borra fisicamente lo que escribieron haciendo que tu archivo vuelva asu estado de ultimo commit, asi que mucho cuidado con este comando.

#### touch .gitignore
Crea una carpeta destinada para archivos, cuando tienes este archivo no se sube al repositorio, no existira para otros, no se vera todo lo que este en el .gitigore, no se vera nada de lo que contenga en el gitignore en platafirmas como GIT HUB.

### STAGE AREA (PREPARADO)
Nos permite seleccionar archivos modificados que es incluiran en el siguiente commit(guardado) y cuales no.
para traer archivos a este estado se debe hacer 
 
 ```Bash
 git add archivo : "agrega el archivo name_archivo, lo hace uno por uno"
 git add . : "agrega todos los archivos que esten obserbados por Git"
 git restore --staged archivo : "para sacar un archivo estado stage area para 
 ```

### REPOSITORIO LOCAL (cONFIRMADO)
Es la ultima fase donde le decimos al repositorio que cree el punto de guardado para que todos los cambios que estan en staged pasen a ser parte del historial.
```bash
 git commit -m "mensaje"
 git reset --soft HEAD~1 : si quieres deshacer el ultimmo commit
```
![Flujo GIT](imagenes/animacion_git.png)