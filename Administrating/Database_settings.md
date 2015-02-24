# Data sources

Linkurious Enterprise connects to local or remote data sources through HTTP and HTTPS. Data sources such as Neo4j servers may provide access to one or multiple graph databases. For instance, it is common to see Neo4j users switch from graph databases on the same Neo4j instance. Linkurious Enterprise handle multiple data source configurations to detect which databases are available through the configured data sources.

Data sources must be defined when Linkurious Enterprise is stopped.



Click on ```Data``` in the administrator dashboard.

![opening the data panel](https://dl.dropboxusercontent.com/s/ldthwja6l1qysm6/104.png?dl=0)

By default, Linkurious Enterprise connects to a Neo4j database located at ```http://localhost:7474/```.

![default settings for database](https://dl.dropboxusercontent.com/s/6cnhxqjolt407jf/105.png?dl=0)

# Elasticsearch settings

You can also specify the address of your index server. By default, we use Elasticsearch on the port ```9200``` of the local host.

You can change these settings.

![default settings for elasticsearch](https://dl.dropboxusercontent.com/s/6cnhxqjolt407jf/105.png?dl=0)
