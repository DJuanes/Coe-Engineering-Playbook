# Work Items

Aunque muchos equipos pueden trabajar con una lista plana de elementos, a veces resulta útil agrupar los elementos relacionados en una estructura jerárquica.

## Epicas y Features

Las historias de usuario / Product Backlog Items se convierten en Features, que suelen representar un producto entregable que responde a una necesidad del cliente. Y los Features se convierten en Epicas, que representan una iniciativa de negocio que debe llevarse a cabo.
Cada Feature o Epica debe incluir tantos detalles como el equipo necesite:

* Comprender el alcance.
* Estimar el trabajo necesario.
* Desarrollar pruebas.
* Asegurar de que el producto final cumple los criterios de aceptación.

Detalles que deben añadirse:

* Área de valor: Negocio (entrega directa de valor al cliente) vs. Arquitectura (servicios técnicos para implementar las características del negocio).
* Esfuerzo / Puntos de Historia / Tamaño: Estimación relativa de la cantidad de trabajo necesaria para completar el elemento.
* Valor comercial: Prioridad de un elemento en comparación con otros elementos del mismo tipo.
* Criticidad del tiempo: Los valores más altos indican que un elemento es más crítico de tiempo que los elementos con valores más bajos.
* Fecha objetivo: en la que debe implementarse el feature.

Se pueden utilizar etiquetas de elementos de trabajo para apoyar las consultas y el filtrado.

## Historias de Usuario / Elementos del Backlog del Producto

Cada Historia de Usuario / Elemento del Backlog del Producto debe tener un tamaño tal que pueda ser completado dentro de un sprint.
Debe añadir los siguientes detalles a los elementos:

* Título: Normalmente se expresa como "Como [persona], quiero [realizar una acción], para que [pueda lograr un resultado final]".
* Descripción: Proporcione suficientes detalles para crear una comprensión compartida del alcance y apoyar los esfuerzos de estimación. Céntrese en el usuario, en lo que quiere conseguir y en el motivo. No describa cómo desarrollar el producto. Proporcione suficientes detalles para que el equipo pueda escribir tareas y casos de prueba para implementar el elemento.
  * Incluya revisiones de diseño.
* Criterios de aceptación: Defina lo que significa "Hecho".
* Actividad: Despliegue, Diseño, Desarrollo, Documentación, Requisitos, Pruebas.
* Esfuerzo / Puntos de historia / Tamaño: Estimación relativa de la cantidad de trabajo necesaria para completar el elemento.
* Valor comercial: Prioridad de un elemento en comparación con otros elementos del mismo tipo.
* Estimación original: La cantidad de trabajo estimada necesaria para completar una tarea.

Recuerde utilizar la sección de discusión de los elementos para hacer un seguimiento de los comentarios relacionados, y mencionar a las personas, grupos, elementos de trabajo o PRs cuando sea necesario.

## Tareas

Cada tarea debe tener un tamaño tal que pueda completarse en un día.
Debe añadir al menos los siguientes detalles a los elementos:

* Título.
* Descripción: Proporcione suficientes detalles para crear una comprensión compartida del alcance. Cualquier desarrollador debería ser capaz de tomar el elemento y saber lo que hay que implementar.
  * Incluya revisiones de diseño.
* Referencia a la rama de trabajo en el repositorio de código relacionado.

Recuerde utilizar la sección de discusión de las tareas para hacer un seguimiento de los comentarios relacionados.

## Bugs

Debería utilizar bugs para capturar tanto el problema inicial como los descubrimientos en curso.
Debería añadir al menos los siguientes detalles a los elementos de los bugs:

* Título.
* Descripción.
* Pasos para reproducirlo.
* Información del sistema / Encontrado en la compilación: Configuración del software y del sistema que es relevante para el bug y las pruebas a aplicar.
* Criterios de aceptación: Criterios que hay que cumplir para poder cerrar el bug.
* Integrado en la compilación: Nombre de la compilación que incorpora el código que corrige el bug.
* Prioridad:
  * 1: El producto no debe salir al mercado sin que se haya resuelto correctamente el elemento de trabajo.
  * 2: El producto no debería salir a la venta sin la resolución satisfactoria del elemento de trabajo, pero no es necesario abordarlo inmediatamente.
  * 3: La resolución del elemento de trabajo es opcional en función de los recursos, el tiempo y el riesgo.
* Gravedad:
  * 1 - Crítico: Debe solucionarse. No hay métodos alternativos aceptables.
  * 2 - Alta: Considere la posibilidad de solucionarlo. Existe un método alternativo aceptable.
  * 3 - Medio: (Por defecto).
  * 4 - Bajo.

## Issues / Impedimentos

Representan actividades no planificadas que pueden impedir que el trabajo se realice. Por ejemplo: ambigüedad del feature, problemas de personal o de recursos, problemas con los entornos u otros riesgos que afectan al alcance, la calidad o el calendario.
En general, estos elementos se vinculan a las historias de usuario o a otros elementos de trabajo.

## Acciones de las retrospectivas

Después de una retrospectiva, cada acción que requiera trabajo debe ser rastreada con su propia Tarea o Issue / Impedimento. Estos elementos pueden estar sin parentesco (sin vínculo con el elemento de backlog principal o la historia de usuario).

## Información relacionada

* [Mejores prácticas para la gestión ágil de proyectos - Azure Boards](https://docs.microsoft.com/en-us/azure/devops/boards/best-practices-agile-project-management?view=azure-devops&tabs=agile-process)
* [Definir features y epicas, organizar los elementos del backlog - Azure Boards](https://docs.microsoft.com/en-us/azure/devops/boards/backlogs/define-features-epics?view=azure-devops&tabs=scrum-process)
* [Crear el backlog del producto - Azure Boards](https://docs.microsoft.com/en-us/azure/devops/boards/backlogs/create-your-backlog?view=azure-devops&tabs=agile-process)
* [Añadir tareas para apoyar la planificación de sprints - Azure Boards](https://docs.microsoft.com/en-us/azure/devops/boards/sprints/add-tasks?view=azure-devops)
* [Definir, capturar, clasificar y gestionar bugs o defectos de código - Azure Boards](https://docs.microsoft.com/en-us/azure/devops/boards/backlogs/manage-bugs?view=azure-devops)
* [Añadir y gestionar problemas o impedimentos - Azure Boards](https://docs.microsoft.com/en-us/azure/devops/boards/backlogs/manage-issues-impediments?view=azure-devops)
