# Métricas

## Visión general

Las métricas proporcionan un flujo de datos casi en tiempo real, informando a los operadores y partes interesadas sobre las funciones que está realizando el sistema, así como sobre su estado. A diferencia del logeo y el traceo, los datos métricos tienden a ser más eficientes para transmitir y almacenar.

## Métodos de recolección

Los enfoques de recopilación de métricas se dividen en dos categorías: métricas push y métricas pull. Métricas push significa que el componente de origen envía los datos a un servicio o agente remoto. [Azure Monitor](https://azure.microsoft.com/es-es/services/monitor/) y [statsd](https://github.com/statsd/statsd) son ejemplos de métricas push. Algunos puntos fuertes de las métricas push incluyen:

* Solo requiere la salida de red al destino remoto.
* El componente de origen controla la frecuencia de medición.
* Configuración simplificada ya que el componente solo necesita saber el destino de donde enviar los datos.

Algunas desventajas con este enfoque:

* A escala, es mucho más difícil controlar las velocidades de transmisión de datos, lo que puede provocar la limitación del servicio o pérdida de los valores.
* Es difícil determinar si cada componente está en buen estado y enviando datos.

En el caso de las métricas pull, cada componente de origen publica un endpoint para que el agente de métricas se conecte y recopile las mediciones. [Prometheus](https://prometheus.io/) y su ecosistema de herramientas son un ejemplo de métricas de estilo pull. Los beneficios experimentados al usar una configuración de métricas pull pueden implicar:

* Configuración única para determinar qué se mide y la frecuencia de medición para el entorno local.
* Cada objetivo de medición tiene una metamétrica relacionada con si la recopilación es exitosa o no, que se puede usar como un control de salud general.
* Compatibilidad con el enrutamiento, el filtrado y el procesamiento de métricas antes de enviarlas a un almacén de métricas central global.

Los elementos de preocupación para algunos pueden incluir:

* La configuración y gestión de fuentes de datos puede dar lugar a una configuración compleja.
* La configuración de la red puede agregar más complejidad si es necesario administrar los firewalls y otras ACL para permitir la conectividad.

## Mejores prácticas

### ¿Cuándo debo usar métricas en lugar de logs?

[Logs vs Métricas vs Trazas](../log-vs-metric-vs-trace.md) cubre una guía de alto nivel sobre cuándo utilizar datos métricos y cuándo usar datos de log. Ambos tienen un papel valioso que desempeñar en la creación de sistemas observables.

### ¿Qué se debe medir?

Mediciones críticas del sistema que se relacionan con el estado de la aplicación/máquina, suelen ser excelentes candidatos para alertas. Trabaje con sus colegas de ingeniería y desarrollo para identificar las métricas, pero pueden incluir:

* Utilización de CPU y memoria.
* Tasa de request.
* Longitud de la cola.
* Recuento de excepciones inesperado.
* Métricas de servicio dependientes.

Medidas importantes relacionadas con el negocio, que impulsan la presentación de informes a las partes interesadas. Consulte con las diversas partes interesadas del componente, pero algunos ejemplos pueden incluir:

* Trabajos realizados.
* Duración de la sesión de usuario.
* Visitas al sitio.

### Etiquetas de dimensión

Los sistemas métricos modernos suelen definir una única métrica de serie temporal como la combinación del nombre de la métrica y su diccionario de etiquetas de dimensión. Las etiquetas son una forma excelente de distinguir una instancia de una métrica de otra y, al mismo tiempo, permitir que se realicen agregaciones y otras operaciones en el conjunto para el análisis. Algunas etiquetas comunes utilizadas en las métricas pueden incluir:

* Nombre del contenedor
* Nombre de host
* Versión de código
* Nombre del clúster de Kubernetes
* Región de Azure

## Herramientas recomendadas

* [Azure Monitor](https://docs.microsoft.com/es-es/azure/azure-monitor/overview): servicio que incluye métricas del sistema, análisis de log y más.
* [Prometheus](https://prometheus.io/): una aplicación de monitoreo y alerta en tiempo real. Su formato de exposición para exponer series temporales es la base del formato estándar de OpenMetrics.
* [Thanos](https://thanos.io/): configuración de Prometheus de código abierto y alta disponibilidad con capacidades de almacenamiento a largo plazo.
* [Cortex](https://cortexmetrics.io/): Prometheus a largo plazo, escalable horizontalmente, de alta disponibilidad y multiusuario.
* [Grafana](https://grafana.com/): herramienta de visualización y panel de control de código abierto. Admite orígenes de datos de logs, métricas y trazas distribuidas.
