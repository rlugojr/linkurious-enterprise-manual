## Démarrer

Avant de démarrer Linkurious, lancez d'abord votre serveur Neo4j server et configurez-le. Par défaut, Neo4j 2.2 introduit une autentification basique, voir la section Configuration pour en savoir plus. 

### Démarrer sous un système Linux

Démarrer Linkurious: démarrez `start.sh`. Autre possiilité, démarrez `menu.sh` et sélectionnez  `Start Linkurious processes` à partir de la console.

**Exemple de résultat:**
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

Comme vous pouvez le remaquer, le serveur Linkurious est disponible par défaut sur le port  3000. Cependant, certains pares-feu bloque le trafic réseau pour des ports autres que 80 (HTTP). Voir la section Configurtion pour accepter le trafic sur un port on port 80.


### Démarrer sous MAC OS X


Démarrer Linkurious: démarrez`start.sh.command`. Autre possiilité, démarrez`menu.sh.command` et sélectionnez `Start Linkurious processes` à partir de la console.

**Exemple de résultat:** 
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


### Démarrer sous Windows

Premièrement, afin d'utiliser Linkurious vous avez besoin de [démarrer Neo4j](http://neo4j.com/download/).


[démarrer neo4j](Launching-neo4j.png)

Une fois que le serveur Neo4j a démarré, allez dans le dossier Linkurious.

![Dossier](Folder.png)

Cliquez sur le fichier `start.bat`. Linkurious démarre et vous invite à ouvrir votre navigateur  à l'adresse  http://localhost:3000 pour accèder à l'interface utilisateur. Alternativement, cliquez sur  `menu.bat` et sélectionnez `Start Linkurious processes` à partir de la console.

![Démarrage de linkurious enterprise](Startup.png)

<div class="alert alert-warning">
    <i class="octicon octicon-stop"></i> Le pare-feu de Windows peut vous demander d'autoriser les connections avec Linkurious, dans ce cas cliquer sur Autoriser l'accès.
</div>

Linkurious indexera la base de données de graphe la première fois que vous le démarrerez. Vous pouvez suivre la progression de l'indexation dans le terminal. Une fois terminé, vous pouvez utiliser Linkurious.



