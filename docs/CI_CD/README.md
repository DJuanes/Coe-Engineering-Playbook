# Integración y entrega continuas

La **integración continua** es la práctica de ingeniería que consiste en comitear frecuentemente el código en un repositorio compartido, idealmente varias veces al día, y realizar una compilación automatizada sobre él. Estos cambios se compilan con otros cambios simultáneos en el sistema, lo que permite la detección temprana de problemas de integración entre varios desarrolladores que trabajan en un proyecto. Las interrupciones de la compilación debidas a fallos de integración se tratan como el problema de mayor prioridad para todos los desarrolladores de un equipo y, por lo general, el trabajo se detiene hasta que se solucionan.
Junto con un enfoque de pruebas automatizadas, la integración continua también nos permite probar la compilación integrada, de modo que podamos verificar no sólo que la base de código sigue compilandose correctamente, sino que también sigue siendo funcionalmente correcta. Esta es también una de las mejores prácticas para construir sistemas de software robustos y flexibles.

La **entrega continua** lleva el concepto de integración continua más allá para probar también los despliegues de la base de código integrada en una réplica del entorno en el que se desplegará finalmente. Esto nos permite conocer con antelación cualquier problema imprevisto que surja de nuestros cambios con la mayor rapidez posible y también conocer las brechas en nuestra cobertura de pruebas.
El objetivo de todo esto es asegurar que la rama principal sea siempre implementable, lo que significa que podríamos, si lo necesitáramos, tomar una compilación de la rama principal e implementarla en producción.

Para reforzar estos conceptos puedes leer sobre la [Integración Continua](https://www.martinfowler.com/articles/continuousIntegration.html) y la [Entrega Continua](https://martinfowler.com/bliki/ContinuousDelivery.html).
Para una comprensión mucho más profunda de todos estos conceptos, los libros [Continuous Integration](https://www.amazon.com/Continuous-Integration-Improving-Software-Reducing/dp/0321336380) y [Continuous Delivery](https://www.amazon.com/gp/product/0321601912) proporcionan una base completa.

## Herramientas

* [Azure Pipelines](https://azure.microsoft.com/es-es/services/devops/pipelines/)
* [Jenkins](https://www.jenkins.io/)
* [TravisCI](https://travis-ci.org/)
* [CircleCI](https://circleci.com/)
