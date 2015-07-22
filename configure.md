## Configure

Skip this section if you launch Linkurious with default configuration. You can configure it anytime.

The configuration file is located at `linkurious/data/config/production.json`.

#### Link to the Neo4j server

If it is the first time you run the Neo4j server and the version of Neo4j is >= v2.2:

1. Launch the Neo4j server;
- Open the browser at location http://localhost:7474 ;
- Set a new login and password and remember them to configure Linkurious.

Configure Linkurious:

- Open the configuration file;
- Check the `dataSources/graphdb` settings with the URL of the Neo4j server and set the credentials of the Neo4j server

#### Link to the LDAP service

An identified person of the organization has an Administrator account to Linkurious. He manages other user accounts. User accounts are identified by either a login or an email address. If Linkurious is connected to an LDAP service (preferably OpenLDAP or Active Directory), users are authenticated each time they sign in. 

If you have a LDAP service running in your network, you can use it to authenticate users in Linkurious.
To enable LDAP authentication in Linkurious, edit the configuration file (`linkurious/config/production.json`) and add an `ldap` section under `clientRights`:

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

#### Secured connections

TODO: how to set up HTTPS
