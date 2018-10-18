# Jenkins: Builds

Contenido:

- [Introducción](../jenkins.md)
- [Jobs](jenkins-jobs.md)
- **Builds**
- [Hooks](jenkins-hooks.md)

Llamamos `build` a la ejecución de un `job`. Un `job` tendrá muchos `builds` a lo largo del tiempo. Jenkins conserva los registros (logs) de ejecución de los `builds`.

    _Nota: no confundir el término `build` que han utilizado los desarrolladores de Jenkins para denominar a la ejecución de un job, con "build" referido a una "construcción" dentro de un proyecto software_

Vamos a seguro con el ejemplo de [Jobs](jenkins-jobs.md) en nuestro "Test Lab"


## Test Lab

Vamos con el navegador a la página del job en https://localhost:10080/job/prueba/

![Jenkins - Job listo](img/jenkins-job-ready.png?raw=true "Jenkins - Job listo")

Previamente tenemos que haber accedido a Jenkins con el usuario "redpanda", tal y como se describe en la anterior sección de Jobs.

Lo único que tenemos que hacer es pulsar sobre "Construir ahora"

![Jenkins - Construyendo](img/jenkins-building.png?raw=true "Jenkins - Construyendo")

Una vez ha finalizado el job, la página tendrá este aspecto

![Jenkins - Construcción finalizada](img/jenkins-build-finished.png?raw=true "Jenkins - Construcción finalizada")

Podemos ejecutar el job tantas veces como sea necesario

![Jenkins - Construyendo de nuevo](img/jenkins-building-secondtry.png?raw=true "Jenkins - Construyendo de nuevo")

Después de la segunda ejecución vemos ambos builds

![Jenkins - Segunda construcción finalizada](img/jenkins-build-finished-secondtry.png?raw=true "Jenkins - Segunda construcción finalizada")

Podemos acceder al registro (log) de cualquiera de los `builds`, por ejemplo del segundo http://jenkins-redpanda:10080/job/prueba/2/console

![Jenkins - Registro](img/jenkins-build-log.png?raw=true "Jenkins - Registro")

En los logs podemos ver trazas de cómo se descarga el repositorio y se muestra el contenido del archivo README.md.

Por último, tenemos una visión más clara de los pasos que ejecuta el `build` pulsando sobre "Open Blue Ocean" a la izquierda

![Jenkins - Blue Ocean](img/jenkins-blue-ocean-overview.png?raw=true "Jenkins - Blue Ocean")

... y pulsando sobre uno de los `builds`

![Jenkins - Blue Ocean, build detallado](img/jenkins-blue-ocean-build-details.png?raw=true "Jenkins - Blue Ocean, build detallado")

---

Siguiente: [Hooks](jenkins-hooks.md) - Ir a la [Página principal](../toc.md)
