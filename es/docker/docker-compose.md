# Docker: Docker Compose

Contenido:

- [Introducción](../docker.md)
- [Imágenes](docker-images.md)
- [Containers](docker-networks.md)
- [Redes](docker-networks.md)
- [Volúmenes](docker-volumes.md)
- **Docker Compose**
- [Docker in Docker](docker-in-docker.md)

## Docker Compose

Utilizando imágenes (plantillas) y la capacidad de crear y eliminar containers basados en esas imágenes junto con redes y volúmenes podemos preparar plataformas efímeras completas usando docker compose.

Esta documentación no pretende ser una guía de lo que se puede hacer o no utilizando compose, sino una referencia mínima para poder orquestar pipelines.

La plataforma efímera se define en el archivo "docker-compose.yml". Algunos comandos básicos:

```shell
docker-compose up     # Crea los servicios. Si añadimos la opción "-d" se levantarán los servicios en modo "daemon"
docker-compsose ps    # Muestra los servicios en ejecución
docker-compose down   # Elimina los servicios. Si añadimos la el parámetro "-v" se eliminan también los volúmenes
```

Vamos a utilizar un repositorio de Red Panda para ver el funcionamiento de docker-compose. Utilizaremos un script del propio repositorio "bin/test.sh"

```shell
$ git clone https://github.com/red-panda-ci/jenkins-pipeline-library                            # Clonamnos el repositorio "jenkins-pipeline-library"
Cloning into 'jenkins-pipeline-library'...
remote: Counting objects: 2131, done.
remote: Compressing objects: 100% (52/52), done.
remote: Total 2131 (delta 43), reused 85 (delta 38), pack-reused 2032
Receiving objects: 100% (2131/2131), 343.29 KiB | 1.60 MiB/s, done.
Resolving deltas: 100% (1300/1300), done.
$ cd jenkins-pipeline-library/
$ git checkout run-agents                                                                       # Para el ejemplo trabajaremos con el tag "run-agents"
Note: checking out 'run-agents'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command again. Example:

  git checkout -b <new-branch-name>

HEAD is now at 7d27a6f... New: Agent attachment

$ docker-compose ps                                                                             # Verificamos que no hay servicios en la plataforma
Name   Command   State   Ports
------------------------------
$ docker volume ls                                                                              # Verificamos que no existen volúmeneqs
DRIVER              VOLUME NAME
$ docker network ls                                                                             # Verificamos que únicamente tenemos las redes estándar
NETWORK ID          NAME                DRIVER              SCOPE
83cc08e29b76        bridge              bridge              local
8d0d0aa3be38        host                host                local
be98665938d5        none                null                local
$ bin/test.sh local                                                                             # Levantamos plataforma con el script
# Start jenkins as a docker-compose daemon
Creating network "jenkinspipelinelibrary_default" with the default driver
Creating volume "jenkinspipelinelibrary_jpl-dind-cache" with default driver
Creating jenkinspipelinelibrary_jenkins-dind_1   ... done
Creating jenkinspipelinelibrary_jenkins-agent1_1 ... done
Creating jenkinspipelinelibrary_jenkins-agent2_1 ... done
# Started platform with id 7383a990deed595fcd413a5691308c1189bcc06e8e523c6627560e78dfa4ad75 and port 0.0.0.0:32772
# Copy jenkins configuration and prepare code for testing
fatal: Needed a single revision
Switched to a new branch 'develop'
0da8f202679aecefdee812cba3be148e3cf123ec
Switched to a new branch 'release/v9.9.9'
Switched to a new branch 'hotfix/v9.9.9-hotfix-1'
Switched to a new branch 'jpl-test-promoted'
Switched to a new branch 'jpl-test'
# Waiting for jenkins service to be initialized
# Download jenkins cli
# Prepare agents
# Reload Jenkins configuration
$ docker-compose ps                                                                             # Revisamos los servicios de la plataforma en ejecución
                 Name                                Command               State            Ports
----------------------------------------------------------------------------------------------------------
jenkinspipelinelibrary_jenkins-agent1_1   bash -c tail -f /var/log/*.log   Up
jenkinspipelinelibrary_jenkins-agent2_1   bash -c tail -f /var/log/*.log   Up
jenkinspipelinelibrary_jenkins-dind_1     wrapdocker java -jar /usr/ ...   Up      0.0.0.0:32772->8080/tcp
$ docker ps                                                                                     # Revisamos los containers que se han creado
CONTAINER ID        IMAGE                     COMMAND                  CREATED             STATUS              PORTS                     NAMES
1833d2576f67        jenkins/jnlp-slave        "bash -c 'tail -f /v…"   7 seconds ago       Up 5 seconds                                  jenkinspipelinelibrary_jenkins-agent2_1
feb35fd347dc        redpandaci/jenkins-dind   "wrapdocker java -ja…"   7 seconds ago       Up 5 seconds        0.0.0.0:32772->8080/tcp   jenkinspipelinelibrary_jenkins-dind_1
1ad4efe33b53        jenkins/jnlp-slave        "bash -c 'tail -f /v…"   7 seconds ago       Up 4 seconds                                  jenkinspipelinelibrary_jenkins-agent1_1
$ docker volume ls                                                                              # Revisamos los volúmenes que se han creado
DRIVER              VOLUME NAME
local               58772b1b07e0674cbc69cc053cda44d689d3ab6776ca21fe4063dc73e560da85
local               5e8e481500b30b8c2ae9cd091fe04cdcc625034a2847750e6549ce2b8cbc8f11
local               81b99e45d732f801ce042eabc5ec56d3f7e4a395af2f82e8d76befa0e542811c
local               9fdc23f342a48b9afef65ead049b12cd655265d61e4b447efcdc8d5dfba7583e
local               jenkinspipelinelibrary_jpl-dind-cache
$ docker network ls                                                                             # Revisamos las redes que se han creado
NETWORK ID          NAME                             DRIVER              SCOPE
83cc08e29b76        bridge                           bridge              local
8d0d0aa3be38        host                             host                local
2d55068be4a8        jenkinspipelinelibrary_default   bridge              local
be98665938d5        none                             null                local
$ docker-compose down -v                                                                        # Paramos y eliminamos la plataforma y sus volúmenes
Stopping jenkinspipelinelibrary_jenkins-agent2_1 ... done
Stopping jenkinspipelinelibrary_jenkins-agent1_1 ... done
Stopping jenkinspipelinelibrary_jenkins-dind_1   ... done
Removing jenkinspipelinelibrary_jenkins-agent2_1 ... done
Removing jenkinspipelinelibrary_jenkins-agent1_1 ... done
Removing jenkinspipelinelibrary_jenkins-dind_1   ... done
Removing network jenkinspipelinelibrary_default
Removing volume jenkinspipelinelibrary_jpl-dind-cache
$ docker-compose ps                                                                             # Verificamos que no tenemos containers en ejecución
Name   Command   State   Ports
------------------------------
$ docker volume ls                                                                              # Verificamos que los volúmenes se han eliminado
DRIVER              VOLUME NAME
$ docker network ls                                                                             # Verificamos que la red se ha eliminado
NETWORK ID          NAME                DRIVER              SCOPE
83cc08e29b76        bridge              bridge              local
8d0d0aa3be38        host                host                local
be98665938d5        none                null                local
```

