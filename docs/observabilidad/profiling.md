# Profiling

## Visión general

La creación de perfiles es una forma de análisis que mide varios componentes, como la asignación de memoria, garbage collection, los subprocesos y bloqueos, las pilas de llamadas o la frecuencia y duración de funciones específicas. Se puede usar para ver qué funciones son las más costosas, lo que le permite concentrar su esfuerzo en eliminar las mayores ineficiencias lo más rápido posible. Puede ayudarlo a encontrar interbloqueos, fugas de memoria o asignación de memoria ineficiente, y ayudar a informar las decisiones sobre la asignación de recursos (es decir, CPU o RAM).

## Cómo perfilar las aplicaciones

La creación de perfiles depende en cierta medida del lenguaje. Además, Linux Perf es una buena alternativa, ya que muchos lenguajes tienen enlaces en C/C++.
La creación de perfiles tiene algún costo, ya que requiere inspeccionar la pila de llamadas y, a veces, pausar la aplicación por completo. Considere el costo cuando decida ajustar los parámetros de perfilaje.
Desafortunadamente, cada herramienta de generación de perfiles generalmente usa su propio formato para almacenar perfiles y viene con su propia visualización.

## Herramientas específicas

* (Java, Go, Python, Ruby, eBPF) [Pyroscope](https://github.com/pyroscope-io/pyroscope): perfilado continuo listo para usar.
* (Java and Go) [Flame](https://github.com/yahoo/kubectl-flame): perfilado de contenedores en Kubernetes.
* (Java, Python, Go) [Datadog Continuous Profiler](https://www.datadoghq.com/product/code-profiling/).
* (Java, Python, Go, Node.js) [Instana](https://www.instana.com/blog/instana-announces-the-industrys-first-commercial-continuous-production-profiler/).
* (Go) [profefe](https://github.com/profefe/profefe): construye pprof para proporcionar perfiles continuos.
* (Java) [Opsian](https://opsian.com).
* (Java) [Eclipse Memory Analyzer](https://www.eclipse.org/mat/).
