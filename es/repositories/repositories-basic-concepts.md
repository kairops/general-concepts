# Repositorios: Conceptos básicos

Existen multitud de tutoriales y guías acerca del uso de git. Uno de los mejores recursos es el libro tutorial [pro-git](https://git-scm.com/book/es/v2). La información que ahí figura es realmente extensa y completa.

Podemos ver un repositorio `git` como una suerte de base de datos de código fuente, donde guardamos cada uno de los cambios que vamos desarrollando en nuestra aplicación. Los cambios se guardan en dicha base de datos (**commit**) con un identificador único en forma de _hash_ que sirve para localizar ese conjunto de cambios y diferenciarlo del resto de cambios que hemos guardado previamente. Cada uno de estos conjuntos de cambios lleva asociado un mensaje donde describimos cuáles son esos cambios.

Resumiendo: si vemos el **repositorio** como una _base de datos_, podemos decir que los **commit** son como _registros de una tabla_. 

Tamibén podemos ver un repositorio git como una _máquina del tiempo_ donde se reflejan los cambios que hemos ido haciendo día tras día en nuestro código fuente.

Por tanto:

- Repositorio: lugar donde guardar el código fuente de nuestra aplicación.
- **commit**: conjunto de cambios que guardamos en el repositorio, identificado con un _hash_ generado automáticamente y descrito por nosotros con un mensaje.

La definición de `git` es _gestor de versiones distribuido_. Por tanto existen mecanismo de distribución de esos **commits** del repositorio desde nuestra copia local hacia los ordenadores de otras personas. Un concepto interesante de los repositorio `git` es que actúan de forma _descentralizada_: no existe la necesidad de que mantener un repositorio central de donde descargar el repositorio y donde todos los desarrolladores de una aplicación dejen sus nuevos cambios. Ahora bien: aunque no sea obligatorio ni prescriptivo, es conveniente disponer de ese lugar central.

Aquí es donde entran en juego servicios como Github, Bitbucket y Gitlab, tres de los servicios de alojamiento de repositorios que actúan como almacén centralizado.

Utilizando ambas herramientas, `git` junto con algún servicio centralizado de repositorios, tenemos cubiertas todas las necesidades respecto al ciclo de vida del código fuente de nuestra aplicación:

- Cuando comenzamos a trabajar en una aplicación nos descargamos (**clone**) el código fuente del servidor central.
- Si estamos trabajando en nuevos cambios (**commits**) nos interesa que estén asegurados (**push**) en el servidor central. Además, esos cambios no deben afectar al resto de desarrolladores, por lo que utilizamos una rama (**feature branch**) para avanzar con nuestro desarrollo, ¡no queremos romper nada!.
- Cuando otro desarrollador ha modificado partes de la aplicación, quizá nos interese descargar esos cambios (**pull** / **fetch**) desde el servidor central hacia nuestra copia local del repositorio.
- Al completar nuestros cambios, queremos que nuestro código se vuelva "oficial" y esté disponible para todo el mundo o para poner en producción, por lo que hacemos una mezcla de nuestro código en la rama principal (**merge**)
- A la hora de poner nuestros cambios en procucción, lo hacemos mediante una rama de liberación (**release branch**) que acabará generando una etiqueta de versión (**tag**)

Esto forma parte del flujo de trabajo [git flow](https://nvie.com/posts/a-successful-git-branching-model/). Aunque existen múltiples flujos de trabajo sobre `git`, nosotros iutilizaremos git flow en esta documentación.

## Test lab

Prueba a descargar un repositorio alojado en Github usando `git` para crear una copia local del repositorio en tu PC

```console
MacBook-Pro-de-Pedro-2:testlab pedro.rodriguez$ git clone https://github.com/sergioortegagomez/red-panda-ci-symfony
Cloning into 'red-panda-ci-symfony'...
remote: Counting objects: 220, done.
remote: Compressing objects: 100% (8/8), done.
remote: Total 220 (delta 2), reused 5 (delta 1), pack-reused 211
Receiving objects: 100% (220/220), 43.77 KiB | 311.00 KiB/s, done.
Resolving deltas: 100% (75/75), done.
MacBook-Pro-de-Pedro-2:testlab pedro.rodriguez$ ls
red-panda-ci-symfony
MacBook-Pro-de-Pedro-2:testlab pedro.rodriguez$ cd red-panda-ci-symfony/
MacBook-Pro-de-Pedro-2:red-panda-ci-symfony pedro.rodriguez$ ls
CHANGELOG.md			bin				nginx				source
Jenkinsfile			ci-scripts			php7-fpm
README.md			docker-compose.yml		sonar-project.properties
MacBook-Pro-de-Pedro-2:red-panda-ci-symfony pedro.rodriguez$ git status
On branch master
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean
```

Una vez descargado el repositorio como copia local se puede echar un vistazo al código, modificar, añadir cambios y subirlos de nuevo al servidor remoto. Nuestro proyecto está de alguna forma _conectada_ tanto al servidor central en Github como a la carpeta de nuestro disco duro que contiene el proyecto.

Github es un servicio de alojamiento de repositorios gratuito para proyectos públicos. Se puede utilizar para crear nuestros propios repositorios y practicar.


## Recursos

- [Git, la guía sencilla](http://rogerdudler.github.io/git-guide/index.es.html)
https://medium.com/@sthefany/primeros-pasos-con-github-7d5e0769158c
- [Guía básica de github para principiantes](https://medium.com/@sthefany/primeros-pasos-con-github-7d5e0769158c)