Al levantar la plataforma:

- Se han creado los containers
  - jenkinspipelinelibrary_jenkins-agent1_1
  - jenkinspipelinelibrary_jenkins-agent2_1
  - jenkinspipelinelibrary_jenkins-dind_1
- Se ha creado la red "jenkinspipelinelibrary_default"
- Se han creado los volúmenes
  - 58772b1b07e0674cbc69cc053cda44d689d3ab6776ca21fe4063dc73e560da85
  - 5e8e481500b30b8c2ae9cd091fe04cdcc625034a2847750e6549ce2b8cbc8f11
  - 81b99e45d732f801ce042eabc5ec56d3f7e4a395af2f82e8d76befa0e542811c
  - 9fdc23f342a48b9afef65ead049b12cd655265d61e4b447efcdc8d5dfba7583e
  - jenkinspipelinelibrary_jpl-dind-cache

Para el caso del ejemplo se crea una plataforma de Jenkins dockerizada compuesta por un nodo "master" y dos nodos "slave" conectados. Podemos obvservar cómo se ha añadido el prefijo "jenkinspipelineliberary" a redes, containers y volúmenes. Este prefijo está relacionado con el nombre del directorio donde hemos levantrado la plataforma, en este caso "jenkins-pipeline-library"

Utilizaremos esta misma "plataforma efímera dockerizada" con docker-compose en el apartado posterior de configuración y uso de agetes.

---

Siguiente: [Docker in Docker](docker-in-docker.md) - Ir a la [Página principal](toc.md)
