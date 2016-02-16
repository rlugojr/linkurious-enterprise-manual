## Configurer

<div class="alert alert-info">
    Passez cette étape si vous lancez Linkurious avec la configuration par défaut. Vous pouvez modifier la configuration à tout moment.
</div>

Le fichier de configuration est localisé à l'adresse:  `linkurious/data/config/production.json`. C'est un fichier JSON diviser selon les sections suivantes: 

* **dataSources** - La liste des sources de données auxquelles se connecter
* **allSources** - Les paramètres qui s'appliquent à toutes les sources de données.
    * Configurer des raccourcis, indexer, étendre les noeuds et limites de recherche, taille minimale des requêtes.
* **db** - Le stockage de données interne de Linkurious
* **server** - La configuration du serveur Linkurious
* **access** - Les droits d'accès
    * Autoriser l'autentification, configurer l'autentification LDAP, paramétrer le mode de lecture seule, autoriser la publication en ligne. 
* **clientAnalytics**
    * Action de connections des utilisateurs pour les clients utilisant un compte Google Analytics (désactivé par défaut).
* **sigma** - Les paramètres de Sigma.js.
    * Vous devriez seulement éditer les styles et palettes

### Gestion des données

#### Sources de données

Les sources de données sont des serveurs accessibles par le réseau (local, intranet ou internet) avec des URLs auxquels se connecter. Nous partons du principe que chaque source de données sert une unique base de données de graphes, cependant, elle peut servir une base de données différent la prochaine fois que Linkurious s'y connectera. Par exemple, vous pouvez charger une base de données sur votre serveur Neo4j, puis redémarrer le serveur avec une autre base de données. Linkurious utilisera l'identifiant de stockage pour identifier la base de données, ainsi vous pourrez passer d'une base de données à une autre facilement.

Linkurious peut se connecter à plusieurs sources de données en même temps. Les utilisateurs sélectionnerons avec quelle base de données travailler dans l'interface et pourrions passer de l'une à l'autre.

Les sources de données sont configurées dans la clé **dataSources** qui est une liste de sources de données potentielles. Une unique source de données est configurée par défaut pour se connecter au serveur Neo4j. chaque source de données contient les paramètres suivants:

* **name** (optionnel) - Un nom lisible (human-readable name).
* **graphdb** - Le serveur de base de données de graphes auquel se connecter 
    * **vendor** - `"neo4j"`. Seuls les sserveurs Neo4j sont supportés
    * **url** - `"http://127.0.0.1:7474/"`. Linkurious appelera le REST API Neo4j à cette addresse.
    * **writeURL** (optionnel) - Si fournit, Linkurious enverra les requêtes d'écriture à la base de données de graphes à cet endroit et les requêtes de lecture à son **url** endpoint.
    * **user** (optionnel) - L'identifiant si l'autentification est activé sur le serveur de la base de données de graphes. 
    * **password** (optionel) - Le mot de passe si l'autentification est activé sur le serveur de la base de données de graphes.
* **index** - Le moteur de recherche.
    * **vendor** - `"elasticSearch"`. Seuls les serveurs d'ElasticSearch sont supportés.
    * **host** - `"127.0.0.1"` pour utiliser l'index incorporé. Vous pouvez spécifier l'hôte de votre propre serveur ElasticSearch.
    * **port** - `9201` pour utiliser l'index incorporé. Vous pouvez spécifier le port de votre propre serveur ElasticSearch.. 
    * **forceReindex** - `false`. Linkurious re-indexera toujours la base de données de graphes sur startup si `true`, sinon les Administrateurs devront le déclencher à partir du tableau de bord de gestion (voir le chapitre Gestion).

Les réglages suivants s'appliquent à toutes les sources de données. Ils sont disponible dans le menu **allSources**.

Paramètres généraux:

* **connectionRetries** - `10`. Le nombre de connexions maximales tentées pour chaque soure de données et au moteur de recherche avant de les considérer comme déconnectées. 
* **pollInterval** - `10`. Vérifie si la source de donnée et le moteur de recherche sont connectés à chaque intervalles (en secondes).

Paramètres du moteur de recherche:

* **indexationChunkSize** - `5000`. Le nombre de noeuds et de liens remontés à chaque paquet durant l'indexation de la base de données de graphes 
* **searchAddAllThreshold** - `500`. Le nombre maximal de résultats de recherche que l'utilisateur peut ajouter à une visulisation en une fois. 
* **searchThreshold** - `3000`. Le nombre maximal de résultats de recherches qui peuvent êtres donnés 
* **minSearchQueryLength** - `3`. Le nombre de caractères nécessaires pour déclencher une recherche. Paramètrez `1` pour fournir des résultats en direct à partir du premier caractère. 

Paramètres d'exploration des graphes:

* **maxPathLength** - `20`. La longueur maximale du chemin le plus court donné par Linkurious. Trouver le chemin le plus court est une opération coûteuse. Paramètrer un petit nombre limitera les ressources utilisées par la source de données pour réaliser cette opération, et reournera des résultats plus rapidement.  
* **shortestPathsMaxResults** - `10`. Le nombre maximal de chemin le plus court données.
* **rawQueryTimeout** - `60000`. Abandonne une requête à la base de donnée si le temps est dépassé (en secondes) 
* **defaultFuzziness** - `0.9`. Valeur par défaut pour rechercher vaguement entre 0 et 1. Une valeur de `1` signifie une correspondance exacte avec la requête. 
* **expandThreshold** - `50`. Lorsque les utilisateurs développe un noeud avec trop de voisins, Linkurious demandera d'affiner la rechercher pour que moins de voisins soit donnés. 

#### Connexion à un serveur Neo4j

Si c'est la première fois que vous démarrez un serveur Neo4j et que vous utilisez Neo4j v2.2 ou une version plus récente, vous avez besoin de configurer ainsi:  

1. Démarrez le serveur Neo4j
- Ouvrez le moteur de recherche à l'adresse: http://127.0.0.1:7474 ;
- Paramètrez un nouvel utilisateur et mot de passe, et rappelez vous en afin de pouvoir configurez Linkurious.

Configurer Linkurious:

- Ouvrez le dossier de configuration;
- Trouvez les paramètres `graphdb` de la source de données;
- Paramètrez l'URL du serveur Neo4j;
- Paramètrez l'utilisateur et le mot de passe du serveur Neo4j.

Linkurious s'y connectera la prochaine fois que vous le démarrez.

#### Gestion des instances Neo4j

Linkurious peut gérer (le démarrer et l'arrêter quand Linkurious démarre et s'arrête) votre sserveur Neo4jafin de simplifier vos scripts d'administration. Pour activer cette option (disponible sous Linuc et Mac OSX), il suffit de paramètrer **neo4jPath** dans **allSources** au chemin du répertoire d'origine de Neo4j's. Vous aurez alors un nouveau "Neo4j server" d'entrée dans le rapport de statuts du menu de la console Linkurious' (voir le chapitre Gérer>Surveillance).

#### Connexion au moteur de recherche

Le moteur de recherche incorporé ElasticSearch peut-être remplacer par votre propre ElasticSearch. Editez le fichier de configurationpour paramètrer l'`index` de la source de donnée avec l'URL et les connexions à votre moteur ElasticSearch. Linkurious créera un index pour chaque base de données de graphes, avec des noms d'index préfixés par`linkurious_`.

#### Stockage de données interne

Linkurious stocke les informations telles que les visualisations, les utilisateurs et les permissions dans un dossier de données séparé de la base de données de graphes. Par défaut, Linkurious utilise une base de données SQLite. MySQL et PostgreSQL arsont aussi disponible mais doivent être installées manuellemente.

Le stockage de données interne est configuré dans la clé `db`:

* **name** - `"linkurious"`. Le nom de la base de donnés.
* **username** (optional) - L'identifiant de l'administrateur de la base de données. 
* **password** (optional) - Le mot de passe de l'administrateur de la base de données. 
* **options** - 
    * **dialect** - `"sqlite"`. Valeurs disponibles: `"mysql"`, `"postgres"`.
    * **storage** (optionnel) - `"server/database.sqlite"`. Le chemin du fichier de la base de données, relatif au répertoire `data`. Exigé pour SQLite.
    * **host** (optionnel) - Exigé pour MySQL et PostgreSQL.
    * **port** (optional) - Exigé pour MySQL et PostgreSQL.


