# Documentación

Todo proyecto de desarrollo de software requiere documentación. El [desarrollo ágil de software](https://agilemanifesto.org/) valora más el software en funcionamiento que la documentación exhaustiva. Aun así, los proyectos deben incluir la información clave necesaria para entender el desarrollo y el uso del software generado.
La documentación no debería ser una idea de última hora. Se deben crear diferentes documentos y materiales escritos durante todo el ciclo de vida del proyecto, según las necesidades del mismo.

## Objetivos

* Facilitar la incorporación de los nuevos miembros del equipo.
* Mejorar la comunicación y la colaboración entre los equipos.
* Mejorar la transición del proyecto a otro equipo.

## Desafíos

Cuando trabajamos en un proyecto de ingeniería, solemos encontrarnos con uno o varios de estos retos relacionados con la documentación:

* Inexistente
  * No hay documentación de ingreso, por lo que se tarda mucho en configurar el entorno cuando te unes al proyecto.
  * Ningún documento en la wiki que explique los repositorios existentes, por lo que no puedes saber cuál de repositorios disponibles debes clonar.
  * No hay un README principal, así que no sabes por dónde empezar cuando clonas un repositorio.
  * No hay una sección de "cómo contribuir", así que no sabes cuál es la política de ramas, dónde añadir nuevos documentos, etc.
  * No hay directrices de código, por lo que todo el mundo sigue diferentes convenciones de nomenclatura, etc.
* Oculto
  * Imposible encontrar documentación útil ya que está dispersa.
  * Los procesos útiles se explican fuera de la herramienta de gestión del backlog y no se vinculan en ningún sitio.
  * Decisiones tomadas en canales diferentes a la herramienta de gestión de backlogs y no registradas en ninguna parte.
* Incompleto
  * No hay una política clara sobre las ramas, por lo que cada uno nombra sus ramas de forma diferente.
  * Faltan ajustes en el documento "cómo ejecutar esto" que son necesarios para ejecutar la aplicación.
* Inexacto
  * Documentos no actualizados junto con el código, por lo que no mencionan las carpetas correctas, las configuraciones, etc.
* Obsoletos
  * Documentos de diseño que ya no se aplican, en el mismo lugar que los documentos válidos. ¿Cuál muestra las últimas decisiones?
* Desordenados (tema / fecha)
  * Los documentos no están organizados por tema/trabajo, por lo que no es fácil encontrar la información relevante cuando se cambia a un nuevo flujo de trabajo.
  * Los logs de decisiones de diseño están desordenados y sin una fecha que ayude a determinar cuál es la decisión final sobre algo.
* Duplicado
  * No hay un archivo de configuración disponible en un lugar centralizado como única fuente de verdad, por lo que los desarrolladores deben seguir compartiendo sus propias versiones, y terminamos con muchos archivos que podrían o no funcionar.
* Una idea tardía
  * Documentos clave creados varias semanas después de iniciado el proyecto: incorporación, funcionamiento de la aplicación, etc.
  * Documentos creados en el último momento, justo antes de finalizar el proyecto, olvidando que también ayudan al equipo mientras trabaja en el proyecto.

## Qué documentación debe existir

* [Proyecto y repositorios](./guia/../guía/project-and-repositories.md)
* [Mensajes de commit](m)
* [Pull Requests](./guía/pull-requests.md)
* [Código](./guía/code.md)
* [Elementos de trabajo (Work Items)](./guía/work-items.md)
* [APIs REST](./guía/rest-apis.md)

## Mejores prácticas

* [Establecimiento y gestión de la documentación](./mejores%20prácticas/establish-and-manage.md)
* [Creación de una buena documentación](./mejores%20prácticas/good-documentation.md)
* [Sustitución de la documentación por la automatización](./mejores%20prácticas/automation.md)

## Herramientas

* [Wikis](./herramientas/wikis.md)
* [Lenguajes](./herramientas/languages.md)
  * [markdown](./herramientas/languages.md#markdown)
  * [mermaid](./herramientas/languages.md#mermaid)
* [Cómo automatizar comprobaciones sencillas](./herramientas/automation.md)
* [Integración con Teams/Slack](./herramientas/integrations.md)

## Recetas

* [Uso de DocFx y Companion Tools para generar un sitio web de documentación](./recetas/using-docfx-and-tools.md)
* [Desplegar el sitio web de documentación de DocFx en un sitio web de Azure automáticamente](./recetas/deploy-docfx-azure-website.md)
* [Cómo crear un sitio web estático para su documentación basado en MkDocs y Material para MkDocs](./recetas/static-website-with-mkdocs.md)

## Recursos

* [Tipos de documentación de software y mejores prácticas](https://blog.prototypr.io/software-documentation-types-and-best-practices-1726ca595c7f)
* [¿Por qué es importante la documentación del proyecto?](https://www.greycampus.com/blog/project-management/why-is-project-documentation-important)
