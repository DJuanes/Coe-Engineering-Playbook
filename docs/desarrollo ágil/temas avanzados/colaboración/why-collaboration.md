# Por qué colaboración

## Por qué es importante la colaboración

Nuestro objetivo es ser altamente colaborativo porque cuando codificamos juntos, tenemos un mejor rendimiento, una mayor velocidad de sprint y un mayor grado de intercambio de conocimientos en todo el equipo.
Hay dos patrones comunes que utilizamos para la colaboración:

* Programación en parejas ("pairing"): dos ingenieros asignados a una historia compartida y trabajando en ella a la vez durante el sprint. Un ingeniero es el principal (propietario de la historia) y el otro es el secundario (asignado al emparejamiento). La [definición](https://www.agilealliance.org/glossary/pairing) coincide con la de la Agile Alliance.
* Programación en enjambre ("swarming"): tres o más ingenieros colaboran en un elemento de alta prioridad para llevarlo a término.

## Cómo programar las parejas

Como se ha mencionado, cada historia se asigna intencionadamente a una pareja. La persona asignada al emparejamiento puede estar en proceso de perfeccionamiento, sin embargo, son socios iguales en el esfuerzo de desarrollo. A continuación se exponen algunas directrices generales para el emparejamiento:

* Tras la asignación de la historia/elemento del backlog del producto (PBI), la pareja debe definir deliberadamente cómo trabajar juntos y tener una definición firme del trabajo que debe completarse. Esta información debe expresarse claramente en la descripción de la historia y en los criterios de aceptación. Las expectativas al respecto deben ser comunicadas y acordadas por ambos ingenieros y deben hacerse antes de cualquier sesión de trabajo real.
* El propietario de la historia y su par asignado no se limitan a dividir el trabajo y a sincronizarlo regularmente: trabajan activamente juntos en las mismas tareas y pueden compartir sus pantallas a través de una sesión en línea de Teams. Las herramientas de colaboración como [VS Live Share](https://visualstudio.microsoft.com/es/services/live-share/) pueden ser preferibles a compartir pantallas. No es necesario que toda la colaboración se base en compartir pantallas.
* Durante las sesiones de colaboración, un ingeniero proporciona el entorno de desarrollo mientras el otro ve y comenta activamente de forma verbal.
* Los ingenieros se intercambian a menudo de una sesión a otra para que todos tengan tiempo de controlar el teclado.
* Los ingenieros aprovechan las ramas de features para la colaboración durante el desarrollo de cada historia para tener pequeños Pull Requests al final del sprint.
* El código se comitea en el repositorio por ambos miembros del par asignado donde y cuando tiene sentido a medida que se completan las tareas.
* El emparejamiento asignado es la voz que representa a ambos durante la daily mientras es apoyado por el propietario de la historia.
* Tener los nombres de ambos visibles en el PBI puede ser útil durante las ceremonias del sprint y conducir a una mayor responsabilidad por parte del par asignado. Un ejemplo de esto usando las tarjetas Azure DevOps se puede encontrar aquí.

## Por qué la programación por parejas ayuda a la colaboración

La programación en parejas ayuda a la colaboración porque ambos ingenieros comparten la misma responsabilidad de llevar la historia a término. Se trata de un ejercicio mutuamente beneficioso porque, mientras que el propietario de la historia suele tener más experiencia en la que apoyarse, el asignado al emparejamiento aporta un punto de vista nuevo que no se ve enturbiado por la repetición.
Otros beneficios son:

* Menos defectos y mayor responsabilidad. El hecho de contar con dos pares de ojos permite a los ingenieros tener más oportunidades de detectar errores y recordar tareas que a menudo se pasan por alto, como la escritura de pruebas unitarias y de integración.
* El emparejamiento permite a los ingenieros con diferente experiencia y conocimientos aprender unos de otros colaborando y recibiendo comentarios en tiempo real.
* Incluso algo tan sencillo como describir el problema en voz alta puede ayudar a descubrir problemas o errores en el código.
* El emparejamiento puede ayudar a la lluvia de ideas, así como a validar detalles como la coherencia de los nombres de las variables.

## Cuándo se debe programar el enjambre

Es importante saber que no todos los PBI necesitan utilizar el enjambre. Algunos sprints pueden incluso no justificar el enjambre en absoluto. Utilice enjambre cuando:

* El trabajo es lo suficientemente complejo como para tener mentes colectivas colaborando.
* La tarea en la que trabaja el enjambre se ha convertido en un bloqueador de otras historias.
* Se descubre una incógnita que necesita un esfuerzo de colaboración para formar una decisión sobre cómo avanzar. El conocimiento y la experiencia colectivos ayudan a hacer avanzar la historia más rápidamente y, en última instancia, producen un código de mejor calidad.
* Surge un conflicto o una diferencia de opinión no resuelta durante una sesión de emparejamiento. Promueva que el trabajo se convierta en una sesión enjambre para ayudar a resolver el conflicto.

## Cómo programar el enjambre

Tan pronto como la pareja se entera de que el PBI va a justificar el enjambre, lo pone en conocimiento del resto del equipo. Los miembros del equipo aceptan o se ofrecen como voluntarios para ayudar.

* El propietario de la historia (o la persona asignada al emparejamiento) envía a los interesados una invitación a la convocatoria de equipos. Esto permite que el enjambre tenga un tiempo de concentración dedicado al bloquear el tiempo en los calendarios.
* Durante una sesión de enjambre, un ingeniero puede desviarse si hay algo que necesita ser manejado mientras el enjambre aborda el problema principal en cuestión, y luego vuelve a conectarse e informa. Esto permite al enjambre centrarse en un aspecto central y estar todos en la misma página.
* La llamada a los equipos se repite hasta que se encuentra una solución o se formula un camino alternativo.

## Por qué la programación en enjambre ayuda a la colaboración

* La programación en enjambre permite que el conocimiento y la experiencia colectiva del equipo se reúnan de forma enfocada y unificada.
* El enjambre no sólo ayuda a cerrar el item más rápidamente, sino que también ayuda al equipo a comprender los puntos fuertes y débiles de cada uno.
* Permite al equipo construir un mayor nivel de confianza y trabajar como una unidad cohesionada.

## Cuándo decidir enjambrar, emparejar y/o dividir

* Aunque se puede dedicar mucho tiempo a la programación en parejas, tiene sentido dividir el trabajo cuando la gente entiende cómo se va a llevar a cabo y el trabajo a realizar es en gran medida prescriptivo.
* Una vez que la historia ha sido asignada conjuntamente por ambos ingenieros, éstos pueden optar por abordar algunas tareas por separado y luego combinar el trabajo al final.
* La programación en parejas es más útil cuando los ingenieros no tienen perfectamente claro lo que hay que hacer o cómo se puede hacer.
* El enjambre se lleva a cabo cuando los dos ingenieros asignados a la historia necesitan experiencia que podrían aportar otros miembros del equipo.

## Beneficios de una mayor colaboración

Compartir el conocimiento y reunir a los ingenieros es un aspecto importante de los compromisos de trabajo. Somos responsables de demostrar los fundamentos de la ingeniería y dejar al cliente en un lugar mejor después de que nos desvinculemos. Esto sólo puede suceder si colaboramos y nos comprometemos juntos como un equipo. Además de mejorar la calidad del software, esto también añade un aspecto social beneficioso a los proyectos.

## Recursos

* [Cómo añadir un campo personalizado de emparejamiento en Azure DevOps User Stories](add-pairing-field-azure-devops-cards.md): añadir un campo personalizado de tipo Identidad en Azure DevOps para el emparejamiento
* [Sobre Pair Programming - Martin Fowler](https://martinfowler.com/articles/on-pair-programming.html)
* [Lecciones prácticas de Pair Programming](https://github.com/The-V8/pair-programming-sessions): se pueden utilizar (y adaptar) para apoyar la introducción de la programación por pares en su equipo.
