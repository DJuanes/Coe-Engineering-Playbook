# Detección de secretos

Es importante asegurar que los secretos no lleguen a la base de código y comprometan la seguridad de los datos de nuestra aplicación. La mejor manera de hacerlo es introduciendo una forma sencilla y fácil de detectar secretos durante su desarrollo, y en sus pipelines CI/CD. Esta sección describe cómo podemos utilizar el framework de código abierto [Yelp Detect-Secrets](https://github.com/Yelp/detect-secrets). La herramienta Yelp Detect-Secrets utiliza un modelo de Entropía de Shannon para detectar secretos en las bases de código y evita que se introduzcan nuevos secretos.

## Pre-Commit Hook para detectar secretos

El pre-commit hook de Detect-Secrets es una herramienta que evita que los secretos entren en el código en una de las primeras etapas del desarrollo, evitando que el secreto quede en el historial de Git.

### Configuración del entorno

A continuación se presentan dos formas de configurar el entorno en función de su caso de uso.

* [Pre-Commit Hook dentro del Repo existente](https://github.com/wbreza/pre-commit-hooks/blob/main/detect-secrets/README.md)
  * Un simple script de instalación arranca los repos existentes con pre-commit hooks y scripts para ayudar a gestionar el ciclo de vida de la detección de secretos
* [Pre-Commit Hook con nuevo repo](https://github.com/wbreza/baseline-security-seed/blob/main/SECURITY.md)
  * Contiene todo lo anterior, además de soporte para contenedores de desarrollo utilizando la imagen universal de contenedores de desarrollo de Github.
  * También incluye un flujo de trabajo de GitHub para realizar adicionalmente la detección de secretos dentro de los pull requests

## Extensión de Azure DevOps para detectar secretos

Esta extensión escanea la base de código en busca de secretos usando sofisticados algoritmos como la entropía de Shannon y reporta los hallazgos en el modelo Azure DevOps Pipeline para permitir una rápida retroalimentación y respuesta de los equipos de desarrollo. Como extensión desplegada en la canalización CI/CD, Detect Secrets no depende de que los desarrolladores cambien su entorno de desarrollo. Dependiendo de cómo esté configurada su canalización, puede llevar a situaciones en las que los secretos se filtren al repositorio antes de ser detectados. La filtración de secretos en el repositorio requiere una limpieza, por lo que se recomienda el uso de protecciones de precommit y CI/CD.

### Configuración

Actualmente esta extensión está en vista previa privada y para obtener acceso a ella, contacta con un miembro del Área de Soluciones de Seguridad enviando un correo electrónico a csesecuritysa@microsoft.com.

### A continuación se muestra la configuración YAML para esta herramienta

* Añada el plugin Detect-Secrets desde el asistente de tareas y configure la herramienta para que apunte a su ubicación de origen y al archivo de la lista de palabras (lista permitida). La ubicación de la fuente por defecto apuntará al directorio raíz de sus repositorios.

```YAML
- task: CSEDetectSecrets@1
  inputs:
    sourceLocation: '$(Build.Repository.LocalPath)'
    usingwordListFile: true
    wordListFile: 'allow-list.txt'
```

* Para informar sobre los resultados del escaneo de detect-secrets añada lo siguiente debajo de la tarea de Yelp:

```YAML
- task: PublishTestResults@2
  displayName: 'Publish Test Results'

  inputs:
    testResultsFormat: 'JUnit'
    testResultsFiles: 'report.xml'
    searchFolder: '$(Build.Repository.LocalPath)'
```

### Notas sobre los argumentos del escáner

El escaneo invocará el escáner detect-secrets con los argumentos `-C <ruta al directorio raíz> scan --force-use-all-plugins`. Si desea dirigir la herramienta a un directorio específico, añada la ubicación deseada en el YAML, por ejemplo, `$(Build.Repository.LocalPath)/desired_path` y tendrá que actualizar la ruta searchFolder: $(Build.Repository.LocalPath) para ver los resultados del escaneo.
Si el pipeline está configurado sin que scanNonGitFiles esté configurado para su pipeline, entonces el argumento `--all-files` se establecerá para escanear los artefactos git en su pipeline también.
`setFailureasWarning` se establecerá en false a menos que se indique lo contrario, lo que hará que la tarea falle si se produce un hallazgo.

### Notas sobre el Argumento de Escaneo Allow-List

Para mitigar los falsos positivos puede añadir una lista de permitidos.
Primero debe añadir una lista permitida en su repositorio; se trata de un archivo de texto con un nombre de su elección que contiene una lista de secretos permitidos separados por un retorno de carro.
A continuación, debe marcar la casilla "¿Utilizar un archivo de lista de palabras?" y luego rellenar el campo "Ubicación del archivo de lista de palabras secretas en el repositorio" con su nueva ubicación de archivo.
Guarde y ejecute la canalización. Si se encuentra con más falsos positivos en su canalización, simplemente añádalos a su nuevo archivo de lista permitida.

### Informes

Después de que la herramienta detect-secrets se haya ejecutado en el pipeline, fallará en rojo con el número de secretos encontrados en el repositorio, o pasará en verde con ningún secreto encontrado.
Para ver los resultados detallados completos, navegue hasta los resultados de la ejecución de detect-secrets haciendo clic en el número de job que acaba de ejecutarse.
Al hacer clic en el campo `<run #>` se accede a una página de Azure DevOps que contiene las siguientes pestañas: "Resumen", "Tests", "Análisis".
Si seleccionas la pestaña "Tests" iras a un resumen que muestra el archivo(s) sospechoso(s), el número de línea, y una versión hash del secreto junto con cuántos secretos fueron encontrados en el repositorio clasificado como "<#> Total de pruebas".

## Escenario nominal para la utilización de la herramienta

Un resultado nominal para garantizar que no se introduzcan secretos en el código fuente es utilizar estas dos herramientas.
Los equipos pueden aplicar Detect Secrets a la canalización CI/CD para proteger el proyecto independientemente de las prácticas de desarrollo de los colaboradores individuales. Los individuos pueden aplicar Detect Secrets como una comprobación previa al envío para reducir la posibilidad de que un accidente haga que un secreto se vincule al repositorio del proyecto. Siguiendo ambas prácticas se obtiene la mejor cobertura y siguiendo las instrucciones anteriores se puede reutilizar completamente el mismo archivo world-list de pre-commit en la extensión CI/CD.

## Lecturas adicionales

* [Yelp/detect-secrets](https://github.com/Yelp/detect-secrets): Una forma empresarial de detectar y prevenir secretos en el código.
