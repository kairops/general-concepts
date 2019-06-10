# Repositorios: Conceptos básicos

Contenido:

- [Introducción](../repositories.md)
- **Conceptos básicos**
- [Acciones principales](repositories-main-actions.md)
- [Colaboración](repositories-collaboration.md): Branching & merging, resolución de conflictos
- [Conceptos de "git flow"](repositories-git-flow.md): master, develop, feature, release, hotfix
- [Versionado](repositories-tags.md): Tags

Existen multitud de tutoriales y guías acerca del uso de git. Uno de los mejores recursos es el libro tutorial [pro-git](https://git-scm.com/book/es/v2). La información que ahí figura es realmente extensa y completa.

Podemos ver un repositorio `git` como una suerte de base de datos de código fuente donde almacenamos cada uno de los cambios que vamos haciendo en nuestra aplicación. Los cambios se guardan agrupados en conjuntos denominados **commit** identificados mediante un _hash_ que sirve para localizar ese conjunto de cambios y diferenciarlo del resto. Cada uno de estos **commit** lleva asociada su descripción en forma de mensaje.

Si vemos el **repositorio** como una _base de datos_ los **commit** serían _registros de una tabla_.

Tamibén podemos ver un repositorio git como una _máquina del tiempo_ donde se guardan los cambios que hemos ido haciendo día tras día en nuestro código fuente.

Por tanto:

- **Repositorio**: lugar donde guardamos el código fuente de nuestra aplicación.
- **commit**: conjunto de cambios que guardamos en el repositorio, identificado con un _hash_ generado automáticamente y descrito por un mensaje.

Una definición de `git` es _gestor de versiones distribuido_. Existen mecanismos de distribución de esos **commits** del repositorio desde nuestra copia local. Un concepto interesante de los repositorio `git` es que actúan de forma _descentralizada_: no existe la necesidad de que mantener un repositorio central de donde descargar el repositorio y donde todos los desarrolladores de una aplicación dejen sus nuevos cambios. Ahora bien: aunque no sea obligatorio ni prescriptivo, es conveniente disponer de ese repositorio central.

Aquí es donde entran en juego servicios como [GitHub](https://github.com), [Bitbucket](https://bitbucket.org) y [GitLab](https://about.gitlab.com/), tres de los principales servicios centralizados de repositorios.

Utilizando ambas `git` junto con alguno de estos servicios tenemos cubiertas todas las necesidades respecto al [Ciclo de Vida](application-lifecicle.md) del código fuente de nuestra aplicación:

- Cuando comenzamos a trabajar en una aplicación nos descargamos (**clone**) el código fuente desde el servidor central.
- Si estamos trabajando en nuevos cambios (**commits**) nos interesa que estén asegurados (**push**) en el servidor central. Además, esos cambios no deben afectar al resto de desarrolladores, por lo que utilizamos una rama (**feature branch**) para avanzar con nuestro desarrollo, ¡no queremos romper nada!.
- Cuando otro desarrollador ha modificado partes de la aplicación, quizá nos interese descargar esos cambios (**pull** / **fetch**) desde el servidor central hacia nuestra copia local del repositorio.
- Al completar nuestras modificaciones, queremos que nuestro código se vuelva "oficial" y esté disponible para todo el mundo o para poner en producción, por lo que hacemos una mezcla (**merge**) de nuestro código en la rama principal de desarrollo (**develop**).
- A la hora de poner nuestros cambios en procucción, lo hacemos mediante una rama de liberación (**release branch**) que acabará llevando nuestro código a la rama principal (**master**) y generando una etiqueta de versión (**tag**).

Estos pasos forman parte del flujo de trabajo [git flow](https://nvie.com/posts/a-successful-git-branching-model/). Aunque existen múltiples flujos de trabajo sobre `git`, nosotros utilizaremos git flow en esta documentación.

## Test lab

Prueba a descargar un repositorio alojado en GitHub usando `git` para crear una copia local del repositorio en tu PC

[![asciicast](https://asciinema.org/a/10jPI94JORcOnokmpAJOJgZp6.png)](https://asciinema.org/a/10jPI94JORcOnokmpAJOJgZp6)

Una vez descargado el repositorio como copia local se puede echar un vistazo al código, modificar, añadir cambios y subirlos de nuevo al servidor remoto. Nuestro proyecto está de alguna forma _conectado_ tanto al servidor central en GitHub como a la carpeta de nuestro disco duro que contiene el proyecto.

GitHub es un servicio de alojamiento de repositorios gratuito para proyectos públicos. Podemos utilizarlo para crear nuestros propios repositorios y practicar.

---

Siguiente: [Acciones principales](repositories-main-actions.md) - Ir a la [Página principal](../toc.md)
