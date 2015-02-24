# Data sources

Linkurious Enterprise connects to local or remote data sources through HTTP and HTTPS. Data sources such as Neo4j servers may provide access to one or multiple graph databases. For instance, it is common to see Neo4j users switch from graph databases on the same Neo4j instance. Linkurious Enterprise handles multiple data source configurations and detects which databases are available behind the connected data sources.

Stop Linkurious Enterprise to add new data sources.

Go to  ```\linkurious\config``` in your Linkurious Enterprise directory.

Open the ```production.json``` file. Look for ```dataSources```. It is an array of data source configuration. By default, a single data source is defined for Linkurious Enterprise to connect to a Neo4j database located at ```http://localhost:7474/```. Duplicate the default configuration and edit graphdb vendor and url to define a second data source.

Restart Linkurious Enterprise.

Click on ```Data``` in the Administration dashboard to edit the data source configuration and to handle data indexing.

![opening the data panel](https://dl.dropboxusercontent.com/s/ldthwja6l1qysm6/104.png?dl=0)

![default settings for database](https://dl.dropboxusercontent.com/s/6cnhxqjolt407jf/105.png?dl=0)

In the administrator dashboard, notice that we may switch the data source in the breadcrumb when multiple data sources are connected.

# Elasticsearch settings

You can also specify the address of your index server. By default, we use Elasticsearch on the port ```9200``` of the local host.

You can change these settings.

![default settings for elasticsearch](https://dl.dropboxusercontent.com/s/6cnhxqjolt407jf/105.png?dl=0)