<div class="alert alert-warning">
    GLIBC >= v1.14 doit être installé sur le serveur afin d'utiliser SQLite. Vous pouvez vérifier la version disponible pour votre système à l'adresse  <a href="http://distrowatch.com/search.php?ostype=All&category=All&origin=All&basedon=All&notbasedon=None&desktop=All&architecture=All&package=All&status=Active">http://distrowatch.com</a>.
</div>

### Serveur web

Le serveur web de Linkurious délivre l'application aux utilisateurs finaux par HTTP/S. Il est configuré dans la clé `server` :

* **domain** - `localhost`. Le domaine ou sous domaine utilisé pour accèder au serveur web. C'est obligatoire d'e l'éditer pour une publication en ligne des visualisations. Il est aussi utilisé pour restreindre la validité des cookies à un domaine ou à un sous domaine. 
* **listenPort** - `3000`. Le port du serveur web. Certains pares-feu bloquent le trafic réseau aux ports autre que  80 (HTTP). Etant donné que seuls les utilisateurs  `root` peuvent écouter sur les ports < 1024, vous pourriez vouloir réorienter le trafic de 80 à 3000 comme suit: 

```
>sudo iptables -t nat -A PREROUTING -p tcp --dport 80 -j REDIRECT --to-port 3000
```

### Sécurité

Plusieurs options de sécurité peuvent être activées selon vos besoins. La clé  `cookieSecret` du  `server` est déterminée aléatoirement au démarrage de Linkurious.  

#### Cookies

Dans la clé `server` :

* **cookieSecret** - La clé secrète utilisé pour encrypter la session de cookie. Aléatoire au premier démarrage.  

#### Partage des ressources d'origines croisées (CORS)

Dans la clé  `server`:

* **allowOrigin** - `"*"`. Défini la politique de partage des ressources d'origine croisées (CORS). Accepte les requêtes sites croisés HTTP/S par défaut (wildcard).

#### Image cross-origin (côté client)

Dans la clé `sigma`:

* **imgCrossOrigin** - `"anonymous"`. Restreint l'origine des images affichées en visualisations pour prévenir le démarage de code malveillants sur la carte graphique de l'utilisateur. Montre des images de quelconque origine par défaut.

#### Encryptage de communications c end-to-end avec SSL

Les communications externes avec le serveur de Linkurious server peuvent être encryptées sans installer un logiciel tiers.

Dans la clé `server` :

* **listenPortHttps** - `3443`. Le port du serveur web si HTTPS est activé. Voir la section Install pour apprendre pourquoi vous ne devriez pas directement paramètrer `443`.
* **useHttps** - `false`. Encrypter les communications via HTPPS si `true`. Exige un certificat SSL valide. 
* **forceHttps** - `false`. Force tout trafic à utiliser seulement HTTP si `true`. Le serveur rejetera toute requête HTTP.
* **certificateFile** (optionnel) - Le chemin relatif au certificat SSL.
* **certificateKeyFile** (optionnel) - Le chemin relatif à une clé publique du certificat SSL.

Si le serveur Linkurious, les sources de données, et le moteur de recherche sont installés sur des machines différentes, nous recommendons d'encrypter la communication entre elles. Celà protègera contre le reniflage de paquets de votre intranet ou sur une infrastructure cloud. Merci de vous référer à la documentation de Neo4j et d'ElasticSearch pour activer HTTPS. 

#### Droits d'accès des utilisateurs  

Le système d'accès des utilisateurs est configuré dans la clé `access`:

* **authRequired** - `false`. Rejeter les requêtes d'une session anonyme si `true`, sinon, toutes les requêtes seront liées à un compte "Unique User" . Paramètrez-le `false` pour lancer Linkurious pour la première fois, ou s'il y a un unique utilisateur. 
* **dataEdition** - `true`. Autorise la création, l'édition, et la suppression de noeuds et de liens dans toutes les sources de données. Les administrateurs peuvent règler les permissions des utilisateurs, voir le chapitre Administration. Si `false`, toutes les requêtes d'édition envoyées par Linkurious seront rejetées.
* **widget** - `true`. Active la publication en ligne de visualisations. Les visualisations publiées sont accessibles par les utilisateurs anonymes Plus d'informations dans la section **Gérer > Publier** du manuel.
* **loginTimeout** - `3600`. Déconnecte l'utilisateur après une période d'inactivité (en secondes) 
* **ldap** - La connexion au service LDAP (voir ci-dessous).

