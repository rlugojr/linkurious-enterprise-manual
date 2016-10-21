# Neo4j to Elasticsearch synchronization

You can automatically synchronize you Neo4j graph database with an Elasticsearch index using the [neo4j-to-elasticsearch](https://github.com/graphaware/neo4j-to-elasticsearch) plugin.
A Linkurious-compatible version of this plugin is available for Neo4j v3.0.4.
Linkurious-compatible-versions can be built for later versions of Neo4j [**on request**](support@linkurio.us).

Using the neo4j-to-elasticsearch plugin makes it unnecessary to re-index the Neo4j database in Linkurious an external source (not Linkurous) updates the data. The data in Elasticsearch is always up-to-date (with a couple of seconds of latency sometimes).

How does it work?
==
When the neo4j-to-elasticsearch plugin is installed, all changes to the Neo4j database are automatically replicated to the configured Elasticsearch instance.

How can I use it?
==
You need Linkurious v1.4 or later.
1. Download and install [Elasticsearch](https://www.elastic.co/downloads/elasticsearch)
2. Download the [neo4j-to-elasticsearch plugin JAR (v3.0.4)](https://dl.dropboxusercontent.com/u/20754236/graphaware-neo4j-to-elasticsearch-3.0.4.43.7-SNAPSHOT.jar)
3. Download the [GraphAware server plugin JAR (v3.0.4)](http://products.graphaware.com/download/framework-server-community/graphaware-server-community-all-3.0.4.43.jar)
4. Copy both JARs to the `./plugins` directory inside Neo4j
5. Edit your Neo4j configuration file (in `./conf/neo4j.conf`) and add the following lines at the beginning of the file:
```
com.graphaware.runtime.enabled=true
com.graphaware.module.ES.1=com.graphaware.module.es.ElasticSearchModuleBootstrapper
com.graphaware.module.ES.mapping=AdvancedMapping
com.graphaware.module.ES.keyProperty=ID()
# Elasticsearch server host
com.graphaware.module.ES.uri=localhost
# Elasticsearch server port
com.graphaware.module.ES.port=9200
# whether to index relationships in Elasticsearch (default: false)
com.graphaware.module.ES.relationship=(true)
```
6. restart Neo4j
7. Edit the Linkurious configuration in `linkurious/data/config/production.json` and change you data-source configuration like this:
```
"dataSources": [{
  "readOnly": false,
  "graphdb": {
    "vendor": "neo4j",
    "url": "http://127.0.0.1:7474",
    "user": null,
    "password": null
  },
  "index": {
    "vendor": "neo2es"
  }
}]
```
8. Restart Linkurious


