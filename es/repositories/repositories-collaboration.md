# Repositorios: Colaboración

Contenido:

- [Introducción](../repositories.md)
- [Conceptos básicos](repositories/repositories-basic-concepts.md)
- [Acciones principales](repositories/repositories-main-actions.md): clone, add / rm, commit, push, pull
- **Colaboración: Branching & merging, resolución de conflictos**
- [Conceptos de "git flow"](repositories/repositories-git-flow.md): master, develop, feature, release, hotfix
- [Versionado](repositories/repositories-tags.md): Tags

El uso de `git` es se ha vuelto prácticamente obligatorio si estamos hablando de gestión de código fuente en desarrollo de software. Si bien tiene sentido utilizar `git` cuando trabajamos solos, es al trabajar con más gente cuando `git` nos proporciona mecanismos avanzados de colaboración.

Hablemos sobre ramas, mezclas y resolución de conflictos

## Ramas

Actúan como una copia aislada del código, donde podemos efectuar todos los cambios que sean necesarios sin afectar al resto. Es como disponer de una copia de toda la base de código en un directorio diferente del sistema de archivos.

En nuestro repositorio de ejemplo, podemos crear una rama nueva con `git checkout -b ...`

Ejemplos:

- `git checkout -b pruebas origin/master` // Creamos una rama "pruebas" a partir de la rama "master" del repositorio en la copia local de nuestro repositorio
- `git push origin pruebas` // Subimos la nueva rama "pruebas" al servidor remoto

Podemos hacer las pruebas descritas en el [Test Lab de Acciones Principales](repositories-main-actions.md#Test-Lab) sobre la rama "pruebas" recién creada.

Una función adicional de `git checkout` es cambiar de una rama a otra.

Ejemplos:

- `git checkout develop` // Nos situamos a la rama "develop"
- `git checkout master` // Cambiamos a la rama "master"
- `git checkout pruebas` // Volvemos a nuestra rama "pruebas" (la rama debe existir en el repositorio)

En cada cambio de rama `git` actualiza los ficheros de nuestra copia de trabajo para dejarlos tal y como se encuentran registrados en esa rama. Si un fichero existe en la rama "pruebas", no existe en la rama "develop" y hacemos un cambio de "pruebas" a "develop", el fichero _desaparece_ al hacer el cambio. Si volvemos de la rama "develop" a la rama "pruebas", el fichero _vuelve a aparecer_.

## Mezclas

Es recomendable hacer las modificaciones al código fuente en nuestra propia rama. Cuando hemos finalizado los cambios, nos llevamos esas modificaciones y toda su historia a la rama principal de desarrollo mediante una mezcla (**merge**).

Aprendiendo desde un ejemplo, el flujo de trabajo típico para un `merge` es el siguiente:

_Tomaremos como ejemplo la rama "pruebas" como nuestra rama de desarrollo y la rama "develop" como el destino donde queremos llevar nuestros cambios_

- Nos aseguramos de que todos los cambios de nuestra rama "pruebas" están subidos al servidor remoto (`git commit...` / `git push ..`). Podemos comprobar el estado de nuestra copia local del repositorio con `git status`.
- Cambiamos a la rama "develop", donde queremos llevar nuestras modificaciones (`git checkout develop`).
- Nos aseguramos que la rama "develop" está sincronizada con los últimos cambios subidos al servidor remoto (`git pull`).
- Hacemos la mezcla de código: nos "traemos" los cambios de nuestra rama "pruebas" (`git merge pruebas`).
- Subimos la rama "develop" actualizada con nuestras modificaciones al servidor remoto (`git push`)

Tenemos todos los detalles en el [Test Lab](#Test-Lab).

## Resolución de conflictos

Tendremos un conflicto en el repositorio si estamos haciendo modificaciones en algún fichero y otro desarrollador también ha hecho modificaciones del mismo fichero y las ha subido al servidor remoto.

El conflicto se pone de manifiesto cuando tratamos de hacer "pull" y traer los cambios en el repositorio remoto. `git` tiene un sistema inteligente de gestión para las modificaciones, pero hay ciertos casos en los que no puede tomar la decisión de qué hacer y es el desarrollador quien ha de indicar cuáles de las las modificaciones son las correctas.

Lejos de suponer algo negativo, los conflictos fomentan la colaboración entre desarrolladores. Elaborar software y desarrollar algoritmos es una tarea en la mayoría de las ocasiones individual, aislada y reflexiva. Los conflictos en código son una oportunidad para socializar ;)

Veremos un caso práctico en el que se produce y resuelve un conflicto en la sección siguiente "Test Lab".

## Test Lab

Simularemos el trabajo de dos desarrolladores distintos. Para cada desarrollador vamos a:

- Clonar el repositorio de ejemplo
- Crear una rama nueva
- Hacer modificaciones de un fichero en la rama nueva
- Confirmar los cambios en nuestra copia local y subirlos al servidor remoto
- Llevar nuestros cambios a la rama principal de desarrollo "develop" con un `merge`
- Subir esa mezcla de "develop" al servidor remoto

### Modificaciones developer 1

[![asciicast](https://asciinema.org/a/202866.png)](https://asciinema.org/a/202866)

Hemos clonado el repositorio en dos directorios distintos de nuestro PC (("~/testlab/dev1" y "~/testlab/dev2")) con objeto de disponer de la misma situación de partida para ambos desarrolladores "simulados".

En este primer paso hemos creado una rama nueva "dev1" a partir de la rama "develop", hemos hecho un cambio en el archivo README.md y hemos subido nuestras modificaciones al repositorio remoto

### Modificaciones developer 2

[![asciicast](https://asciinema.org/a/202868.png)](https://asciinema.org/a/202868)

En una operación similar a la anterior, hemos trabajado creando una rama "dev2" a partir de la rama "develop", posteriormente hicimos cambios en esa rama "dev2" y los subimos al servidor remoto.

### Mezcla de ramas, aparición y resolución de conflicto

[![asciicast](https://asciinema.org/a/202870.png)](https://asciinema.org/a/202870)

El primer desarrollador lleva sus cambios de la rama "dev1" hacia la rama "develop" del repositorio, resultando que todas las operaciones finalizan correctamente.

Cuando nos traemos las novedades del servidor remoto con `git pull` sobre la rama `develop` podemos ver cómo se descarga también la rama "dev2", que el segundo desarrollador ya había subido a remoto.

---

[![asciicast](https://asciinema.org/a/202874.png)](https://asciinema.org/a/202874)

El segundo desarrollador trata de llevar sus modificaciones a la rama principal de desarrollo y se encuentra con que en la rama "develop" el primer desarrollador ha modificado el fichero README.md. Por tanto, tenemos un conflicto

Para resolver el conflicto hemos utilizado Visual Studio Code. 

![VSCode - Show conflicts](img/vscode-show-conflicts.png?raw=true "VSCode - Show conflicts")

En este caso aceptamos ambos cambios en el fichero README.md, confirmamos y subimos al repositorio remoto.

![VSCode - Resolve conflicts](img/vscode-resolve-conflicts.png?raw=true "VSCode - Resolve conflicts")

## Conclusión

Git es una herramienta muy completa que permite colaborar con el código fuente de un proyecto en un equipo de desarrollo de prácticamente cualquier tamaño. No obstante, pueden surgir conflictos durante los `merge` que se realizan.

Conocer y manejar adecuadamente `git` nos habilita a resolver conflictos de una manera sencilla.

---

Siguiente: [Conceptos de "git flow"](repositories-git-flow.md) - Ir a la [Página principal](../toc.md)
