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

5. If your deployment is security critical, please make sure that you will not run Linkurious with a `root` account.

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

5. If your deployment is security critical, please make sure that you will not run Linkurious with a `root` account.

### Windows systems

![picture of the download folder](https://dl.dropboxusercontent.com/s/1y73tkflooy9bi9/11.png?dl=0)

[Unzip](http://customize.org/help/How_To_Unzip_A_File) that file in the folder of your choice.

![linkurious enterprise folder](https://dl.dropboxusercontent.com/s/l06cj5kmlrku3ls/12.png?dl=0)

### How to run multiple instances of Linkurious

Linkurious is designed to run a single instance per machine.
While it is not recommended and with no guarantee to work, you may run multiple instances of Linkurious by doing the following:

Copy the entire linkurious directory (the one including this file) to a new place, and edit the `data/config/production.json` file:
You will need to change ``listenPort`` to set a different port from the one used in the `production.json` file. You may also edit `graphdb` and `db.storage`.

This is an example of a second instance of Linkurious served on `http://localhost:3001`, that calls the Neo4j API on the port `7475`:

```JavaScript
{
  "dataSources": [{
    "graphdb": {
      "vendor": "neo4j",
      "url": "http://localhost:7475"
    },
    "index": {
      "vendor": "elasticSearch",
      "host": "localhost",
      "port": 9201
    }
  }],
  "db": {
    "username": null,
    "password": null,
    "logging": true,
    "options": {
      "dialect": "sqlite",
      "storage": "database_secondInstance.sqlite"
    }
  },
  "server": {
    "listenPort": 3001,
    "clientFolder": "/public",
    "cookieSecret": "zO6Yb7u5H907dfEcmjS8pXgWNEo3B9pNQF8mKjdzRR3I64o88GrGLWEjqNq1Yx5"
  }
}
```

If you use the ElasticSearch software bundled with Linkurious, you will also need to modify the configuration in `system/elasticsearch/config/elasticsearch.yml` to set an alternate port to the default of 9201.

Finally, note that it is not currently possible to install different versions of Linkurious as a system service, at the same time, on the same machine.
