# Jenkins: Jobs

Contenido:

- [Introducción](../jenkins.md)
- **Jobs**
- [Builds](jenkins-builds.md)
- [Hooks](jenkins-hooks.md)

Son el elemento principal de Jenkins. Contienen una serie de pasos que definimos a nuestra conveniencia, y que podemos ejecutar tantas veces como se requiera.

Podemos añadir parámetros de ejecución, asociar los Jobs a repositorios alojados en GitHub o GitLab, etc.

Para entender mejor qué es un job utilizaremos un container Docker con toda la configuración necesaria para que se ejecute Jenkins en nuestra máquina. Nos serviremos del proyecto de Red Panda CI [Jenkins-dind](https://github.com/red-panda-ci/jenkins-dind)

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

Podemos iniciar sesión en el servicio con el usuario "redpanda" y contraseña "redpanda".

![Jenkins - Accediendo al área privada](img/jenkins-auth.png?raw=true "Jenkins - Accediendo al área privada")

Una vez hayamos finalizado nuestras pruebas, destruimos el container y toda su configuración de esta forma

```console
$ docker stop jenkins-dind
```

### Crear Job

Nuestra instancia de Jenkins _dockerizada_ no tiene configurado ningún job. Vamos a crear uno que se descargará este mismo repositorio de documentación (!)

Hemos iniciado sesión, lo primero que nos informa Jenkins es que podemos crear una nueva tarea ("job") y nos ofrece un enlace

![Jenkins - Página principal](img/jenkins-user-logged.png?raw=true "Jenkins - Página principal")

Pulsamos sobre el enlace "Crear una nueva tarea". En la siguiente página ponemos "prueba" en la caja de texto, seleccionamos "Pipeline" como tipo de proyecto y pulsamos sobre "OK".

![Jenkins - Creando job](img/jenkins-creating-job.png?raw=true "Jenkins - Creando job")

Pasamos a la página de configuración del Job, vamos a la sección "Pipeline" de la parte inferior y ponemos el siguiente código.

```groovy
pipeline {
    agent any

    stages {
        stage('Inicio') {
            steps  {
                echo "Inicio"
            }
        }
        stage('Clonar fuentes') {
            steps  {
                git url: 'https://github.com/red-panda-ci/general-concepts.git'
            }
        }
        stage('Mostrar README.md') {
            steps  {
                sh "cat README.md"
            }
        }
        stage('Limpiar workspace') {
            steps  {
                deleteDir()
            }
        }
    }
}
```

Dejamos el resto como está y pulsamos sobre "Guardar".

![Jenkins - Configurando job](img/jenkins-configuring-job.png?raw=true "Jenkins - Configurando job")

Pulsando sobre "Guardar" nuestro job de Jenkins estará listo.

![Jenkins - Job listo](img/jenkins-job-ready.png?raw=true "Jenkins - Job listo")

La sintaxis del job es "Jenkins Declarative Pipeline", un DSL construido sobre groovy. Se pueden apreciar distintos stages (etapas), steps (pasos), algunas directivas como "agent" y algunas instrucciones como "sh". Aunque no tengamos dominio sobre código groovy o sobre "Declarative Pipeline", se puede intuir fácilmente lo que hace el job.

En la página sobre [Builds](jenkins-builds.md) veremos ejemplos de ejecución del job.

---

Siguiente: [Builds](jenkins-builds.md) - Ir a la [Página principal](../toc.md)
