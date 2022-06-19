# Observabilidad en Machine Learning

El proceso de desarrollo del sistema de software con componente de aprendizaje automático es más complejo que el software tradicional. Necesitamos monitorear cambios y variaciones en tres dimensiones: el código, el modelo y los datos. Podemos distinguir dos etapas de la vida útil de dicho sistema: la experimentación y la producción que requieren diferentes enfoques de la observabilidad, como se analiza a continuación:

## Modelo en experimentación y tuning

La experimentación es un proceso para encontrar un modelo de aprendizaje automático adecuado y sus parámetros mediante el entrenamiento y la evaluación de dichos modelos con uno o más conjuntos de datos.
Al desarrollar y ajustar modelos de aprendizaje automático, los científicos de datos están interesados en observar y comparar métricas de rendimiento seleccionadas para varios parámetros del modelo. También necesitan una forma confiable de reproducir un proceso de entrenamiento, de modo que un conjunto de datos y parámetros dados produzcan los mismos modelos.
Hay muchas soluciones de evaluación de métricas de modelos disponibles, tanto de código abierto (MLFlow, TensorBoard) como propietarias (Azure Machine Learning, Application Insights).

## Modelo en producción

El modelo entrenado se puede implementar en producción como contenedor. El servicio Azure Machine Learning proporciona SDK para implementar el modelo como Azure Container Instance y publica el punto de conexión REST. Puede monitorearlo utilizando métodos de observabilidad de microservicios. MLFLow es una forma alternativa de implementar el modelo ML como servicio.

## Entrenamiento y reentrenamiento

Para volver a entrenar automáticamente el modelo, puede usar AML Pipelines o Azure Databricks. Al volver a entrenarse con AML Pipelines, puede monitorear la información de cada ejecución, incluida la salida, los logs y varias métricas en el panel de experimentos de Azure Portal, o extraerla manualmente con el SDK de AML.

## Rendimiento del modelo a lo largo del tiempo: data drift

Volvemos a entrenar los modelos de aprendizaje automático para mejorar su rendimiento y hacer que los modelos estén mejor alineados con los datos que cambian con el tiempo. Sin embargo, en algunos casos, el rendimiento del modelo puede degradarse. Esto puede suceder en caso de que los datos cambien drásticamente y ya no muestren los patrones que observamos durante el desarrollo del modelo. Este efecto se denomina data drift. Azure Machine Learning Service tiene una función de vista previa para observar e informar la deriva de datos. Este [artículo](https://docs.microsoft.com/es-es/azure/machine-learning/how-to-monitor-datasets?tabs=python) lo describe en detalle.

## Versionado de datos

Se recomienda como práctica agregar una versión a todos los conjuntos de datos. Puede crear un conjunto de datos de Azure ML con versión para este propósito, o crear una versión manual si usa otros sistemas.
