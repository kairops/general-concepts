# Repositorios: Acciones principales

Contenido:

- [Introducción](../repositories.md)
- [Conceptos básicos](repositories-basic-concepts.md)
- **Acciones principales**
- [Colaboración](repositories-collaboration.md): Branching & merging, resolución de conflictos
- [Conceptos de "git flow"](repositories-git-flow.md): master, develop, feature, release, hotfix
- [Versionado](repositories-tags.md): Tags

Explicaremos las principales acciones o comandos de `git`. Vamos a trabajar utilizando el intérprete de comandos de sistema.

Lejos de ser una guía completa, la explicación se corresponde a un uso básico de la herramienta `git` y la utilizaremos de referencia para esta documentación.

## clone

Sirve para descargar en el disco duro de nuestro PC el repositorio alojado remotamente en Github, Bitbucket o Gitlab. Esta acción se ejecuta una única vez.

`git` inicializa el repositorio y "se trae" toda la información existente en el servidor remoto: commits, ramas y tags. La copia local del repositorio (lo que nos acabamos de descargar) se queda enlazada:

- Al repositorio remoto, de tal forma que podemos subir nuestros cambios o commits mediante un `push` y descargar los nuevos cambios del repositorio remoto mediante `pull` o `fetch`.
- A la carpeta de nuestro disco duro que contiene el repositorio, desde donde podemos añadir conjuntos de cambios al repositorio con `commit`, trabajar con ramas usando `checkout`. En el momento de hacer el `clone` se crea un directorio ".git" dentro de la misma carpeta del repositorio, que contiene toda la información que `git` maneja, por ejemplo la configuración en el archivo ".git/config".

Ejemplo:

- `git clone https://github.com/pedroamador/red-panda-ci-symfony` // Se descarga el repositorio indicado en nuestro disco duro local

## add / rm

En nuestro día a día vamos añadir, modificar o borrar archivos de código fuente de la aplicación en nuestro disco duro. Tal y como hemos dicho antes, cuando descargamos el repositorio por primera vez mediante el `clone`, `git` se queda el repositorio unido a un directorio local ".git".

`git` es, de alguna forma, consciente de todas esas modificaciones. 

- Utilizando `git add` preparamos nuestros cambios. Se preparan tanto los archivos nuevos como los que hemos modificado.
- Mediante `git rm` informamos a `git` que estamos eliminando un archivo de nuestro directorio de trabajo.

En ambos casos, los cambios quedan preparados para incorporar al repositorio mediante un `commit` posterior.

Ejemplos:

- `git add file_dev1.txt` // Preparamos un fichero para añadir a nuestra copia local del repositorio
- `git add -A` // Preparamos para añadir al repositorio todos los cambios que hemos hecho

## commit

Tiene dos significados:

- Como acción o comando de `git` se utiliza para añadir un conjunto de cambios a nuestro repositorio local.
- Como entidad, referido a uno de los múltiples "conjuntos de cambios" de nuestro repositorio.

Ejemplos:

- `git commit -m "Modificaciones en la API"` // Añadimos todos los cambios que tenemos preparados a nuestra copia local identificados son el mensaje "Modificaciones en la API"
- `git log --oneline` // Vemos un listado-resumen con todos los `commits` (conjuntos de cambios) de la rama en la que estamos situados.

## push

Este comando envía todos los `commits` que hemos realizado en nuestra copia local del repositorio y que están pendientes de enviar hacia el servidor remoto.

Ejemplo:

- `git push origin master`  // Subimos o "empujamos" nuestros cambios hacia el servidor remoto.

## pull

Descarga los cambios que se han hecho en el servidor remoto a nuestra copia local. Podemos decir que "se trae las cosas nuevas".

Es posible que las modificaciones deban mezclarse (`merge`) con el código en el que estamos trabajando. 

Ejemplo:

- `git pull origin master` // Se descarga o "tira de" las novedades que tiene el servidor remoto.

## Test lab

Haremos lo siguiente:

- Descargar el repositorio desde el servidor remoto a una carpeta local de nuestro equipo
- Realizar cambios en uno de los archivos
- Confirmar esos cambios en nuestra copia local del repositorio
- Añadir un archivo nuevo al repositorio
- Confirmar de nuevo los cambios
- Subir ambos commits al servidor remoto

Nos serviremos del proyecto de Github [CI Symfony](https://github.com/sergioortegagomez/red-panda-ci-symfony). Tendremos que crear una cuenta en Github y hacer un "fork" del repositorio en nuestro espacio de usuario. Como resultado deberíamos tener algo como esto 

https://github.com/pedroamador/red-panda-ci-symfony

_NOTA: en la URL del repositorio, sustituir "pedroamador" por el identificador del usuario personal de cada cual Github_

### Descargar el repositorio

[![asciicast](https://asciinema.org/a/naljgSDPFA9NKYwTRj8s8puUl.png)](https://asciinema.org/a/naljgSDPFA9NKYwTRj8s8puUl)

En este primer paso lo que `git` ha hecho por nosotros ha sido:

- Conectar con el servidor remoto, en este caso Github
- Crear la carpeta "red-panda-ci-symfony" en nuestro disco duro
- Descargar el código fuente del proyecto y guardarlo en la carpeta recién creada
- Enlazar nuestra carpeta local con el repositorio remoto

El `clone` nos deja situados en la rama principal del repositorio, en este caso `master`. Veremos detalles acerca de ramas más adelante.

### Modificar un archivo y hacer un commit

[![asciicast](https://asciinema.org/a/WLYkACmCjiWK50URKLXwN2ICo.png)](https://asciinema.org/a/WLYkACmCjiWK50URKLXwN2ICo)

Hagamos un repaso de lo sucedido:

- Modificamos el archivo README.md
- Comprobamos `git status` y  `git diff` que efectivamente hemos hecho modificaciones
- Preparamos los cambios para añadir al repositorio con `git add ...`
- Confirmamos nuestros cambios en la copia local con `git commit ...`

### Añadir un archivo nuevo y hacer un commit

[![asciicast](https://asciinema.org/a/YztCIF7iF7KLnSX3e2NlTsX7M.png)](https://asciinema.org/a/YztCIF7iF7KLnSX3e2NlTsX7M)

En este caso:

- Creamos un archivo nuevo "new_file.txt"
- Lo preparamos para añadir al repositorio `git add new_file.txt`
- Confirmamos nuestros cambios en la copia local del repositorio con `git commit ... `

Al final podemos ver como tenemos 2 nuevos "commits" que subir al servidor remoto

### Subir cambios al servidor remoto

[![asciicast](https://asciinema.org/a/lqKgA9YPbHts7Jwa66ReF0GmN.png)](https://asciinema.org/a/lqKgA9YPbHts7Jwa66ReF0GmN)

En este último paso:

- Subimos nuestros cambios locales al servidor remoto con `git push -u origin master`
- Vemos como nuestros dos nuevos "commits" aparecen en el histórico con `git log --oneline`

---

Siguiente: [Colaboración](repositories-collaboration.md) - Volver a [Página principal](../toc.md) |
