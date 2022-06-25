# Kubernetes UI Dashboards

Este documento cubre las opciones y los beneficios de varios Kubernetes UI Dashboards, que son herramientas útiles para monitorear y depurar su aplicación en clústeres de Kubernetes.

## Ventajas y casos de uso

* Permite la capacidad de ver, administrar y monitorear los aspectos operativos del clúster de Kubernetes.
* Los beneficios de usar un dashboard de interfaz de usuario incluyen lo siguiente:
  * Ver una descripción general del clúster
  * Implementar aplicaciones en el clúster
  * Solucionar problemas de aplicaciones que se ejecutan en el clúster
  * Ver, crear, modificar y eliminar recursos de Kubernetes
  * Ver métricas básicas de recursos, incluido el uso de recursos para objetos de Kubernetes
  * Ver y acceder a los registros
  * Ver en vivo el estado de los pods
* Diferentes dashboards pueden proporcionar diferentes funcionalidades, y el caso de uso para elegir un dashboard en particular dependerá de los requisitos.

## Open Source Dashboards

Actualmente hay varios dashboards disponibles para monitorear sus aplicaciones o administrarlas con Kubernetes:

* [Octant](https://github.com/vmware-tanzu/octant)
* [Prometheus y Grafana](https://prometheus.io/docs/visualization/grafana/)
  * [Kube Prometheus Stack Chart](https://github.com/prometheus-community/helm-charts/tree/main/charts/kube-prometheus-stack): proporciona una manera fácil de operar el monitoreo de clústeres de Kubernetes de un extremo a otro con Prometheus utilizando Prometheus Operator.
* [K8Dash](https://github.com/skooner-k8s/skooner)
* [kube-ops-view](https://github.com/hjacobs/kube-ops-view): una herramienta para visualizar la ocupación y utilización de nodos
* [Lens](https://k8slens.dev/): herramienta de escritorio del lado del cliente
* [Thanos](https://github.com/thanos-io/thanos) y [Cortex](https://cortexmetrics.io/docs/): implementaciones multiclúster

## Referencias

* [Alternativas a Kubernetes Dashboard](https://octopus.com/blog/alternative-kubernetes-dashboards)
* [Prometheus y Grafana con Kubernetes](https://tanzu.vmware.com/developer/guides/observability-prometheus-grafana-p1/)
