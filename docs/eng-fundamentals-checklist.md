# Checklist de los fundamentos de la ingeniería

Esta checklist ayuda a garantizar que nuestros proyectos cumplen con nuestros fundamentos de ingeniería.

## Control del código fuente

- [ ] La rama principal está bloqueada.
- [ ] Las fusiones se realizan a través de PRs.
- [ ] Los PRs hacen referencia a elementos de trabajo relacionados.
- [ ] El historial de commit es consistente y los mensajes de commit son informativos.
- [ ] Convenciones de nomenclatura de ramas consistentes.
- [ ] Documentación clara de la estructura del repositorio.
- [ ] Los secretos no forman parte del historial de confirmaciones ni se hacen públicos.

Más detalles sobre el control de [código fuente](control de codigo fuente/README.md)

## Seguimiento de elementos de trabajo

- [ ] Todos los elementos se registran en Azure DevOps (o similar).
- [ ] El tablero está organizado (swim lanes, feature tags, technology tags).

Más detalles sobre la gestión del backlog

## Testing

- [ ] Las pruebas unitarias cubren la mayoría de los componentes (>90% si es posible).
- [ ] Las pruebas de integración se ejecutan para probar la solución e2e.

Más detalles sobre las [pruebas automatizadas](testing automatizado/README.md)

## CI/CD

- [ ] El proyecto ejecuta CI con construcción y pruebas automatizadas en cada PR.
- [ ] El proyecto utiliza CD para gestionar los despliegues en un entorno de réplica antes de fusionar los PR.
- [ ] La rama principal siempre está disponible.

Más detalles sobre la [integración y entrega continua](ci-cd/README.md)

## Seguridad

- [ ] El acceso sólo se concede en función de las necesidades
- [ ] Los secretos se almacenan en lugares seguros y no se registran en el código
- [ ] Los datos se cifran en tránsito y en reposo y las contraseñas se codifican.
- [ ] ¿Está el sistema dividido en segmentos lógicos con separación de intereses? Esto ayuda a limitar las vulnerabilidades de seguridad.

Más detalles sobre la [seguridad](securidad/README.md)

## Observabilidad

- [ ] Los eventos funcionales y de negocio significativos se rastrean y se recogen las métricas relacionadas.
- [ ] Se registran los fallos y errores de la aplicación.
- [ ] Se supervisa la salud del sistema.
- [ ] Los datos de observabilidad del lado del cliente y del servidor pueden diferenciarse.
- [ ] La configuración del log puede modificarse sin necesidad de cambiar el código.
- [ ] El contexto del tracing entrante se propaga para permitir la depuración de problemas de producción.

Más detalles sobre la [observabilidad](observabilidad/README.md)

## Agilidad/Scrum

- [ ] El líder del proceso (fijo/rotativo) dirige el standup diario
- [ ] El proceso ágil está claramente definido dentro del equipo.
- [ ] El Dev Lead (+ PO/Otros) es responsable de la gestión y el refinamiento del backlog.
- [ ] Se establece un acuerdo de trabajo entre los miembros del equipo y el cliente.

Más detalles sobre el desarrollo ágil

## Revisiones del código

- [ ] Existe un acuerdo claro en el equipo sobre la función de las revisiones de código.
- [ ] El equipo tiene una checklist de la revisión del código o un proceso establecido.
- [ ] Un número mínimo de revisores (normalmente 2) para una fusión de PR se hace cumplir por política.
- [ ] Se establecen linters/analizadores de código, pruebas unitarias y compilaciones exitosas para las fusiones de PR.
- [ ] Hay un proceso para imponer una revisión rápida.

Más detalles sobre las [revisiones de código](revisiones de codigo/README.md)

## Retrospectivas

- [ ] Las retrospectivas se realizan al final de cada sprint.
- [ ] El equipo identifica de 1 a 3 experimentos propuestos para probar cada sprint para mejorar el proceso.
- [ ] Los experimentos tienen propietarios y se añaden al backlog del proyecto.
- [ ] El equipo lleva a cabo una retrospectiva más larga para los hitos y la finalización del proyecto.

Más detalles sobre las retrospectivas

## Experiencia del desarrollador (DevEx)

Los desarrolladores del equipo pueden

- [ ] Construir/Compilar el código fuente para verificar que no tiene errores de sintaxis y que se compila.
- [ ] Ejecutar todas las pruebas automatizadas.
- [ ] Iniciar el lanzamiento de extremo a extremo para simular la ejecución en un entorno desplegado.
- [ ] Adjuntar un depurador a la solución iniciada o a las pruebas automatizadas en ejecución, establecer puntos de interrupción, recorrer el código e inspeccionar las variables.
- [ ] Instalar automáticamente las dependencias en su IDE.
- [ ] Utilizar los valores de configuración locales de dev.

Más detalles sobre la experiencia del desarrollador
