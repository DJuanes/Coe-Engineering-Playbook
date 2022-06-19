# Observabilidad de pipelines de CI/CD

Con la creciente complejidad de las canalizaciones de entrega, es muy importante tener en cuenta la Observabilidad en el contexto de la creación y el release de aplicaciones.

## Beneficios

* Tener la instrumentación adecuada durante el tiempo de compilación ayuda a obtener información sobre las diversas etapas del proceso de compilación y release.
* Ayuda a los desarrolladores a comprender dónde se encuentran los cuellos de botella en el rendimiento de la canalización, según los datos recopilados. Esto ayuda a tener conversaciones basadas en datos sobre la identificación de latencia entre trabajos, problemas de rendimiento, tiempos de carga/descarga de artefactos, lo que proporciona información valiosa sobre la disponibilidad y la capacidad de los agentes.
* Ayuda a identificar tendencias en fallas, lo que permite a los desarrolladores realizar rápidamente un análisis de causa raíz.
* Ayuda a proporcionar una vista de toda la organización del estado de la canalización para identificar fácilmente las tendencias.

## Puntos a considerar

* Es importante identificar los KPIs para evaluar un pipeline de CI/CD exitoso. Cuando sea necesario, se puede agregar un seguimiento adicional para registrar mejor las métricas de KPI.
* Los informes básicos sobre las canalizaciones están disponibles de forma inmediata. Es importante evaluar estos informes con respecto a los KPI para comprender si se necesita una solución de informes personalizados para sus canalizaciones. Si es necesario, se pueden crear paneles personalizados con herramientas de terceros como Grafana o Power BI Dashboards.
