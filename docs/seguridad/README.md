# Seguridad

Los desarrolladores deben adherirse a las prácticas estándar recomendadas por la industria para el diseño y la implementación seguros del código. Esto significa que nuestros ingenieros deben entender los [10 principales riesgos de seguridad de las aplicaciones web de la OWASP](https://owasp.org/www-project-top-ten/), así como la forma de mitigar tantos de ellos como sea posible, utilizando los recursos siguientes.
Si busca una forma rápida de empezar a evaluar su aplicación o diseño, consulte el documento "Referencia rápida de prácticas de codificación seguras" que aparece a continuación, que contiene una lista de comprobación detallada de conceptos de alto nivel que puede validar que se están realizando correctamente. Esta checklist cubre muchos errores comunes asociados con la lista OWASP Top 10, y debería ser la cantidad mínima de esfuerzo que se pone en la seguridad.

## Solicitud de revisiones de seguridad

Cuando solicite una revisión de seguridad para su aplicación, asegúrese de que se ha familiarizado con las [reglas de participación](./rules-of-engagement.md). Esto le ayudará a preparar la aplicación para la prueba, así como a entender los límites del alcance de la misma.

## Referencias rápidas

* [Referencia rápida sobre prácticas de codificación seguras](https://owasp.org/www-pdf-archive/OWASP_SCP_Quick_Reference_Guide_v2.pdf)
* [Referencia rápida sobre la seguridad de las aplicaciones web](https://owasp.org/www-pdf-archive//OWASP_Web_Application_Security_Quick_Reference_Guide_0.3.pdf)
* [Mentalidad de seguridad/creación de un programa de seguridad Inicio rápido](https://github.com/OWASP/Quick-Start-Guide/blob/master/OWASP%20Quick%20Start%20Guide.pdf?raw=true)
* [Detección automatizada de secretos](./secret-detection.md)

## Seguridad de Azure DevOps

* [Prácticas de ingeniería de seguridad de DevSecOps](https://www.microsoft.com/en-us/securityengineering/devsecops)
* [Visión general de la protección de datos de Azure DevOps](https://docs.microsoft.com/en-us/azure/devops/organizations/security/data-protection?view=azure-devops)
* [Seguridad e identidad en Azure DevOps](https://docs.microsoft.com/en-us/azure/devops/organizations/security/about-security-identity?view=azure-devops)

## DevSecOps

Introduzca la seguridad en su proyecto en las primeras fases. La sección [DevSecOps](../ci_cd/dev-sec-ops/README.md) cubre las prácticas de seguridad, la automatización, las herramientas y los marcos de trabajo como parte de la aplicación CI.

## OWASP Cheat Sheets

> Nota: OWASP está considerado como el estándar en información sobre seguridad informática. OWASP mantiene una extensa serie de cheat sheets que cubren todos los Top 10 de OWASP y más. A continuación, se han resumido los más relevantes. Para ver todas las cheat sheets, consulta [Cheat Sheet Index](https://github.com/OWASP/CheatSheetSeries/blob/master/Index.md).

* [Autorización](https://github.com/OWASP/CheatSheetSeries/blob/master/cheatsheets/Authorization_Cheat_Sheet.md)
* [Análisis de superficie de ataque](https://github.com/OWASP/CheatSheetSeries/blob/master/cheatsheets/Attack_Surface_Analysis_Cheat_Sheet.md)
* [Content Security Policy (CSP)](https://github.com/OWASP/CheatSheetSeries/blob/master/cheatsheets/Content_Security_Policy_Cheat_Sheet.md)
* [Prevención Cross-Site Request Forgery (CSRF)](https://github.com/OWASP/CheatSheetSeries/blob/master/cheatsheets/Cross-Site_Request_Forgery_Prevention_Cheat_Sheet.md)
* [Prevención de secuencias de comandos en sitios cruzados (XSS)](https://github.com/OWASP/CheatSheetSeries/blob/master/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.md)
* [Almacenamiento criptográfico](https://github.com/OWASP/CheatSheetSeries/blob/master/cheatsheets/Cryptographic_Storage_Cheat_Sheet.md)
* [Deserialización](https://github.com/OWASP/CheatSheetSeries/blob/master/cheatsheets/Deserialization_Cheat_Sheet.md)
* [Seguridad de Docker/Kubernetes (k8s)](https://github.com/OWASP/CheatSheetSeries/blob/master/cheatsheets/Docker_Security_Cheat_Sheet.md)
* [Validación de entradas](https://github.com/OWASP/CheatSheetSeries/blob/master/cheatsheets/Input_Validation_Cheat_Sheet.md)
* [Gestión de claves](https://github.com/OWASP/CheatSheetSeries/blob/master/cheatsheets/Key_Management_Cheat_Sheet.md)
* [Defensa contra la inyección de comandos del sistema operativo](https://github.com/OWASP/CheatSheetSeries/blob/master/cheatsheets/OS_Command_Injection_Defense_Cheat_Sheet.md)
* [Ejemplos de parametrización de consultas](https://github.com/OWASP/CheatSheetSeries/blob/master/cheatsheets/Query_Parameterization_Cheat_Sheet.md)
* [Prevención de la falsificación de solicitudes del lado del servidor](https://github.com/OWASP/CheatSheetSeries/blob/master/cheatsheets/Server_Side_Request_Forgery_Prevention_Cheat_Sheet.md)
* [Prevención de inyecciones SQL](https://github.com/OWASP/CheatSheetSeries/blob/master/cheatsheets/SQL_Injection_Prevention_Cheat_Sheet.md)
* [Redirecciones y reenvíos no validados](https://github.com/OWASP/CheatSheetSeries/blob/master/cheatsheets/Unvalidated_Redirects_and_Forwards_Cheat_Sheet.md)
* [Seguridad de los servicios web](https://github.com/OWASP/CheatSheetSeries/blob/master/cheatsheets/Web_Service_Security_Cheat_Sheet.md)
* [Seguridad XML](https://github.com/OWASP/CheatSheetSeries/blob/master/cheatsheets/XML_Security_Cheat_Sheet.md)

## Herramientas

> Nota: Aunque algunas herramientas son agnósticas, la siguiente lista está orientada a la seguridad de Cloud Native, con un enfoque en Kubernetes.

* Escaneo de vulnerabilidad
  * [SonarCloud](https://sonarcloud.io/): se integra con Azure Devops con el clic de un botón.
  * [Snyk](https://github.com/snyk/cli)
  * [Trivy](https://github.com/aquasecurity/trivy)
  * [Cloudsploit](https://github.com/aquasecurity/cloudsploit)
  * [Anchore](https://github.com/anchore/anchore-engine)
  * [Otras herramientas de OWASP](https://owasp.org/www-community/Vulnerability_Scanning_Tools)
  * [Vea por qué debe comprobar las vulnerabilidades en todas las capas de la pila](https://sysdig.com/blog/image-scanning-best-practices/), así como un par de consejos útiles para reducir la superficie de los ataques.
* Seguridad en tiempo de ejecución
  * [Falco](https://github.com/falcosecurity/falco)
  * [Tracee](https://github.com/aquasecurity/tracee)
  * [Kubelinter](https://github.com/stackrox/kube-linter): puede que no se califique completamente como seguridad en tiempo de ejecución, pero ayuda a asegurar que está habilitando las mejores prácticas.
* Autorización binaria
  La autorización binaria puede ocurrir tanto en la capa de registro de Docker, como en tiempo de ejecución. La comprobación de la autorización asegura que la imagen está firmada por una autoridad de confianza. Esto puede ocurrir tanto para imágenes de terceros como para imágenes internas. Llevando esto un paso más allá, la firma debería ocurrir sólo en imágenes donde todo el código ha sido revisado y aprobado. La autorización binaria puede reducir tanto el impacto de los daños causados por un entorno de alojamiento comprometido, como los daños causados por personal interno malintencionado.
  * [Harbor](https://github.com/goharbor/harbor/)
    * [Operador disponible](https://github.com/goharbor/harbor-operator)
  * [Portieris](https://github.com/IBM/portieris)
  * [Notary](https://github.com/notaryproject/notary): harbor aprovecha Notary internamente.
  * [TUF](https://github.com/theupdateframework/python-tuf)
* Otra seguridad K8s
  * [OPA](https://github.com/open-policy-agent/opa), [Gatekeeper](https://github.com/open-policy-agent/gatekeeper) y la [biblioteca Gatekeeper](https://github.com/open-policy-agent/gatekeeper-library/tree/master/library)
  * [cert-manager](https://github.com/cert-manager/cert-manager) para un fácil aprovisionamiento de certificados y rotación automática.
  * [Habilite rápidamente mTLS entre sus microservicios con Linkerd](https://linkerd.io/2.11/features/automatic-mtls/).

## Enlaces útiles

* [Guía de requisitos no funcionales](m)
