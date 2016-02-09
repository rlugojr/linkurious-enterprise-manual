## Contrôle

### Contrôle du processus

Linkurious démarre 3 processus différents lorsqu'il est lancé:
1. `node` (or `node.exe`): Le processus interne gestionnaire ( gestionnaire [PM2](https://github.com/Unitech/pm2) )  
2. `node` (or `node.exe`): Le processus du serveur Linkurious
3. `java` (or `java.exe`): Le serveur d'indexation incorporé [ElasticSearch](https://www.elastic.co/) 

Vérifiez si ces processus fonctionnent en ouvrant le menu du répertoire Linkurious (voir de quelle manière pour chaque sytème ci-dessous). Le menu apparaît comme dans les images ci-dessous:


![menu](Menu.png)


#### Linux systems

Run `menu.sh` (the status is above the menu). Alternately, run `menu.sh status`.

#### Mac OS X systems

Run `menu.sh.command` (the status is above the menu). Alternately, run `menu.sh.command status`.

#### Windows systems

Run `menu.bat` (the status is above the menu). Alternately, run `menu.bat status`.

### Status

#### Application

The application status can be retrieved by querying the Web server as follows:

> curl http://127.0.0.1:3000/api/status

**Success response:**

```
HTTP/1.1 200 OK
{
  "status": {
    "code": 200,
    "name": 'initialized',
    "message": 'Linkurious ready to go :)'
  }
}
```

Where "code" is the status code of the server (100: starting, 200: OK, >400: problem), "name" is the name of the current server status, and "message" describes the current server status.

#### Data sources

The status of all data sources can be retrieved by querying the web server as follows:

> curl http://127.0.0.1:3000/api/dataSources

**Success response:**

```
HTTP/1.1 200 OK
{
  "sources": [
    {"name":"Database #0","configIndex":0, "key":"a2e3c50f", "connected":true},
    {"name":"Database #1","configIndex":1, "key":null, "connected":false},
    {"name":"Database #2","configIndex":2, "key":null, "connected":false}
  ]
}
```

Where "configIndex" is the index of the data-source in the 'dataSources' configuration list (see the Configure section), "key" is the unique key that identifies the data-source (null when the source is not connected), and "connected" is `true` if the source is currently available.
