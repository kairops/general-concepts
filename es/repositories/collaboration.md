# Repositorios: Colaboración

El uso de `git` es se ha vuelto prácticamente obligatorio si estamos hablando de gestión de código fuente en desarrollo de software. Si bien tiene sentido utilizar `git` cuando trabajamos solos, es al trabajar con más gente cuando `git` nos proporciona mecanismos avanzados de colaboración.

Hablemos sobre ramas, mezclas y resolución de conflictos

## Ramas

Actúan como una copia aislada del código, donde podemos efectuar todos los cambios que sean necesarios sin afectar al resto. Es como disponer de una copia en un directorio diferente.

En nuestro repositorio de ejemplo, podemos crear una rama nueva con `git checkout -b ...`

Ejemplos:

- `git checkout -b pruebas origin/master` // Creamos una rama "pruebas" a partir de la rama "master" del repositorio en la copia local de nuestro repositorio
- `git push origin pruebas` // Subimos la nueva rama "pruebas" al servidor remoto

Podemos hascer las mismas pruebas descritas en el [Test Lab de Acciones Principales](repositories-main-actions.md#Test-Lab) sobre la rama "pruebas" recién creada.

Una función adicional de `git checkout` es cambiar de una rama a otra.

Ejemnplos:

- `git checkout develop` // Nos situamos a la rama "develop"
- `git checkout master` // Cambiamos a la rama "master"
- `git checkout pruebas` // Vomvemos a nuestra rama "pruebas" (la rama debe existir en el repositorio)

En cada cambio de rama `git` actualiza los ficheros de nuestra copia de trabajo para dejarlos tal y como se encuentran en esa rama. Si un fichero existe en la rama "pruebas", no existe en la rama "develop" y hacemos un cambio de "pruebas" a "develop", el fichero desaparece. Al volver de la rama "develop" a la rama "pruebas", el fichero vuelve a aparecer.

## Mezclas

Es recomendable hacer nuestras modificaciones al código fuente en nuestra propia rama. Cuando hemos finalizado los cambios, nos llevamos esas modificaciones y toda su historia a la rama principal de desarrollo mediante una mezcla (**merge**).

Aprendiendo desde un ejemplo, el flujo de trabajo típico para un `merge` es el siguiente:

_Tomaremos como ejemplo la rama "pruebas" como nuestra rama de desarrollo y la rama "develop" como el destino donde queremos llevar nuestros cambios_

- Nos aseguramos de que todos los cambios de nuestra rama "pruebas" están subidos al servidor remoto (`git commit...` / `git push ..`). Podemos comprobar el estado de nuestra copia local del repositorio con `git status`.
- Cambiamos a la rama "develop", donde queremos llevar nuestras modificaciones (`git checkout develop`).
- Nos aseguramos que la rama "develop" está sincronizada con los últimos cambios subidos al servidor remoto (`git pull`).
- Hacemos la mezcla de código: nos "traemos" los cambios de nuestra rama "pruebas" (`git merge pruebas`).
- Subimos la rama "develop" actualizada con nuestras modificaciones al servidor remoto (`git push`)

Veremos esto con detalle en el [Test Lab](#Test-Lab).

## Resolución de conflictos


## Test Lab

Vamos a simular el trabajo de dos desarrolladores distintos. Para cada desarrollador vamos a:

- Clonar el repositorio de ejemplo
- Crear una rama nueva
- Hacer modificaciones de un fichero en la rama nueva
- Confirmar los cambios en nuestra copia local y subirlos a remoto
- Llevar nuestros cambios a la rama perincipal de desarrollo "develop" con un `merge`
- Subir esa mezcla de "develop" al servidor remoto

Haremos las modificaciones con ambos usuarios sobre el mismo fichero en el mismo contenido, por tanto vamos a generar un conflicto que resolveremos posteriormente.

