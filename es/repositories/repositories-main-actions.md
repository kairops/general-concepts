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
MacBook-Pro-de-Pedro-2:testlab pedro.rodriguez$ git clone https://github.com/pedroamador/red-panda-ci-symfony
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

Emularemos el comportamiento de un equipo de desarrollo formado por dos personas. Cada miembro de nuestro equipo:

- Descargará el repositorio desde el servidor central a una carpeta de equipo local
- Hará un cambio en un archivoº
- Subirá sus cambios al repositorio

Nos valdremos del proyecto de Github [CI Symfony](https://github.com/sergioortegagomez/red-panda-ci-symfony). Tendremos que crear un usuario en Github y hacer un "fork" del repositorio en nuestro espacio de usuario. El resultado tendría que parecerse a esto 

https://github.com/pedroamador/red-panda-ci-symfony

## Descarga del repositorio

*Desarrollador 1*

```console
MacBook-Pro-de-Pedro-2:~ pedro.rodriguez$ mkdir -p testlab/dev1
MacBook-Pro-de-Pedro-2:~ pedro.rodriguez$ cd testlab/dev1/
MacBook-Pro-de-Pedro-2:dev1 pedro.rodriguez$ git clone https://github.com/pedroamador/red-panda-ci-symfony
Cloning into 'red-panda-ci-symfony'...
remote: Counting objects: 225, done.
remote: Total 225 (delta 0), reused 0 (delta 0), pack-reused 225
Receiving objects: 100% (225/225), 47.71 KiB | 372.00 KiB/s, done.
Resolving deltas: 100% (70/70), done.
```

*Desarrollador 2*

```console
MacBook-Pro-de-Pedro-2:~ pedro.rodriguez$ mkdir -p testlab/dev2
MacBook-Pro-de-Pedro-2:~ pedro.rodriguez$ cd testlab/dev2/
MacBook-Pro-de-Pedro-2:dev2 pedro.rodriguez$ git clone https://github.com/pedroamador/red-panda-ci-symfony
Cloning into 'red-panda-ci-symfony'...
remote: Counting objects: 225, done.
remote: Total 225 (delta 0), reused 0 (delta 0), pack-reused 225
Receiving objects: 100% (225/225), 47.71 KiB | 372.00 KiB/s, done.
Resolving deltas: 100% (70/70), done.
```

_NOTA: en la URL del repositorio, sustituir "pedroamador" por el identificador de usuario personal de Github_

En este primer paso lo que `git` ha hecho por nosotros ha sido:

- Conectar con el servidor central, en este caso Github
- Crear la carpeta "red-panda-ci-symfony" en nuestro disco duro
- Descargar el código fuente del proyecto y guardarlo en la carpeta recién creada
- Enlazar nuestra carpeta local con el repositorio remoto

## Realizar cambios en archivos locales

*Desarrollador 1*

```console
MacBook-Pro-de-Pedro-2:~ pedro.rodriguez$ cd ~/testlab/dev1
MacBook-Pro-de-Pedro-2:red-panda-ci-symfony pedro.rodriguez$ cat README.md 
# red-panda-ci-symfony
MacBook-Pro-de-Pedro-2:red-panda-ci-symfony pedro.rodriguez$ echo -e "\nCambios hechos por el usuario 1\n===============================" >> README.md 
MacBook-Pro-de-Pedro-2:red-panda-ci-symfony pedro.rodriguez$ git diff
diff --git a/README.md b/README.md
index 3c81f03..377e356 100644
--- a/README.md
+++ b/README.md
@@ -1 +1,4 @@
 # red-panda-ci-symfony
+
+Cambios hechos por el usuario 1
+===============================
MacBook-Pro-de-Pedro-2:red-panda-ci-symfony pedro.rodriguez$ git add README.md
MacBook-Pro-de-Pedro-2:red-panda-ci-symfony pedro.rodriguez$ git status
On branch master
Your branch is up to date with 'origin/master'.

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	modified:   README.md

MacBook-Pro-de-Pedro-2:red-panda-ci-symfony pedro.rodriguez$ git commit -m "Mis cambios"
[master 6f608d1] Mis cambios
 1 file changed, 3 insertions(+)
MacBook-Pro-de-Pedro-2:red-panda-ci-symfony pedro.rodriguez$ git push
Counting objects: 3, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 984 bytes | 984.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/pedroamador/red-panda-ci-symfony
   f82069f..6f608d1  master -> master
```

Hagamos un repaso de lo sucedido:

- Hemos modificado el archivo README.md
- Hemos comprobado con `git diff` que efectivamente hicimos modificaciones
- Hemos confirmado nuestros cambios en la copia local con `git commit ... `
- Hemos subido los cambios al servidor remoto con `git push`

*Desarrollador 2*

TBD