##### Connexion au service LDAP

Dans Linkurious, les administrateurs gère les comptes des autres utilisateurs. Les comptes d'utilisateurs sont définis soit par un identifiant ou une adresse email. Si Linkurious est connecté à un service LDAP (de préférence OpenLDAP ou Active Directory), les utilisateurs sont autentifiés chaque fois qu'il se connectent. Si vous avez un service LDAP en route sur votre réseau, vous pouvez l'utilisé pour autentifier les utilisateurs de Linkurious. Notez que Linkurious stocke les mots de passe encryptés pour les utilisateurs non autentifiés par LDAP. 

Pour autoriser l'autentification LDAP dans Linkurious, paramètrer la configuration. 

Pour Microsoft Active Directory, ajoutez une section `msActiveDirectory` sà l'intérieur de `access`:

```JavaScript
"access": {
  // [...]
  "msActiveDirectory": {
    "enabled": true,
    // URL of the Active Directory server to connect to
    "url": "ldap://ldap.lks.com",
    // Base 'Domain Name' in which users will be searched
    "baseDN": "dc=ldap,dc=lks,dc=com",
    // Domain of your Active Directory server
    "domain": "ldap.lks.com"
  }
}
```

Pour OpenLDAP, ajoutez une section `ldap` à l'intérieur de `access`:

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

Merci de vous référer à la documentation de votre fournisseur LDAP.

<div class="alert alert-warning">
    Contactez votre administrateur réseau pour vous assurer que votre ordinateur sur lequel est installé Linkurious peut se connecter à un service LDAP. 
</div>

#### Permissions des utilisateurs pour les sources de données 

Les administrateurs peuvent affinés les permission des utilisateurs pour chaque source de données. voir le chapitre Administration pour en savoir plus.

### Connexion

Linkurious peut enregistrer des événements du côté serveur et du côté client. 

#### Enregistrements serveurs

Le serveur Linkurious enregistre différents événements dans des fichiers à l'adresse `data/manager/logs/Linkurious-Server-*.log`. Ils sont utiles pour fixer des problèmes et et vous devrier les inclure dans vos tickets d'incidents. Les événements du serverincorporé ElasticSearch peut être trouvé dans `data/manager/logs/ElasticSearch-Server-*.log`.

#### Enregistrements clients

Le client Linkurious cenregistrer les actions d'utilisateurs en envoyant les événements à votre compte Google Analytics. Ils fournissent des informations sur la manière dont l'application est utilisée, quelles options sont les plus utiles, etc. Cette option est désactivée par défaut et aucun script extérne n'est lors injecté. elle se configure dans la clé `clientAnalytics`:

* **enabled** - `false`. 
* **code** - Code universels Analytics code de forme "UA-XXXXX-xx".
* **domain** - `"none"`. Le domaine à partir duquel Linkurious est accessible par les utilisateurs, exemple: "www.example.com", ou "none".

#### Pistes d'audit

Audit trails allows you to record detailed logs about the operations performed on your graph database by the users of Linkurious Enterprise. The log files contain JSON lines. You can easily bind a log management system like [Logstash](https://www.elastic.co/products/logstash) to interpret them. This feature is disabled by default. The following settings are available within the `auditTrail` key:

* **enabled** - `false`. Enable the audit trail recording if `true`.
* **logFolder** - `"audit-trail"`. Where to store the log files. This path is relative to the `data` directory located at the root of your Linkurious installation.
* **fileSizeLimit** - `5242880`. Maximum size in byte of one log file (default: 5MB). A new file is created when the limit is reached (files rotations) to avoid enormous log files.
* **strictMode** - `false`. Ensure that the operation has been logged before returning the result to the user if `true`. Might have a big impact on the server responsiveness.
* **mode** - `"rw"`. Will record READ actions (`"r"`), WRITE actions (`"w"`), or both (`"rw"`).
