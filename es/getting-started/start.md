## Iniciar

Antes de iniciar Linkurious, por favor arranque su servidor Neo4j y configure sus credenciales primero. Neo4j 2.2 introduce autenticación básica por defecto, consulte la sección de Configuración para más detalle.

### Ejecutar en sistemas Linux

Iniciar Linkurious: ejecute `start.sh`. Alternativamente, ejecute `menu.sh` y seleccione `Start Linkurious processes` desde la consola.

**Resultado de ejemplo:**
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

Como usted puede ver, el servidor Linkurious está disponible por defecto en el puerto 3000. Sin embargo, algunos cortafuegos bloquean tráfico de red en puertos diferentes al 80 (HTTP). Consulte la sección de Configuración para aceptar tráfico en el puerto 80.


### Ejecutar en MAC OS X


Iniciar Linkurious: ejecute `start.sh.command`. Alternativamente, ejecute `menu.sh.command` y seleccione `Start Linkurious processes` desde la consola.

**Resultado de ejemplo:** 
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


### Ejecutar en Windows

Antes de nada, para utilizar Linkurious usted necesita [arrancar Neo4j](http://neo4j.com/download/).


![arrancando neo4j](https://github.com/Linkurious/linkurious-enterprise-manual/raw/master/en/getting-started/Launching-neo4j.png)

Una vez que el servidor de Neo4j haya arrancado correctamente, acceda al directorio de Linkurious.

![directorio](https://github.com/Linkurious/linkurious-enterprise-manual/raw/master/en/getting-started/Folder.png)

Haga clic en el archivo `start.bat`. Linkurious inicia y le solicita abrir su navegador web en http://localhost:3000 para acceder a la interfaz de usuario. Alternativamente, haga clic en `menu.bat` y seleccione `Start Linkurious processes` desde la consola.

![inicio de linkurious enterprise](https://github.com/Linkurious/linkurious-enterprise-manual/raw/master/en/getting-started/Startup.png)

<div class="alert alert-warning">
    <i class="octicon octicon-stop"></i> El cortafuegos de Windows podría pedirle autorizar conexiones con Linkurious: si es así, haga clic en Autorizar acceso.
</div>

Linkurious indexará la base de datos de grafos la primera vez que lo inicie. Usted puede seguir el proceso de indexación en la terminal. Una vez haya terminado ¡usted puede utilizar Linkurious!


