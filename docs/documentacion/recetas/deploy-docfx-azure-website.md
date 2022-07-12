# Implementar el sitio web de documentación de DocFx en un sitio web de Azure automáticamente

En el artículo [Uso de DocFx y las herramientas complementarias para generar un sitio web de documentación](./using-docfx-and-tools.md) se describe el proceso para generar el contenido de un sitio web de documentación utilizando DocFx. En este documento se describe cómo configurar un sitio web de Azure para alojar el contenido y automatizar el despliegue en el mismo utilizando un pipeline en Azure DevOps.
El ejemplo [QuickStart](https://github.com/mtirionMSFT/DocFxQuickStart) que se proporciona para una configuración rápida de la generación de DocFx también contiene los archivos explicados en este documento. Especialmente las carpetas .pipelines y de infraestructura.
Si se utiliza la carpeta QuickStart se pueden seguir los siguientes pasos. En la carpeta de infraestructura se encuentran los archivos Terraform para crear el sitio web en un entorno Azure. De forma inmediata, el script creará un sitio web en el que se puede desplegar el contenido de la documentación.

## Instalar Terraform

Puede utilizar herramientas como Chocolatey para instalar Terraform:

```shell
choco install terraform
```

## Establecer las variables adecuadas

En el inicio rápido, la autenticación está deshabilitada. Si quieres habilitarla, asegúrate de haber creado una aplicación en Azure AD y tener el ID de cliente. Este ID de cliente debe ser establecido como el valor de la variable client_id en variables.tf. En el main.tf asegúrese de descomentar la configuración de autenticación en el servicio de la aplicación. Para más información consulte [Configurar la autenticación de Azure AD - Azure App Service](https://docs.microsoft.com/en-us/azure/app-service/configure-authentication-provider-aad).
Si quieres establecer un dominio personalizado para tu sitio web de documentación con un certificado SSL tienes que hacer algunos pasos adicionales. Tienes que crear un Key Vault y almacenar el certificado allí. El siguiente paso es descomentar y establecer los valores en variables.tf. También tienes que descomentar los pasos necesarios en main.tf. Todo se indica mediante cuadros de comentarios. Para más información ver [Añadir un certificado TLS/SSL en Azure App Service](https://docs.microsoft.com/en-us/azure/app-service/configure-ssl-certificate?tabs=apex%2Cportal).
En los siguientes párrafos encontrará información adicional sobre el certificado SSL, el dominio personalizado y Azure App Service. Si está familiarizado con ello o no lo necesita, continúe en [Despliegue de los recursos de Azure desde su máquina local](#despliegue-de-los-recursos-de-azure-desde-su-máquina-local).

### Certificado SSL

Para asegurar un sitio web con un nombre de dominio personalizado y un certificado, puede encontrar los pasos a seguir en el artículo [Añadir un certificado TLS/SSL en Azure App Service](https://docs.microsoft.com/en-us/azure/app-service/configure-ssl-certificate?tabs=apex%2Cportal). Ese artículo también contiene una descripción de las formas de obtener un certificado y los requisitos para un certificado. Si quieres empezar con un certificado de desarrollo para probar el proceso, puedes crear uno tú mismo. Puedes hacerlo en PowerShell con el siguiente script. Reemplace:

* **[SU DOMINIO]** con el dominio que desea registrar
* **[CONTRASEÑA]** con la contraseña del certificado.
* **[FILENAME]** para el nombre del archivo de salida del certificado.

Puedes almacenar este script en un archivo de script de PowerShell.

```powershell
$cert = New-SelfSignedCertificate -CertStoreLocation cert:\currentuser\my -Subject "cn=[YOUR DOMAIN]" -DnsName "[YOUR DOMAIN]"
$pwd = ConvertTo-SecureString -String '[PASSWORD]' -Force -AsPlainText
$path = 'cert:\currentuser\my\' + $cert.thumbprint
Export-PfxCertificate -cert $path -FilePath [FILENAME].pfx -Password $pwd
```

El certificado debe almacenarse en Key Vault. Vaya a `Configuración > Certificados` en el menú de la izquierda del Key Vault y haga clic en `Generar/Importar`. Proporcione estos detalles:

* Método de creación del certificado: `Import`
* Nombre del certificado: por ejemplo, `ssl-certificate`
* Cargar archivo de certificado: seleccione el archivo en disco para ello.
* Contraseña: es la [CONTRASEÑA] a la que nos referimos anteriormente.

### Registro de dominios personalizados

Para utilizar un dominio personalizado hay que hacer algunas cosas. El proceso en el portal de Azure se describe en el artículo [Tutorial: Asignar un nombre DNS personalizado existente a Azure App Service](https://docs.microsoft.com/en-us/azure/app-service/app-service-web-tutorial-custom-domain?tabs=a%2Cazurecli). Una parte importante se describe en el apartado [Obtener un ID de verificación del dominio](https://docs.microsoft.com/en-us/azure/app-service/app-service-web-tutorial-custom-domain?tabs=a%2Cazurecli#2-get-a-domain-verification-id). Este ID necesita ser registrado con la descripción DNS como un registro TXT.
Es importante saber que este ID de verificación de dominio personalizado es el mismo para todos los recursos web en la misma suscripción de Azure. Consulte [este problema de StackOverflow](https://stackoverflow.com/questions/64309200/is-the-custom-domain-verification-shared-across-an-azure-subscription). Esto significa que este ID debe ser registrado sólo una vez para una suscripción Azure. Y esto permite la (re)creación de un servicio de aplicación con el dominio personalizado a través del script.

### Añadir permisos Get para Microsoft Azure App Service

Azure App Service necesita acceder a Key Vault para obtener el certificado. Esto es necesario para la primera ejecución, pero también cuando se renueva el certificado en el Key Vault. Para ello, Azure App Service accede a Key Vault con la identidad proporcionada por el recurso App Service. Esta identidad se puede encontrar con el nombre principal del servicio abfa0a7c-a6b6-4736-8310-5855508787cd o Microsoft Azure App Service y es de tipo Application. Este ID es el mismo para todas las suscripciones de Azure. Debe tener permisos de obtención de secretos y certificados. Para obtener más información, consulte este artículo [Importar un certificado desde Key Vault](https://docs.microsoft.com/en-us/azure/app-service/configure-ssl-certificate?tabs=apex%2Cportal#import-a-certificate-from-key-vault).

### Añadir el dominio personalizado y el certificado SSL al servicio de la aplicación

Una vez que tenemos el certificado SSL y hay un registro de DNS completo como se ha descrito, podemos descomentar el código en el script Terraform de la carpeta Quick Start para adjuntarlo al App Service. En este script es necesario referenciar el certificado en el Key Vault común y utilizarlo en la vinculación del nombre de host personalizado. El nombre de host personalizado se asigna también en el script. La configuración `ssl_state` debe ser `SniEnabled` si está utilizando un certificado SSL. Ahora la creación del sitio web autenticado con un dominio personalizado está automatizada.

## Despliegue de los recursos de Azure desde su máquina local

Abra un símbolo del sistema. Para que los comandos se ejecuten, necesitas tener una conexión con tu suscripción de Azure. Esto se puede hacer usando Azure Cli. Escribe este comando:

```shell
az login
```

Esto utilizará el navegador web para conectarse a su cuenta. Puede comprobar la suscripción conectada con este comando:

```shell
az account show
```

Si tiene que cambiar a otra suscripción, utilice este comando donde sustituye _[id]_ por el id de la suscripción a seleccionar:

```shell
az account set --subscription [id]
```

Una vez hecho esto, ejecute este comando para inicializar:

```shell
terraform init
```

Ahora puedes ejecutar el comando para planificar lo que hará el script. Ejecuta este comando cada vez que se realicen cambios en los scripts de terraformación:

```shell
terraform plan
```

Inspeccione el resultado mostrado. Si es lo que espera, aplique estos cambios con este comando:

```shell
terraform apply
```

Cuando se le pida la aprobación, escriba "sí" y ENTER. También puede añadir el flag -auto-aprobación al comando apply.

## Despliegue del sitio web desde un pipeline

La mejor manera de crear los recursos y desplegarlos, es hacerlo automáticamente en un pipeline. Para ello se proporciona el pipeline .pipelines/documentation.yml. Cree un pipeline y haga referencia a este archivo YAML.
> **IMPORTANTE:** la carpeta Quick Start contiene un web.config que es necesario para el despliegue en IIS o Azure App Service. Esto permite el uso del archivo json para las solicitudes de búsqueda. Si no tienes esto en su lugar, la búsqueda de texto nunca devolverá nada y resultará en 404.

Usted tiene que crear una conexión de servicio en su entorno DevOps para conectarse a la suscripción de Azure que desea implementar.

> **IMPORTANTE:** establece las variables AzureConnectionName con el nombre de la Conexión de Servicio y AzureAppServiceName con el nombre que determinaste en el infrastructure/variables.tf.
