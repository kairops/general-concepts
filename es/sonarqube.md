# SonarQube

Con Sonar disponemos de un servicio de inspección contínua de código. Sonar realiza análisis estático del código fuente de nuesgtro proyecto en busca de no conformidades, revisando indicadores de complejidad ciclomática, errores de seguridad (poner una password en claro), o "CodeSmells" (código "apestoso", literalmente). Se basa en motores de reglas para diferentes lenguajes, como JAVA, PHP, Python o C#, y está disponible de forma gratuita.

Para cada no conformidad creará una incidencia en su sistema de gestión indicando de forma detallada cuál es el problema y cuáles las recomendaciones

## Testlab

Podemos efectuar un análisis con Sonarqube usando Docker sin necesidad de disponer de un servicio alojado siguiendo las indicaciones de este proyecto

<https://github.com/newtmitch/docker-sonar-scanner>

1. Levantamos servicio de Sonar dockerizado

```console
docker run -d --name sonarqube -p 9000:9000 -p 9092:9092 sonarqube
```

2. Esperamos que el servicio de sonar esté disponible en esta url <http://localhost:9000>

3. Ejecutamos el análisis

```console
docker run -ti -v $(pwd):/root/src --link sonarqube newtmitch/sonar-scanner
```

Una vez finalizado el proceso análisis, tendremos disponible el proyecto y sus métricas en <http://localhost:9000/dashboard?id=MyProjectKey>. También se creará el directorio `.scannerwork` en el raíz de nuestro repositorio. Se puede (y se debe) borrar este directorio tras el análisis.

Si disponemos de un sistema OS/X o Windos el análisis puede tardar demasiado. Podemos acelerar el proceso ejecutando el análisis de esta forma:

```console
docker run --rm -ti -v $(pwd):/tmp/src:cached --link sonarqube newtmitch/sonar-scanner bash -c "cp -rp /tmp/src/ /root/src; sonar-scanner -Dsonar.projectBaseDir=/root/src"
```

## Recursos adicionales

- [Página principal de Sonarqube](https://www.sonarqube.org/)
- [Docker Sonar Scanner](https://github.com/newtmitch/docker-sonar-scanner)
- [ERP de Pharmadux (Odoo)](https://github.com/informaticaph/PXGO_00064_2014_PHA)

---

Siguiente: [QA](qa.md) - Ir a la [Página principal](toc.md)
