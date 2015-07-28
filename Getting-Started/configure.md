## Configure

<div class="alert alert-info">
    Skip this section if you launch Linkurious with the default configuration. You can modify the configuration anytime.
</div>

The configuration file is located at `linkurious/data/config/production.json`. It is a JSON file divided in the following sections:

* **dataSources** - The list of data sources to connect to.
* **allSources** - Settings that apply to all data sources.
    * Configure shortest paths, indexing, node expand and search limits, minimal search query length.
* **db** - The internal data store of Linkurious.
* **server** - The Linkurious server configuration.
* **access** - The access rights.
    * Enable authentication, configure LDAP authentication, set data read-only mode.
* **clientAnalytics**
    * Log user actions in the client using a Google Analytics account (disabled by default).
* **sigma** - The settings of Sigma.js.
    * You should only edit the styles and palette keys.

### Data management

#### Data sources

Data sources are servers accessible through the network (local, intranet or internet) with URLs to connect to. We assume that each data source serves a single graph database, however it may serve a different database the next time Linkurious will connect to it. For instance, you may load a database on your Neo4j server, then restart the server with another database. Linkurious will use the store ID to identify the database, so that you can switch between databases easily.

Linkurious can connect to many data sources at the same time. End users will select which database to work on in the interface, and switch between them. 

Data sources are configured within the **dataSources** key, which is a list of potential data sources. A single data source is configured by default to connect to a local Neo4j server. Each data source contains the following settings:

* **name** (optional) - A human-readable name.
* **graphdb** - The graph database server to connect to.
    * **vendor** - `"neo4j"`. Only Neo4j servers are supported.
    * **url** - `"http://localhost:7474/"`. Linkurious will call the Neo4j REST API on this address.
    * **writeURL** (optional) - If provided, Linkurious will send WRITE requests to the graph database to this endpoint and READ requests to the **url** endpoint.
    * **user** (optional) - The username if authentication is enabled on the graph database server.
    * **password** (optional) - The password if authentication is enabled on the graph database server.
* **index** - The search engine.
    * **vendor** - `"elasticSearch"`. Only ElasticSearch servers are supported.
    * **host** - `"localhost"` to use the embedded ElasticSearch index. You can specify the host of your own ElasticSearch server
    * **port** - `9201` to use the embedded ElasticSearch server. You can specify the port of your own ElasticSearch server. 
    * **forceReindex** - `true`. Linkurious will always re-index the graph database on startup if `true`, otherwise the administrators will have to trigger it from the Administration dashbard (see Administration Chapter).

The following settings applies to all data sources. They are available in the **allSources** key.

General settings:

* **connectionRetries** - `10`. The maximum number of connection attempts to each data source and to the search engine before stating them as disconnected.
* **pollInterval** - `10`. Check if the data sources and search engine are connected at each interval (in second).

Search engine settings:

* **indexationChunkSize** - `5000`. The number of nodes and edges retrieved at each batch during indexing the graph database.
* **searchAddAllThreshold** - `500`. The maximum number of search results that the user can add to a Visualization at once.
* **searchThreshold** - `3000`. The maximum number of search results that can be returned.
* **minSearchQueryLength** - `3`. The number of characters needed to trigger a search query. Set `1` to provide live results from the first character typed by the user.

Graph exploration settings:

* **maxPathLength** - `20`. The maximum shortest path length returned by Linkurious. Finding the shortest paths is a costly operation. Setting a small number will limit the resources used by the data source for performing this operation, and will return results faster.
* **shortestPathsMaxResults** - `10`. The maximum of shortest paths returned.
* **rawQueryTimeout** - `60000`. Abandon a query to the database if the time is over (in second).
* **expandThreshold** - `50`. When the user expands a node with too many neighbors, Linkurious will ask to refine the query so that fewer neighbors are returned.

Neo4j instance management settings:
Linkurious can manage your Neo4j server for you in order to simplify your administration scripts. To enable this feature (available on Linux and Max OSX only), simply set the **neo4jPath** key in **allSources** to the absolute path of Neo4j's home directory. You will notice a new "Neo4j server" entry in the status report of Linkurious' administration menu.  

#### Connection to a Neo4j server

If it is the first time you run a Neo4j server and you use Neo4j v2.2 or a more recent version, you need to configure the credentials:

1. Launch the Neo4j server;
- Open the browser at location http://localhost:7474 ;
- Set a new user and password, and remember them to configure Linkurious.

Configure Linkurious:

- Open the configuration file;
- Find the `graphdb` settings of the data source;
- Set the URL of the Neo4j server;
- Set the user and password of the Neo4j server.

Linkurious will connect to it the next time you start it.

#### Connection to the search engine

The embedded ElasticSearch engine may be replaced by your own ElasticSearch cluster. Edit the configuration file to set the `index` settings of the data source with the URL and credentials of your ElasticSearch cluster. Linkurious will create an index for each graph database, with index names prefixed by `linkurious_`.

