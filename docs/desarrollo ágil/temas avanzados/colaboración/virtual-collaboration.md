# Colaboración Virtual y Pair Programming

La programación en parejas es el método de trabajo de facto que utilizan la mayoría de las grandes organizaciones de ingeniería. Dos desarrolladores, que trabajan de forma sincronizada, miran la misma pantalla e intentan codificar y diseñar juntos, lo que a menudo da como resultado un código mejor y más claro que el que cualquiera de ellos podría producir individualmente.
La programación en pareja funciona bien en las circunstancias adecuadas, pero pierde parte de su encanto cuando se ejecuta en un entorno completamente virtual. La configuración virtual sigue implicando que dos desarrolladores miren a la misma pantalla y hablen de sus diseños, pero a menudo hay problemas logísticos con los que hay que lidiar.
Los modelos de trabajo virtual son diferentes de los modelos presenciales a los que estamos acostumbrados. La programación en parejas, en su esencia, se basa en los siguientes principios:

* Generar claridad a través de la comunicación
* Producir una mayor calidad a través de la colaboración
* Crear propiedad a través de la contribución equitativa

El Red Team Testing (RTT) es un método de programación alternativo que utiliza los mismos principios pero con algunas de las ventajas que ofrecen los métodos de trabajo virtual.

## Red Team Testing

El Red Team Testing toma prestado su nombre del paradigma "Red Team" y "Blue Team" de las pruebas de penetración, y es una forma colaborativa y paralela de trabajar virtualmente. En el Red Team Testing, dos desarrolladores deciden conjuntamente la interfaz, la arquitectura y el diseño del programa, y luego se separan para la fase de implementación. Un desarrollador escribe las pruebas utilizando la interfaz pública, intentando realizar pruebas de casos límite, validación de entradas y otras pruebas de estrés de la interfaz. El segundo desarrollador escribe simultáneamente la implementación que finalmente se probará.

## Cuándo seguir la estrategia RTT

La RTT funciona bien en determinadas circunstancias. Si la colaboración tiene que ser virtual y toda la comunicación es virtual, la RTT reduce la necesidad de una comunicación constante y mantiene las ventajas de una sesión de diseño conjunta. Esto tiene en cuenta el elemento humano: La comunicación virtual es más agotadora que la comunicación en persona.
La RTT también funciona bien cuando hay un consenso total, o ninguno, sobre la finalidad del código. Dado que la creación del diseño de forma conjunta y el acuerdo para implementarlo y probarlo forman parte del método de la RTT, ésta crea forzosamente claridad a través de la iteración y la comunicación.

## Beneficios

El RTT tiene muchas de las mismas ventajas que el Pair Programming y el desarrollo orientado a pruebas, pero trata de actualizarlas para un entorno virtual.

* La implementación y las pruebas del código pueden realizarse en paralelo, a larga distancia o a través de zonas horarias, lo que reduce el tiempo total que se tarda en terminar de escribir el código.
* La RTT mantiene el paradigma de la programación por parejas, pero reduce la necesidad de la comunicación por vídeo o la comunicación constante entre los desarrolladores.
* La RTT permite centrarse detalladamente en el diseño y la alineación de la ingeniería antes de implementar cualquier código, lo que da lugar a interfaces más limpias y sencillas.
* RTT fomenta que las pruebas se prioricen junto a la implementación, en lugar de que las pruebas sigan o se vean influenciadas por la implementación del código.
* La documentación es una parte inherente de la RTT, ya que tanto el implementador como el probador necesitan una documentación correcta y actualizada, en la fase de implementación.

## Lo que se necesita para que la RTT funcione bien

* La exigencia de una comunicación constante y un buen trabajo en equipo puede suponer un reto; las actualizaciones diarias entre los miembros del equipo son esenciales para mantener la alineación en los distintos requisitos del código.
* La claridad del diseño del código y la estrategia de pruebas debe establecerse de antemano y documentarse como referencia. La falta de un diseño establecido provocará una desalineación entre las dos piezas principales de trabajo y la necesidad de una refactorización que requerirá mucho tiempo.
* La RTT no funciona bien si sólo un desarrollador conoce el diseño general. La comunicación en equipo es fundamental para garantizar que todos los desarrolladores que participan en la RTT están en la misma página.
