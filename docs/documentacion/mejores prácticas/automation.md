# Sustitución de la documentación por la automatización

Puedes documentar cómo configurar tu máquina de desarrollo con la versión correcta del framework necesaria para ejecutar el código, qué extensiones son útiles para desarrollar la aplicación con tu editor, o cómo configurar tu editor para lanzar y depurar la aplicación. Si es posible, una mejor solución es proporcionar los medios para automatizar la instalación de herramientas, el inicio de la aplicación, etc., en su lugar.
A continuación se ofrecen algunos ejemplos:

## Contenedores de desarrollo en Visual Studio Code

La extensión [Visual Studio Code Remote - Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) le permite utilizar un contenedor Docker como un entorno de desarrollo completo. Le permite abrir cualquier carpeta dentro de un contenedor (o montada en él) y aprovechar todo el conjunto de funciones de Visual Studio Code.
Información adicional: [Desarrollando dentro de un contenedor](https://code.visualstudio.com/docs/remote/containers).

## Lanzar configuraciones y tareas en Visual Studio Code

Las [configuraciones de lanzamiento](https://code.visualstudio.com/Docs/editor/debugging#_launch-configurations) permiten configurar y guardar los detalles de configuración de la depuración.
Las [tareas](https://code.visualstudio.com/Docs/editor/tasks) pueden configurarse para ejecutar scripts e iniciar procesos, de modo que muchas de estas herramientas existentes pueden utilizarse desde VS Code sin tener que introducir una línea de comandos o escribir nuevo código.