#### Internal data store

Linkurious stores information such as visualizations, users, and permissions into a data store separate from the graph databases. By default, Linkurious uses an SQLite database. MySQL and PostgreSQL are also available but they should be installed manually.

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
    GLIBC >= v1.14 must be installed on the server for SQLite. You can check the version available on unix systems on <a href="http://distrowatch.com">http://distrowatch.com</a>.
</div>

### Web server

The web server of Linkurious delivers the application to end users through HTTP/S. It is configured within the `server` key:

* **listenPort** - `3000`. The port of the web server. Some firewalls block network traffic ports other than 80 (HTTP). Since only `root` users can listen on ports < 1024, you may want reroute traffic from 80 to 3000 as follows.

```
>sudo iptables -t nat -A PREROUTING -p tcp --dport 80 -j REDIRECT --to-port 3000
```

### Security

Multiple security features can be enabled according to your needs. The `cookieSecret` key of the `server` is randomized at the first start of Linkurious.

#### Cookies

Within the `server` key:

* **cookieSecret** - The secret key used to encrypt the session cookie. Randomized on first start.
* **cookieDomain** (optional) -  Restrict the validity of cookies to a domain or subdomain.

#### Cross-origin resource sharing (CORS)

Within the `server` key:

* **allowOrigin** - `"*"`. Define the cross-origin resource sharing (CORS) policy. Accept cross-site HTTP/S requests by default (wildcard).

#### Image cross-origin (client-side)

Within the `sigma` key:

* **imgCrossOrigin** - `"anonymous"`. Restrict the origin of images displayed in visualizations to prevent running malicious code on the graphic card of users. Display images from any origin by default.

#### End-to-end encrypted communications with SSL

External communications with the Linkurious server can be encrypted with SSL without installing third-party software.

Within the `server` key:

* **listenPortHttps** - `3443`. The port of the web server if HTTPS is enabled. See the Install section to learn why you should not set `443` directly.
* **useHttps** - `false`. Encrypt communications through HTTPS if `true`. Require a valid SSL certificate.
* **forceHttps** - `false`. Force all traffic to use HTTPS only if `true`. The server will reject all HTTP requests.
* **certificateFile** (optional) - The relative path to the SSL certificate.
* **certificateKeyFile** (optional) - The relative path to a public key of the SSL certificate.

If the Linkurious server, data sources, and the search engine are installed on different machines, we recommend to encrypt internal communication between them. It will protect you against packet sniffing on your intranet or on a cloud infrastructure. Please refer to the documentation of Neo4j and ElasticSearch to enable HTTPS.

#### User access rights

The user access system is configured within the `access` key:

* **authRequired** - `false`. Reject requests of anonymous sessions if `true`, otherwise all requests will be related to a "Unique User" account. Set it `false` to launch Linkurious for the first time, or if there is a single user.
* **dataEdition** - `true`. Enable the creation, edition, and deletion of nodes and edges in all data sources. Administrators can fine-tune user permissions, see the Administration Chapter. If `false`, all edition requests sent through Linkurious to the data sources will be rejected.
* **loginTimeout** - `3600`. Log the user out after a period of inactivity (in second).
* **ldap** - The connection to the LDAP service (see below).

##### Connection to the LDAP service

In Linkurious, administrators manage other user accounts. User accounts are identified by either a login or an email address. If Linkurious is connected to an LDAP service (preferably OpenLDAP or Active Directory), users are authenticated each time they sign in. If you have a LDAP service running in your network, you can use it to authenticate users in Linkurious. Notice that Linkurious stores encrypted passwords for users not authenticated by LDAP.

To enable LDAP authentication in Linkurious, edit the configuration file to add an `ldap` section inside `access`. Example:

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

Please refer to the documentation of your LDAP provider.

<div class="alert alert-warning">
    Contact your network administrator to ensure that the machine where Linkurious is installed can connect to the LDAP service.
</div>

#### User permissions to the data sources

Administrators can set fine-grained permissions to end users for each data source. See the Administration Chapter to learn more.

### Logging

Linkurious can log events at server side and at client side.

#### Server logs

The Linkurious server logs various events into files at `data/manager/logs/Linkurious-Server-*.log`. They are helpful to fix issues and you should include them to your support tickets.
Logs of the embedded ElasticSearch server can be found in `data/manager/logs/ElasticSearch-Server-*.log`.

#### Client logs

The Linkurious client can log user actions by sending events to your Google Analytics account. They provide information of the way the application is used, which features are the most useful, etc. This feature is disabled by default and no external script is injected in this case. It is configured within the `clientAnalytics` key:

* **enabled** - `false`. 
* **code** - Universal Analytics code of the form "UA-XXXXX-xx".
* **domain** - `"none"`. The domain from which Linkurious is accessible to the users, e.g. "www.example.com", or "none".

#### Audit trails

This feature is not available yet.
