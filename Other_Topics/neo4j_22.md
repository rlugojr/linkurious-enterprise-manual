## Neo4j 2.2


Linkurious Enterprise is compatible with Neo4j 2.2. This version of Neo4j increases performance by ~20%, and provides basic authentication by default. We recommend you switch to it.

To do so follow these simple steps:

* The first time the Neo4j server is launched with a new database, go to http://localhost:7474/ and initialize your login/password;
* Edit the file ```linkurious\config\production.json``` and fill in the ```dataSources``` fields called ```user``` and ```password```;
* Run Linkurious and you're good to go!

A ```production.json``` configuration example:

      "graphdb": {
        "vendor": "neo4j",
        "url": "http://localhost:7474",
        "user": "neo4j",
        "password": "pwd",
        "templates": {
          "nodes": [],
          "relationships": []
        }