# Herramientas de revisión de código

## Personalizar Azure DevOps

### Tableros de tareas

* AzDO: [personalizar tarjetas](https://docs.microsoft.com/en-us/azure/devops/boards/boards/customize-cards?view=azure-devops)
* AzDO: [agregar columnas en el tablero de tareas](https://docs.microsoft.com/en-us/azure/devops/boards/sprints/customize-taskboard?view=azure-devops#add-columns)

### Políticas del revisor

* Configuración del grupo de revisores requerido en AzDO - [Incluir automáticamente revisores de código](https://docs.microsoft.com/en-us/azure/devops/repos/git/branch-policies?view=azure-devops&tabs=browser#automatically-include-code-reviewers)

## Configuración de políticas de ramas

* AzDO: [Configurar directivas de ramas](https://docs.microsoft.com/en-us/azure/devops/repos/git/branch-policies?view=azure-devops&tabs=browser#configure-branch-policies)
* AzDO: Configuración de políticas de rama con la herramienta CLI:
  * [Crear un archivo de configuración de políticas](https://docs.microsoft.com/en-us/azure/devops/cli/policy-configuration-file?view=azure-devops#create-a-policy-configuration-file)
  * [Política de recuento de aprobaciones](https://docs.microsoft.com/en-us/rest/api/azure/devops/policy/configurations/create?view=azure-devops-rest-5.1#approval-count-policy)
* GitHub: [Configuración de ramas protegidas](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/defining-the-mergeability-of-pull-requests/about-protected-branches)

## Visual Studio Code

### GitHub: [GitHub Pull Requests](https://marketplace.visualstudio.com/items?itemName=GitHub.vscode-pull-request-github)

Admite el procesamiento de pull requests de GitHub dentro de VS Code.

1. Abra el complemento desde la barra de actividad.
2. Seleccione Asignado a mí.
3. Seleccione un PR.
4. En Descripción, puede elegir Verificar la rama y acceder al Modo de revisión y obtener una experiencia más integrada.

### Azure DevOps: [Azure DevOps Pull Requests](https://marketplace.visualstudio.com/items?itemName=ankitbko.vscode-pull-request-azdo)

Admite el procesamiento de pull requests de Azure DevOps dentro de VS Code.

1. Abra el complemento desde la barra de actividad.
2. Seleccione Asignado a mí.
3. Seleccione un PR.
4. En Descripción, puede elegir Verificar la rama y acceder al Modo de revisión y obtener una experiencia más integrada.
