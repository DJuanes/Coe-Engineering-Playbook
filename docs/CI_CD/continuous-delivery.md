# Continuous Delivery

La inspiración detrás de la entrega continua es entregar constantemente software valioso a los usuarios con mayor frecuencia. La aplicación de los principios y prácticas expuestos en este documento le ayudará a reducir el riesgo, eliminar las operaciones manuales y aumentar la calidad y la confianza.
El despliegue de software implica los siguientes principios:

* Aprovisionar y gestionar el tiempo de ejecución del entorno de la nube para su aplicación.
* Instalar la versión de la aplicación de destino en sus entornos de nube.
* Configurar su aplicación, incluyendo los datos necesarios.

Una canalización de entrega continua es una manifestación automatizada de su proceso para agilizar estos mismos principios de forma coherente y repetible.

## Objetivo

* Seguir las mejores prácticas de la industria para entregar los cambios de software a los clientes.
* Establecer la coherencia de los principios rectores y las mejores prácticas al ensamblar flujos de trabajo de entrega continua.

## Guía general

### Definir una estrategia de release

Es importante establecer un entendimiento común en torno a la estrategia/diseño de release durante la fase de planificación de un proyecto. Este entendimiento incluye el despliegue y el mantenimiento de la aplicación a lo largo de su SDLC.

#### Principios de la estrategia de release

Continuous Delivery por Jez Humble, David Farley cubren las consideraciones clave a seguir cuando se crea una estrategia de release:

* Partes encargadas de los despliegues en cada entorno, así como encargadas del release.
* Estrategia de gestión de activos y configuración.
* Enumeración de los entornos disponibles para las pruebas de aceptación, capacidad, integración y aceptación por parte del usuario, así como el proceso por el que se moverán las compilaciones a través de estos entornos.
* Descripción de los procesos que se seguirán para el despliegue en los entornos de prueba y producción, como las solicitudes de cambio que se abrirán y las aprobaciones que deben concederse.
* Descripción del método por el que se gestionará la configuración en tiempo de despliegue y de ejecución de la aplicación, y cómo se relaciona esto con el proceso de despliegue automatizado.
* Descripción de la integración con cualquier sistema externo. ¿En qué fase y cómo se prueban como parte de un release? ¿Cómo se comunica el operador técnico con el proveedor en caso de problema?
* Un plan de recuperación de desastres para poder recuperar el estado de la aplicación tras un desastre. ¿Qué pasos habrá que dar para reiniciar o volver a desplegar la aplicación en caso de que falle?
* Planificación del tamaño y la capacidad de producción: ¿Cuántos datos creará su aplicación en vivo? ¿Cuántos archivos de log o bases de datos necesitará? ¿Cuánto ancho de banda y espacio en disco necesitará? ¿Qué latencia esperan los clientes?
* Cómo funciona el despliegue inicial en producción.
* Cómo se gestionará la corrección de defectos y la aplicación de parches en el entorno de producción.
* Cómo se gestionarán las actualizaciones del entorno de producción, incluida la migración de datos. Cómo se llevarán a cabo las actualizaciones de la aplicación sin destruir su estado.

### Release de la aplicación y promoción del entorno

Su proceso de release debe tomar el artefacto de compilación desplegable creado desde su etapa de commit y desplegarlo en todos los entornos de la nube, comenzando con su entorno de test.
El entorno de test actúa como una puerta para validar si su conjunto de pruebas se completa con éxito. Esta validación siempre debe comenzar en un entorno de prueba mientras se inspecciona la versión desplegada integrada desde la rama de features / release que contiene sus cambios de código.
Los cambios de código liberados en el entorno de pruebas suelen tener como objetivo la rama principal o la rama de release.

#### El primer despliegue

El primer despliegue de cualquier aplicación debe mostrarse al cliente en un entorno similar al de producción (UAT) para solicitar su opinión desde el principio. El entorno de UAT se utiliza para obtener la aceptación del propietario del producto y, en última instancia, promover el release a producción.

