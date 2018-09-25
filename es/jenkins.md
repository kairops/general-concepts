# Jenkins

Contenido:

- [Introducción](#introducción)
- [Jobs](jenkins/jenkins-jobs.md)
- [Builds](jenkins/jenkins-builds.md)
- [Hooks](jenkins/jenkins-hooks.md)

## Introducción

[Jenkins](http://jenkins.io/) es una herramienta de orquestación de tareas. Si atendemos a su definición en la [Wikipedia](https://es.wikipedia.org/wiki/Jenkins), _"Jenkins es un software de Integración Continua Open Soruce escrito en Java"_.

En la práctica, Jenkins es capaz de ejecutar unas tareas o "jobs" que definimos en el sistema. A cada ejecución de `job` se le denomina `build`, pudiendo iniciarse dicha ejecución de forma manual, con una programación de tiempo y recurrencia determinadas (a modo de tarea programada), o bien mediante la conexión a través de webhooks con distintos sistemas y servicios, por ejemplo un servicio de alojamiento de repositorios (Github, Bitbucket, Gitlab), una herramienta de inspección continua de código como SonarQube, etc.

Está enmarcada como una pieza más dentro de las herramientas de gestión de ciclo de vida de software. Podemos programar `jobs` con etapas una serie de pasos que se ejecutan uno detrás de otro o en paralelo, como pueden ser Build, Test, Deploy o Release. Utilizamos Jenkins para Integración Continua, Despliegue Continuo y/o Entrega Continua de software.

Al tratarse de una herramienta libre de código abierto, existe una gran comunidad a su alrededor. Dispone de _plugins_ que cubren casi cualquier necesidad.

Hay alternativas a Jenkins, como [Travis](https://travis-ci.org/), [Bamboo](https://es.atlassian.com/software/bamboo), [Circle CI](https://circleci.com/), etc.

### Recursos

Aparte de la extensa [documentación oficial](https://jenkins.io/doc/), podemos encontrar multitud de guías sobre primeros pasos con Jenkins.

Dos guías introductorias:

- [Guiadev](https://guiadev.com/introduccion-a-jenkins/)
- [Software Quality Team Blog](https://qateamblog.wordpress.com/2017/04/23/introduccion-a-jenkins/)

Y dos tutoriales en forma de workshop:

- [Jenkins Workshop - Red Panda CI](https://github.com/red-panda-ci/jenkins-workshop)
- [Jenkins Pipeline Workshop - Red Panda CI](https://github.com/red-panda-ci/jenkins-pipeline-workshop)
