## Data sources

Linkurious Enterprise connects to local or remote data sources through HTTP and HTTPS. Data sources such as Neo4j servers may provide access to one or multiple graph databases. For instance, it is common to see Neo4j users switch between graph databases on the same Neo4j instance. Linkurious Enterprise handles multiple data source configurations and detects which databases are available behind the connected data sources.

We stop Linkurious Enterprise to add new data sources.

We go to  ```\linkurious\config``` in our Linkurious Enterprise directory.

We open the ```production.json``` file. We look for ```dataSources```. It is an array of data source configuration. By default, a single data source is defined for Linkurious Enterprise to connect to a Neo4j database located at ```http://localhost:7474/```. Duplicate the default configuration and edit graphdb vendor and url to define a second data source.

We restart Linkurious Enterprise.

We click on ```Data``` in the Administration dashboard.

![opening the data panel](https://dl.dropboxusercontent.com/s/ldthwja6l1qysm6/104.png?dl=0)

We can now edit the data source configuration, set up and trigger data indexing.

![default settings for database](https://dl.dropboxusercontent.com/s/6cnhxqjolt407jf/105.png?dl=0)

Notice that we may switch the data source in the breadcrumb when multiple data sources are connected.

## Search index

We may change the address of the index server. By default, we use Elastic on the port ```9200``` of the local host.

![default settings for elastic](https://dl.dropboxusercontent.com/s/6cnhxqjolt407jf/105.png?dl=0)
