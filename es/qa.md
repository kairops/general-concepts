# Calidad

Contenido:

- [Añadir Calidad a un proyecto existente](#añadir-calidad-a-un-proyecto-existente)
- [Recursos adicionales](#recursos-adicionales)

## Añadir Calidad a un proyecto existente

El desarrollo de software es un proceso muy complejo, con muchas variantes y aristas. Podemos enmarcar el proceso de desarrollo como un hito dentro de una serie de acontecimientos que llevan a un "entregable":

![QA - Sin testing](img/qa-step1.png?raw=true "QA - Sin testing")

Si la intención es dotar a los proyectos de "Procesos de QA", la opción más lógica parece hacer un proceso de QA al finalizar el desarrollo, justo antes del "delivery":

![QA - Testing al final](img/qa-step2.png?raw=true "QA - Testing al final")

Ese proceso de QA consiste en revisar el entregable ejecutando una por una las pruebas que estén definidas y contrastando el "Resultado obtenido" con el "Resultado esperado". En el caso de que el entregable sea una aplicación, las pruebas que pasamos estarán definidas en un "Test Case Document".

Dicho "Test Case Document" es una recopilación de los Criterios de Aceptación, aquellas "Cosas que debe cumplir" cada una de las funcionalidades que se desarrollan. Ejemplo: si tenemos una pantalla de login, un Criterio de Aceptación válido podría ser rellenar el usuario con "nombre", la contraseña con "password", pulsar en "login" y verificar que llegamos a la zona privada del usuario, comprobando que aparece el texto "Conectado como nombre".

¿De donde salen los Criterios de Aceptación? Se definen tomando cada una de las funcionalidades a desarrollar y acordando, antes de comenzar el desarrollo, con qué pruebas concretas podremos verificar que lo desarrollado cumplirá con los requisitos. Dicho esto, definimos que el "Proceso de QA" en realidad consiste en recoger esos Criterios de Aceptación en el momento de definición de requisitos, con objeto de comprobar que éstos se cumplen una vez finalizado el desarrollo:

![QA - Criterios de Aceptación](img/qa-step3.png?raw=true "QA - Criterios de Aceptación")

Se puede tener la percepción de que incorporar procesos de QA al proyecto puede suponer retrasos en las entregas. Podemos adelantar los procesos de testing a "tiempo de desarrollo", verificando de forma temprana el cumplimiento de los Criterios de Aceptación en la medida que el desarrollo avanza:

![QA - Test case individual](img/qa-step4.png?raw=true "QA - Test case individual")

Cada una de las tareas que tiene definidos Criterios de Aceptación se podría comprobar inmediatamente después de que finalice su desarrollo. El objetivo es adelantar lo máximo posible la detección de las "no conformidades", sin tener que esperar a que estén finalizadas el 100% de las tareas de un entregable concreto. Sigue siendo necesario ejecutar un ciclo completo de "Test case" antes de la entrega. Adelantar las tareas de QA a tiempo de desarrollo nos ayuda a reducir al máximo las no conformidades detectadas durante la ejecución de este "Test case" completo previo a la entrega.

Son necesarias algunas cosas, muy pocas en realidad, para que este proceso de "Testing Continuo" pueda llevarse a cabo de forma ágil en tiempo de desarrollo:

- Disponer de un juego de datos iniciales predefinido. Las pruebas se basan en "tenemos A", "hacemos B", "obtenemos C", existe una dependencia A => B => C.
- Disponer de un mecanismo de carga para esos datos iniciales (el juego de datos iniciales, o las "A"-es del punto anterior) que se pueda ejecutar a discreción desde el equipo de QA.
- Disponer de un entorno en exclusiva donde poder ejecución las pruebas.
- Tener automatizado el delivery ("build & release" de aplicación o "build & deploy" de backend / frontend / infraestructura).

Una vez hecha la entrega surge la pregunta de: ¿está todo bien? Desde QA se puede disipar esa incertidumbre ejecutando un nuevo "set" de pruebas, previamente definido y acordado, que nos permita certificar que todo es correcto, y que denominamos "Sanity Test"

![QA - Sanity test](img/qa-step5.png?raw=true "QA - Sanity test")

Dentro de estos flujos de tareas que hemos definido se pueden implementar automatizaciones, evolucionando hacia integración continua, testing continuo y entrega continua como parte de procesos de desarrollo ágil. Eso será otra historia.

Como conclusión: Es posible incorporar procesos de QA a cualquier proyecto que esté ya en marcha, con el enfoque más adecuado para aumentar la percepción de Calidad de los entregables, sin que sea visto por los involucrados en el proyecto como algo que supone retraso en las entregas.

## Recursos adicionales

- [Calidad e Integración Continua. Una introducción](https://github.com/carlescliment/sinatra-personal-webpage/blob/master/_publications/calidad-e-integracion-continua-enero-2012.md) _by Carles Climent Granell_

---

Siguiente: [Jobs](application-lifecicle.md) - Ir a la [Página principal](toc.md)
