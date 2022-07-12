# Acuerdos de trabajo

Un acuerdo de trabajo es un documento, o un conjunto de documentos que describen cómo trabajamos juntos como equipo y cuáles son nuestras expectativas y principios.
El acuerdo de trabajo lo crea el equipo al principio del proyecto y se guarda en el repositorio para que esté disponible para todos los que trabajan en el proyecto.
Los siguientes son ejemplos de secciones y puntos que pueden formar parte de un acuerdo de trabajo, pero cada equipo debe componer el suyo propio y ajustar los tiempos, los canales de comunicación, las políticas de nomenclatura de las ramas, etc., a las necesidades de su equipo.

## General

* Trabajamos como un solo equipo hacia un objetivo común y un alcance claro
* Nos aseguramos de que la voz de todos sea escuchada y atendida
* Mostramos a todos los miembros del equipo el mismo respeto
* Trabajamos como un equipo para tener expectativas comunes de entrega técnica que se documentan en un [Manifiesto del Equipo](./team-manifesto.md).
* Nos aseguramos de repartir nuestra experiencia y habilidades en el equipo, de modo que no se dependa de una sola persona para una sola habilidad

## Comunicación

* Comunicamos toda la información relevante para el equipo a través del canal de Teams del proyecto
* Añadimos todos los spikes técnicos, estudios comerciales y otra documentación técnica al repositorio del proyecto a través de revisiones de diseño asíncronas en los PRs

## Calidad y no cantidad

* Acordamos una [Definición de Hecho](./definition-of-done.md) para nuestras historias de usuario y sprints y nos regimos por ella.
* Seguimos las mejores prácticas de ingeniería, como el [CoE Engineering Playbook](../../../index.md)

## Ritmo Scrum

Actividad | Cuándo | Duración | Quién | Responsable | Objetivo
---------|----------|---------|---------|---------|---------
 Daily | Mar-Vie 9:30AM | 15 min | Todos | Scrum Master | Lo que se ha logrado, los próximos pasos, los bloqueos
 Demo | Lunes 9:30AM | 1 hora | Todos | Líder del desarrollo | Presentar el trabajo realizado y dar por finalizada de la historia de usuario
 Retro | Lunes 10:30AM | 1 hora | Todos | Scrum Master | Equipos de Desarrollo comparten aprendizajes y lo que se puede mejorar
 Planning | Lunes 11:30AM | 1 hora | Todos | PO | Dimensionar y planificar las historias de usuario para el sprint
 Creación de tareas | después de la planning | - | Todos | Equipo de desarrollo | Crea tareas para aclarar y determinar la velocidad
 Refinamiento del backlog | Miércoles 2PM | 1 hora | Líder del desarrollo, PO | PO | Preparar el siguiente sprint y asegurar que las historias estén listas para el siguiente sprint

## Scrum Master / Líder de proceso

El Líder de Proceso es responsable de liderar cualquier práctica de scrum o ágil para permitir que el proyecto avance.

* Facilitar las dailys y responsabilizar al equipo de su asistencia y participación.
* Mantener la reunión en movimiento como se describe en la página de Standup del proyecto.
* Asegurar de que todos los elementos estén documentados y de que cada uno tenga un propietario y una fecha de vencimiento y haga un seguimiento de las cuestiones abiertas.
* Anotar lo que sea necesario después de la planificación/reunión.
* Asegurar de que los elementos se trasladan al parking lot y asegurar el seguimiento posterior.
* Mantener una ubicación que muestre el trabajo y el estado del equipo y eliminar los impedimentos que lo bloquean.
* Hacer que el equipo se responsabilice de los resultados de forma solidaria.
* Asegurar de que la documentación del proyecto está actualizada.
* Garantizar el seguimiento de los elementos de las retros y de las reuniones diarias.
* Facilitar la retrospectiva del sprint.
* Entrenar al Product Owner y al equipo en el proceso, según sea necesario.

## Gestión del Backlog

* Trabajamos juntos en una [Definición de Listo](./definition-of-ready.md) y todas las historias de usuario asignadas a un sprint tienen que seguir esto
* Comunicamos en qué estamos trabajando a través del tablero
* Nos asignamos una tarea cuando estamos listos para trabajar en ella (no antes) y la pasamos a activa
* Capturamos cualquier trabajo que hagamos relacionado con el proyecto en una historia de usuario/tarea
* Cerramos nuestras tareas/historias de usuario sólo cuando están hechas (como se describe en la [Definición de Hecho](./definition-of-done.md))
* Trabajamos con el PM si queremos añadir una nueva historia de usuario al sprint
* Si añadimos nuevas tareas al tablero, nos aseguramos de que coinciden con los criterios de aceptación de la historia de usuario. Si no coincide con los criterios de aceptación, debemos discutir con el PM para ver si necesitamos una nueva historia de usuario para la tarea o si debemos ajustar los criterios de aceptación.

## Gestión del código

* Seguimos la convención de nomenclatura de ramas de git flow para las ramas e identificamos el número de la tarea, por ejemplo, feature/123-add-working-agreement
* Fusionamos todo el código en las ramas principales a través de PRs
* Todos los PR son revisados por lo menos por una persona
* Siempre revisamos los PRs existentes antes de empezar a trabajar en una nueva tarea
* Revisamos los PRs abiertos al final del stand-up para asegurarnos de que todos los PRs tienen revisores.
* Tratamos la documentación como código y aplicamos los mismos [estándares a Markdown](../../../revisiones%20de%20codigo/recetas/markdown.md) que al código
