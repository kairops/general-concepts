# Ciclo de Vida: Evolución y adaptación

Contenido:

- [Introducción](../application-lifecicle.md)
- **Ciclo de vida: Evolución y adaptación**
- [CI-CD-CD](al-cicdcd.md)
- [Entregabilidad](al-releaseability.md)
- [Pipeline](al-pipeline.md): Develop, Build, Test, Deploy, Release
- [Etiquetas y versionado semántico](al-semver.md)
- [Changelog](al-changelog.md)

## Ciclo de vida como evolución

Es posible trabajar en un proyecto unipersonal y desarrollar el software editando el código directamente en el servidor de proucción. En este caso _Ciclo de Vida_ supone acceder al servidor y editar el código. Seguramente hubo actividades previas tales como configurar el servidor instalando lo necesario: servicio web, base de datosm, etc. Tal vez tengamos el servicio web y el de base de datos en nuestro PC, junto con algún IDE, para desarrollar y probar nuestros cambios antes de su despliegue en el servidor.

Todas esas actividades formarán parte de nuestro _Ciclo de Vida_:

 - Instalar y configurar las herramientas de desarrollo y los servicios en nuestro PC
 - Instalar y configurar los servicios en el servidor
 - Desarrollar y probar los cambios en nuestro PC
 - Acceder al servidor para subir el código nuevo

A medida que la aplicación y el equipo de desarrollo del proyecto crecen vamos a incorporar lo necesario para que nuestros "entregables" tengan la máxima calidad posible: herramientas de gestión y seguimiento de tareas, entornos de desarrollo / pruebas / preproducción / producción, herramientas de control de código fuente, tests unitarios, test funcionales, servicios de alojamiento de código, servicios de integración continua con procesos de promoción del código, y un largo etcétera.

## Ciclo de vida como adaptación

El _Ciclo de Vida_ de cada aplicación se puede adaptar a la complejidad de cada contexto. Dentro de una misma aplicación pueden coexistir variantes del _Ciclo de Vida_ para acomodar distintos componentes. Podría darse el caso de una aplicación formada por dos componentes, los administradores del servicio y otro para los usuarios finales, en los que estén involucrados dos equipos de desarrollo direrentes.

---

Siguiente: [CI-CD-CD](al-cicdcd.md) - Ir a la [Página principal](../toc.md)
