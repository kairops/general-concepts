# Docker

Contenido:

- **Introducción**
- [Imágenes](docker/docker-images.md)
- [Containers](docker/docker-containers.md)
- [Redes](docker/docker-networks.md)
- [Volúmenes](docker/docker-volumes.md)
- [Docker Compose](docker/docker-compose.md)
- [Docker in Docker](docker/docker-in-docker.md)

_Siguiendo el principio [DRY](https://es.wikipedia.org/wiki/No_te_repitas), todo el contenido de esta sección viene del repositorio [Jenkins Workshop](https://github.com/red-panda-ci/jenkins-workshop) del mismo autor_

## Introucción

Trabajaremos con 4 diferentes elementos de docker:

- Imágenes
- Containers
- Redes
- Volúmenes

Existen opciones comunes a todos los elementos:

```shell
docker ${item} ls          # Listar todos los elementos de su tipo. Opcional "-a" en containers e imágenes
docker ${item} rm          # Borrar un elemento. Opcional "-f" para forzar el borrado
docker ${item} prune       # Borrar todos los elementos de un tipo. Opcional "-f" no pide confirmación.
```

Como ${item} podemos usar:

- image
- container
- network
- volume

Tenemos sistaxis específicas para elementos concretos, por ejemplo son equivalentes:

```shell
docker ps -a              # Equivalente a "docker container ls -a"
docker images             # Equivalente a "docker image ls"
docker rmi ubuntu         # Equivalente a "docker image rm ubuntu"
```

Hay opciones que podemos usar en algunos elementos, en otros no:

```shell
docker container ps       # Equivalente a "docker container ls -a"
docker image ps           # Incorrecto, con esto tendremos un error
```

Podemos obtener ayuda de docker para cada uno de los comandos con "docker help"

```shell
docker help container     # Listado de opciones de "docker container"
docker help container ps  # Listado de opciones de "docker container ps"
```

### Recursos adicionales

- [Jenkins Workshop - Red Panda CI](https://github.com/red-panda-ci/jenkins-workshop)

---

Siguiente: [Imágenes](docker/docker-images.md) - Ir a la [Página principal](toc.md)
