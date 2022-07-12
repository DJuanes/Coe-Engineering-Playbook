# Definición de Listo

Cuando el equipo de desarrollo elige una historia de usuario de la parte superior del backlog, la historia debe tener suficiente detalle para estimar el trabajo necesario para completarla dentro del sprint. Si tiene suficiente detalle para estimar, está lista para ser desarrollada.

## Qué es

La definición de Listo es el acuerdo realizado por el equipo de scrum en torno a cuán completa debe estar una historia de usuario para ser seleccionada como candidata a ser estimada en la planificación del sprint. Se puede codificar como una lista de comprobación en las historias de usuario utilizando las [plantillas de temas de GitHub](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/configuring-issue-templates-for-your-repository) o las [plantillas de elementos de trabajo de Azure DevOps](https://docs.microsoft.com/en-us/azure/devops/boards/backlogs/work-item-template?view=azure-devops&tabs=browser).
Puede entenderse como una lista de comprobación que ayuda al Product Owner a asegurarse de que la historia de usuario que ha escrito contiene todos los detalles necesarios para que el equipo de scrum entienda el trabajo que hay que hacer.
Ejemplos:

- [ ] ¿Tiene la descripción los detalles, incluidos los valores de entrada necesarios para implementar la historia de usuario?
- [ ] ¿Tiene la historia de usuario criterios de aceptación claros y completos?
- [ ] ¿La historia de usuario responde a la necesidad de la empresa?
- [ ] ¿Podemos medir los criterios de aceptación?
- [ ] ¿Es la historia de usuario lo suficientemente pequeña como para ser implementada en poco tiempo, pero lo suficientemente grande como para proporcionar valor al cliente?
- [ ] ¿Está bloqueada la historia de usuario? Por ejemplo, ¿depende de algo de lo siguiente?
  - La finalización de un trabajo pendiente
  - Un entregable proporcionado por otro equipo

## Quién la escribe

La lista de comprobación de la disponibilidad puede ser redactada por un Product Owner de acuerdo con el equipo de desarrollo.

## Cuándo debe actualizarse una definición de listo

Actualice o cambie la definición de listo cada vez que el equipo de scrum observe que falta información en las historias de usuario que impacta recurrentemente en la planificación.

## Qué debe evitarse

La lista de verificación de listo debe contener elementos que se apliquen ampliamente. No incluya elementos o detalles que sólo se apliquen a una o dos historias de usuario. Esto puede convertirse en una sobrecarga al escribir las historias de usuario.

## Cómo preparar las historias

En el caso de que el trabajo más prioritario aún no esté listo, todavía puede ser posible avanzar. He aquí algunas estrategias que pueden ayudar:

- Las sesiones de [refinamiento del backlog](./../gestión%20de%20backlog/README.md) son un buen momento para validar que las historias de usuario de alta prioridad tengan una descripción clara, criterios de aceptación y un valor de negocio demostrable. También es un buen momento para desglosar las historias grandes que probablemente no se puedan completar en un solo sprint.
- Las sesiones de priorización son un buen momento para priorizar las historias de usuario que desbloquean otro trabajo de alta prioridad bloqueado.
- Las historias de usuario bloqueadas a menudo se pueden desglosar de manera que se desbloquee una parte del alcance de las historias originales. Esta es una buena manera de avanzar incluso cuando parte del trabajo está bloqueado.
