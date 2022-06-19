# Python Code Reviews

## Guía de estilo

* Los desarrolladores deben seguir la [guía de estilo de PEP8](https://pep8.org/) con [sugerencias de tipo](https://peps.python.org/pep-0484/). El uso de sugerencias de tipo en conjunto con el linting evita errores comunes que son difíciles de depurar.
* Los proyectos deben verificar el código de Python con herramientas automatizadas.
* Se debe agregar Linting para compilar la validación, y tanto el formato de código como el de Linting se pueden agregar a los pre-commit hooks y a VS Code.

## Análisis de código / Linting

Los 2 linters de python más populares son [Pylint](https://pypi.org/project/pylint/) y [Flake8](https://pypi.org/project/flake8/). Ambos verifican el cumplimiento de PEP8 pero varían un poco en qué otras reglas verifican. En general, Pylint tiende a ser un poco más estricto y da más falsos positivos, pero ambas son buenas opciones.
Tanto Pylint como Flake8 se pueden configurar en VS Code usando la extensión python de VS Code.

### Pylint

Instalar Pylint

```bash
pip install pylint
```

Ejecutar Pylint

```bash
pylint src  # lint the source directory
```

### Flake8

Flake8 es un contenedor simple y rápido de [Pyflakes](https://github.com/PyCQA/pyflakes) (para detectar errores de codificación) y [pycodestyle](https://github.com/PyCQA/pycodestyle) (para pep8).

Instalar Flake8

```bash
pip install flake8
```

Agregar extensión para la herramienta [pydocstyle](https://github.com/PyCQA/pydocstyle) (para [doc strings](https://peps.python.org/pep-0257/)) a flake8.

```bash
pip install flake8-docstrings
```

Agregar extensión para la herramienta [pep8-naming](https://github.com/PyCQA/pep8-naming) (para [convenciones de nombre](https://peps.python.org/pep-0008/#naming-conventions) en pep8) a flake8.

```bash
pip install pep8-naming
```

Ejecutar Flake8

```bash
flake8 .    # lint the whole project
```

## Formateo automático de código

### Black

[Black](https://github.com/psf/black) es una herramienta de formato de código. Elimina toda la necesidad de que pycodestyle regañe sobre el formato, por lo que el equipo puede concentrarse en el contenido frente al estilo. No es posible configurar black para sus propias necesidades de estilo.

```bash
pip install black
```

Formatear código python

```bash
black [file/folder]
```

### Autopep8

[Autopep8](https://github.com/hhatto/autopep8) es más indulgente y permite una mayor configuración si desea un formato menos estricto.

```bash
pip install autopep8
```

Formatear código python

```bash
autopep8 [file/folder] --in-place
```

### yapf

[yapf](https://github.com/google/yapf) (Yet Another Python Formatter) es un formateador de Python de Google basado en ideas de gofmt. También es más configurable y una buena opción para el formato de código automático.

```bash
pip install yapf
```

Formatear código python

```bash
yapf [file/folder] --in-place
```

## VS Code Extensions

### [Python]((https://marketplace.visualstudio.com/items?itemName=ms-python.python)

Es la extensión base que debería haber instalado para el desarrollo de Python con VS Code. Permite intellisense, depuración, linting (con los linters anteriores), pruebas con pytest o unittest y formateo de código con los formateadores mencionados anteriormente.

### [Pyright](https://marketplace.visualstudio.com/items?itemName=ms-pyright.pyright)

Esta extensión aumenta VS Code con verificación de tipo estático cuando usa sugerencias de tipo.

```python
def add(first_value: int, second_value: int) -> int:
    return first_value + second_value
```

## Validación de compilación

Para automatizar el linting con flake8 y las pruebas con pytest en Azure Devops, puede agregar el siguiente fragmento a su archivo azure-pipelines.yaml.

```yaml
trigger:
  branches:
    include:
    - develop
    - master
  paths:
    include:
    - src/*

pool:
  vmImage: 'ubuntu-latest'

jobs:
- job: LintAndTest
  displayName: Lint and Test

  steps:

  - checkout: self
    lfs: true

  - task: UsePythonVersion@0
    displayName: 'Set Python version to 3.6'
    inputs:
      versionSpec: '3.6'

  - script: pip3 install --user -r requirements.txt
    displayName: 'Install dependencies'

  - script: |
      # Install Flake8
      pip3 install --user flake8
      # Install PyTest
      pip3 install --user pytest
    displayName: 'Install Flake8 and PyTest'

  - script: |
      python3 -m flake8
    displayName: 'Run Flake8 linter'

  - script: |
      # Run PyTest tester
      python3 -m pytest --junitxml=./test-results.xml
    displayName: 'Run PyTest Tester'

  - task: PublishTestResults@2
    displayName: 'Publish PyTest results'
    condition: succeededOrFailed()
    inputs:
      testResultsFiles: '**/test-*.xml'
      testRunTitle: 'Publish test results for Python $(python.version)'
```

## Pre-commit hooks

Pre-commit hooks le permiten formatear y lintear el código localmente antes de enviar el PR.
Agregar pre-commit hooks para su repositorio de python es fácil usando el paquete pre-commit.

1. Instale pre-commit y agréguelo a requirements.txt

    ```bash
    pip install pre-commit
    ```

2. Agregue un archivo .pre-commit-config.yaml en la raíz del repositorio, con las deseadas acciones previas al commit.

    ```yaml
    repos:
    -   repo: https://github.com/ambv/black
        rev: stable
        hooks:
        - id: black
        language_version: python3.6
    -   repo: https://github.com/pre-commit/pre-commit-hooks
        rev: v1.2.3
        hooks:
        - id: flake8
    ```

3. Cada desarrollador que desee configurar pre-commit hooks puede ejecutar

    ```bash
    pre-commit install
    ```

## Code Review Checklist

Además de la Checklist de Code Review (), también debe buscar estos elementos de revisión de código específicos de python:

* [ ] ¿Todos los paquetes nuevos utilizados están incluidos en requirements.txt?
* [ ] ¿Pasa el código todas las comprobaciones lint?
* [ ] ¿Las funciones usan sugerencias de tipo y hay algún error de sugerencia de tipo?
* [ ] ¿El código es legible y usa construcciones pythonic siempre que sea posible?
