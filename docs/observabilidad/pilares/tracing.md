# Tracing

## Visión general

Produce la información necesaria para observar series de operaciones correlacionadas en un sistema distribuido. Una vez recopilados, muestran la ruta, las medidas y las fallas en una transacción de extremo a extremo.

## Mejores prácticas

* Asegúrese de que se rastreen al menos las transacciones clave.
* Incluya en cada traza la información necesaria para identificar las versiones de software. Esto es importante para correlacionar las implementaciones y la degradación del sistema.
* Asegúrese de que las dependencias estén incluidas en la traza.
* Si los costos son una preocupación, use el muestreo, evitando descartar errores, comportamientos inesperados e información crítica.
* No reinvente la rueda, utilice las herramientas existentes para recopilar y analizar los datos.
* Asegúrese de que se sigan las políticas y restricciones de información de identificación personal.

## Herramientas recomendadas

* [Azure Monitor](https://docs.microsoft.com/es-es/azure/azure-monitor/overview): incluye métricas del sistema, análisis de logs y más.
* [Jaeger Tracing](https://www.jaegertracing.io/): traceo distribuido de extremo a extremo de código abierto.
* [Grafana](https://grafana.com/): herramienta de visualización y dashboard de código abierto. Admite orígenes de datos de log, métricas y seguimiento distribuido.

Considere usar OpenTelemetry ya que implementa la propagación de contexto multiplataforma de código abierto para transacciones distribuidas de extremo a extremo sobre componentes heterogéneos listos para usar. Se encarga de crear y administrar automáticamente el objeto Trace Context entre una pila completa de microservicios implementados en diferentes pilas técnicas.
