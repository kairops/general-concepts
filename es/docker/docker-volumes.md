# Docker: Volúmenes

Contenido:

- [Introducción](../docker.md)
- [Imágenes](docker-images.md)
- [Containers](docker-networks.md)
- [Redes](docker-networks.md)
- **Volúmenes**
- [Docker Compose](docker-compose.md)
- [Docker in Docker](docker-in-docker.md)

Teniendo en cuenta que los containers son _efímeros_ y desaparecen cuando finaliza su ejecución, podremos utilizar los volúmenes para que los datos de un directorio determinado de un container puedan persistir más allá del fin de ejecución del propio container.

Aplicamos los mismos comandos que con los otros elementos: "ls", "rm", "inspect" o "prune".
Vamos a crear, listar, inspeccionar y luego eliminar un volumen llamado "test"

```shell
$ docker volume ls
DRIVER              VOLUME NAME
$ docker volume create test
test
$ docker volume ls
DRIVER              VOLUME NAME
local               test
$ docker volume inspect test
[
    {
        "CreatedAt": "2018-02-27T17:34:01+01:00",
        "Driver": "local",
        "Labels": {},
        "Mountpoint": "/var/lib/docker/volumes/test/_data",
        "Name": "test",
        "Options": {},
        "Scope": "local"
    }
]
$ docker volume rm test
test
$ docker volume ls
DRIVER              VOLUME NAME
```

Tratamiento "cattle" (ganado) de volúmenes, al igual que hicimos con las redes

```shell
$ docker volume ls
DRIVER              VOLUME NAME
$ for a in 1 2 3 4 5 6 7 8 9 10; do echo "Creando volumen test_$a"; docker volume create test_$a; done
Creando volumen test_1
test_1
Creando volumen test_2
test_2
Creando volumen test_3
test_3
Creando volumen test_4
test_4
Creando volumen test_5
test_5
Creando volumen test_6
test_6
Creando volumen test_7
test_7
Creando volumen test_8
test_8
Creando volumen test_9
test_9
Creando volumen test_10
test_10
$ docker volume ls
DRIVER              VOLUME NAME
local               test_1
local               test_10
local               test_2
local               test_3
local               test_4
local               test_5
local               test_6
local               test_7
local               test_8
local               test_9
$ docker volume prune -f
Deleted Volumes:
test_5
test_6
test_7
test_9
test_1
test_3
test_4
test_2
test_8
test_10

Total reclaimed space: 0B
$ docker volume ls
DRIVER              VOLUME NAME
```

Ejemplo de persistencia de datos usando un volumen con nombre

- Creamos nuevo container "ubuntu" con un volumen con nombre montado en la carpeta /opt (opción "-v test:/opt") con ejecución interactiva (opción "-ti" junto con el "/bin/bash" al final) y creamos un fichero con contenido en /opt

```shell
$ docker volume ls
DRIVER              VOLUME NAME
$ docker run -ti --rm -v test:/opt ubuntu /bin/bash
root@3754a029ecac:/# ls /opt  
root@3754a029ecac:/# echo "test content" > /opt/testfile
root@3754a029ecac:/# ls -l /opt
total 4
-rw-r--r-- 1 root root 13 Feb 27 16:44 testfile
root@3754a029ecac:/# cat /opt/testfile 
test content
```

- Finalizams ejecución ("exit") y comprobamos que el container no existe (debido a opción "--rm") y tenemos un volumen nuevo "test"

```shell
root@3754a029ecac:/# exit
$ docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
$ docker volume ls
DRIVER              VOLUME NAME
local               test
$ docker volume inspect test
[
    {
        "CreatedAt": "2018-02-27T17:44:57+01:00",
        "Driver": "local",
        "Labels": null,
        "Mountpoint": "/var/lib/docker/volumes/test/_data",
        "Name": "test",
        "Options": {},
        "Scope": "local"
    }
]
```

- Ejecutamos un nuevo container "ubuntu" con el volumen "test" montado en /opt, mismas condiciones que el anterior. Comprobamos que el contenido existe en el nuevo container ejecutado desde la imagen "ubuntu"

```shell
$ docker run -ti --rm -v test:/opt ubuntu /bin/bash
root@4c3d264d087b:/# ls -l /opt
total 4
-rw-r--r-- 1 root root 13 Feb 27 16:44 testfile
root@4c3d264d087b:/# cat /opt/testfile 
test content
```

- Finalizamos ejecución y eliminamos volumen

```shell
root@4c3d264d087b:/# exit
$ docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
$ docker volume ls
DRIVER              VOLUME NAME
local               test
$ docker volume prune
WARNING! This will remove all volumes not used by at least one container.
Are you sure you want to continue? [y/N] y
Deleted Volumes:
test

Total reclaimed space: 13B
$ docker volume ls
DRIVER              VOLUME NAME
```

Podemos exponer una carpeta del sistema "host" en el container

- Creamos carpeta nueva y ponemos contenido en un fichero en esa carpeta

```shell
$ ls -l
total 0
$ mkdir test
$ ls -l
total 4
drwxrwxr-x 2 prodriguez prodriguez 4096 feb 27 17:59 test
$ echo "New test content" > test/testfile_1
$ cat test/testfile_1 
New test content
```

- Ejecutamos nuevo container con esa carpeta montada en "/opt" (comando "-v `pwd`/test:/opt"). Comprobamos que tiene el fichero creado en el paso anterior

```shell
$ docker run --rm -ti -v `pwd`/test:/opt ubuntu /bin/bash
root@e82278e6cd80:/# ls -l /opt/testfile_1 
-rw-rw-r-- 1 1000 1000 17 Feb 27 16:59 /opt/testfile_1
root@e82278e6cd80:/# cat /opt/testfile_1 
New test content
```

- Desde el container añadimos contenido al fichero

```shell
root@e82278e6cd80:/# echo "More content generated into the container" >> /opt/testfile_1 
root@e82278e6cd80:/# cat /opt/testfile_1 
New test content
More content generated into the container
```

- Finalizamos ejecución y comprobamos que tenemos en nuestro fichero en el "host" el contenido que hemos añadimos desde dentro del contanier

```shell
root@e82278e6cd80:/# exit
$ docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
$ cat test/testfile_1 
New test content
More content generated into the container
```

Son ejemplos simples con los que tener un poco de visión de cómo orquestar los distintos componentes: imágenes, redes, containers, volúmenes

---

Siguiente: [Docker Compose](docker-compose.md) - Ir a la [Página principal](toc.md)
