## Technology

![architecture](http://linkurio.us/images/lke-technical-diagram.svg)

Linkurious Enterprise is the sum of two components:

* the Web client, whichs runs in a browser and provides users with a graphical interface to explore graphs visually;
* the platform, which is a middleware server application that provides REST services to search and browse graphs, edit graph data, build and share visualizations.

The platform contains:
* a graph module, which enables graph data access and edition;
* a search module, which enables advanced search in graph nodes and relationships data;
* an access module, which enables managing and applying data-access and data-edition restictions to user groups;
* a persistence module, to save visualizations and other items to disk.

The platform runs on any system able to support Java and Node.js, including Windows, Linux and Mac OS.

The Linkurious platform communicates with your Neo4j graph database and your ElasticSearch index (existing in your infrastructure, or built-in) through HTTP APIs: each components may run on different computers on your network.

Linkurious Enterprise is based on Open Source technology:

* the platform is built on top of [Node.js](http://nodejs.org/) to enable high performance on any modern Linux, Mac or Windows computer;
* the platform's search module uses [ElasticSearch](http://www.elasticsearch.org/) for real-time full-text search in nodes and relationships;
* the platform's persistence module uses [Sequelize.js](http://docs.sequelizejs.com/en/latest/) to enable persistence to [SQLite](https://sqlite.org/), [MySQL](https://www.mysql.com/) or [PostgreSQL](http://www.postgresql.org/) with minimal configuration;
* the client is built using [Angular.js](https://angularjs.org/) for a smooth cross-browser user experience;
* the client's interactive visualizations are powered by [Linkurious.js](https://github.com/Linkurious/linkurious.js) for high performances and advanced interactions with graphs in the browser.

