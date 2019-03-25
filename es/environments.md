# Entornos de ejecución

Contenido:

- [Definición](#definición)
- [Categorías](#categorías)
- [Microservicios](#microservicios)

## Definición

Conjunto completo de elementos que habilita la ejecución de una aplicación.

Como "elemento" tendremos un servicio, como el servicio web proporcionado por Apache / Nginx, un motor de base de datos como mysql, un certificado HTTPS, un nombre de dominio, un almacenamiento donde guardar imágenes subidas por el usuario... virtualmente podría tratarse de _cualquier cosa que ayude a que nuestra aplicación funcione_.

## Categorías

Podemos disponer de varios entornos de ejecución, cada uno destinado a un propósito distinto. Respecto a los _elementos_ de un entorno, deben ser equivalentes. La potencia de un entorno local es distinta a la potencia de un entorno de producción, aunque los servicios ofrecidos y desplegados deben ser del mismo tipo (no necesariamente en el mismo número).

Ejemplo: balanceo de carga y servicio WEB. El entorno local de desarrollo dispondrá de un balanceador y dos elementos que dan servicio WEB (por ejemplo, dos nginx), y en el entorno de producción tendremos un "balanceador como servicio" (podría ser un ELB, o un balanceador hardware como un F5) y un servicio WEB formado por decenas o cientos de instancias con Nginx.

Algunas categorías de entornos típicas:

- Entorno local de desarrollo. Destinado a ejecutarse en el PC de un desarrollador.
- Entorno de integración. Compartido por todos los miembros del equipo, destinado a pruebas de integración.
- Entorno de validación / calidad / pruebas. Aquel en el que ejecutamos test de aceptación (BDD), pruebas de carga, pruebas de seguridad, etc.
- Entorno de preproducción. El más cercano al entorno de producción, en cuanto a diversidad y número de elementos de los servicios. Aquí ejercitamos la [entregabilidad](application-lifecicle/al-releasability.md) de nuestra aplicación.
- Entorno de producción. No es necesario añadir mucho más: go live!

## Microservicios

...y arquitectura hexagonal, kubernetes, entornos efímeros provisionados por feature branch. Queda pendiente de contar para cuando haya algo interesante que decir :)

---

Siguiente: [Repositorios](repositories.md) - Ir a la [Página principal](toc.md)
