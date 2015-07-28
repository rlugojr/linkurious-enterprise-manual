## Monitoring

### Process monitoring

Linkurious starts 3 separate processes when launched:
1. `node` (or `node.exe`): The internal process manager (a [PM2](https://github.com/Unitech/pm2) manager)  
2. `node` (or `node.exe`): The Linkurious Server process
3. `java` (or `java.exe`): The embedded [ElasticSearch](https://www.elastic.co/) indexation server.

Check if these processes are alive by opening the menu from the Linkurious directory (see how on each operating system below). The menu looks like the following image:


![color-scale](https://raw.githubusercontent.com/Linkurious/linkurious-enterprise-manual/master/screenshots/143.png)


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