#### Criterios para un entorno similar al de producción

* Ejecuta el mismo sistema operativo que producción.
* Tiene instalado el mismo software que producción.
* Tiene el mismo tamaño y configuración que producción.
* Refleja la topología de red de producción.
* Se ejecutan pruebas de carga simuladas similares a las de producción después de un release para hacer visible cualquier degradación de la latencia o el rendimiento.

#### Modelado del pipeline de release

Es fundamental modelar su proceso de prueba y release para establecer un entendimiento común entre los ingenieros de aplicaciones y las partes interesadas del cliente. Específicamente, alinear las expectativas de cuántos entornos de nube deben ser pre-aprovisionados, así como definir las funciones y responsabilidades.

#### Etapas del pipeline de release

El pipeline de release debe tener en cuenta las siguientes condiciones:

* Selección del release: El desarrollador que lleva a cabo las pruebas de la aplicación debe tener la capacidad de seleccionar la versión de release que va a desplegar en el entorno de test.
* Despliegue: liberar el artefacto de compilación desplegable de la aplicación en el entorno de nube de destino.
* Configuración: Las aplicaciones deben ser configuradas de forma consistente en todos sus entornos. Esta configuración se aplica en el momento del despliegue. Los datos confidenciales, como los secretos y certificados de la aplicación, deben estar guardados en un almacén de claves y secretos de PaaS totalmente gestionado. Todos los secretos utilizados por la aplicación deben obtenerse internamente dentro de la propia aplicación. Los secretos no deberían estar expuestos dentro del entorno de ejecución.
* Migración de datos: Prepueble el estado de la aplicación y/o los registros de datos que se necesitan para su entorno de tiempo de ejecución. Esto también puede incluir los datos de prueba necesarios para su conjunto de pruebas de integración.
* Prueba de humo de despliegue. Su prueba de humo también debe verificar que su aplicación está apuntando a la configuración correcta.
* Realice cualquier escenario de prueba de aceptación manual o automatizada.
* Apruebe la puerta de release para promover la versión de la aplicación al entorno de la nube de destino.

#### Releases de preproducción

Las aplicaciones candidatas deben desplegarse en un entorno similar al de producción para llevar a cabo las pruebas finales manuales/automatizadas (incluidas las pruebas de capacidad).

### Reversión de releases

Su estrategia de release debe tener en cuenta los escenarios de reversión en caso de fallos inesperados después de un despliegue.
La reversión de releases puede ser complicada. Si no hay cambios en los datos que deban ser revertidos, entonces puede simplemente activar un nuevo release candidato para la última versión de producción conocida y promover ese release a lo largo de su pipeline de CD.

## Referencias

* [Entrega continua](https://www.continuousdelivery.com/) por Jez Humble, David Farley.
* [Integración continua vs. entrega continua vs. despliegue continuo](https://www.atlassian.com/continuous-delivery/principles/continuous-integration-vs-delivery-vs-deployment)
* [Anillos de despliegue](https://docs.microsoft.com/en-us/azure/devops/migrate/phase-rollout-with-rings?view=azure-devops)

### Herramientas

* [Flux](https://fluxcd.io/docs/concepts/) para gitops
* [Flujo de trabajo CI/CD usando GitOps](https://docs.microsoft.com/es-es/azure/azure-arc/kubernetes/conceptual-gitops-ci-cd#example-workflow)
* [Tekton](https://github.com/tektoncd) para pipelines nativos de Kubernetes
* [Argo Workflows](https://github.com/argoproj/argo-workflows)
* [Flagger](https://github.com/fluxcd/flagger) para potentes lanzamientos nativos de Kubernetes, incluyendo blue/green, canary y A/B testing.
* No está muy relacionado con Kubernetes, pero echa un vistazo a [jsonnet](https://jsonnet.org/), un lenguaje de plantillas para reducir la repetición de tareas y aumentar el intercambio entre sus manifiestos yaml/json.
