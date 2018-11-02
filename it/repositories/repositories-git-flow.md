# Repositorios: Git Flow

Contenido:

- [Introducción](../repositories.md)
- [Conceptos básicos](repositories/repositories-basic-concepts.md)
- [Acciones principales](repositories/repositories-main-actions.md): clone, add / rm, commit, push, pull
- [Colaboración](repositories/repositories-collaboration.md): Branching & merging, resolución de conflictos
- **Conceptos de "git flow": master, develop, feature, release, hotfix**
- [Versionado](repositories/repositories-tags.md): Tags

Existen [diversos](https://dzone.com/articles/workflows-git) [tipos](https://buddy.works/blog/5-types-of-git-workflows) de flujo de trabajo asociados a `git`, que pueden ajustarse a distintas necesidades o distintos usos y costumbres de los equipos de desarrollo. 

Utilizaremos [Git Flow](https://nvie.com/posts/a-successful-git-branching-model/?) para nuestros ejemplos y "Test Labs". En la elaboración de esta guía se ha utilizado "Git Flow" junto con fork / pull request para elaborar el versionado y el [CHANGELOG.md](/CHANGELOG.md) del proyecto.

Como resumen del funcionamiento principal:

- El trabajo con Git Flow utiliza las llamadas "feature branches", con el nombre "feature/*" para desarrollar las distintas características de la aplicación de forma aislada.
- Las ramas de features se mezclan en la rama principal "develop" del repositorio cuando se finaliza el desarrollo de la característica.
- Cuando se quiere liberar una nueva versión, se crea una "release branch" etiquetada como "release/*".
- Una vez realizados los últimos test y ajustes en la rama de release, ésta se mezcla hacia la rama maestra del repositorio "master", a la rama principal de desarrollo "develop" y se crea una etiqueta o "tag" con el nombre de la release.
- Se habilita realizar hotfixes en ramas de nombre "hotfix/*" que salen de "master" y se reintegran en él, creando una etiqueta con el nombre del hofix.

Utilizando línea de comandos, todas las acciones de Git Flow comienzan con la orden `git flow ...`

Ejemplos:

- `git flow init` // Se configura la copia local del repositorio con las "extensiones" de git flow siguiendo un asistente
- `git flow feature start ejemplo` // Se crea una feature branch "ejemplo" en una llamada "feature/ejemplo"
- `git flow feature publish ejemplo` // Se publica la feature branch "ejemplo" en el servidor remoto con el nombre de rama "feature/ejemplo"
- `git flow feature finish ejemplo` // Se reintegra la feature branch "ejemplo" en la rama principal de desarrollo "develop"

En realidad, el uso de `git flow` supone un atajo al uso de comandos de `git`. Cada acción de `git flow` se traduce en una o varias acciones de git. 

## Test Lab

[![asciicast](https://asciinema.org/a/202939.png)](https://asciinema.org/a/202939)

- Descargamos el repositorio de ejemplo
- Inicializamos nuestra copia local del repositorio con la configuración de git flow.
- Creamos una feature branch llamada "ejemplo" y la publicamos en el servidor remoto
- Hacemos un cambio en el archivo "README.md" y subimos los cambios al servidor remoto, todo en nuestra _feature branch_
- Llevamos las modificaciones desde nuestra feature branch hacia la rama principal de desarrollo "develop".
- Finalizamos subiendo nuestro código al servidor remoto y borrando la rama "feature/ejemplo" del servidor remoto.

---

Siguiente: [Versionado](repositories-tags.md) - Ir a la [Página principal](../toc.md)
