# Jenkins: Jobs

Son el elemento principal de Jemkins. Contienen una serie de pasos que definimos a nuestra conveniencia, y que podemos ejecutar tantas veces como se requiera. 

Podemos añadir parámetros de ejecución, asociar los jobs a repositorios alojados en Github o Gitlab, etc.

Para entender mejor qué es un job, podemos utilizar un container docker con toda la configuración necesaria para que se ejecute Jenkins en nuestra máquina.

## Test Lab

Necesitamos disponer de [Docker](https://docker.io/) instalado en nuestro PC

### Arranque y parada de Jenkins

Arrancamos el container de Jenkins de esta forma

```console
$ docker run --privileged --rm -d --name jenkins-dind -e JENKINS_USER=redpanda -e JENKINS_PASS=redpanda -p 10080 redpandaci/jenkins-dind:latest
```

Usaremos un navegador para acceder a la dirección http://localhost:10080 (en las capturas de pantalla la dirección es http://jenkins-redpanda:10080)

_Captura de pantalla del container de Jenkins iniciando_

![Jenkins - Arrancando container](img/jenkins-starting.png?raw=true "Jenkins - Arrancando container")

_Jenkins listo para operar_

![Jenkins - Servicio iniciado](img/jenkins-started.png?raw=true "Jenkins - Servicio iniciado")

Podemos iniciar sesióin en el servicio con el usuario "redpanda" y contraseña "redpanda".

![Jenkins - Accediendo al área privada](img/jenkins-auth.png?raw=true "Jenkins - Accediendo al área privada")

Una vez hayamos finalizado nuestras pruebas, destruimos el container y toda su configuración de esta forma

```console
$ docker stop jenkins-dind
```

### Crear Job

Nuestra instancia de Jenkins dockerizada no tiene ningún job inicialmente. Vamos a dar de alta un Job que se descargará este mismo repositorio de documnentación (!)

Hemos iniciado sesión, lo primero que nos informa Jenkins es que podemos crear una nueva tarea ("job") y nos ofrece un enlace

![Jenkins - Página principal](img/jenkins-user-logged.png?raw=true "Jenkins - Página principal")

[TBD]