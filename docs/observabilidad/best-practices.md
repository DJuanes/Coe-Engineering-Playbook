# Prácticas Recomendadas

* Id. de correlación: incluya un identificador único al comienzo de la interacción para vincular los datos agregados de varios componentes del sistema y proporcionar una vista holística.
* Supervisar el estado de los servicios y proporcionar información sobre el rendimiento y el comportamiento del sistema.
* Los servicios dependientes se deben supervisar correctamente. Además, las métricas relacionadas con los servicios dependientes deben capturarse y registrarse.
* Los defectos, bloqueos y fallas se registran como eventos discretos. Esto ayuda a los ingenieros a identificar las áreas problemáticas durante las fallas.
* La configuración de logueo se puede controlar sin cambios en el código.
* Las métricas sobre la latencia y la duración se recopilen y se puedan agregar.
* Comience poco a poco y agregue donde haya impacto en el cliente.
* Es importante que todos los datos que se recopilen contengan un contexto rico y relevante.
* La información de identificación personal o cualquier otra información confidencial nunca debe registrarse.
* Comprobaciones de estado: se deben agregar comprobaciones de estado adecuadas para determinar si el servicio está en buen estado y listo para atender el tráfico.
