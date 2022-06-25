# Herramientas y Patrones

Hay una serie de herramientas modernas para hacer que los sistemas sean observables. Al identificar y/o crear herramientas que funcionen para su sistema, aquí hay algunas cosas que debe considerar para ayudar a guiar las opciones.

* Debe ser simple de integrar y fácil de usar.
* Debe ser posible agregar y visualizar datos.
* Las herramientas deben proporcionar datos en tiempo real.
* Debe ser capaz de guiar a los usuarios al área del problema con un contexto apropiado de extremo a extremo.

## Opciones

* [Loki](loki.md)
* [OpenTelemetry](OpenTelemetry.md)
* [Kubernetes Dashboards](KubernetesDashboards.md)
* [Prometheus](Prometheus.md)

## Malla de servicio (Service Mesh)

Aprovechar una malla de servicio que sigue el patrón [Sidecar](https://www.oreilly.com/library/view/designing-distributed-systems/9781491983638/ch02.html#:~:text=The%20sidecar%20pattern%20is%20a,first%20is%20the%20application%20container.&text=In%20addition%20to%20the%20application,without%20the%20application%20container's%20knowledge.) configura rápidamente un conjunto de métricas y trazas.
Un sidecar funciona interceptando todo el tráfico entrante y saliente hacia su imagen. Luego agrega encabezados de seguimiento a cada solicitud y emite un conjunto estándar de logs y métricas. Estas métricas son extremadamente poderosas para la observabilidad, lo que permite que cada servicio, ya sea del lado del cliente o del lado del servidor, aproveche un conjunto unificado de métricas, que incluyen:

* Latencia
* Bytes
* Tasa de solicitud
* Tasa de error
