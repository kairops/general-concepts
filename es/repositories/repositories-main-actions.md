# Repositorios: Acciones principales

- Explicaremos las principales acciones o comandos de `git`. Vamos a trabajar utilizando línea de comandos de sistema.
- Lejos de ser una guía completa, la explicación se corresponde a un uso básico de la herramienta `git` y la utilizaremos de referencia para esta documentación.

## clone

Sirve para descargar en el disco duro de nuestro PC el repositorio alojado remotamente en Github, Bitbucket o Gitlab. Esta acción se ejecuta una única vez.

`git` inicializa el repositorio y "se trae" toda la información desde el servidor remoto: commits, ramas y tags. La copia local del repositorio (lo que nos acabamos de descargar) se queda enlazada:

- Al repositorio remoto, de tal forma que podemos subir nuestros cambios o commits mediante un `push` y descargar los cambios nuevos de repositorio remoto mediante `pull` o `fetch`.
- A una carpeta de nuestro disco duro, donde podemos añadir conjuntos de cambios al repositorio con `commit`, trabajar con ramas con `checkout`. Se creará un directorio ".git" dentro de la carpeta donde se descargó el repositorio, que contiene toda la información que `git` maneja acerca del repositorio, pof ejemplo la configuración en el archivo ".git/config".

Ejemplo: 

```console
MacBook-Pro-de-Pedro-2:testlab pedro.rodriguez$ git clone https://github.com/red-panda-ci/red-panda-ci-symfony
Cloning into 'red-panda-ci-symfony'...
remote: Counting objects: 220, done.
remote: Compressing objects: 100% (8/8), done.
remote: Total 220 (delta 2), reused 5 (delta 1), pack-reused 211
Receiving objects: 100% (220/220), 43.77 KiB | 244.00 KiB/s, done.
Resolving deltas: 100% (75/75), done.
MacBook-Pro-de-Pedro-2:testlab pedro.rodriguez$ ls -l
total 0
drwxr-xr-x  17 pedro.rodriguez  staff  544 Sep 19 07:20 red-panda-ci-symfony
MacBook-Pro-de-Pedro-2:testlab pedro.rodriguez$ cd red-panda-ci-symfony/
MacBook-Pro-de-Pedro-2:red-panda-ci-symfony pedro.rodriguez$ git status 
On branch master
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean
MacBook-Pro-de-Pedro-2:red-panda-ci-symfony pedro.rodriguez$ cat .git/config 
[core]
	repositoryformatversion = 0
	filemode = true
	bare = false
	logallrefupdates = true
	ignorecase = true
	precomposeunicode = true
[remote "origin"]
	url = https://github.com/red-panda-ci/red-panda-ci-symfony
	fetch = +refs/heads/*:refs/remotes/origin/*
[branch "master"]
	remote = origin
	merge = refs/heads/master
```

El `clone` nos deja situados en la rama principal del repositorio, en este caso `master`. Veremos detalles acerca de ramas más adelante.

## add / rm

En nuestro día a día vamos a modificar, añadir o borrar archivos de código fuente de nuestro repositorio. Tal y como hemos dicho antes, cuando descargamos el repositorio por primera vez mediante el `clone`, `git` deja el repositorio unido a un directorio local ".git".

`git` es consciente de todas esas modificaciones. 

- Utilizando `git add` preparamos nuestros cambios.
- Mediante `git rm` informamos a `git` que estamos eliminando un archivo de nuestro directorio de trabajo.

En ambos casos, los cambios quedan preparados para incorporar al repositorio mediante un `commit` posterior.

## commit

Tiene dos significados:

- Referido a la acción o comando de `git` que añade un conjunto de cambios a nuestro repositorio local.
- Referido al propio "conjunto de cambios" de nuestro repositorio.

Ejemplo:

`git commit -m "Modificaciones en la API"` // Añadimos todos los cambios que tenemos preparados a nuestra copia local identificados son el mensaje "Modificaciones en la API"

## push

Este comando envía todos los `commits` (conjuntos de cambios) que hemos realizado en nuestra copia local hacia el servidor remoto.

Ejemplo:

`git push origin master` 

Se trata de la mejor forma de asegurar que nuestras modificaciones al proyecto están a buen recaudo.

## pull

Descarga los cambios que se han hecho en el servidor remoto a nuestra copia local. Podemos decir que "se trae las cosas nuevas".

Es posible que las modificaciones deban mezclarse (`merge`) con el código en el que estamos trabajando. 

Ejemplo:

`git pull origin master`

## Test lab

TBD