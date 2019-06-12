# Ciclo de vida: Changelog

Contenido:

- [Introducción](../application-lifecicle.md)
- [Ciclo de vida: Evolución y adaptación](al-evolution-and-adaptation.md)
- [CI-CD-CD](al-cicdcd.md)
- [Entregabilidad](al-releasability.md)
- [Pipeline](al-pipeline.md): Develop, Build, Test, Deploy, Release
- **Changelog**

Es importante que mantengamos en nuestro proyecto un log de cambios, o Changelog, lo más preciso posible, que recoja la información de cambios para cada una de las versiones que vayamos liberando de nuestro proyecto. La motivación para elaborar un Changelog la tenemos en el proyecto [keep a changelog](https://keepachangelog.com/en/1.0.0/)

Como ejemplo, podemos tomar el [Changelog de este proyecto](https://github.com/kairops/general-concepts/blob/master/CHANGELOG.md). Se aprecia la estructura simple con el nombre de cada release, la fecha y los cambios en detalle, agrupados por categorías. Cada cambio tiene un enlace hacia el `commit` del repositorio correspondiente.

Conseguir un Changelog como este es tan sencillo como seguir reglas sencillas a la hora de escribir los mensajes de commit de nuestro proyecto. Como ejemplo, la versión v0.4.0 de nuestro proyecto figura así en el archivo de Changelog

```markdown
## v0.4.0 (2018-09-27)

### New

* Add QA page [ES] ([7b13494](https://github.com:kairops/general-concepts/commit/7b13494))

### Update

* Add navitation links to QA page [ES] ([48544ee](https://github.com:kairops/general-concepts/commit/48544ee))

### Build

* Update CHANGELOG.md to v0.4.0 with Red Panda JPL ([6a6a122](https://github.com:kairops/general-concepts/commit/6a6a122))
```

Si echamos un vistazo a los mensajes de commit de esa versión en nuestro repositorio tenemos lo siguiente:

```console
$ git log v0.3.0..v0.4.0 --no-merges --oneline
6a6a122 (tag: v0.4.0) Build: Update CHANGELOG.md to v0.4.0 with Red Panda JPL
48544ee Update: Add navitation links to QA page [ES]
7b13494 New: Add QA page [ES]
```

El mensaje de commit "New: Add QA Page [ES]" lleva a una entrada en el changelog con el mismo texto, dentro de la sección "New" y con un enlace al commit.

En el proyecto [Docker Command: GIT Chagnelog Generator](https://github.com/kairops/dc-git-changelog-generator) tenemos una implementación en bash script de un generador automático de changelog basado en los mensajes de commit de un repositorio.

## Recursos adicionales

- [keep a changelog](https://keepachangelog.com/en/1.0.0/)
- [Docker Command: GIT Changelog Generator](https://github.com/kairops/dc-git-changelog-generator)

---

Ir a la [Página principal](../toc.md)
