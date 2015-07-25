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

Double-click on `start.bat`.
