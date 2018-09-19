# Conceptos generales

Recopilación de conceptos generales relacionados con desarrollo de software.

La motivación surge de la necesidad de documentar una aplicación LAMP desarrollada hace años basada en symfony para que en la empresa que la usa tengan un mínimo de documentación sobre el desarrollo y puedan darle soporte y continuidad. En el momento de abordar esto desconocen conceptos que para mí son básicos, como qué es un entorno, cómo usar git, cómo funciona github / bitbucket / gitlab, qué es docker y cómo funciona, etc.

Esta documentación nace para quedar obsoleta: trata sobre una aplicación WEB que en 2018 puede considerarse "legacy" puesto que se comenzó a desarrollar en 2011. Obviando aquellos detalles particulares de la aplicación, comparto el resto por si le resulta útil a alguien.

Como ayuda para elaborar este material se utilizará el proyecto [Red Panda CI symfony](https://github.com/red-panda-ci/red-panda-ci-symfony.git) que en su día hizo [Sergio Ortega Gómez](https://github.com/sergioortegagomez) como prueba de concepto. Gracias, Sergio :)

## Nociones

- [Entornos](environments.md) de ejecución
- [Repositorios](repositories.md): git, Github / Gitlab / Bitbucket
- [Docker](docker.md)
- [Jenkins](jenkins.md)
- [Sonar](sonar.md)

## Repositorios

- [Conceptos básicos](repositories/repositories-basic-concepts.md)
- Acciones principales: clone, add / rm, commit, push, pull
- Colaboración: Branching & merging, resolución de conflictos
- Conceptos de "git flow": master, develop, feature, release, hotfix
- Versionado: Tags

## Uso básico de Docker

- Imágenes
- Containers
- Volúmenes
- Redes
- Compose

## Uso básico de Jenkins

- Jobs
- Builds
- Hooks

## Uso básico de Sonar

TBD

## Conceptos de QA

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
