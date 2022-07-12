# Cómo crear un sitio web estático para su documentación basado en mkdocs y mkdocs-material

[MkDocs](https://www.mkdocs.org/) es una herramienta creada para crear sitios web estáticos a partir de archivos markdown. Otras alternativas son [Sphinx](https://www.sphinx-doc.org/en/master/) y [Jekyll](https://jekyllrb.com/).
MkDocs es una buena opción ya que:

* Es fácil de configurar y se ve muy bien.
* Funciona bien con markdown.
* Utiliza una pila de Python.

A modo de comparación, Sphinx genera principalmente documentos a partir del formato de texto reestructurado (rst), y Jekyll está escrito en Ruby.
Para configurar un sitio web MkDocs, los principales activos necesarios son:

* Un archivo `mkdocs.yaml`. Este es el archivo de configuración que define la apariencia del sitio web, la navegación, los plugins utilizados y más.
* Una carpeta llamada `docs` que contiene los archivos fuente de la documentación.
* Una [acción de GitHub](https://docs.github.com/es/actions/learn-github-actions/understanding-github-actions) para generar automáticamente el sitio web (por ejemplo, en cada commit a main).
* Una lista de plugins utilizados durante la fase de compilación del sitio web.

La configuración local es muy sencilla. Ver [Introducción a MkDocs](https://www.mkdocs.org/getting-started/) para más detalles.
Para publicar el sitio web, hay una buena [integración con GitHub para almacenar el sitio web como una página de GitHub](https://www.mkdocs.org/user-guide/deploying-your-docs/).

## Enlaces adicionales

* [Plugins de MkDocs](https://github.com/mkdocs/mkdocs/wiki/MkDocs-Plugins)
* [Los mejores plugins y personalizaciones de MkDocs](https://chrieke.medium.com/the-best-mkdocs-plugins-and-customizations-fc820eb19759)
