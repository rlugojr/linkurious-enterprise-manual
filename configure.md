## Configure

The configuration file is located at `linkurious/data/config/production.json`.

#### Link to the Neo4j server

If it is the first time you run the Neo4j server and the version of Neo4j is >= v2.2:

1. Launch the Neo4j server;
- Open the browser at location http://localhost:7474 ;
- Set a new login and password and remember them to configure Linkurious.

Configure Linkurious:

- Open the configuration file;
- Check the `dataSources/graphdb` settings with the URL of the Neo4j server and set the credentials of the Neo4j server


Skip this section if you launch Linkurious with default configuration. You can configure it anytime.