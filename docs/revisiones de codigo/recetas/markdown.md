# Markdown Code Reviews

## Guía de estilo

* La documentación se trata como cualquier otro código fuente y se deben seguir las mismas reglas y listas de verificación.
* La documentación debe usar una buena sintaxis de Markdown para garantizar que se analice correctamente y seguir las pautas de un buen estilo de escritura para garantizar que el documento sea fácil de leer y comprender.

## Markdown

Markdown es un lenguaje de marcado ligero que puede usar para agregar elementos de formato a documentos de texto sin formato. Es uno de los lenguajes de marcado más populares del mundo.
Puede encontrar más información y documentación completa [aquí](https://www.markdownguide.org/).

## Linting

Markdown tiene una forma específica de formatearse. Es importante respetar este formato, de lo contrario, algunos intérpretes estrictos no mostrarán correctamente el documento. Los linters a menudo se usan para ayudar a los desarrolladores a crear documentos correctamente al verificar la sintaxis, la gramática y el idioma inglés correctos de Markdown.
Una buena configuración incluye un linter markdown que se usa durante la edición y la verificación del PR de compilación, y un linter de gramática que se usa mientras se edita el documento. La siguiente es una lista de linters que podrían usarse en esta configuración.

### markdownlint

[markdownlint](https://github.com/markdownlint/markdownlint) es un linter para markdown que verifica la sintaxis de Markdown y también aplica reglas que hacen que el texto sea más legible. [Markdownlint-cli](https://github.com/igorshubovych/markdownlint-cli) es una CLI fácil de usar basada en Markdownlint.
Está disponible como [ruby gem](https://github.com/markdownlint/markdownlint), un [paquete npm](https://github.com/DavidAnson/markdownlint), una [CLI de Node.js](https://github.com/igorshubovych/markdownlint-cli) y una [extensión de VS Code](https://github.com/DavidAnson/vscode-markdownlint). La extensión [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) de VS Code también detecta todos los errores de markdownlint.

Una lista completa de reglas de markdownlint está disponible [aquí](https://github.com/DavidAnson/markdownlint/blob/main/doc/Rules.md).

### proselint

[proselint](http://proselint.com/) es una utilidad de línea de comandos que comprueba jerga, errores ortográficos, redundancia, lenguaje corporativo y otros problemas relacionados con el lenguaje.
Está disponible como [paquete de python](https://github.com/amperser/proselint/#checks) y como [paquete de node](https://www.npmjs.com/package/proselint).

## VS Code Extensions

### Write Good Linter

La [extensión Write Good Linter](https://marketplace.visualstudio.com/items?itemName=travisthetechie.write-good-linter) se integra con VS Code para brindar consejos sobre gramática y lenguaje mientras se edita el documento.

extensión markdownlint
La [extensión markdownlint](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint) examina los documentos de Markdown y muestra advertencias sobre violaciones de reglas durante la edición.

## Validación de compilación

### Linting para validación de PR

Para automatizar el linting con markdownlint para la validación de PR en las acciones de GitHub como lo hacemos en este repositorio, use el siguiente YAML.

```yaml
name: Markdownlint

on:
  push:
    paths:
      - "**/*.md"
  pull_request:
    paths:
      - "**/*.md"

jobs:
  lint:

    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v2
    - name: Use Node.js
      uses: actions/setup-node@v1
      with:
        node-version: 12.x
    - name: Run Markdownlint
      run: |
        npm i -g markdownlint-cli
        markdownlint "**/*.md" --ignore node_modules
```

### Comprobación de enlaces

Para automatizar la verificación de enlaces en sus archivos markdown, agregue la acción markdown-link-check a su pipeline de validación:

```yaml
  markdown-link-check:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@master
    - uses: gaurav-nelson/github-action-markdown-link-check@v1

```

Puede encontrar más información sobre las opciones de acción de markdown-link-check en la [página de inicio de markdown-link-check](https://github.com/gaurav-nelson/github-action-markdown-link-check)

## Code Review Checklist

Además de la Checklist de Code Review (), también debe buscar estos elementos de revisión de código específicos de la documentación:

* [ ] ¿El documento es fácil de leer y comprender y sigue buenas pautas de escritura?
* [ ] ¿Hay una única fuente de verdad o el contenido se repite en más de un documento?
* [ ] ¿La documentación está al día con el código?
* [ ] ¿La documentación es técnica y éticamente correcta?
