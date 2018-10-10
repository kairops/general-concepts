# Ciclo de vida

Vamos a definir _Ciclo de vida_ del software como las actividades, técnicas, tácticas, servicios, procesos y herramientas relacionadas con la creación y explotación de una aplicación en todos sus aspectos. Sabemos que el _desarrollo_ supone la actividad principal, pero no es la única actividad. Cuanto más entidad tiene el proyecto software en el que estamos inmersos, más personas trabajan en él y más importancia tiene el concepto _Ciclo de Vida_.

Podemos extender el _Ciclo de Vida_ a otras actividades más allá de la puesta en producción del software, añadiendo métricas y alarmas en el entorno de producción, con _feedback loops_ que derivan en tareas de mantenimiento, soporte o características nuevas y que suponen modificaciones del código fuente que nos llevan [al punto de partida](#ciclo-de-vida).

Lo más habitual es encontrar el concepto de _Ciclo de Vida_ asociado a una serie de pasos ejecutados en orden análisis, diseño, desarrollo, pruebas, integración, despliegue, quizá a un proceso interativo e incremental que se repite una y otra vez en el tiempo. Bajo cierto punto de vista, si es necesario disponer de una herramienta de orquestación tipo Jenkins, su instalación, configruación, despliegue y mantenimiento también forma parte del _Ciclo de Vida_, al igual que el resto de herramientas, servicios, actividades, técnicas, tácticas y procesos.

Es posible trabajar en un proyecto unipersonal y desarrollar el software editandol el código directamente en el servidor. En este caso _Ciclo de Vida_ supone acceder al servidor, editar el código, y listo. Seguramente hubo actividades previas como configurar el servidor instalando lo necesario: servicio web, base de datosm, etc. Aunque no hayamos prestado demasiada atención, nuestro _Ciclo de Vida_ incluye esas tareas.

A medida que la aplicación y el equipo de desarrollo del proyecto crecen vamos a incorporar lo necesario para que nuestros "entregables" tengan la máxima calidad posible: herramientas de gestión de tareas e incidencias, entornos de desarrollo / pruebas / preproducción / producción, herramientas de control de código fuente, tests unitarios, test funcionales, servicios de alojamiento de código, servicios de integración continua con procesos de promoción del código, y un largo etcétera.

El _Ciclo de Vida_ de cada aplicación puede ser diferente adaptándose a la complejidad de cada contexto. Dentro de una misma aplicación pueden coexistir variantes en su _Ciclo de Vida_ para acomodar distintos componentes. Podría darse el caso de una aplicación formada por dos componentes, uno para los usuarios y otro para los administradores del sistema, en los que estén involucrados dos equipos de desarrollo direrentes.

Trataremos un _Ciclo de Vida_ "tipo" definiendo:

- Configuración y puesta en marcha del [entorno local](application-lifecicle/al-local-environment.md) (ver [entornos](environments.md))
- [Pipeline](application-lifecicle/al-pipeline.md): Develop, Build, Test, Deploy, Release
- [Entregabilidad]((application-lifecicle/al-releaseability.md))
- Etiquetas y versionado semántico
- Changelog
