# Estructura de un Sprint

El propósito de este documento es:

- Organizar el contenido en el playbook para una rápida referencia y descubrimiento
- Proporcionar el contenido en una estructura lógica que refleje el proceso de ingeniería
- Una jerarquía extensible que permita a los equipos compartir conocimientos profundos sobre el tema

## La primera semana de un proyecto

### Antes de comenzar el proyecto

- [ ] Discutir y empezar a redactar los Acuerdos de Equipo. Actualice estos documentos con cualquier decisión de proceso tomada a lo largo del proyecto
  - Acuerdo de trabajo
  - Definición de Listo
  - Definición de Hecho
  - Estimación
- [ ] Establecer el/los repositorio/s
  - Decidir la estructura del repositorio
  - Añadir README.md, .gitignore, etc.
- [ ] Construir un Backlog de Producto
  - Configurar un proyecto en la herramienta de gestión de proyectos elegida (Azure DevOps)
  - Invertir en buenas historias de usuario y criterios de aceptación
  - Guía sobre los requisitos no funcionales


### Día 1

- [ ] Planificar el primer sprint
  - Acordar el objetivo del sprint y cómo medir el progreso del mismo
  - Determinar la capacidad del equipo
  - Asignar historias de usuario al sprint y dividir las historias de usuario en tareas
  - Establecer los límites del trabajo en curso (WIP)
- [ ] Decidir los frameworks de test y discutir las estrategias de testeo
  - Discutir el propósito y los objetivos de los tests y cómo medir la cobertura de los mismos
  - Acordar cómo separar los tests unitarios de los de integración, carga y humo
  - Diseñar los primeros casos de prueba
- [ ] Decidir la denominación de las ramas
- [ ] Discutir las necesidades de seguridad y verificar que los secretos se mantienen fuera del control de origen

### Día 2

- [ ] Configurar el control de código fuente
  - Acordar las mejores prácticas para los commits
- [ ] Configurar la integración continua básica con linters y pruebas automatizadas
- [ ] Establecer reuniones para los Stand-ups diarios
  - Discutir el propósito, los objetivos, los participantes y la guía de facilitación
  - Discutir el calendario y cómo llevar a cabo una reunión eficaz.
- [ ] Si el proyecto tiene subequipos, establecer un Scrum de Scrums

### Día 3

- [ ] Acordar el estilo de código y cómo asignar los Pull Requests
- [ ] Establecer la validación de la compilación para los Pull Requests (2 revisores, linters, pruebas automatizadas) y acordar la definición de Hecho
- [ ] Acordar una estrategia de fusión de código
- [ ] Acordar frameworks y estrategias de logging y observabilidad

### Día 4

- [ ] Configurar el despliegue continuo
  - Determinar qué entornos son apropiados para esta solución
  - Para cada entorno, discutir el propósito, cuándo debe activarse el despliegue, los aprobadores de predespliegue, la cancelación del despliegue.
- [ ] Decidir una estrategia de versiones

### Día 5

- [ ] Realización de una Demo del Sprint
- [ ] Realizar una retrospectiva
  - Determinar los participantes necesarios, la forma de captar las aportaciones (herramientas) y los resultados
  - Establecer un calendario y discutir la facilitación, la estructura de la reunión, etc.
- [ ] Refinar el Backlog
  - Determinar los participantes necesarios
  - Actualizar la definición de "listo".
  - Actualizar las estimaciones y el documento de estimación
