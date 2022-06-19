# Continuous Integration

Alentamos a los equipos de ingeniería a realizar una inversión inicial durante el Sprint 0 de un proyecto para establecer una canalización automatizada y repetible que integre continuamente el código y libere los ejecutables del sistema para los entornos de nube de destino. Cada integración debe ser verificada por un proceso de compilación automatizado que asegure que pasa un conjunto de tests de validación y detecte cualquier error.
Estos [principios](https://martinfowler.com/articles/continuousIntegration.html) mapean directamente las [prácticas](https://en.wikipedia.org/wiki/Agile_software_development) ágiles del ciclo de vida del desarrollo de software.

## Metas

La automatización de integración continua es una parte integral del ciclo de vida de desarrollo de software destinado a reducir los errores de integración de compilación y maximizar la velocidad en un equipo de desarrollo.
Una sólida canalización de automatización de compilación:

* Acelera la velocidad del equipo
* Previene problemas de integración
* Evita el caos de última hora durante las fechas de lanzamiento
* Proporciona un ciclo rápido de retroalimentación para el impacto de los cambios locales en todo el sistema
* Separa etapas de compilación e implementación
* Mide e informa métricas sobre fallas/éxitos de compilación
* Aumenta la visibilidad en todo el equipo permitiendo una comunicación más estrecha
* Reduce los errores humanos, que es probablemente la parte más importante de la automatización de las compilaciones.

## Definición de compilación administrada en Git

### Los artefactos de código/manifiesto requeridos para construir su proyecto deben mantenerse dentro de su(s) repositorio(s) de git de su(s) proyecto(s)

* Las definiciones de canalización de compilación específicas del proveedor de CI deben residir dentro de su(s) repositorio(s) de git de proyecto(s).

## Automatización de compilación

Una compilación automatizada debe abarcar los siguientes principios:

### Compilación

* Un solo paso dentro de su canalización de compilación que compila su proyecto de código en un solo artefacto de compilación.

### Unit Testing

* Su definición de compilación incluye pasos de validación para ejecutar un conjunto de tests unitarios automatizados para garantizar que los componentes de la aplicación cumplan con su diseño y se comporten según lo previsto.

### Comprobaciones de estilo de código

* El código debe formatearse según los estándares de codificación acordados. Dichos estándares mantienen el código consistente y, lo que es más importante, fácil de leer y refactorizar para el equipo. La consistencia en el estilo del código fomenta la propiedad colectiva de los equipos Scrum del proyecto.
* Hay varias herramientas de validación de estilo de código abierto disponibles para elegir ([code style checks](https://github.com/checkstyle/checkstyle), [StyleCop](https://en.wikipedia.org/wiki/StyleCop)). La sección [Code Reviews](../revisiones de codigo/recetas/README.md) tiene sugerencias para linters y estilos preferidos para varios lenguajes.
* Recomendamos incorporar herramientas de análisis de seguridad dentro de la etapa de compilación de su canalización, como: escáner de credenciales, detección de riesgos de seguridad, análisis estático, etc.
* Los estándares de código se mantienen dentro de un único archivo de configuración. Debe haber un paso en la canalización de compilación que afirme que el código en el último commit se ajusta a la definición de estilo conocida.

### Script de compilación

* Un solo comando debe tener la capacidad de compilar el sistema. Esto también es cierto para las compilaciones que se ejecutan en un servidor CI o en una máquina local de desarrolladores.

### Sin dependencias IDE

* Es esencial tener una compilación que se pueda ejecutar a través de scripts independientes y que no dependa de un IDE en particular. Los destinos de canalización de compilación se pueden activar localmente en sus escritorios a través del IDE de su elección. El proceso de compilación también debe mantener la flexibilidad suficiente para ejecutarse dentro de un servidor de CI.

### Comprobaciones de seguridad de DevOps

* Introduzca seguridad a su proyecto en las primeras etapas. Siga la sección [DevSecOps](dev-sec-ops/README.md) para introducir prácticas de seguridad, automatización, herramientas y frameworks como parte de la CI.

## Dependencias del entorno de compilación

### Configuración del entorno local automatizado

* Alentamos a mantener una experiencia de desarrollador consistente para todos los miembros del equipo. Debe haber un manifiesto/proceso automatizado central que agilice la instalación y configuración de cualquier dependencia de software. De esta forma, los desarrolladores pueden replicar localmente el mismo entorno de compilación que el que se ejecuta en un servidor de CI.
* Los scripts de automatización de compilación a menudo requieren paquetes de software específicos y una versión preinstalada dentro del entorno de tiempo de ejecución del sistema operativo.
* Todos los desarrolladores del equipo deberían poder emular el entorno de compilación desde su escritorio local, independientemente de su sistema operativo.
* Para los proyectos que usan VS Code, aprovechar Dev Containers realmente puede ayudar a estandarizar la experiencia del desarrollador local en todo el equipo.
* Se deben considerar herramientas de empaquetado de software bien establecidas como Docker, Maven, npm, etc. al diseñar su cadena de herramientas de automatización de compilación.

### Documentación de la configuración local

* El proceso de configuración para un entorno de compilación local debe estar bien documentado y ser fácil de seguir para los desarrolladores.

## Infrastructure as Code

Administre la mayor cantidad posible de lo siguiente, como código:

* Archivos de configuración
* Gestión de configuración (es decir, automatización de variables de entorno)
* Gestión de secretos
* Aprovisionamiento de recursos en la nube
* Asignaciones de roles
* Escenarios de prueba de carga
* Reglas y condiciones de monitoreo/alertas de disponibilidad

Desvincular la infraestructura del código base de la aplicación simplifica el paso de los equipos de ingeniería a las aplicaciones nativas de la nube.

### Por qué

* Los cambios repetibles y auditables en la infraestructura facilitan la reversión a buenas configuraciones conocidas y la rápida expansión sin tener que conectar manualmente los recursos de la nube.
* Los proyectos de referencia de IAC probados permiten que más equipos de ingeniería implementen soluciones seguras y escalables a un ritmo mucho más rápido
* Permite simplificar los escenarios de "lift and shift" abstrayendo las complejidades de la computación nativa en la nube lejos de los equipos de desarrolladores de aplicaciones.

### IAC DevOPS: operaciones por Pull Request

* El proceso de implementación de la infraestructura se basa en un repositorio que contiene el estado esperado actual del sistema/entorno de Azure.
* Los cambios operativos se realizan en el sistema en ejecución al realizar confirmaciones en este repositorio.
* Git también proporciona un modelo simple para auditar implementaciones y retroceder a un estado anterior.

### Patrones recomendados

* Usted define la infraestructura como código en las plantillas de Terraform/ARM/Ansible
* Las plantillas son pilas de recursos en la nube repetibles que se centran en conjuntos de configuración alineados con las necesidades de escalado y rendimiento de la aplicación.

### Principios de la IAC

#### Automatice el entorno de Azure

* Todos los recursos de la nube se aprovisionan a través de un conjunto de infraestructura como plantillas de código. Esto también incluye secretos, ajustes de configuración de servicios, asignaciones de roles y condiciones de monitoreo.
* Azure Portal debe proporcionar una vista de solo lectura de los recursos del entorno. Cualquier cambio aplicado al entorno debe realizarse únicamente a través de la cadena de herramientas IAC CI.
* El aprovisionamiento de entornos en la nube debe ser un proceso repetible que se basa en los artefactos del código de infraestructura registrados en nuestro repositorio de git.

#### Flujo de trabajo de CI de IAC

* Cuando los archivos de plantilla de IAC cambian a través de un flujo de trabajo basado en Git, una canalización de compilación de CI crea, valida y concilia el estado actual del entorno de infraestructura de destino con el estado esperado. El plan de ejecución de infraestructura candidato para estos entornos fijos es revisado por un administrador como verificación de entrada antes de la etapa de implementación de la canalización que aplica el plan de ejecución.

#### Acceso de solo lectura del desarrollador a los recursos de la nube

* Las cuentas de desarrollador en Azure Portal deben tener acceso de solo lectura a los recursos del entorno de IAC en Azure.

#### Automatización de secretos

* Las plantillas de IAC se implementan a través de un sistema CI/CD que tiene integrada la automatización de secretos. Evite aplicar cambios a secretos y/o certificados directamente en Azure Portal.

#### Automatización de tests de integración de infraestructura

* Los tests de integración de un extremo a otro se ejecutan como parte de su proceso de IAC CI para inspeccionar y validar que un entorno esté listo para usar.

#### Documentación de Infraestructura

* La implementación y la topología de la plantilla de recursos en la nube deben documentarse y comprenderse bien con el README del repositorio git de IAC.
* Se deben documentar los pasos de configuración del entorno local y del flujo de trabajo de CI.

## Validación de la configuración

Las aplicaciones utilizan la configuración para permitir diferentes comportamientos en tiempo de ejecución y es bastante común utilizar archivos para esto. Como desarrolladores, podemos introducir errores al editar estos archivos, lo que causaría problemas para que la aplicación se inicie y/o se ejecute correctamente. Aplicando técnicas de validación tanto en la sintaxis como en la semántica de nuestra configuración, podemos detectar errores antes de que la aplicación se despliegue y ejecute, mejorando la experiencia del desarrollador.

### Ejemplos de archivos de configuración de aplicaciones

* JSON, con soporte para tipos de datos y estructuras de datos complejas
* YAML, un superconjunto de JSON con soporte para tipos de datos y estructuras complejas
* TOML, un superconjunto de JSON y un formato de archivo de configuración formalmente especificado

### ¿Por qué validar la configuración de la aplicación como un paso separado?

* Depuración más fácil y ahorro de tiempo: Con un paso de validación de la configuración en nuestro pipeline, podemos evitar ejecutar la aplicación sólo para descubrir que falla. Se ahorra tiempo en tener que desplegar y ejecutar, esperar y luego darse cuenta de que algo está mal en la configuración. Además, también ahorra tiempo en revisar los logs para averiguar qué falló y por qué.
* Mejor experiencia del usuario/desarrollador: Un simple recordatorio al usuario de que algo en la configuración no está en el formato correcto puede marcar la diferencia entre un proceso de despliegue exitoso y la frustración de tener que adivinar lo que salió mal.
* Evitar la corrupción de datos y las brechas de seguridad: Dado que los datos llegan desde una fuente no confiable, como un usuario o un servicio web externo, es particularmente importante validar la entrada.

### ¿Qué es el esquema Json?

[JSON-Schema](https://json-schema.org/) es el estándar de los documentos JSON que describe la estructura y los requisitos de sus datos JSON. Aunque se llama JSON-Schema, también es común utilizar este método para los YAML, ya que es un superconjunto de JSON. El esquema es muy sencillo; señalar qué campos pueden existir, cuáles son obligatorios u opcionales, qué formato de datos utilizan. Sobre esa premisa básica se pueden añadir otras reglas de validación, junto con información legible para el ser humano. Los metadatos viven en los esquemas, que también son archivos .json.

### ¿Cómo implementar la validación de esquemas?

La implementación de la validación de esquemas se divide en dos: la generación de los esquemas y la validación de los archivos yaml/json con esos esquemas.

### Generación

Hay dos opciones para generar un esquema:

* [Desde el código](https://json-schema.org/implementations.html#from-code): podemos aprovechar los modelos y objetos existentes en el código y generar un esquema personalizado.
* [Desde los datos](https://json-schema.org/implementations.html#from-data): podemos tomar muestros yaml/json que reflejen la configuración en general y utilizar las distintas herramientas online para generar un esquema.

### Validación

El esquema tiene más de 30 [validadores](https://json-schema.org/implementations.html#validators) para diferentes lenguajes, por lo que no es necesario que lo codifiques tú mismo.

## Validación de la integración

Una manera eficaz de identificar los errores en su compilación a un ritmo rápido es invertir temprano en un conjunto fiable de tests automatizados que validan la funcionalidad de base del sistema:

### Tests de integración de extremo a extremo

* Incluya pruebas en su proceso para validar que la versión candidata se ajusta a las afirmaciones de funcionalidad empresarial automatizada. Cualquier error debe ser reportado en los resultados de los tests, incluyendo la prueba fallida y el seguimiento de la pila correspondiente. Todas los tests deben ser invocadas a través de un único comando.
* Mantenga la compilación rápida. Tenga en cuenta el tiempo de ejecución de los tests automatizados cuando decida introducir dependencias como bases de datos, servicios externos y carga de datos simulados. Considere la posibilidad de añadir límites máximos de tiempo de espera para las validaciones largas para fallar rápidamente y mantener una alta velocidad en todo el equipo.

### Evitar el checkin de compilaciones falladas

* Las comprobaciones automatizadas de las compilaciones, los tests, las ejecuciones de lint, etc. deberían validarse localmente antes de confirmar los cambios en el repositorio.

### Informar de los fallos de compilación

* Si el paso de compilación falla, el estado de ejecución de la cadena de compilación debe ser reportado como fallido, incluyendo los logs relevantes y las trazas de pila.

### Dependencias de datos de automatización de tests

* Cualquier conjunto de datos simulado que se utilice para los tests unitarios y de integración debe ser chequeado en el repositorio principal. Minimice cualquier dependencia de datos externos con su proceso de compilación.

### Comprobación de la cobertura del código

* Recomendamos integrar las herramientas de cobertura del código en la fase de compilación. La mayoría de las herramientas de cobertura suspenden las compilaciones cuando la cobertura de los tests cae por debajo de un umbral mínimo. El informe de cobertura debería publicarse en su sistema CI para hacer un seguimiento de una serie de variaciones en el tiempo.

## Flujo de trabajo basado en Git

### Compilar en el momento del commit

* Cada commit en el repositorio base debe activar el canal de CI para crear un nuevo candidato a la compilación.
* Los artefactos de compilación se construyen, empaquetan, validan y despliegan continuamente en un entorno de no producción por cada commit. Cada commit contra el repositorio resulta en una ejecución de CI que comprueba las fuentes en la máquina de integración, inicia una compilación y notifica el resultado de la compilación.

### Evitar comentar los tests que fallan

* Evita comentar los tests en la rama principal. Al comentar los tests, obtenemos una indicación incorrecta del estado de la compilación.

### Aplicación de la política de rama

* Las políticas de rama protegida deben ser configuradas en la rama principal para asegurar que las etapas de CI han pasado antes de comenzar una revisión de código. Los aprobadores de la revisión del código sólo comenzarán a revisar un PR una vez que la ejecución de la canalización de CI haya pasado.
* Las compilaciones rotas deberían bloquear las revisiones de los PRs.
* Evita que los commits vayan directamente a la rama principal.

### Estrategia de las ramas

* Las ramas de release deberían activar automáticamente el despliegue de un artefacto de compilación en su entorno de nube de destino. Puedes encontrar una guía en el sitio de documentación de Azure DevOps en la sección [Manage deployments](https://docs.microsoft.com/en-us/azure/devops/repos/git/git-branching-guidance?view=azure-devops#manage-deployments).

## Entrega rápida y diaria

En aras de la transparencia y de la comunicación frecuente entre el equipo de desarrollo, animamos a los desarrolladores a que envíen el código a diario. Este enfoque proporciona visibilidad y acelera la programación por pares en todo el equipo. Estos son algunos principios a tener en cuenta:

### Todos comitean al repositorio cada día

* El código registrado al final del día debe contener pruebas unitarias como mínimo.
* Ejecuta la compilación localmente antes de hacer el check-in para evitar la saturación de fallos de la canalización CI. Deberías verificar qué causó el error, y tratar de resolverlo tan pronto como sea posible. Animamos a los desarrolladores a seguir los [principios lean de SDLC](https://leankit.com/learn/lean/principles-of-lean-development/).
* Aísle el trabajo en pequeñas partes que se relacionen directamente con el valor del negocio y refactorice de forma incremental.

## Entornos aislados

Uno de los objetivos clave de la validación de la compilación es aislar e identificar los fallos en los entornos de test y minimizar cualquier interrupción de producción. Las pruebas automatizadas E2E deben ejecutarse en un entorno que imite el entorno de producción (en la medida de lo posible).

### Test en un clon de producción

* El entorno de producción debe duplicarse en un entorno de test (QA y/o Pre-Prod) como mínimo.

### Las actualizaciones PR desencadenan releases escalonados

* Los nuevos commits relacionados con un pull request deben desencadenar una compilación / release en un entorno de integración. El entorno de producción debe estar totalmente aislado de este proceso.

### Promover los cambios de infraestructura en entornos fijos

* Los cambios en la infraestructura como código deben probarse en un entorno de integración y promoverse a todos los entornos fijos, para luego migrar a producción sin que haya tiempo de inactividad para los usuarios del sistema.

### Tests en producción

* Existen varios enfoques para llevar a cabo de forma segura las pruebas automatizadas para los despliegues de producción. Algunos de ellos pueden ser:
  * Feature flagging
  * A/B testing
  * Traffic shifting

## Acceso de los desarrolladores a los últimos artefactos de la versión

Nuestro flujo de trabajo de desarrollo debe permitir a los desarrolladores obtener, instalar y ejecutar el último ejecutable del sistema. Los ejecutables de la versión deben ser generados automáticamente como parte de nuestros procesos CI/CD.

### Los desarrolladores pueden acceder al último ejecutable

* El último ejecutable del sistema está disponible para todos los desarrolladores del equipo. Debe haber un lugar bien conocido donde los desarrolladores puedan hacer referencia al artefacto.

## Observabilidad de la integración

Los cambios de estado aplicados a la compilación principal deben estar disponibles y ser comunicados a todo el equipo. La centralización de los logs y el estado de los fallos es esencial para los desarrolladores que investigan las compilaciones falladas.
Recomendamos integrar Teams o Slack con las ejecuciones CI/CD, lo que ayuda a mantener al equipo continuamente conectado a los fallos y al estado de las compilaciones.

### Dashboard de alto nivel de integración continua

* Los proveedores de integración continua modernos tienen la capacidad de consolidar e informar del estado de la compilación en un dashboard determinado.
* Tu dashboard de integración continua debería ser capaz de correlacionar un fallo de compilación con un commit de git.

### Badge del estado de compilación en el readme del proyecto

* Debería haber una badge del estado de la compilación incluida en el README raíz del proyecto.

### Notificaciones de compilación

* Tu proceso de CI debería estar configurado para enviar notificaciones a plataformas de mensajería como Teams / Slack una vez que la compilación se complete. Recomendamos crear un canal separado para ayudar a consolidar y aislar estas notificaciones.

## Recursos

* [Mejores prácticas de integración continua de Martin Fowler](https://martinfowler.com/articles/continuousIntegration.html)
* [Pipelines multietapa de Azure DevOps](https://docs.microsoft.com/en-us/azure/devops/pipelines/get-started/multi-stage-pipelines-experience?view=azure-devops)
* [Conceptos clave de Azure Pipeline](https://docs.microsoft.com/en-us/azure/devops/pipelines/get-started/key-pipelines-concepts?view=azure-devops)
* [Entornos de Azure Pipeline](https://docs.microsoft.com/en-us/azure/devops/pipelines/process/environments?view=azure-devops)
* [Artefactos en Azure Pipelines](https://docs.microsoft.com/en-us/azure/devops/pipelines/artifacts/artifacts-overview?view=azure-devops&tabs=nuget)
* [Permisos y roles de seguridad en Azure Pipeline](https://docs.microsoft.com/en-us/azure/devops/pipelines/policies/permissions?view=azure-devops)
* [Aprobaciones y comprobaciones del entorno de Azure](https://docs.microsoft.com/en-us/azure/devops/pipelines/process/approvals?view=azure-devops&tabs=check-pass)
* [Proveedor de Terraform Azure DevOps](https://github.com/microsoft/terraform-provider-azuredevops)
* [Guía de inicio de Terraform con Azure](https://learn.hashicorp.com/collections/terraform/azure-get-started)
* [Configuración de Terraform Remote State Azure](https://docs.microsoft.com/en-us/azure/developer/terraform/store-state-in-azure-storage?tabs=azure-cli)
* [Terratest - Marco de infraestructura de unidades e integración](https://terratest.gruntwork.io/)
* [Documentación Bicep](https://docs.microsoft.com/en-us/azure/azure-resource-manager/bicep/)
* [Ejemplos de Bicep](https://github.com/Azure/bicep)
