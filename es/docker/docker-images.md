# Docker: Imágenes

Contenido:

- [Introducción](../docker.md)
- **Imágenes**
- [Containers](docker-containers.md)
- [Redes](docker-networks.md)
- [Volúmenes](docker-volumes.md)
- [Docker Compose](docker-compose.md)
- [Docker in Docker](docker-in-docker.md)

Podemos considerarlo como plantillas que tomaremos de base para ejecutar containers. en los ejemplos trabajaremos con el registry "docker hub".

Un registry es un repositorio público o provado donde guardaremos nuestras imágenes.

```bash
docker pull redpandaci/jenkins-dind  # Podemos usar "docker image pull redpandaci/jenkins-dind"
docker pull hello-world:latest       # Descargamos la imagen dicker del clásico "Hello, world!" en su última versión
```

Cada vez que hacemos "docker pull" de una imagen:

- En caso que imagen no exista en nuestro PC, se descargará del registry
- Si la imagen ya la tenemos en nuesto PC, comprobará si está actualizada, descargando la última versión en caso necesario

Podemos indicar una versión concreta a la hora de descargar una imagen:

```shell
docker pull redpandaci/jenkins-dind:2.89.4
```

En caso de no especificar versión, se bajará la última (latest)

```shell
docker pull redpandaci/jenkins-dind:latest    # Equivalente a "docker pull redpandaci/jenkins-dind"
```

---

Siguiente: [Containers](docker-containers.md) - Ir a la [Página principal](toc.md)
