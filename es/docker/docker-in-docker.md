# Docker: Docker in Docker

Contenido:

- [Introducción](../docker.md)
- [Imágenes](docker-images.md)
- [Containers](docker-networks.md)
- [Redes](docker-networks.md)
- [Volúmenes](docker-volumes.md)
- [Docker Compose](docker-compose.md)
- **Docker in Docker**

Trabajaremos con un Jenkins dockerizado configurando todo lo necesario para poner a punto pipelines de CI

## Uso de Docker para montaje de Jenkins en local y dockerizado

Partiendo del proyecto Jenkins DIND <https://github.com/red-panda-ci/jenkins-dind> se genera esta imagen de docker <https://hub.docker.com/r/redpandaci/jenkins-dind/>

Utilizaremos la imagen de docker con Jenkins DIND para montar pipelines de ejemplo a partir de una organización de github. El propio proyecto dispone de un pipeline de CI/CD que cubre build, test, creación y "push" de imagen de docker y gestión de release. Se puede tomar ese archivo.

- Levantamos Jenkins en nuestro PC con Docker

```shell
$ docker run --privileged --rm -d --name jenkins-dind -e JENKINS_USER=redpanda -e JENKINS_PASS=redpanda -p 8080 redpandaci/jenkins-dind:2.89.4
Unable to find image 'redpandaci/jenkins-dind:2.89.4' locally
2.89.4: Pulling from redpandaci/jenkins-dind
1be7f2b886e8: Pull complete
6fbc4a21b806: Pull complete
c71a6f8e1378: Pull complete
4be3072e5a37: Pull complete
06c6d2f59700: Pull complete
a93614305743: Pull complete
e4144bdc31e8: Pull complete
3c8f4870fc59: Pull complete
0fa1644eaada: Pull complete
f96180a32711: Pull complete
ec55146fb59e: Pull complete
a15b026a3e3f: Pull complete
a32b2dfb0e74: Pull complete
ac06df183566: Pull complete
9be8a4b72272: Pull complete
00d2f25b9939: Pull complete
548a9b635033: Pull complete
5042fd6bc83e: Pull complete
eac30657d62c: Pull complete
f50a5064892e: Pull complete
Digest: sha256:bde5c5de8c30c4bda31d90552b6e845ed62bc886c808b858b74b6e70c534eca7
Status: Downloaded newer image for redpandaci/jenkins-dind:2.89.4
71a1203f7f9c3fb214925c3732a921af8f3048b84a469660bff04b715e221a92
```

