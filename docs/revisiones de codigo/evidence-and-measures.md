# Evidencia y Medidas

## Evidencia

Muchos de los elementos de control de calidad del código se pueden automatizar o aplicar mediante políticas en los sistemas modernos de seguimiento de elementos de trabajo y control de versiones. La verificación de las políticas en la rama principal en Azure DevOps o GitHub, por ejemplo, puede ser evidencia suficiente de que un equipo de proyecto está realizando revisiones de código.

* Las ramas principales en todos los repositorios tienen políticas de rama. [Configuración de políticas de ramas](tools.md#configuración-de-políticas-de-ramas)
* Todas las compilaciones producidas a partir de repositorios de proyectos incluyen linters apropiados, ejecutan pruebas unitarias.
* Cada elemento de trabajo de error debe incluir un enlace al PR que lo introdujo, una vez que se haya diagnosticado el error. Esto ayuda con el aprendizaje.
* Cada elemento de trabajo de error debe incluir una nota sobre cómo el error podría (o no) detectarse en una revisión de código.
* El equipo del proyecto actualiza regularmente sus checklists de revisión de código para reflejar los problemas comunes que han encontrado.
* Los líderes de desarrollo deben revisar una muestra de PRs y/o ser co-revisores con otros desarrolladores para ayudar a todos a mejorar sus habilidades como revisores de código.

## Medidas

El equipo puede recopilar métricas de revisiones de código para medir su eficiencia. Algunas métricas útiles incluyen:

* Defect Removal Efficiency (DRE): una medida de la capacidad del equipo de desarrollo para eliminar defectos antes del release
* Métricas de tiempo:
  * Tiempo empleado en la preparación de las sesiones de inspección de código
  * Tiempo utilizado en las sesiones de revisión
* Lines of code (LOC) inspeccionadas por unidad de tiempo/reunión

Es una solución perfectamente razonable rastrear estas métricas manualmente, por ejemplo, en un Excel. También es posible utilizar las funciones de las plataformas de gestión de proyectos; por ejemplo, AzDO habilita paneles para métricas, incluido el seguimiento de errores. Puede encontrar complementos listos para usar para varias plataformas o puede optar por implementar estas funciones usted mismo.

## Recursos

* [Una guía para las inspecciones de código](http://www.ganssle.com/inspections.pdf)
* [Eficacia de eliminación de defectos](https://www.westfallteam.com/sites/default/files/papers/defect_removal_effectiveness.pdf)
