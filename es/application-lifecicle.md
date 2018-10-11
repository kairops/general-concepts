# Ciclo de vida

## Definición 

Conjunto de actividades, técnicas, tácticas, servicios, procesos y herramientas relacionadas con la creación y explotación de una aplicación en todos sus aspectos. Sabemos que el _desarrollo_ supone la actividad principal, pero no es la única actividad. Cuanto más entidad tiene el proyecto software en el que estamos inmersos, más personas trabajan en él y más importancia tiene el concepto _Ciclo de Vida_.

Podemos extender el _Ciclo de Vida_ a otras actividades más allá de la puesta en producción del software, añadiendo métricas y alarmas en el entorno de producción, con _feedback loops_ que derivan en tareas de mantenimiento, soporte o características nuevas y que suponen modificaciones del código fuente que nos llevan [al punto de partida](#ciclo-de-vida).

Lo más habitual es encontrar el concepto de _Ciclo de Vida_ asociado a una serie de pasos ejecutados en orden: análisis, diseño, desarrollo, pruebas, integración, despliegue. O quizá a un proceso interativo e incremental que se repite una y otra vez en el tiempo. Bajo cierto punto de vista, si utilizamos servicios, por ejemplo una herramienta de orquestación como pueda ser Jenkins, su instalación, configuración, despliegue, mantenimiento y operación también forma parte del _Ciclo de Vida_, al igual que el resto de herramientas, servicios, actividades, técnicas, tácticas y procesos.

## Ciclo de vida como evolución

Es posible trabajar en un proyecto unipersonal y desarrollar el software editando el código directamente en el servidor. En este caso _Ciclo de Vida_ supone acceder al servidor y editar el código. Seguramente hubo actividades previas como configurar el servidor instalando lo necesario: servicio web, base de datosm, etc. Tal vez tengamos el servicio web y el de base de datos en nuestro PC, junto con algún IDE, para desarrollar y probar las cosas antes de subirlas al servidor.

Todas esas actividades formarán parte de nuestro _Ciclo de Vida_:

 - Instalr y configurar las herramientas de desarrollo y los servicios en nuestro PC
 - Instalar y configurar los servicios en el servidor
 - Desarrollar y probar en nuestro PC
 - Acceder al servidor para subir código o editar código existente

A medida que la aplicación y el equipo de desarrollo del proyecto crecen vamos a incorporar lo necesario para que nuestros "entregables" tengan la máxima calidad posible: herramientas de gestión y seguimiento de tareas, entornos de desarrollo / pruebas / preproducción / producción, herramientas de control de código fuente, tests unitarios, test funcionales, servicios de alojamiento de código, servicios de integración continua con procesos de promoción del código, y un largo etcétera.

## Ciclo de vida como adaptación

El _Ciclo de Vida_ de cada aplicación puede ser diferente adaptándose a la complejidad de cada contexto. Dentro de una misma aplicación pueden coexistir variantes del _Ciclo de Vida_ para acomodar distintos componentes. Podría darse el caso de una aplicación formada por dos componentes, uno para los usuarios y otro para los administradores del sistema, en los que estén involucrados dos equipos de desarrollo direrentes.

## CI-CD-CD

Se trata de tres conceptos estrechamente relacionados con el _Ciclo de Vida_ que nos vamos a encntrar tarde o temprano en desarrollo de software.

- CI -  _Continuous Integration_ (Integración Continua): Práctica de desarrollo de software en la que los miembros de un equipo integran su trabajo frecuentemente. El objetivo es detectar fallos cuanto antes.

- CD - _Continuous Delivery_ (Entrega Continua): Enfoque en el desarrollo de software por el que se garantiza que el software pueda ser liberado en cualquier momento.

- CD - _Continuous Deployment_ (Despliegue Continuo): Proceso automatizado de despliegue de cambios en producción. En general está dirigido por un Pipeline en una serie de pasos o etapas que llevan nuestros cambios desde el PC del desarrollador hasta el servidor de producción en un único proceso.

El concepto de _Entregabilidad_ del software supone aquellas actividades que el equipo del proyecto debe hacer para desarrollar y mantener automatismos que permitan el Despliegue Continuo de la aplicación en el entorno de producción. La _Entrega Continua_ se refiere concretamente este punto.

Gracias a estos automatismos, si tenemnos un grado alto de _Entregabilidad_ podemos garantizar que el despliegue de nuestros cambios se puede hacer en cualquier momento de manera confiable.

Mediante prácticas de _Integración Continua_ mezclamos de manera frecuente nuestros cambios en la rama principal de desarrollo para garantizar que lo que estamos desarrollando es sostenible en la aplicación, que nada deja de funcionar. Esta garantía se certifica con la ejecución de _pruebas_ de diverso tipo: unitarias, funcionales, de integración, de aceptación, de seguridad, de rendimiento, etc.

## Modelo de ejemplo

Trataremos un _Ciclo de Vida_ "tipo" definiendo:

- Configuración y puesta en marcha del [entorno local](application-lifecicle/al-local-environment.md) (ver [entornos](environments.md))
- [Entregabilidad]((application-lifecicle/al-releaseability.md))
- [Pipeline](application-lifecicle/al-pipeline.md): Develop, Build, Test, Deploy, Release
- Etiquetas y versionado semántico
- Changelog
