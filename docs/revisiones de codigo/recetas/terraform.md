# Terraform Code Reviews

## Guía de estilo

* [Terraform style guide](https://github.com/jonbrouse/terraform-style-guide/blob/master/README.md)
* Los proyectos deben verificar los scripts de Terraform con herramientas automatizadas.

## Análisis de código / Linting

### TFLint

[TFLint](https://github.com/terraform-linters/tflint) es un linter de Terraform centrado en posibles errores, mejores prácticas, etc. Una vez que TFLint está instalado en el entorno, se puede invocar mediante la extensión de terraform de VS Code.

## VS Code Extensions

### [Extensión Terraform](https://marketplace.visualstudio.com/items?itemName=hashicorp.terraform)

Esta extensión proporciona capacidades de resaltado, linting, formateo y validación de sintaxis.

### [Extensión Azure Terraform](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azureterraform)

Esta extensión proporciona compatibilidad con comandos de Terraform, visualización de gráficos de recursos e integración de CloudShell dentro de VS Code.

## Validación de compilación

El siguiente script de ejemplo se puede usar para instalar terraform y un linter que luego verifica el formato y los errores comunes.

```shell
#! /bin/bash
set -e

SCRIPT_DIR=$(dirname "$BASH_SOURCE")
cd "$SCRIPT_DIR"

TF_VERSION=0.12.4
TF_LINT_VERSION=0.9.1

echo -e "\n\n>>> Installing Terraform 0.12"
# Install terraform tooling for linting terraform
wget -q https://releases.hashicorp.com/terraform/${TF_VERSION}/terraform_${TF_VERSION}_linux_amd64.zip -O /tmp/terraform.zip
sudo unzip -q -o -d /usr/local/bin/ /tmp/terraform.zip

echo ""
echo -e "\n\n>>> Install tflint (3rd party)"
wget -q https://github.com/wata727/tflint/releases/download/v${TF_LINT_VERSION}/tflint_linux_amd64.zip -O /tmp/tflint.zip
sudo unzip -q -o -d /usr/local/bin/ /tmp/tflint.zip

echo -e "\n\n>>> Terraform version"
terraform -version

echo -e "\n\n>>> Terraform Format (if this fails use 'terraform fmt -recursive' command to resolve"
terraform fmt -recursive -diff -check

echo -e "\n\n>>> tflint"
tflint

echo -e "\n\n>>> Terraform init"
terraform init

echo -e "\n\n>>> Terraform validate"
terraform validate
```

## Code Review Checklist

Además de la Checklist de Code Review (), también debe buscar estos elementos de revisión de código específicos de Terraform:

### Proveedores

* [ ] ¿Todos los proveedores utilizados en los scripts de terraform están versionados para evitar cambios importantes en el futuro?

### Organización del repositorio

* [ ] ¿El código se dividió en módulos reutilizables?
* [ ] ¿Los módulos se dividen en archivos .tf separados cuando corresponde?
* [ ] El repositorio contiene un README.md que describe la arquitectura aprovisionada.
* [ ] Si el código de Terraform se mezcla con el código fuente de la aplicación, ¿el código de Terraform se aísla en una carpeta dedicada?

### Estado de Terraform

* [ ] ¿El proyecto Terraform está configurado con Azure Storage como back-end de estado remoto?
* [ ] ¿La clave de la cuenta de almacenamiento de back-end de estado remoto almacenó una ubicación segura (por ejemplo, Azure Key Vault)?
* [ ] ¿El proyecto está configurado para usar archivos de estado en función del entorno y la canalización de implementación está configurada para proporcionar el nombre del archivo de estado de forma dinámica?

### Variables

* [ ] Si la infraestructura será diferente según el entorno, los parámetros específicos del entorno se proporcionan a través de un archivo .tfvars.
* [ ] Todas las variables tienen información de tipo.
* [ ] Todas las variables tienen una descripción que indica el propósito de la variable y su uso.
* [ ] Los valores predeterminados no se proporcionan para las variables que debe proporcionar un usuario.

### Testing

* [ ] ¿Existen pruebas unitarias y de integración que cubran el código de Terraform?

### Nomenclatura y estructura de código

* [ ] ¿Las definiciones de recursos y las fuentes de datos se utilizan correctamente en los scripts de Terraform?
  * **resource:** Indica a Terraform que la configuración actual se encarga de gestionar el ciclo de vida del objeto
  * **data:** indica a Terraform que solo desea obtener una referencia al objeto existente, pero no desea administrarlo como parte de esta configuración
* [ ] Los nombres de los recursos comienzan con el nombre del proveedor que los contiene seguido de un guión bajo.
* [ ] ¿La función `try` solo se usa con referencias de atributos simples y funciones de conversión de tipos? El uso excesivo de la función para suprimir errores conducirá a una configuración que es difícil de entender y mantener.
* [ ] ¿Las funciones de conversión de tipos explícitas utilizadas para normalizar los tipos solo se devuelven en las salidas del módulo? Las conversiones de tipos explícitas rara vez son necesarias en Terraform porque convertirá los tipos automáticamente cuando sea necesario.
* [ ] ¿La propiedad `Sensitive` en el esquema se establece en `true` para los campos que contienen información confidencial?

### Recomendaciones generales

* [ ] Intente evitar anidar la subconfiguración dentro de los recursos. Cree una sección de recursos separada para los recursos, aunque se puedan declarar como subelementos de un recurso.
* [ ] Nunca codifique ningún valor en la configuración. Declararlos en la sección `locals` si se necesita una variable varias veces como un valor estático y son internos a la configuración.
* [ ] Los nombres de los recursos creados en Azure no deben estar codificados ni ser estáticos. Estos nombres deben ser dinámicos y proporcionados por el usuario mediante un bloque de `variables`. Esto es especialmente útil en las pruebas unitarias cuando se ejecutan varias pruebas en paralelo para intentar crear recursos en Azure pero necesitan nombres diferentes.
* [ ] Es una buena práctica generar el ID de los recursos creados en Azure desde la configuración. Esto es especialmente útil cuando se agregan bloques dinámicos para subelementos/elementos secundarios al recurso principal.
* [ ] Utilice el bloque `required_providers` para establecer la dependencia de los proveedores junto con la versión predeterminada.
* [ ] Utilice el bloque `terraform` para declarar la dependencia del proveedor con la versión exacta y también la versión CLI de terraform necesaria para la configuración.
* [ ] Valide los valores de las variables proporcionados según el uso y el tipo de variable. La validación se puede hacer a las variables agregando un bloque `validation`.
* [ ] Valide que los SKU de los componentes sean los correctos.