- Arrancamos el navegador y abrimos el puerto que corresponda (para nuestro caso <http://0.0.0.0:32775>)

```shell
$ docker ps -a
CONTAINER ID        IMAGE                            COMMAND                  CREATED             STATUS              PORTS                     NAMES
71a1203f7f9c        redpandaci/jenkins-dind:2.89.4   "wrapdocker java -ja…"   22 seconds ago      Up 21 seconds       0.0.0.0:32775->8080/tcp   jenkins-dind
```

Tan sólo tenemos que acceder con el usuario / contraseña que hemos indicado, en nuestro caso "redpanda/redpanda". Vamos a comentar los parámetros del "docker run":

- --privileged => Utilizamos estrategia "docker in docker", es decir, que nuestro Jenkins dockerizado pueda a su vez correr docker
- --rm => El container se borrará de forma automática cuando se pare. ¡Cuidado! Al detener el container todos nuestros datos y configuraciones van a desaparecer
- -d => Ejecución en modo "daemon": nos devuelve el control, se queda ejecutando en segundo plano
- --name jenkins-dind => Le damos un nombre a nuesgtro container
- -e JENKINS_USER=redpanda -e JENKINS_PASS=redpanda => Variables de entorno de usuario y contraseña
- -p 8080 => Cuál es el puerto que vamos a "exponer" en nuestra red. Será mapeado con NAT a un puerto disponible a parti4r del 32767
- redpandaci/jenkins-dind:2.89.4 => Cuál es la imagen de docker hub de la que vamos a partir para levantar el container. Utilizamos la jenkins-dind:2.89.4, que se corresponde con Jenkins LTS 2.89.4

Las configuraciones de prueba del workshop las vamos a realizar sobre este container recién levantado

### Configuración y uso de agentes (nodos)

Si enlazamos con el apartado de Docker Compose, podremos ver como tenemos un Jenkins funcionando con dos agentes:

- agent1
- agent2

El usuario / contreaseña de nuestra instalación es "redpanda/redpanda"

### Gestión de plugins y configuración

La image Docker jenkins-dind con la que estamos trabajando tiene instalados todos los plugins necesarios para ejecutar los pipelines de los ejemplos. Se puede revisar la lista de plugins instalados accediendo en el menú de la izquierda en "Manage Jenkins -> Manage Plugins".
La configuración está accesible en "Manage Jenkins -> Configure System". Sobre este apartado de configuración es necesario realizar un ajuste en configuración para que los pipelines del ejemplo funcionen correctamente: se tiene que añadir el label "docker".

- Accedemos a "Manage Jenkins -> Configure System"
- Buscamos el campo "Labels", que encontraremos vacío, y ponemos "docker"
- Pulsamos en "Save"

### Creación de organización Github y "Engagement" a Jenkins

Tenemos dos opciones para configurar proyectos en nuestro Jenkins: hacerlo uno por uno, repositorio a repositorio, o configurar una organización de Github completa. Cada método tiene sus ventajas e inconvenientes; trabajando con repositorios individuales tenemos configuración más granular, mientras que si lo hacemos a nivel organización únicamente tenemos que configurar una única vez.

Trabajando a "nivel organización github" tendremos:

- Configuración única
- "Engagement" de todos los repositorios de la organización que tengan "Jenkinsfile". Se revisan todas las ramas de todos los repositorios, y se crea un "Job" para cada rama
- Añadiendo un webhook en Github tendremos también auto-engagement de repositorios nuevos que tengan un fichero "Jenkinsfile" versionado

**Primer paso**: Crear una organización en Github

- Accedemos a GitHub con nuestro usuario. En caso de no disponer de usuario de github se puede dar de alta un nuevo usuario de forma gratuita.
- En la página principal de nuestra cuenta pulsamos sobre el "+" en la parte superior derecha. Seleccionamos "New organization"
- Rellenamos los datos de la nueva organización
  - Una nombre que nos parezca adecuado y no esté en uso. Para nuestro ejemplo será "jenkins-workshop-gigigo"
  - Una dirección de mail en "Billing address". Esto no implica coste si seleccionamos la opción "Free"
- Pulsamos sobre "Create organization"

**Segundo paso**: Añadimos un repositorio a nuestra organización

Haremos "fork" del proyecto "testlenium"

- Abrimos la URL <https://github.com/red-panda-ci/testlenium> en el navegador
- Pulsamos sobre "Fork" y seleccionamos la organización que acabamos de crear (en el caso del ejemplo "jenkins-workshop-gigigo")

Si todo ha ido bien tendremos una copia (fork) del repositorio en nuestra organización <https://github.com/jenkins-workshop-gigigo/testlenium>

**Tercer paso**: Creamos un proyecto nuevo en nuestro Jenkins "enganchado" a la organización Github

Embarcamos la organización Github en nuestro Jenkins efímero dockerizado:

- Abrimos la URL de Jenkins <http://0.0.0.0:32775> y accedemos con "redpanda/redpanda"
- Pulsamos sobre "New item" en el menú de la izquierda
- En la página de "New item"
  - Introducimos el nombre de la organización github en la caja de texto ("jenkins-workshop-gigigo" para nuestro ejemplo)
  - Seleccionamos "GitHub Organization" (penúltimo elemento)
  - Pulsamos sobre "OK". Se creará el item y veremos la página de propiedades de la organización
- En la página de propiedades de la organización:
  - Añadimos nuestro usuario / contrraseña de Github en el apartado "Projects":
    - Seleccionamos el botón "Add" en "Credentials" (vemos que hay un desplegable que pone "-none-") y escogemos la primera opción ("jenkins-workshop-gigigo" en nuestro ejemplo)
    - Rellenamos usuario / contraseña con nuestras credenciales de Github y ponemos un texto descriptivo en ID, por ejemplo "github"
    - Al pulsar sobre "Add" volvemos a la página de propiedades, pero esta vez al desplegar en "Credentials" veremos la que acabamos de añadir. Seleccionamos esa.
    - Elegimos qué ramas van a disparar un "build": en la parte de abajo de la página hay una opción "Automatic branch project triggering" con una caja de texto, que rellenamos con "develop". De esta forma tendremos vigilada la rama develop de los repositorios. Para nuestro ejemplo es suficiente, en casos reales tendremos que incluir más ramas, o todas las ramas

Vamos a dejar el resto de opciones tal cual, y pulsamos en "Save" en la parte de abajo de la página para guardar los cambios. En ese momento Jenkins revisa todos los repositorios de la organización, buscando aquellos que tengan un archivo Jenkinsfile en cada una de las ramas vigiladas (recordemos: únicamente la rama "develop"). Para cada repositorio que cumpla con los criterios creará un "job" nuevo en cada rama que tenga archivo Jenkinsfile y ejecutará un "build"; en nuestro caso del ejemplo Jenkins se encontrará con el proyecto "testlenium".

En la parte de abajo a la izquierda de la página veremos "Build Executor Status" con un build en ejecución. Si pinchamos sobre él veremos el build en mientras se ejecuta, pudiendo acceder a la consola (Console Output de la izquierda), o bien podremos pinchar sobre "Open Blue Ocean" para tener una visión con esa interfaz. Sólo tendremos que esperar a que el build finalice para tener como artefactos vídeos de ejecución de los test, tal y como está programado realizarse por el Jenkinsfile del proyecto.

**Cuarto paso**: Configuramos un "hook" a nivel organización

Verificamos que Jenkins ha añadido un Webhook a nuestra organización apuntando a la URL del jenkins dockerizado (en nuestro ejemplo <http://0.0.0.0:32775/github-webhook/>). Si somos capaces de llevar tráfico HTTP al servicio Jenkins dockerizado, cuando sucedan eventos en la organización, como un push, creación de un pull request o creación de un repositorio, Github "llamará" a nuestro Jenkins para que se ponga a trabajar. Esta información la vemos accediendo a la organización Github desde el navegador, y pulsando en "Settings" => "Webhook"

Debido a la naturaleza de este taller (Jenkins efímero, dockerizado) no vamos a entrar en detalles de cómo hacerlo. Tendremos que buscar nosotros los cambios de forma explícita desde nuestro Jenkins. Es decir: usar una y otra vez la opción "Scan".

### Creación de proyecto Bitbucket y "Engagement" a Jenkins

La configuración es similar a la organización de Github. Debemos crear un proyecto bitbucket. En el caso de bitbucket podemos crear un proyecto privado con repositorios privados de manera gratuita. El vídeo no cobre esta parte y se puede experimentar con ello.

RETO: crear proyecto Bitbucket y conectarlo a nuestro Jenkins de pruebas.

---

Siguiente: [Sonar](../sonar.md) - Ir a la [Página principal](toc.md)
