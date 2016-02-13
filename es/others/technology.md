## Tecnología

![architecture](http://linkurio.us/images/lke-technical-diagram.svg)

Linkurious Enterprise es la suma de dos componentes:

* El cliente web, que se ejecuta en un navegador web y proporciona a los usuarios una interfaz gráfica para explorar los grafos de forma visual.
* La plataforma, que es una aplicación de tipo servidor middleware que proporciona servicios REST para buscar y explorar grafos, editar datos del grafo y construir y compartir visualizaciones.

La plataforma contiene:
* Un módulo de grafo, que permite al acceso y edición de los datos del grafo.
* Un módulo de búsqueda, que permite realizar búsquedas avanzadas en los nodos y relaciones del grafo.
* Un módulo de acceso, que permite gestionar y aplicar restricciones de acceso a datos y edición de datos a los grupos de usuarios.
* Un módulo de persistencia, para guardar visualizaciones y otros elementos en el disco.

La plataforma puede ejecutarse en cualquier sistema capaz de soportar Java y Node.js, incluyendo Windows, Linux y Mac OS.

La plataforma Linkurious se comunica con su base de datos Neo4j y su índice ElasticSearch  (existente en su infraestructura, o incluido) a través de APIs HTTP: cada componente podría ejecutarse en diferentes máquinas en su red.

Linkurious Enterprise está basado en tecnología Open Source:

* La plataforma está construida sobre [Node.js](http://nodejs.org/) para permitir alto rendimiento en cualquier sistema moderno Linux, Mac o Windows.
* El módulo de búsqueda de la plataforma utiliza [ElasticSearch](http://www.elasticsearch.org/) para búsquedas full-text en tiempo real sobre nodos y relaciones.
* El módulo de persistencia de la plataforma utiliza [Sequelize.js](http://docs.sequelizejs.com/en/latest/) para permitir to persistencia en [SQLite](https://sqlite.org/), [MySQL](https://www.mysql.com/) o [PostgreSQL](http://www.postgresql.org/) con configuración mínima.
* El cliente está construido con [Angular.js](https://angularjs.org/) para una experiencia fluida en diferentes navegadores web.
* Las visualizaciones interactivas del cliente están basadas en [Linkurious.js](https://github.com/Linkurious/linkurious.js) para conseguir alto rendimiento e interacciones avanzadas con grafos en el navegador.

