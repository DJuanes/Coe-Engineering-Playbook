# Dashboard

## Visión general

El dashboard es una forma de visualización que proporciona de un vistazo los indicadores clave de rendimiento (KPI) del sistema observable. Conectan múltiples fuentes de datos. El dashboard se puede utilizar para:

* Mostrar tendencias
* Identificar patrones
* Medir la eficiencia fácilmente
* Identificar datos atípicos y correlaciones
* Ver el estado de salud o el rendimiento del sistema
* Dar una perspectiva del KPI que es importante para un negocio/proceso

## Mejores prácticas

Las preguntas comunes que debe hacerse al crear un dashboard serían:

* ¿Dónde pasó la mayor parte de su tiempo el usuario?
* ¿Qué busca el usuario?
* ¿Cómo puedo ayudar mejor a mi equipo con alertas y solución de problemas?
* ¿Estuvo el sistema en buen estado durante el último día/semana/mes/trimestre?

Estos son los principios que se deben tener en cuenta al crear dashboards:

* Separe un dashboard en varias secciones para simplificar. Agregar salto de página o ancla (#sección) también es una ventaja, si corresponde.
* Agregue gráficos múltiples y simples. Cree gráficos simples, tenga más de ellos en lugar de un gráfico complicado todo en uno.
* Identifique objetivos o medición de KPI.
* Haga preguntas que puedan ayudar a alcanzar el objetivo o KPI definido.
* Valide las preguntas. Esto se hace a menudo con los stakeholders, patrocinadores, líderes o gerentes de proyecto.
* Observe el dashboard que se construye. ¿Reflejan los datos lo que las partes interesadas se propusieron responder?
* Recuerde siempre que este proceso lleva tiempo. Construir un dashboard es fácil, construir un dashboard observable para mostrar un patrón es difícil.

## Herramientas recomendadas

* [Azure Monitor Workbooks](https://docs.microsoft.com/es-es/azure/azure-monitor/visualize/workbooks-overview): Azure Workbooks, compatible con Markdown, está estrechamente integrado con los servicios de Azure, lo que lo hace altamente personalizable sin necesidad de herramientas adicionales.
* [Creación y uso compartido de paneles de datos de Log Analytics](https://docs.microsoft.com/es-es/azure/azure-monitor/visualize/tutorial-logs-dashboards): dashboard que se puede crear mediante consultas de log en los datos de Log Analytics.
* [Creación de paneles de indicadores clave de rendimiento (KPI) personalizados con Azure Application Insights](https://docs.microsoft.com/es-es/azure/azure-monitor/app/tutorial-app-dashboards): los dashboard también se pueden crear con Application Insights.
* [Creación de un panel de Power BI desde un informe](https://docs.microsoft.com/en-us/power-bi/create-reports/service-dashboard-create): Power Bi es una de las herramientas más sencillas para crear dashboards a partir de fuentes de datos y reportes.
* [Grafana](https://grafana.com/tutorials/): Grafana es una popular herramienta de código abierto para dashboard y visualización.
* [Azure Monitor como origen de datos de Grafana](https://grafana.com/grafana/plugins/grafana-azure-monitor-datasource/): proporciona una integración paso a paso de Azure Monitor con Grafana.
* [Breve comparación de varias herramientas](https://docs.microsoft.com/es-es/azure/azure-monitor/best-practices-analysis).

## Ejemplos y recetas de dashboard

### Azure Workbooks

* Análisis de rendimiento: una medida de cómo funciona el sistema. Plantilla disponible en la galería.
* Análisis de fallas: un informe sobre fallas del sistema con detalles. Plantilla disponible en la galería.
* Índice de rendimiento de la aplicación (Appdex): esta es una forma de medir la satisfacción del usuario. Clasifica el rendimiento en tres zonas en función de un umbral de rendimiento de referencia T. La plantilla para Appdex también está disponible en la galería de Azure Workbooks.

### Application Insights

* [Análisis de retención de usuarios para aplicaciones web con Application Insights](https://docs.microsoft.com/es-es/azure/azure-monitor/app/usage-retention).
* [Análisis de patrones de navegación del usuario mediante flujos de usuarios de Application Insights](https://docs.microsoft.com/es-es/azure/azure-monitor/app/usage-flows).
* [Use Azure Application Insights para entender la forma en que los clientes utilizan su aplicación](https://docs.microsoft.com/es-es/azure/azure-monitor/app/tutorial-users).

### Grafana con Azure Monitor como fuente de datos

* [Azure Kubernetes Service - Métricas de clúster y espacio de nombres](https://grafana.com/grafana/dashboards/10956): Métricas de Container Insights para clústeres de Kubernetes. Utilización del clúster, utilización del espacio de nombres, CPU y memoria del nodo, uso del disco del nodo y E/S del disco, red del nodo y métricas de operación de kubelet docker.
* [Azure Kubernetes Service - Nivel de contenedor y métricas de pod](https://grafana.com/grafana/dashboards/14891): contiene el nivel de contenedor y las métricas de pod, como CPU y memoria, que faltan en el dashboard anterior.

## Resumen

Para crear un dashboard observable, el objetivo es hacer uso de las métricas, los logs y las trazas recopiladss para dar una idea de cómo funciona el sistema, cómo se comporta el usuario e identificar patrones. Hay muchas herramientas y plantillas. Cualquiera que sea la elección, un buen tablero siempre es un tablero que puede ayudarlo a responder preguntas sobre el sistema y el usuario, realizar un seguimiento del KPI y el objetivo y, al mismo tiempo, permitir que se tomen decisiones comerciales informadas.
