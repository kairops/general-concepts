# Ciclo de vida: Pipeline

Es el proceso definido para gestionar todas las actividades que suceden desde que cambiamos una línea de cóodigo en nuestra aplicación hasta que esos cambios se despliegan en un entorno de producción. 

## Ramas

Desde el punto de vista del repositorio de código y sus ramas, los cambios que realizamos en el código fuente de la aplicación siguen una ruta de promoción _hacia produccion_, "viajando" desde nuestra rama de característica como punto de partida (feature branch), donde trabajamos de manera aislada, y realizando distintas pruebas como test unitarios, de integración, de seguridad o de rendimineto por el camino. Puede haber etapas donde nuestro código se someta a una revisión por una persona o un comité antes de integrarse en otra rama. 

Un escenario típico es avanzar el desarrollo en "feature branches" (feature/*) y realizar peticiones de integración (pull requests / merge requests) hacia la rama principal de desarrollo, generalmente denominada "develop". En este caso la rama "develop" no debe ser una rama de trabajo, sino una rama de integración y promoción de cambios hacia otras ramas, generalmente "master".

(TBR) (TBC)