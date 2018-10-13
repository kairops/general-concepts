# Ciclo de vida: Entregabilidad

Contenido:

- [Definición](../application-lifecicle#definición)
- [Ciclo de vida como evolución](../application-lifecicle##ciclo-de-vida-como-evolución)
- [Ciclo de vida como adaptación](../application-lifecicle##ciclo-de-vida-como-adaptación)
- [CI-CD-CD](../application-lifecicle##ci-cd-cd)
- **Entregabilidad**
- [Pipeline](application-lifecicle/al-pipeline.md): Develop, Build, Test, Deploy, Release
- [Etiquetas y versionado semántico](application-lifecicle/al-semver.md)
- [Changelog](application-lifecicle/al-changelog.md)

Una actividad muy importante en cualquier aplicación es la entrega, el despliegue o la puesta en producción. Creamos software para ser entregado de alguna forma.

Nos sirve de muy poco un desarrollo que funciona en la máquina del desarrollador (Eh! En mi local funciona). El software es evolución y adaptación, las características nuevas pueden suponer cambios en las configuraciones del servidor; supone un riesgo trabajar con una receta de puesta en producción obsoleta, con pasos que no hayamos ejercitado nunca.

Se hace necesario pues trabajar en la _Entregabilidad_ de nuestra aplicación. Lo habíamos definido como "aquellas actividades que el equipo del proyecto debe hacer para desarrollar y mantener automatismos que permitan el Despliegue Continuo de la aplicación en el entorno de producción".

El equipo del proyecto hace desarrollos que suponen cambios en la aplicación. Estos desarrollos se realizan en ramas de características (_feature branches_). A medida que se avanza en el desarrollo todos los esfuerzos se dirigen a que los cambios resuelvan lo que esté previsto deban resolver, a la vez que se mantiene el funcionamiento del resto de la aplicación. Es decir, que no "se rompe" nada.

Una vez que los cambios están listos, se llevan a la rama principal de desarrollo. El equipo del proyecto debe garantizar que esos cambios son _potencialmente entregables_, que se van a poder desplegar en el entorno de producción en cualquier momento, revisando y modificando, si es necesario, los procesos y _scripts_ de despliegue. Estos automatismos son al fin y al cabo software, código fuente que ha pasado por ciclos de desarrollo y pruebas.

La _Entregabilidad_ del software supone que los automatismos se han revisado y se han probado con los nuevos cambios. Las pruebas que se han realizado fuera del entorno de producción garantizan que en el momento del despliegue todo irá bien.

Haciendo iteraciones cortas y aumentando la frecuencia de entregas tendremos una _Entregabilidad_ más confiable, porque habremos ejecutado más veces los automatismos de despliegue. Si pasa demasiado tiempo entre relases, esa garantía y esa confianza es menor.

---

Siguiente: [Pipeline](application-lifecicle/al-pipeline.md) - Ir a la [Página principal](../toc.md)
