# Reglas de participación

Al realizar el análisis de seguridad, se espera que el probador siga las reglas que se exponen a continuación. Esto es para estandarizar el alcance de las pruebas de aplicaciones y proporcionar una conciencia concreta de lo que se considera "fuera del alcance" para el análisis de seguridad.

## Reglas de participación - Para los que solicitan la revisión

* WAF pueden estar instalados y configurados, pero no permiten ningún bloqueo automático. Esto puede ralentizar mucho a la persona que realiza la prueba.
* Del mismo modo, si un servicio se está ejecutando en una máquina virtual, asegúrese de que servicios como `fail2ban` estén desactivados.
* No puede realizar cambios en la aplicación en ejecución hasta que la prueba haya finalizado. Esto es para evitar que se rompa accidentalmente un ataque en curso que de otro modo sería válido.
* Los resultados de la revisión no se consideran "definitivos". Un equipo de seguridad orquestado por la organización debe realizar siempre una revisión de seguridad antes de pasar una aplicación a producción.

## Reglas de participación - Para aquellos que realizan pruebas

* No intente realizar ataques de denegación de servicio o de otra manera de colapsar los servicios. Se tolera el escaneo activo pesado, pero no se permiten los derribos deliberados.
* No interactuar con seres humanos. La suplantación de credenciales u otros ataques del lado del cliente están prohibidos. Se anima a detallar los ataques XSS y similares como parte de la prueba, pero no los aproveche contra usuarios o clientes internos.
* Ataque desde un único punto. Especialmente si la aplicación está actualmente en manos del cliente, proporcione la dirección IP o el nombre del host atacante para evitar que salten las alarmas.
