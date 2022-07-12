# Cómo automatizar comprobaciones sencillas

Si quieres automatizar algunas comprobaciones en tus documentos Markdown, hay varias herramientas que puedes aprovechar. Por ejemplo:

* [Análisis de código / Linting](./../../revisiones%20de%20codigo/recetas/markdown.md#code-analysis-linting)
  * [markdownlint](./../../revisiones%20de%20codigo/recetas/markdown.md#markdownlint) para verificar la sintaxis de Markdown y aplicar reglas que hagan el texto más legible.
  * [markdown-link-check](https://github.com/tcort/markdown-link-check) para extraer enlaces de los textos Markdown y comprobar si cada enlace está vivo (200 OK) o muerto.
  * [proselint](./../../revisiones%20de%20codigo/recetas/markdown.md#proselint) para revisar la jerga, los errores ortográficos, la redundancia, el lenguaje corporativo y otros problemas relacionados con el lenguaje.
  * [Imagen Docker para node-markdown-spellcheck](https://github.com/tmaier/docker-markdown-spellcheck), una imagen docker ligera para revisar la ortografía de los archivos markdown.
* [Extensiones de VS Code](./../../revisiones%20de%20codigo/recetas/markdown.md#vs-code-extensions)
  * [markdownlint](./../../revisiones%20de%20codigo/recetas/markdown.md#markdownlint-extension) para examinar los documentos Markdown y obtener advertencias sobre las violaciones de las reglas durante la edición.
* Automatización
  * [pre-commit](https://pre-commit.com/) para usar scripts hook de Git para identificar problemas simples antes de enviar nuestro código o documentación para su revisión.
  * Comprobar la [validación de la compilación](./../../revisiones%20de%20codigo/recetas/markdown.md#build-validation) para automatizar el linting para PRs.
  * Comprobar la [canalización CI para una mejor documentación](./ci_cd/../../../CI_CD/continuous-integration/markdown-linting/README.md) de una canalización de ejemplo con markdownlint, markdown-link-check y write-good.

## Sobre las reglas de linting

El equipo debe tener claro qué reglas de linting son necesarias y no deben ser anuladas con herramientas o comentarios. El equipo debe llegar a un consenso sobre cuándo anular las reglas de las herramientas.
