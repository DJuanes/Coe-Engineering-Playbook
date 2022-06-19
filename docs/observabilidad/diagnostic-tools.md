# Herramientas de diagnostico

Además de logging, tracing y métricas, existen herramientas adicionales para ayudar a diagnosticar problemas cuando las aplicaciones no se comportan como se esperaba. En estos casos, las herramientas de diagnóstico específicas de la plataforma o el lenguaje de programación entran en juego y son útiles para depurar problemas de memoria, perfilar el uso de la CPU o la causa de los retrasos.

## Perfiladores y analizadores de memoria

Hay dos tipos de herramientas de diagnóstico que puede utilizar: generadores de perfiles y analizadores de memoria.

### Profiling

La creación de perfiles es una técnica en la que toma pequeñas instantáneas de todos los subprocesos en una aplicación en ejecución para ver el seguimiento de la pila de cada subproceso durante un período específico. Esta herramienta puede ayudarlo a identificar dónde está gastando tiempo de CPU durante la ejecución de su aplicación. Hay dos técnicas principales para lograr esto: muestreo de CPU e instrumentación.
El muestreo de CPU es un método no invasivo que toma instantáneas de todas las pilas en un intervalo establecido. Es la técnica más común para generar perfiles y no requiere ninguna modificación en su código.
La instrumentación es la otra técnica en la que inserta un pequeño fragmento de código al principio y al final de cada función que le indicará al generador de perfiles el tiempo dedicado a la función, el nombre de la función, los parámetros y otros. De esta manera, modifica el código de su aplicación en ejecución. Esto tiene dos efectos: su código puede ejecutarse un poco más lento, pero por otro lado, tiene una vista más precisa de cada función y clase que se ha ejecutado.

### Analizadores de memoria

Los analizadores de memoria y los volcados de memoria son otro conjunto de herramientas de diagnóstico que puede utilizar para identificar problemas en su proceso. Normalmente, este tipo de herramientas toman toda la memoria que el proceso está usando en un momento dado y la guardan en un archivo que se puede analizar.
Hay varias formas de realizar un volcado de memoria según el sistema operativo que esté utilizando. Además, cada sistema operativo tiene su propio depurador que puede cargar este volcado de memoria y explorar el estado del proceso en el momento en que se realizó el volcado de memoria.
Los depuradores más comunes son:

* Windows: [WinDbg y WinDgbNext](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/debugger-download-tools) (incluidos en el SDK de Windows), Visual Studio también puede cargar un volcado de memoria para un proceso de .NET Framework y .NET Core
* Linux - [GDB es el depurador de GNU](https://www.sourceware.org/gdb/)
* Mac OS - [LLDB Debugger](https://lldb.llvm.org/)

Hay una gama de herramientas de diagnóstico específicas de la plataforma del desarrollador que se pueden utilizar:

* [.NET Core](https://docs.microsoft.com/en-us/dotnet/core/diagnostics/#net-core-diagnostic-global-tools), [GitHub Repo](https://github.com/dotnet/diagnostics)
* [Java](https://docs.oracle.com/en/java/javase/16/troubleshoot/general-java-troubleshooting.html)
* [Python](https://docs.python.org/3/library/debug.html)
* [Node.js](https://github.com/nodejs/diagnostics)

## Entorno para perfilado

Para crear un perfil de aplicación lo más cercano posible a la producción, se debe considerar el entorno en el que se pretende que la aplicación se ejecute en producción y podría ser necesario realizar una instantánea del estado de la aplicación bajo carga.

### Diagnóstico en contenedores

Para aplicaciones monolíticas, las herramientas de diagnóstico se pueden instalar y ejecutar en la máquina virtual que las aloja. La mayoría de las aplicaciones escalables se desarrollan como microservicios y tienen interacciones complejas que requieren instalar las herramientas en los contenedores que ejecutan el proceso o aprovechar un contenedor [sidecar](https://docs.microsoft.com/es-es/azure/architecture/patterns/sidecar). Algunas plataformas exponen endpoints para interactuar con la aplicación y devolver un volcado.
