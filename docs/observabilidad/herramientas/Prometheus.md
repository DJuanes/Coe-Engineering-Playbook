# Prometheus

## Visión general

Es un conjunto de herramientas de monitoreo y alerta de código abierto basado en datos de métricas de series temporales. Se ha convertido en una solución de métrica estándar de facto en el mundo nativo de la nube y se usa ampliamente con Kubernetes.
El núcleo de Prometheus es un servidor que extrae y almacena métricas. Hay otras numerosas características y componentes opcionales, como un administrador de alertas y bibliotecas de clientes para lenguajes de programación para ampliar las funcionalidades de Prometheus más allá de lo básico.

## ¿Por qué Prometheus?

* Prometheus es una base de datos de series de tiempo y permite rastrear, monitorear y agregar eventos o mediciones a lo largo del tiempo.
* Prometheus es una herramienta basada en extracción. También es compatible con el modelo push para impulsar métricas.
* La visualización de la serie temporal se puede realizar directamente a través de su interfaz de usuario web.
* Prometheus proporciona un potente lenguaje de consulta funcional llamado PromQL (Prometheus Query Language) que permite al usuario agregar datos de series temporales en tiempo real.

## Integración con otras herramientas

Las bibliotecas de cliente de Prometheus le permiten agregar instrumentación a su código y exponer métricas internas a través de un endpoint HTTP. Las bibliotecas de cliente oficiales de Prometheus actualmente son Go, Java o Scala, Python y Ruby. Las bibliotecas de terceros no oficiales incluyen: .NET/C#, Node.js y C++.
El formato de métricas de Prometheus es compatible con una amplia gama de herramientas y servicios, que incluyen:

* [Azure Monitor](https://docs.microsoft.com/en-us/azure/azure-monitor/containers/container-insights-prometheus-integration)
* [Stackdriver](https://cloud.google.com/stackdriver/docs/solutions/gke/prometheus)
* [Datadog](https://docs.datadoghq.com/integrations/prometheus/)
* [CloudWatch](https://aws.amazon.com/blogs/containers/using-prometheus-metrics-in-amazon-cloudwatch/)
* [New Relic](https://docs.newrelic.com/docs/integrations/prometheus-integrations/get-started/send-prometheus-metric-data-new-relic/)
* [Flagger](https://docs.flagger.app/tutorials/prometheus-operator)
* [Grafana](https://grafana.com/docs/grafana/latest/getting-started/getting-started-prometheus/)
* [GitLab](https://docs.gitlab.com/ee/user/project/integrations/prometheus.html)
* [etc...](https://prometheus.io/docs/operating/integrations/)

Existen numerosos [exportadores](https://prometheus.io/docs/instrumenting/exporters/) que se utilizan para exportar métricas existentes desde bases de datos, hardware, herramientas de CI/CD, sistemas de mensajería, API y otros sistemas de monitoreo de terceros. Además de las bibliotecas de clientes y los exportadores, existe una cantidad importante de [puntos de integración](https://prometheus.io/docs/operating/integrations/) para el descubrimiento de servicios, el almacenamiento remoto, las alertas y la gestión.

## Referencias

* [Documentos de Prometheus](https://prometheus.io/docs)
* [Mejores prácticas de Prometheus](https://prometheus.io/docs/practices)
* [Grafana con Prometheus](https://prometheus.io/docs/visualization/grafana/)
