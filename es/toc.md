# Conceptos generales

Recopilación de conceptos generales relacionados con desarrollo de software.

La motivación es la necesidad de documentar una aplicación LAMP desarrollada hace años basada en symfony para que en la empresa que la utiliza tengan un mínimo de documentación. En el momento de abordar esto desconocen conceptos que para mí son básicos, como qué es un entorno, el uso de git, manejo de gitlab, docker, etc.

Por último, esta información nace para ser obsoleta en una aplicación WEB que en 2018 puede considerarse "legacy" puesto que se comenzó a desarrollar en 2011. Obviando aquellos detalles particulares de la aplicación, comparto el resto por si le puede resultar útil a alguien.

Como ayuda para elaborar este material se utilizará el proyecto [Red Panda CI symfony](ttps://github.com/red-panda-ci/red-panda-ci-symfony.git)

## Nociones

- [Entornos de ejecución](environments.md)
- Jenkins
- Github / Gitlab / Bitbucket

## Uso básico de git

- Repositorio
- Conceptos básicos: commit, push, pull
- Branching & merging
- Resolución de conflictos
- Git flow: master, develop, features, releases, hotfixes
- Tags

## Uso básico de docker

- Imágenes
- Containers
- Volúmenes
- Redes
- Compose

## QA

- Calidad
- BDD
- Ejecución local de pruebas
- Sonarqube

## Ciclo de vida

- Configuración y puesta en marcha de entorno local
- Pipeline: Develop, Testing, Release, Deploy
- Entregabilidad: CI-CD-CD
- Etiquetas y versionado semántico
- Changelog
