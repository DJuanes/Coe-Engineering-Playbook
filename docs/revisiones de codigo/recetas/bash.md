# Bash Code Reviews

## Guía de estilo

* [Google's Bash Style Guide](https://google.github.io/styleguide/shellguide.html)

## Análisis de código / Linting

Los proyectos deben verificar el código bash con [shellcheck](https://github.com/koalaman/shellcheck) como parte del proceso de CI. Además de linting, [shfmt](https://github.com/mvdan/sh) se puede usar para formatear automáticamente scripts de shell.

## Configuración del proyecto

### vscode-shellcheck

La extensión Shellcheck debe usarse en VS Code, proporciona capacidades de análisis de código estático y problemas de linting de reparación automática.

## Formateo automático de código

### shell-format

La extensión shell-format formatea automáticamente sus scripts bash, archivos docker y varios archivos de configuración. Depende de shfmt, que puede hacer cumplir las verificaciones de la guía de estilo de Google para bash.

## Validación de compilación

Para automatizar este proceso en Azure DevOps, puede agregar el siguiente fragmento de código a su archivo azure-pipelines.yaml. Esto borrará cualquier script en la carpeta ./scripts/.

```yaml
- bash: |
    echo "This checks for formatting and common bash errors. See wiki for error details and ignore options: https://github.com/koalaman/shellcheck/wiki/SC1000"
    export scversion="stable"
    wget -qO- "https://github.com/koalaman/shellcheck/releases/download/${scversion?}/shellcheck-${scversion?}.linux.x86_64.tar.xz" | tar -xJv
    sudo mv "shellcheck-${scversion}/shellcheck" /usr/bin/
    rm -r "shellcheck-${scversion}"
    shellcheck ./scripts/*.sh
  displayName: "Validate Scripts: Shellcheck"

```

Además, sus scripts de shell se pueden formatear en su canalización de compilación usando la herramienta shfmt. Para integrar shfmt en su canal de compilación, haga lo siguiente:

```yaml
- bash: |
    echo "This step does auto formatting of shell scripts"
    shfmt -l -w ./scripts/*.sh
  displayName: "Format Scripts: shfmt"

```

Las pruebas unitarias que usan [shunit2](https://github.com/kward/shunit2) también se pueden agregar a la canalización de compilación, usando el siguiente bloque:

```yaml
- bash: |
    echo "This step unit tests shell scripts by using shunit2"
    ./shunit2
  displayName: "Format Scripts: shfmt"

```

## Pre-Commit Hooks

Todos los desarrolladores deben ejecutar shellcheck y shfmt como pre-commit hooks.

Paso 1
Ejecute `pip install pre-commit`. Alternativamente, puede ejecutar `brew install pre-commit` si está utilizando homebrew.

Paso 2
Agregue el archivo .pre-commit-config.yaml a la raíz del proyecto go. Ejecute shfmt en el pre-commit agregándolo al archivo .pre-commit-config.yaml como se muestra a continuación.

```yaml
-   repo: git://github.com/pecigonzalo/pre-commit-fmt
    sha: master
    hooks:
      -   id: shell-fmt
          args:
            - --indent=4

```

```yaml
-   repo: https://github.com/shellcheck-py/shellcheck-py
    rev: v0.7.1.1
    hooks:
    -   id: shellcheck

```

Paso 3
Ejecute `$ pre-commit install` para configurar los scripts de git hook

## Dependencias

Los scripts Bash se utilizan a menudo para "unir" otros sistemas y herramientas. Como tal, los scripts de Bash a menudo pueden tener dependencias numerosas y/o complicadas. Considere el uso de contenedores Docker para asegurarse de que los scripts se ejecuten en un entorno portátil y reproducible que contenga todas las dependencias correctas. Para asegurarse de que los scripts dockerizados sean fáciles de ejecutar, considere hacer que el uso de Docker sea transparente para la persona que llama al script envolviendo el script en un 'bootstrap' que verifica si el script se está ejecutando en Docker y se vuelve a ejecutar en Docker si no es así. Esto proporciona lo mejor de ambos mundos: ejecución sencilla de scripts y entornos coherentes.

```yaml
if [[ "${DOCKER}" != "true" ]]; then
  docker build -t my_script -f my_script.Dockerfile . > /dev/null
  docker run -e DOCKER=true my_script "$@"
  exit $?
fi

# ... implementation of my_script here can assume that all of its dependencies exist since it's always running in Docker ...

```

## Code Review Checklist

Además de la Checklist de Code Review (), también debe buscar estos elementos de revisión de código específicos de bash:

* [ ] ¿Este código utiliza opciones de shell integradas como set -o, set -e, set -u para el control de ejecución de scripts de shell?
* [ ] ¿El código está modularizado? Los scripts de shell se pueden modularizar como módulos de python. Las partes de los scripts bash deben obtenerse en proyectos bash complejos.
* [ ] ¿Todas las excepciones se manejan correctamente? Las excepciones deben manejarse correctamente utilizando códigos de salida o señales de captura.
* [ ] ¿Pasa el código todas las verificaciones linting según shellcheck y las pruebas unitarias según shunit2?
* [ ] ¿El código usa rutas relativas o rutas absolutas? Deben evitarse las rutas relativas, ya que son propensas a los ataques del entorno. Si se necesita una ruta relativa, verifique que la variable PATH esté configurada.
* [ ] ¿El código toma credenciales como entrada del usuario? ¿Las credenciales están enmascaradas o encriptadas en el script?
