# Ciclo de vida: Pipeline

Contenido:

- [Introducción](../application-lifecicle.md)
- [Ciclo de vida: Evolución y adaptación](al-evolution-and-adaptation.md)
- [CI-CD-CD](al-cicdcd.md)
- [Entregabilidad](al-releaseability.md)
- **Pipeline**
- [Etiquetas y versionado semántico](al-semver.md)
- [Changelog](al-changelog.md)

Es el proceso definido para gestionar todas las actividades que suceden desde que cambiamos una línea de cóodigo en nuestra aplicación hasta que esos cambios se despliegan en un entorno de producción. Consta de una serie de pasos o etapas, como pueden ser construcción, pruebas, release y despliegue en distintos entornos.

Desde el punto de vista del [repositorio de código](../repositories.md) y sus ramas, los cambios que realizamos en el código fuente de la aplicación siguen una ruta de promoción _hacia produccion_, "viajando" desde nuestra rama de característica (feature branch) como punto de partida, donde trabajamos de manera aislada, y realizando distintas pruebas como test unitarios, de integración, de seguridad o de rendimineto por el camino. Puede haber etapas donde nuestro código se someta a una revisión por una persona o un comité antes de integrarse en otra rama.

Un modelo de trabajo típoco es el "Git Feature Branch Workflow", donde se trabaja en ramas aisladas y realizan peticiones de integración (pull requests / merge requests) hacia la rama principal de desarrollo, generalmente denominada "develop". En este caso la rama "develop" no debe ser una rama de trabajo, sino una rama de integración y promoción de cambios hacia otras ramas, generalmente "master".

El mantenimiento del Pipeline en una aplicación es responsabilidad de todo equipo de proyecto.

Ejemplos:

![Ejemplo de Pipeline](img/realworld-pipeline-flow.png?raw=true "Ejemplo de Pipeline")

![Ejemplo de Pipeline con Jenkins](img/jenkins-pipeline-example.png?raw=true "Ejemplo de Pipeline con Jemnkins")

## Referencias

- [Jenkins Pipeline](https://jenkins.io/doc/book/pipeline/)
- [Git Feature Branch Workflow](https://www.atlassian.com/git/tutorials/comparing-workflows/feature-branch-workflow)

---

Siguiente: [Etiquetas y versionado semántio](al-semver.md) - Ir a la [Página principal](../toc.md)
