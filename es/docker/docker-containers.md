# Docker: Containers

Contenido:

- [Introducción](../docker.md)
- [Imágenes](docker-images.md)
- **Containers**
- [Redes](docker-networks.md)
- [Volúmenes](docker-volumes.md)
- [Docker Compose](docker-compose.md)
- [Docker in Docker](docker-in-docker.md)

Se pueden considerar "objetos" de la "clase" imagen.

```shell
$ docker run hello-world                   # Ejecución del clásico "Hello, World!

[...]

$ docker container ps -a                        # Listado de containers, tanto que están en ejecución como los que finalizaron
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS                     PORTS               NAMES
64897191cb95        hello-world         "/hello"            1 second ago        Exited (0) 2 seconds ago                       unruffled_ardinghelli
$ docker container rm unruffled_ardinghelli     # Borrado de container
unruffled_ardinghelli
$ docker ps -a                                  # Atajo para "docker container ps -a"
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
```

---

Siguiente: [Redes](docker-networks.md) - Ir a la [Página principal](toc.md)
