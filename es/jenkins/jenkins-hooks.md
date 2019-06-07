# Jenkins: Hooks

Contenido:

- [Introducción](../jenkins.md)
- [Jobs](jenkins-jobs.md)
- [Builds](jenkins-builds.md)
- **Hooks**

Los hooks suponen el pegamento que une todas las fases en un proceso de CI/CD. El caso básiso es:

- Hacemos `commit` de nuestros cambios en nuetra copia local del repositorio.
- Empujamos los cambios al servidor centra mediante un `push`.
- El servidor recibe los cambios y dispara un build de Jenkins mediante una petición HTTP.

Llamamos _hook_ a esta petición http. Por un lado, configuramos en el servidor central ([GitHub](https://github.com), [Bitbucket](https://bitbucket.org) o [GitLab](https://about.gitlab.com/)) para que realice esa llamada. Por otro lado, configuramos Jenkins para que atienda a esas peticiones y ejecute una construcción del trabajo que especifiquemos.

Como referencia tenemos la documentación de [Jenkins](https://jenkins.io/solutions/github/) y la de [GitHub](https://resources.github.com/whitepapers/practical-guide-to-CI-with-Jenkins-and-GitHub/). Es necesario que nuestro Jenkins tenga instalado el plugin de [GitHub](https://wiki.jenkins.io/display/JENKINS/GitHub+Plugin).

---

Siguiente: [Docker](../docker.md) - Ir a la [Página principal](toc.md)
