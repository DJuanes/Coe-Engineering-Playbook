# YAML(Azure Pipelines) Code Reviews

## Guía de estilo

* [Referencia del esquema YAML](https://docs.microsoft.com/en-us/azure/devops/pipelines/yaml-schema/?view=azure-pipelines&tabs=schema%2Cparameter-schema&viewFallbackFrom=azure-devops).

## Análisis de código / Linting

El linter YAML más popular es la extensión [YAML](https://marketplace.visualstudio.com/items?itemName=redhat.vscode-yaml). Esta extensión proporciona validación YAML, esquematización de documentos, finalización automática, compatibilidad con desplazamiento y funciones de formateador.

## VS Code Extensions

Hay una extensión de [Azure Pipelines para VS Code](https://marketplace.visualstudio.com/items?itemName=ms-azure-devops.azure-pipelines) para agregar resaltado de sintaxis y autocompletado. También lo ayuda a configurar la compilación e implementación continuas de Azure WebApps sin salir de VS Code.

## Descripción general de YAML en Azure Pipelines

Cuando se activa la canalización, antes de ejecutar la canalización, hay algunas fases, como [Tiempo de encolado, Tiempo de compilación y Tiempo de ejecución](https://adamtheautomator.com/azure-devops-variables/#Pipeline_Execution_Phases), donde las variables se interpretan por su [sintaxis de expresión de tiempo de ejecución](https://docs.microsoft.com/en-us/azure/devops/pipelines/process/variables?view=azure-devops&tabs=yaml%2Cbatch#runtime-expression-syntax).
Cuando se activa la canalización, todos los archivos YAML anidados se expanden para ejecutarse en Azure Pipelines. Esta lista de verificación contiene algunos consejos y trucos para revisar todos los archivos YAML anidados.
Estos documentos pueden ser útiles al revisar archivos YAML:

* [Documentación YAML de Azure Pipelines](https://docs.microsoft.com/en-us/azure/devops/pipelines/yaml-schema/?view=azure-pipelines)
* [Secuencia de ejecución de canalización](https://docs.microsoft.com/en-us/azure/devops/pipelines/process/runs?view=azure-devops)
* [Conceptos clave para los nuevos Azure Pipelines](https://docs.microsoft.com/en-us/azure/devops/pipelines/get-started/key-pipelines-concepts?view=azure-devops)

## Code Review Checklist

Además de la Checklist de Code Review (), también debe buscar estos elementos de revisión de código específicos de Azure Pipelines YAML:

### Estructura del pipeline

* [ ] Los pasos se entienden bien y los componentes son fácilmente identificables. Asegúrese de que haya una descripción adecuada `displayName:` para cada paso de la canalización.
* [ ] Los pasos o etapas de la canalización se comprueban en Azure Pipelines para comprender mejor los componentes.
* [ ] En caso de que tenga archivos YAML anidados complejos, la canalización en Azure Pipelines se edita para encontrar el archivo raíz desencadenante.
* [ ] Se visitan todas las referencias del archivo de plantilla para garantizar que un pequeño cambio no provoque cambios importantes; cambiar un archivo puede afectar a varias canalizaciones
* [ ] Los scripts en línea largos en el archivo YAML se mueven a archivos de script

### Estructura YAML

* [ ] Los componentes reutilizables se dividen en plantillas YAML separadas.
* [ ] Las variables se separan por entorno almacenadas en plantillas o grupos de variables.
* [ ] Se tienen en cuenta los cambios de valor de las variables en el tiempo de encolado, el tiempo de compilación y el tiempo de ejecución.
* [ ] Se consideran los valores de sintaxis de variables utilizados con la sintaxis de macro, la sintaxis de expresión de plantilla y la sintaxis de expresión de tiempo de ejecución.
* [ ] Las variables pueden cambiar durante la canalización, los parámetros no.
* [ ] Las variables/parámetros no utilizados se eliminan en la canalización.
* [ ] ¿La canalización cumple con los criterios de condiciones de etapa/trabajo?

### Comprobación de permisos y seguridad

* [ ] Los valores secretos no deben imprimirse en la canalización, `issecret` se usa para imprimir secretos para la depuración.
* [ ] Si la canalización utiliza grupos de variables en la biblioteca, asegúrese de que la canalización tenga acceso a los grupos de variables creados.
* [ ] Si la canalización tiene una tarea remota en otro repositorio/organización, ¿tiene acceso?
* [ ] Si la canalización intenta acceder a un archivo seguro, ¿tiene el permiso?
* [ ] Si la canalización requiere aprobación para las implementaciones del entorno, ¿quién es el aprobador?
* [ ] ¿Necesita guardar secretos y administrarlos? ¿Consideró usar Azure KeyVault?
