## Configure

**Skip this section if you launch Linkurious with the default configuration. You can configure it anytime.**

The configuration file is located at `linkurious/data/config/production.json`. It is a JSON file divided in the following sections:

* **dataSources** - The list of data sources to connect to
* **allSources** - General settings
    * Configure shortest paths, indexing, node expand and search limits, minimal search query length.
* **db** - The internal data store of Linkurious
    * Default database: an embedded SQLite database. You may switch to another SQL database for production.
* **server**
    * The Linkurious server. :warning: Replace `cookieSecret` with your own value.
* **logger** - The amount of information logged by the server.
* **access** - The access rights
    * Enable authentication, configure LDAP authentication, set data read-only mode.
* **clientAnalytics**
    * Log user actions in the client to your Google Analytics account (disabled by default).
* **sigma**
    * The settings of Sigma.js. You should only edit the following:
   * **styles**
       * You may edit the default styles of nodes and edges. See [sigma.plugins.designer](https://github.com/Linkurious/sigma.js/tree/plugin/designer/plugins/sigma.plugins.designer) to learn more.
   * **palette**
       * The default color palette of nodes and edges. See [sigma.plugins.designer](https://github.com/Linkurious/sigma.js/tree/plugin/designer/plugins/sigma.plugins.designer) to learn more.

#### Data sources

Data sources are servers accessible through the network (local, intranet or internet) with URLs to connect to. We assume that each data source serves a single graph database, however it may serve a different database the next time Linkurious will connect to it. For instance, you may load a database on your Neo4j server, then restart the server with another database. Linkurious will use the store ID to identify the database, so that you can switch between databases easily.

Linkurious can connect to many data sources at the same time. End users will select which database to work on, and switch between them. 

Data sources are configured within the **dataSources** key, which is a list of potential data sources. Each data source contains the following settings:

* **name** (optional) - A human-readable name.
* **graphdb** - The graph database server to connect to.
    * **vendor** - `"neo4j"`. Only Neo4j servers are supported.
    * **url** - `"http://localhost:7474/"`. Linkurious will call the Neo4j REST API on this address.
    * **writeURL** (optional) - If provided, Linkurious will send WRITE queries to the graph database through this address.
    * **user** (optional) - The username if authentication is enabled on the graph database server.
    * **password** (optional) - The password if authentication is enabled on the graph database server.
* **index** - The search engine.
    * **vendor** - `"elasticSearch"`. Only ElasticSearch servers are supported.
    * **host** - `"localhost"`.
    * **port** - `9200`.
    * **forceReindex** - `false`. If `true`, Linkurious will always re-index the graph database on startup.

The following settings applies to all data sources. They are available in the **allSources** key.

General settings:

* **connectionRetries** - `10`. The maximum number of connection attempts to each data source and to the search engine before stating them as disconnected.
* **pollInterval** - `10`. Check if the data sources and search engine are connected at each interval (in second).

Search engine settings:

* **indexationChunkSize** - `5000`. The number of nodes and edges retrieved at each batch during indexing the graph database.
* **searchAddAllThreshold** - `500`. The maximum number of search results that the User can add to a Visualization at once.
* **searchThreshold** - `3000`. The maximum number of search results that can be returned.
* **minSearchQueryLength** - `3`. The number of characters needed to trigger a search query. Set `1` to provide live results from the first character typed by the User.

Graph exploration settings:

* **maxPathLength** - `20`. The maximum shortest path length returned by Linkurious. Finding the shortest paths is a costly operation. Setting a small number will limit the resources used by the data source for performing this operation, and will return results faster.
* **shortestPathsMaxResults** - `10`. The maximum of shortest paths returned.
* **rawQueryTimeout** - `1000`. Abandon a query to the database if the time is over (in second).
* **expandThreshold** - `10`. When the User expands a node with too many neighbors, Linkurious will ask to refine the query so that fewer neighbors are returned.

#### Connect to a Neo4j server

If it is the first time you run the Neo4j server and you use Neo4j v2.2 or a more recent version:

1. Launch the Neo4j server;
- Open the browser at location http://localhost:7474 ;
- Set a new user and password, and remember them to configure Linkurious.

Configure Linkurious:

- Open the configuration file;
- Find the `graphdb` settings of the data source;
- Set the URL of the Neo4j server;
- Set the user and password of the Neo4j server.

Linkurious will connect to it the next time you start it.

#### Connect to the search engine

The embedded ElasticSearch engine may be replaced by your own ElasticSearch cluster. Edit the configuration file to set the `index` settings of the data source with the URL and credentials of your ElasticSearch cluster. Linkurious will create an index for each graph database, with index names prefixed by `linkurious_`.

#### Connect to the LDAP service

In Linkurious, Administrators manage other user accounts. User accounts are identified by either a login or an email address. If Linkurious is connected to an LDAP service (preferably OpenLDAP or Active Directory), users are authenticated each time they sign in. If you have a LDAP service running in your network, you can use it to authenticate users in Linkurious.

To enable LDAP authentication in Linkurious, edit the configuration file and add an `ldap` section inside `access`:

```JavaScript
"access": {
  // [...]
  "ldap": {
    // If true, Linkurious will try to connect to LDAP server on startup 
    // using 'bindDN' and 'bindPassword'
    "enabled": true,
    // URL of the LDAP server to connect to
    "url": "ldap://ldap.forumsys.com:389",
    // 'Domain Name' of the LDAP account used to binding
    "bindDN": "cn=read-only-admin,dc=example,dc=com",
    // password of the LDAP account used for binding
    "bindPassword": "password",
    // Base 'Domain Name' in which users will be searched
    "baseDN": "dc=example,dc=com'",
    // name of the LDAP attribute containing the USERNAME of a user
    "usernameField": "uid",
    // name of the LDAP attribute containing the PASSWORD of a user
    "passwordField": "userPassword",
    // name of the LDAP attribute containing the EMAIL of a user
    "emailField": "mail"
  }
}
```

#### Internal data store

Linkurious stores information such as visualizations, users, and permissions into a data store different from the graph databases. By default, Linkurious uses an SQLite database. MySQL and PostgreSQL are also available.

The internal data store is configured within the `db` key:

* **name** - `"linkurious"`. The name of the database.
* **username** (optional) - The username of the admin user of the database.
* **password** (optional) - The password of the admin user of the database.
* **options** - 
    * **dialect** - `"sqlite"`. Available values: `"mysql"`, `"postgres"`.
    * **storage** (optional) - `"data/server/database.sqlite"`. The relative path to the database file. Required for SQLite.
    * **host** (optional) - Required for MySQL and PostgreSQL.
    * **port** (optional) - Required for MySQL and PostgreSQL.


<div class="alert alert-warning">
    <i class="octicon octicon-stop"></i> GLIBC >= v1.14 must be installed on your computer for <b>SQLite</b>. You can check the version available on unix systems on http://distrowatch.com .
</div>

#### Web server


#### Logger

* **level** - `"info"`. Set the amount of server information stored. Available levels: `debug`, `error`.

#### Access rights


#### Client analytics


#### Default style of visualizations


