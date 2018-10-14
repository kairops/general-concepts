# Entornos de ejecución

Contenido:

- [Definición](#definición)
- [Categorías](#categorías))
- [Microservicios](#microservicios)

## Definición

Conjunto completo de elementos que habilita la ejecución de una aplicación.

Como "elemento" podemos ubicar un servicio, como el servicio web proporcionado por apache o nginx, un motor de base de datos como podría ser mysql, un certificado HTTPS, un nombre de dominio, el almacenamiento donde guardamos los archivos subidos por el usuario... virtualmente podría tratarse de cualquier cosa que ayude a que nuestra aplicación funcione.

## Categorías

Podemos disponer de varios entornos de ejecución, cada uno destinado a un propósito distinto. Respecto a los elementos de un entorno, deben ser equivalentes. La potencia de un entorno local es distinta a la potencia de un entorno de producción, aunque los servicios ofrecidos y desplegados deben ser del mismo tipo (no necesariamente en el mismo número).

Ejemplo: balanceo de carga y servicio WEB. El entorno de desarrollo dispondrá de un balanceador y dos elementos que dan servicio WEB (por ejemplo, dos nginx), y en el entorno de producción tendremos un "balanceador como servicio" (podría ser un ELB, o un balanceador hardware como un F5) y un servicio WEB formado por decenas o cientos de instancias con NGINX.

Algunas categorías de entornos típicas:
 
- Entorno local. Destinado a ejecutarse en el PC de un desarrollador.
- Entorno de integración. Compartido por todos los miembros del equipo, destinado a pruebas de integración.
- Entorno de validación / calidad / pruebas. Aquel en el que ejecutamos test de aceptación (BDD), de carga, de seguridad, etc.
- Entorno de preprocucción. El más cercano al entorno de producción, en cuanto a diversidad y número de elementos de los servicios. Aquí ejercitamos la entregabilidad de nuestra aplicación.
- Entorno de producción. No es necesario añadir mucho más: go live!

## Microservicios

...y arquitectura hexagonal, kubernetes, entornos efímeros provisionados por feature branch. Queda pendiente de contar para cuando haya algo interesante que decir :)
