## Start

### Run on Linux systems


Start Linkurious: `>./start.sh`. Example output:
```Text
info: Loaded configuration from file (production)
[PM2] Spawning PM2 daemon
[PM2] PM2 Successfully daemonized
info: Started: Linkurious Server.
info: Started: ElasticSearch Server.
info: Starting Linkurious Enterprise v0.10.0
info: Loaded configuration from file (production)
info: Status [Linkurious] 100 : Starting Linkurious in production mode... 
info: Status [SqlDB] 100 : Starting SQL database 
info: Status [DataService] 100 : Starting data service. 
info: Status [WebServer] 100 : Starting Web Server
info: First run, initialization ...
info: Status [SqlDB] 101 : The SQL database is up.
info: Status [SqlDB] 200 : The SQL database is synced.
info: Status [WebServer] 200 : The Web server is listening on port 3000 (HTTP)
info: Data-source #0 connected successfully (graph:neo4j v2.1.6 - index:elasticSearch v1.4.5)
info: Status [DataService] 200 : 1 data-sources connected. 
info: Status [Linkurious] 200 : Linkurious ready to go :) 
info: Status [DataService] 201 : A data-source is currently indexing.
Linkurious is ready at URL: http://127.0.0.1:3000/
```

As you can notice, the Linkurious server is available by default on port 3000. However, some firewalls block network traffic ports other than 80 (HTTP). Since only `root` users can listen on this ports, you may want reroute traffic from 80 to 3000.
```
>sudo iptables -t nat -A PREROUTING -p tcp --dport 80 -j REDIRECT --to-port 3000
```


### Run on MAC OS X


Start Linkurious: `>./start.sh.command`. Example output:
```Text
info: Loaded configuration from file (production)
[PM2] Spawning PM2 daemon
[PM2] PM2 Successfully daemonized
info: Started: Linkurious Server.
info: Started: ElasticSearch Server.
info: Starting Linkurious Enterprise v0.10.0
info: Loaded configuration from file (production)
info: Status [Linkurious] 100 : Starting Linkurious in production mode... 
info: Status [SqlDB] 100 : Starting SQL database 
info: Status [DataService] 100 : Starting data service. 
info: Status [WebServer] 100 : Starting Web Server
info: First run, initialization ...
info: Status [SqlDB] 101 : The SQL database is up.
info: Status [SqlDB] 200 : The SQL database is synced.
info: Status [WebServer] 200 : The Web server is listening on port 3000 (HTTP)
info: Data-source #0 connected successfully (graph:neo4j v2.1.6 - index:elasticSearch v1.4.5)
info: Status [DataService] 200 : 1 data-sources connected. 
info: Status [Linkurious] 200 : Linkurious ready to go :) 
info: Status [DataService] 201 : A data-source is currently indexing.
Linkurious is ready at URL: http://127.0.0.1:3000/
```


### Run on Windows

First of all, in order to use Linkurious Enterprise you need to [launch Neo4j](http://neo4j.com/download/). Download it, install it and launch it.

![launching neo4j](https://dl.dropboxusercontent.com/s/6sm5ja9ubvw5xhk/14.png?dl=0)

Ready? Go in the Linkurious Enterprise folder.

![picture of the dashboard](https://dl.dropboxusercontent.com/s/ml00vswfi4ggipt/13.png?dl=0)

Click on the ```start``` file on Windows. On Linux run ```linkurious.sh start```, on MAC run ```linkurious.sh.command start```. Linkurious Enterprise starts [Node.js](http://nodejs.org/), [ElasticSearch](http://www.elasticsearch.org/) and opens up your browser.

![linkurious enterprise startup](https://dl.dropboxusercontent.com/s/adrxil2q8ysfry5/16.png?dl=0)

> About Neo4j 2.2 Linkurious Enterprise is compatible with Neo4j 2.2. This version of Neo4j increases performance by ~20%, and provides basic authentication by default. In order to use it, you need to setup your credential first. Follow these steps:

>* The first time the Neo4j server is launched with a new database, go to http://localhost:7474/ and initialize your login/password;
* Edit the file ```linkurious\config\production.json``` and fill in the ```dataSources``` fields called ```user``` and ```password```;
* Run Linkurious Enterprise and you're good to go!

>A ```production.json``` configuration example:

      "graphdb": {
        "vendor": "neo4j",
        "url": "http://localhost:7474",
        "user": "neo4j",
        "password": "pwd",
        "templates": {
          "nodes": [],
          "relationships": []
        }

The first time you launch Linkurious Enterprise, it will index the data you are storing on Neo4j. You can follow the progress of the indexation in the Node.js screen. Once it is over, you can use Linkurious Enterprise!

![picture of the dashboard](https://dl.dropboxusercontent.com/s/2ax4yybrbs0x0o5/1.png?dl=0)

Windows might ask you to authorize Linkurious Enterprise : if so, click yes.

![authorize linkurious enterprise](https://dl.dropboxusercontent.com/s/e9phzsvvf7zy991/15.png?dl=0)

> To close Linkurious Enterprise on Windows, simply close all the terminal windows. On Linux run  ```linkurious.sh stop ``` and on MAC run  ```linkurious.sh.command stop ```.

