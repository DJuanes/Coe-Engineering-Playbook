# Logs vs Métricas vs Trazas

## Métricas

Su propósito es informar sobre la salud y las operaciones con respecto a un componente o sistema. Una métrica representa una medida de un punto en el tiempo de una fuente en particular. Las métricas también se prestan muy bien a la agregación previa dentro del componente antes de la recopilación, lo que reduce el costo de cómputo para procesar y almacenar grandes cantidades de series temporales. Debido a la eficiencia con la que se procesan y almacenan las métricas, se presta muy bien para su uso en alertas automatizadas.

## Logs

Informan sobre los eventos discretos que ocurrieron dentro de un componente o un conjunto de componentes. Estos datos enriquecidos tienden a ser mucho más grandes que los datos métricos y pueden causar problemas de procesamiento, especialmente si los componentes se registran de forma demasiado detallada. Por lo tanto, el uso de datos de log tiende a evitarse y depende de las métricas para esos datos. Una vez que la telemetría resalta las posibles fuentes de problemas, los datos de log filtrados para esas fuentes se pueden usar para comprender lo que ocurrió.

## Trazas

A diferencia del logueo, abarca una vista mucho más amplia y continua de una aplicación. El objetivo es seguir el flujo de un programa y la progresión de los datos.
Su propósito no es reactivo, sino que se centra en la optimización. Al tracear a través de una pila, los desarrolladores pueden identificar cuellos de botella y enfocarse en mejorar el rendimiento.
Cuando ocurre un problema, el tracing le permite ver cómo llegó allí:

* Cual función.
* La duración de la función.
* Parámetros pasados.

## Guía de uso

* Utilice métricas para realizar un seguimiento de la ocurrencia de un evento, el conteo de elementos, el tiempo necesario para realizar una acción o para informar el valor actual de un recurso (CPU, memoria, etc.)
* Utilice logs para realizar un seguimiento de la información detallada sobre un evento también supervisado por una métrica, en particular errores, advertencias u otras situaciones excepcionales.
* Una traza proporciona visibilidad sobre cómo se procesa una solicitud en varios servicios en un entorno de microservicios.
