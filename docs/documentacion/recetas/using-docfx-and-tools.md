# Uso de DocFx y las herramientas complementarias para generar un sitio web de documentación

Si quieres una manera fácil de tener un sitio web con toda tu documentación proveniente de archivos Markdown y comentarios provenientes del código, puedes usar [DocFx](https://dotnet.github.io/docfx/). El sitio web generado por DocFx también incluye capacidades de búsqueda rápida. Consulte también la publicación del blog [Proporcionar documentación de calidad en su proyecto con DocFx y las herramientas complementarias](https://mtirion.medium.com/providing-quality-documentation-in-your-project-with-docfx-and-companion-tools-76aed42b1ddd) para obtener más explicaciones sobre la solución.

## Requisitos previos

La mejor manera de seguir este documento es clonando primero el ejemplo de [DocFxQuickStart](https://github.com/mtirionMSFT/DocFxQuickStart). Copie el contenido de la carpeta QuickStart a la raíz de su propio repositorio para empezar en su propio entorno.

## Inicio rápido

1. Azure DevOps: crea un proyecto y crea una Conexión de Servicio a tu entorno Azure. Clona el repositorio.
2. Carpeta QuickStart: Copiar el contenido de la carpeta QuickStart que hay en el repositorio que se encuentra en [DocFxQuickStart](https://github.com/mtirionMSFT/DocFxQuickStart) a la raíz del repositorio.
3. Azure: Cree un resource group donde se deben crear los recursos del sitio web de documentación.
4. Cree los recursos de Azure: Rellena los valores por defecto en infrastructure/variables.tf y ejecuta los comandos de [Despliegue de los recursos de Azure desde su máquina local](deploy-docfx-azure-website.md#despliegue-de-los-recursos-de-azure-desde-su-máquina-local) para crear los recursos Azure.
5. Pipeline: Rellena las variables en .pipelines/documentation.yml, commitea los cambios y envia el contenido del repositorio a tu rama. Ahora puedes crear un pipeline en tu proyecto Azure DevOps que utilice el .pipelines/documentation.yml y ejecutarlo.

## Referencias

* [DocFX - generador de documentación estática](https://dotnet.github.io/docfx/index.html)
* [Implementar el sitio web de documentación de DocFx en un sitio web de Azure automáticamente](./deploy-docfx-azure-website.md)
* [Proporcionar documentación de calidad en su proyecto con DocFx y las herramientas complementarias](https://mtirion.medium.com/providing-quality-documentation-in-your-project-with-docfx-and-companion-tools-76aed42b1ddd)
* [Monorepo para principiantes](https://mtirion.medium.com/monorepo-for-beginners-45d5059ab40e)
