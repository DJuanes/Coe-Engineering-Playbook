# Logging

## Visión general

Los logs son eventos discretos con el objetivo de ayudar a los ingenieros a identificar las áreas problemáticas durante las fallas.

## Métodos de recolección

Dos de las técnicas estándar son un enfoque de escritura directa o basado en agentes.
Los eventos de log escritos directamente se manejan en el proceso del componente en particular, generalmente utilizando una biblioteca provista. Azure Monitor tiene capacidades de envío directo, pero no se recomienda para un uso serio o de producción. Este enfoque tiene algunas ventajas:

* No hay un proceso externo para configurar o monitorear
* Sin administración de archivos de log para evitar problemas de falta de espacio en disco.

Desventajas potenciales de este enfoque:

* Uso de memoria potencialmente mayor si la biblioteca en particular está usando un búfer respaldado por memoria.
* En el caso de una interrupción prolongada del servicio, los datos de log pueden perderse o truncarse debido a las limitaciones del búfer.
* El logeo de procesos de múltiples componentes administrará y emitirá logs individualmente, lo que puede ser más complejo de administrar.

La recopilación de logs basada en agentes se basa en un proceso externo que se ejecuta en la máquina host, y el componente en particular emite datos de log estándar o archivo. Escribir datos de log en stdout es la práctica preferida cuando se ejecutan aplicaciones dentro de un entorno de contenedor como Kubernetes. El runtime del contenedor redirige la salida a los archivos, que luego puede procesar un agente. [Azure Monitor](https://azure.microsoft.com/es-es/services/monitor/), [Grafana Loki](https://github.com/grafana/loki), [Logstash](https://www.elastic.co/es/logstash/) y [Fluent Bit](https://fluentbit.io/) son ejemplos de agentes de envío de logs.
Hay varias ventajas cuando se utiliza un agente para recopilar y enviar archivos de log:

* Configuración centralizada.
* Recopilación de múltiples fuentes de datos con un solo proceso.
* Preprocesamiento local y filtrado de datos de log antes de enviarlos a un servicio central.
* Utilizar el espacio en disco como un búfer de datos durante una interrupción del servicio.

Este enfoque no está exento de desventajas:

* Se requieren recursos exclusivos de CPU y memoria para el procesamiento de datos de log.
* Espacio de disco persistente para almacenamiento en búfer.

## Mejores prácticas

* Preste atención a los niveles de log. Registrar demasiado aumentará los costos y disminuirá el rendimiento de la aplicación.
* Asegúrese de que la configuración de log se pueda modificar sin cambios de código.
* Si está disponible, aproveche los niveles de log por categoría que permiten una configuración de log granular.
* Verifique los niveles de log antes de iniciar sesión, evitando así asignaciones y costos de manipulación de cadenas.
* Asegúrese de que las versiones de servicio estén incluidas en los logs para poder identificar versiones problemáticas.
* Loguee una excepción generada solo una vez. En sus controladores, solo detecte las excepciones esperadas que pueda manejar correctamente.
* Ajuste los niveles de log en producción. Durante una nueva versión, la verbosidad se puede aumentar para facilitar la identificación de errores.
* Si utiliza muestreo, impleméntelo en el nivel de servicio en lugar de definirlo en el sistema de log. De esta manera tenemos control sobre lo que se registra.
* Incluya solo fallas de controles de estado y solicitudes no del negocio.
* Asegúrese de que un mal funcionamiento del sistema no provoque el almacenamiento de logs repetitivos.
* No reinvente la rueda, utilice las herramientas existentes para recopilar y analizar los datos.
* Asegúrese de que se sigan las políticas y restricciones de información de identificación personal.
* Asegúrese de que se capturen y registren los errores y las excepciones en los servicios dependientes.

### Si hay suficientes datos de log, ¿es necesario instrumentar métricas?

[Logs vs Métricas vs Trazas](../log-vs-metric-vs-trace.md) cubre una guía de alto nivel sobre cuándo utilizar datos métricos y cuándo usar datos de log. Ambos tienen un papel valioso que desempeñar en la creación de sistemas observables.

### ¿Tiene problemas para identificar qué loguear?

Al inicio de la aplicación:

* Errores irrecuperables desde el inicio.
* Advertencias si la aplicación aún se puede ejecutar, pero no como se esperaba.
* Información sobre el estado del servicio al inicio (número de compilación, configuraciones cargadas, etc.)

Por solicitud entrante:

* Información básica para cada solicitud entrante: la URL, cualquier dimensión de usuario/inquilino/solicitud, código de respuesta devuelto, latencia, tamaño de carga útil, recuentos de logs, etc.
* Advertencia por cualquier excepción inesperada, detectada solo en el controlador/interceptor superior y logeada con o junto a la información de solicitud, con seguimiento de pila.

Por solicitud saliente:

* Información básica para cada solicitud saliente: la URL, cualquier dimensión de usuario/inquilino/solicitud, código de respuesta devuelto, latencia, tamaños de carga útil, recuentos de logs devueltos, etc.

## Herramientas recomendadas

* [Azure Monitor](https://docs.microsoft.com/es-es/azure/azure-monitor/overview): incluye métricas del sistema, análisis de logs y más.
* [Grafana Loki](https://grafana.com/oss/loki/): una plataforma de agregación de logs de código abierto, basada en los aprendizajes de la comunidad de Prometheus para la recopilación y el almacenamiento altamente eficientes de datos de log a escala.
* [The Elastic Stack](https://www.elastic.co/es/what-is/elk-stack): una pila tecnológica de análisis de logs de código abierto que utiliza Logstash, Beats, Elastic Search y Kibana.
* [Grafana](https://grafana.com/): herramienta de visualización y dashboard de código abierto. Admite orígenes de datos de log, métricas y seguimiento distribuido.
