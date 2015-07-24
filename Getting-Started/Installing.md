## Install

### Linux systems

1. Unzip your copy of Linkurious:
`>unzip linkurious-linux-v0.10.0.zip`.

2. Enter the Linkurious folder: `>cd linkurious-linux`.

3. Check the configuration and make sure that the URL of you Neo4j database is correctly specified: `>head ./data/config/production.json`. Example output:
```JSON
{
  "dataSources": [{
    "graphdb": {
      "vendor": "neo4j",
      "url": "http://localhost:7474",
      "user": null,
      "password": null
    }
```

4. If you need to change the URL of Neo4j or specify a user/password, edit the configuration file with your favorite editor. When adding a user/password, remember to put these strings between quotes (`"`).

5. You your deployment is security critical, please make sure that you are not running Linkurious with a `root` account.

6. Start Linkurious: `>./start.sh`. Example output:
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

7. As you can notice, the Linkurious server is available by default on port 3000. However, some firewalls block network traffic ports other than 80 (HTTP) and 443 (HTTPS). Since only `root` users can use there ports, you may want reroute traffic from 80 to 3000 as follows:
`> sudo iptables -t nat -A PREROUTING -p tcp --dport 80 -j REDIRECT --to-port 3000`

### Mac OSX systems

1. Unzip your copy of Linkurious:
`>unzip linkurious-osx-v0.10.0.zip`.

2. Enter the Linkurious folder: `>cd linkurious-osx`.

3. Check the configuration and make sure that the URL of you Neo4j database is correctly specified: `>head ./data/config/production.json`. Example output:
```JSON
{
  "dataSources": [{
    "graphdb": {
      "vendor": "neo4j",
      "url": "http://localhost:7474",
      "user": null,
      "password": null
    }
```

4. If you need to change the URL of Neo4j or specify a user/password, edit the configuration file with your favorite editor. When adding a user/password, remember to put these strings between quotes (`"`).

5. You your deployment is security critical, please make sure that you are not running Linkurious with a `root` account.

6. Start Linkurious: `>./start.sh.command`. Example output:
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



### Windows systems

![picture of the download folder](https://dl.dropboxusercontent.com/s/1y73tkflooy9bi9/11.png?dl=0)

[Unzip](http://customize.org/help/How_To_Unzip_A_File) that file in the folder of your choice.

![linkurious enterprise folder](https://dl.dropboxusercontent.com/s/l06cj5kmlrku3ls/12.png?dl=0)

