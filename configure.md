## Configure

**Skip this section if you launch Linkurious with default configuration. You can configure it anytime.**

The configuration file is located at `linkurious/data/config/production.json`. It is a JSON file divided in the following sections:

* **dataSources** - The list of data sources to connect to
* **allSources** - General settings
    * Configure shortest paths, indexing, node expand and search limits, minimal search query length.
* **db** - The internal data store of Linkurious
    * Default database: an embedded SQLite database. You may switch to another SQL database for production.
* **server**
    * The Linkurious server. :warning: Replace `cookieSecret` with your own value.
* **logger**
    * Set the amount of server information stored. Default: `info` level. Available levels: `debug`, `error`.
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

Linkurious can connect to multiple data sources at the same time. Data sources are configured within the **dataSources** key, which is a list of potential data sources. Each data source contains the following settings:

* **name** (optional) - A human-readable name.
* **graphdb** - The graph database server to connect to.
    * **vendor** - `neo4j`
    * **url** - `http://localhost:7474/` Linkurious will call the Neo4j REST API on this url.
    * **writeURL** (optional) - 
    * **user** (optional) - 
    * **password** (optional) - 
* **index**
    * The search engine.
    * Default engine: `elasticSearch`.


#### Link to the Neo4j server

If it is the first time you run the Neo4j server and you use Neo4j v2.2 or a more recent version:

1. Launch the Neo4j server;
- Open the browser at location http://localhost:7474 ;
- Set a new login and password, and remember them to configure Linkurious.

Configure Linkurious:

- Open the configuration file;
- Check the `dataSources/graphdb` settings with the URL of the Neo4j server and set the credentials of the Neo4j server.

#### Link to the LDAP service

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

#### Link to the search engine

The embedded ElasticSearch engine may be replaced by your own ElasticSearch cluster. Edit the configuration file to set the `dataSources/index` settings with the URL and credentials of your ElasticSearch cluster. Linkurious will create an index for each graph database, with index names prefixed by `linkurious_`.

#### Secured connection through HTTPS

TODO
