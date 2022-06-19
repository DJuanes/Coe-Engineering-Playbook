# Guía para Alertas

Uno de los objetivos de construir sistemas altamente observables es proporcionar información valiosa sobre el comportamiento de la aplicación. Los sistemas observables permiten que los problemas se identifiquen y emerjan a través de alertas antes de que los usuarios finales se vean afectados.

## Mejores prácticas

* Lo más importante que debe hacer antes de crear alertas es implementar la observabilidad. Sin sistemas de monitoreo implementados, se vuelve casi imposible saber qué actividades deben monitorearse y cuándo alertar a los equipos.
* Identificar cuál debe ser la calidad de servicio viable mínima de la aplicación. No es lo que pretende entregar, pero es aceptable para el cliente. Estos Service Level Objectives (SLO) son una métrica para medir el rendimiento de la aplicación.
* Los SLO se definen con respecto a los usuarios finales. Las alertas deben buscar un impacto visible para el usuario. Por ejemplo, alertas sobre la tasa de solicitudes, la latencia y los errores.
* Utilizar herramientas de script automatizadas para imitar las rutas de código importantes relacionadas con actividades en la aplicación. Cree políticas de alerta sobre los eventos que impactan al usuario.
* Se recomienda a los ingenieros que presten atención a su sistema de monitoreo para que se puedan definir alertas y umbrales precisos.
* Establecer un canal principal para las alertas que necesitan atención inmediata y etiquete al equipo o personas indicadas según la naturaleza del incidente. No es necesario enviar todas las alertas al canal principal de guardia.
* Establecer un canal secundario para los elementos que deben investigarse y que aún no afectan a los usuarios. Estos elementos serán los que los servicios de ingeniería revisarán regularmente para monitorear la salud del sistema.
* Es importante aprender de cada incidente y mejorar continuamente el proceso. Después de que se haya clasificado cada incidente, realice una autopsia del escenario. Ocurrirán escenarios y situaciones que no se consideraron inicialmente, y el flujo de trabajo post-mortem es una excelente manera de resaltar eso para mejorar el monitoreo/alertas del sistema.
