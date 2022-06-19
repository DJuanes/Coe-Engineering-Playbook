# Observability as Code

En la medida de lo posible, la configuración y administración de los activos de observabilidad, como el aprovisionamiento de recursos en la nube, las alertas de monitoreo y los dashboard, deben administrarse como código. La observabilidad como código se logra utilizando cualquiera de las plantillas Terraform / Ansible / ARM / Bicep.

## Ejemplos de Observability as Code

* Dashboards as Code: los dashboards de monitoreo se pueden crear como plantillas JSON o XML. Esta plantilla se mantiene con control de código fuente. La automatización se puede construir para habilitar el dashboard. [Creación mediante programación de paneles de Azure](https://docs.microsoft.com/es-es/azure/azure-portal/azure-portal-dashboards-create-programmatically).
* Alerts as Code: las alertas se pueden crear en Azure mediante el uso de plantillas de Terraform o ARM. Estas alertas se pueden controlar desde el origen y se pueden implementar como parte de las canalizaciones. Algunas referencias de cómo hacer esto son: [Terraform Monitor Metric Alert](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/monitor_metric_alert). Las alertas también se pueden crear en función de la consulta de log analytics y se pueden definir como código mediante [Terraform Monitor Scheduled Query Rules Alert](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/monitor_scheduled_query_rules_alert#example-usage).
* Automatización de consultas de Log Analytics: hay varios casos de uso en los que puede ser necesaria la automatización de consultas de log analytics. Por ejemplo, generación automática de informes, ejecución de consultas personalizadas mediante programación para análisis, depuración, etc. Para que estos casos de uso funcionen, las consultas de log deben estar controladas por fuente y la automatización se puede crear mediante Log Analytics REST o Azure CLI.

## Por qué

* Hace que la configuración sea repetible y automatizable. También evita la configuración manual de alertas de monitoreo y dashboards desde cero en todos los entornos.
* Los dashboards configurados ayudan a solucionar errores durante la integración y la implementación (CI/CD).
* Podemos auditar los cambios y revertirlos si hay algún problema.
* Identificar información procesable a partir de los datos de métricas generados en todos los entornos.
* La configuración y gestión de los activos de observabilidad como el umbral de alerta, la duración y los valores de configuración mediante IaC nos ayudan a evitar errores u omisiones de configuración durante la implementación.
* Al practicar la observabilidad como código, el equipo puede revisar los cambios de manera similar a otras contribuciones de código.
