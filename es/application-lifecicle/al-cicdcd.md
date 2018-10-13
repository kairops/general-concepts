# Ciclo de Vida: CI-CD-CD

Contenido:

- [Introducción](../application-lifecicle.md)
- [Ciclo de vida: Evolución y adaptación](al-evolution-and-adaptation.md)
- **CI-CD-CD**
- [Entregabilidad](al-releaseability.md)
- [Pipeline](al-pipeline.md)
- [Changelog](al-changelog.md)

Se trata de tres conceptos estrechamente relacionados con el _Ciclo de Vida_:

- CI -  _Continuous Integration_ (Integración Continua): Práctica de desarrollo de software en la que los miembros de un equipo integran su trabajo frecuentemente. El objetivo es detectar fallos cuanto antes.

- CD - _Continuous Delivery_ (Entrega Continua): Enfoque en el desarrollo de software por el que se garantiza que los cambios en el código puedan ser desplegados en cualquier momento en el entorno de producción.

- CD - _Continuous Deployment_ (Despliegue Continuo): Proceso automatizado de despliegue de cambios en producción. En general está dirigido por un Pipeline en una serie de pasos o etapas que conducen el código desde que sale del PC del desarrollador hasta que se despliega en el entorno de producción en un único proceso.

Mediante prácticas de _Integración Continua_ mezclamos de manera frecuente nuestros cambios en la rama principal de desarrollo para garantizar que lo que estamos desarrollando es sostenible en la aplicación y que nada deja de funcionar. Esta garantía se certifica con la ejecución de _pruebas_ de diverso tipo: unitarias, funcionales, de integración, de aceptación, de seguridad, de rendimiento, etc.

El concepto de _Entregabilidad_ del software supone aquellas actividades que el equipo del proyecto debe hacer para desarrollar y mantener automatismos que permitan una puesta en producción sin fricciones de la aplicación. Justo aquí tenemos una relación directa con la _Entrega Continua_.

Por último, gracias a los automatismos, si hemos ejercitado bien la _Entregabilidad_ podemos garantizar que los cambios que hemos integrado en la rama principal de desarrollo se pueden poner en producción en cualquier momento de manera confiable, llegando a un grado de madurez en el que aseguremos el _Despliegue Continuo_ de los cambios.

---

Siguiente: [Entregabilidad](al-releaseability.md) - Ir a la [Página principal](../toc.md)
