# Loki

Loki es un sistema de agregación de registros multiusuario, de alta disponibilidad y escalable horizontalmente, creado por Grafana Labs inspirado en los aprendizajes de Prometheus. Ambas herramientas siguen la misma arquitectura, que es un agente que recopila métricas en cada uno de los componentes del sistema de software, un servidor que almacena los registros y también el tablero de Grafana, que accede al servidor loki para construir sus visualizaciones y consultas. Loki tiene tres componentes principales:

## Promtail

Es la parte agente de Loki. Se puede usar para tomar registros de varios lugares, como var/log/ por ejemplo. La configuración de Promtail es un archivo yaml llamado ```config-promtail.yml```. En este archivo, se describen todas las rutas y fuentes de registro que se agregarán en Loki Server.

## Loki Server

Es responsable de recibir y almacenar todos los registros recibidos de todos los diferentes sistemas.

## Grafana Dashboards

Son responsables de crear las visualizaciones y realizar consultas.

## ¿Por qué usar Loki?

La razón principal para usar Loki en lugar de otras herramientas de agregación de registros es que Loki optimiza el almacenamiento necesario. Lo hace siguiendo el mismo patrón que Prometheus, que indexa las etiquetas y crea fragmentos del propio registro, utilizando menos espacio que simplemente almacenando los registros sin procesar.

## Referencias

* [Sitio oficial de Loki](https://grafana.com/oss/loki/)
* [Insertar logs en Loki](https://grafana.com/docs/loki/latest/getting-started/get-logs-into-loki/)
* [Agregar fuente de Loki a Grafana](https://grafana.com/docs/grafana/latest/datasources/loki/#adding-the-data-source)
* [Mejores prácticas de Loki](https://grafana.com/docs/loki/latest/best-practices/)
