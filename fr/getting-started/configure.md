## Configurer

<div class="alert alert-info">
    Passez cette étape si vous lancez Linkurious avec la configuration par défaut. Vous pouvez modifier la configuration à tout moment.
</div>

Le fichier de configuration est localisé à l'adresse:  `linkurious/data/config/production.json`. C'est un fichier JSON divisé selon les sections suivantes: 

* **dataSources** - La liste des sources de données auxquelles se connecter
* **allSources** - Les paramètres qui s'appliquent à toutes les sources de données.
    * Configurer des raccourcis, indexer, étendre les noeuds et limites de recherche, taille minimale des requêtes.
* **db** - Le stockage interne de données de Linkurious
* **server** - La configuration du serveur Linkurious
* **access** - Les droits d'accès
    * Autoriser l'authentification, configurer l'authentification LDAP, paramétrer le mode de lecture seule, autoriser la publication en ligne. 
* **clientAnalytics**
    * Enregistrer les actions de connection des utilisateurs pour les clients utilisant un compte Google Analytics (désactivé par défaut).
* **sigma** - Les paramètres de Sigma.js.
    * Vous devriez seulement éditer les styles et palettes

### Gestion des données

#### Sources de données

Les sources de données sont des serveurs accessibles par le réseau (local, intranet ou internet) avec des URLs auxquels se connecter. Nous partons du principe que chaque source de données sert une unique base de données de graphe, cependant, elle peut servir une base de données différente la prochaine fois que Linkurious s'y connectera. Par exemple, vous pouvez charger une base de données sur votre serveur Neo4j, puis redémarrer le serveur avec une autre base de données. Linkurious utilisera l'identifiant de stockage ('store ID') pour identifier la base de données, ainsi vous pourrez passer d'une base de données à une autre facilement.

Linkurious peut se connecter à plusieurs sources de données en même temps. Les utilisateurs peuvent sélectionner la base de données dans l'interface passer des unes aux autres. 

Les sources de données sont configurées dans la clé **dataSources** qui est une liste de sources de données potentielles. Une unique source de données est configurée par défaut pour se connecter au serveur Neo4j. Chaque source de données contient les paramètres suivants:

* **name** (optionnel) - Un nom lisible (human-readable name).
* **graphdb** - Le serveur de base de données de graphes auquel se connecter 
    * **vendor** - `"neo4j"`. Les serveurs Neo4j et Titan sont supportés. Valeurs possibles: `"neo4j"`, `"titan"`.
    * **url** - `"http://127.0.0.1:7474/"`. Linkurious appelera l'API REST de Neo4j à cette adresse par défaut. Elle doit être de la forme ws://GREMLIN_SERVER_IP:GREMLIN_SERVER_PORT (ex: `"ws://192.168.0.5:8182"`) pour Titan.
    * **writeURL** (optionnel, Neo4j uniquement) - Si fourni, Linkurious enverra les requêtes d'écriture à la base de données de graphes à cet endroit et les requêtes de lecture à son **url**.
    * **configurationPath** (optionnel, Titan uniquement) - Si fourni, doit être le chemin absolu du fichier de configuration de Titan sur le serveur Gremlin (ex: `"/usr/local/titan/conf/titan-cassandra-es.properties"`) 
    * **user** (optionnel) - L'identifiant utilisateur si l'authentification est activée sur le serveur de la base de données de graphes. 
    * **password** (optionnel) - Le mot de passe utilisateur si l'authentification est activée sur le serveur de la base de données de graphes.
* **index** - Le moteur de recherche.
    * **vendor** - `"elasticSearch"`. Seuls les serveurs d'ElasticSearch sont supportés.
    * **host** - `"127.0.0.1"` pour utiliser l'index embarqué. Vous pouvez spécifier l'hôte de votre propre serveur ElasticSearch.
    * **port** - `9201` pour utiliser l'index e. Vous pouvez spécifier le port de votre propre serveur ElasticSearch.. 
    * **forceReindex** - `false`. Linkurious ré-indexera toujours la base de données de graphes au démarrage si `true`, sinon les Administrateurs devront le déclencher à partir du tableau de bord d'Administration (voir le chapitre Gestion).

Les réglages suivants s'appliquent à toutes les sources de données. Ils sont disponibles dans la clé **allSources**.

Paramètres généraux:

* **connectionRetries** - `10`. Le nombre de connexions maximales tentées vers le moteur de recherche pour chaque source de données et avant de les considérer comme déconnectées. 
* **pollInterval** - `10`. Vérifie si la source de données et le moteur de recherche sont connectés à chaque intervalle (en secondes).

Paramètres du moteur de recherche:

* **indexationChunkSize** - `5000`. Le nombre de noeuds et de liens récupérés à chaque appel durant l'indexation de la base de données de graphes 
* **searchAddAllThreshold** - `500`. Le nombre maximal de résultats de recherche que l'utilisateur peut ajouter à une visulisation en une fois. 
* **searchThreshold** - `3000`. Le nombre maximal de résultats de recherche qui peuvent  être donnés 
* **minSearchQueryLength** - `3`. Le nombre de caractères nécessaires pour déclencher une recherche. Paramétrez à `1` pour fournir des résultats en direct dès le premier caractère. 

Paramètres d'exploration des graphes:

* **maxPathLength** - `20`. La longueur maximale du chemin le plus court donné par Linkurious. Trouver le chemin le plus court est une opération coûteuse. Paramétrer un petit nombre limitera les ressources utilisées par la source de données pour réaliser cette opération, et retournera des résultats plus rapidement.  
* **shortestPathsMaxResults** - `10`. Le nombre maximal de chemins les plus courts données.
* **rawQueryTimeout** - `60000`. Abandonne une requête à la base de données si le temps est dépassé (en secondes) 
* **defaultFuzziness** - `0.9`. Valeur par défaut pour effectuer une recherche floue entre 0 et 1. Une valeur de `1` signifie une correspondance exacte avec la requête. 
* **expandThreshold** - `50`. Lorsque les utilisateurs déploient un noeud avec trop de voisins, Linkurious demandera d'affiner la rechercher pour que moins de voisins soit donnés. 

#### Connexion à un serveur Neo4j

Si vous démarrez le serveur Neo4j pour la première fois et que vous utilisez Neo4j v2.2 ou une version plus récente, vous avez besoin de configurer ainsi:  

1. Démarrez le serveur Neo4j
- Ouvrez le navigateur web à l'adresse: http://127.0.0.1:7474 ;
- Paramètrez un nouvel identifiant et mot de passe, et rappelez-vous en afin de pouvoir configurer Linkurious.

Configurer Linkurious:

- Ouvrez le dossier de configuration;
- Trouvez les paramètres `graphdb` de la source de données;
- Paramétrez l'URL du serveur Neo4j;
- Paramétrez l'utilisateur et le mot de passe du serveur Neo4j.

Linkurious s'y connectera au prochain démarrage.

#### Administration des instances Neo4j

Linkurious peut administrer (le démarrage et l'arrêt quand Linkurious démarre et s'arrête) votre serveur Neo4j afin de simplifier vos scripts d'administration. Pour activer cette option (disponible sous Linux et Mac OSX), il suffit de paramétrer **neo4jPath** dans **allSources** au chemin du répertoire d'origine de Neo4j. Vous aurez alors un nouveau "serveur Neo4j" d'entrée dans le rapport de statut du menu de la console Linkurious (voir le chapitre Gérer>Surveillance).

#### Connexion à Titan/Gremlin serveur

Ceci est un exemple de configuration de Linkurious pour se connecter à Titan 1.x via le serveur Gremlin.

```JavaScript
"dataSources": [
  {
    "name": "My Titan DB",
    "graphdb": {
      "vendor": "titan",
     "url": "ws://192.168.0.5:8182",
     "configurationPath": "/usr/local/titan/config/titan-cassandra-es.properties"
    },
    "index": {
      "vendor": "elasticSearch",
      "host": "127.0.0.1",
      "port": 9201,
      "forceReindex": false,
      "dynamicMapping": false
    }
  }
]
```

#### Connexion au moteur de recherche

Le moteur de recherche embarqué ElasticSearch peut être remplacé par votre propre instance de ElasticSearch. Editez le fichier de configuration pour paramétrer l'`index` de la source de données avec l'URL et les connexions à votre moteur ElasticSearch. Linkurious créera un index pour chaque base de données de graphe, avec des noms d'index préfixés par`linkurious_`.

#### Stockage interne de données 

Linkurious stocke les informations telles que les visualisations, les utilisateurs et les permissions dans une base de données séparée de la base de données de graphe. Par défaut, Linkurious utilise une base de données SQLite. MySQL et PostgreSQL sont aussi disponibles mais doivent être installées manuellement.

Le stockage interne de données est configuré dans la clé `db`:

* **name** - `"linkurious"`. Le nom de la base de données.
* **username** (optionnel) - L'identifiant de l'administrateur de la base de données. 
* **password** (optionnel) - Le mot de passe de l'administrateur de la base de données. 
* **options** - 
    * **dialect** - `"sqlite"`. Valeurs disponibles: `"mysql"`, `"postgres"`.
    * **storage** (optionnel) - `"server/database.sqlite"`. Le chemin du fichier de la base de données, relatif au répertoire `data`. Exigé pour SQLite.
    * **host** (optionnel) - Exigé pour MySQL et PostgreSQL.
    * **port** (optionnel) - Exigé pour MySQL et PostgreSQL.


<div class="alert alert-warning">
    GLIBC >= v1.14 doit être installé sur le serveur afin d'utiliser SQLite. Vous pouvez vérifier la version disponible pour votre système à l'adresse  <a href="http://distrowatch.com/search.php?ostype=All&category=All&origin=All&basedon=All&notbasedon=None&desktop=All&architecture=All&package=All&status=Active">http://distrowatch.com</a>.
</div>

### Serveur web

Le serveur web de Linkurious délivre l'application aux utilisateurs par HTTP/S. Il est configuré dans la clé `server` :

* **domain** - `localhost`. Le domaine ou sous domaine utilisé pour accèder au serveur web. Il est obligatoire de l'éditer pour une publication en ligne des visualisations. Il est aussi utilisé pour restreindre la validité des cookies à un domaine ou à un sous domaine. 
* **listenPort** - `3000`. Le port du serveur web. Certains pares-feu bloquent le trafic réseau aux ports autres que  80 (HTTP). Etant donné que seuls les utilisateurs  `racine` peuvent écouter sur les ports < 1024, vous pourriez vouloir réorienter le trafic de 80 à 3000 comme suit: 

```
>sudo iptables -t nat -A PREROUTING -p tcp --dport 80 -j REDIRECT --to-port 3000
```

### Sécurité

Plusieurs options de sécurité peuvent être activées selon vos besoins. La clé  `cookieSecret` du  `serveur` est déterminée aléatoirement au démarrage de Linkurious.  

#### Cookies

Dans la clé `server` :

* **cookieSecret** - La clé secrète utilisé pour encrypter la session de cookies. Aléatoire au premier démarrage.  

#### Partage des ressources d'origines croisées (CORS)

Dans la clé  `server`:

* **allowOrigin** - `"*"`. Défini la politique de partage des ressources d'origines croisées (CORS). Par défaut, accepte les requêtes sites croisés HTTP/S (wildcard).

#### Image cross-origin (côté client)

Dans la clé `sigma`:

* **imgCrossOrigin** - `"anonymous"`. Restreint l'origine des images affichées pour prévenir le démarage de codes malveillants sur la carte graphique de l'utilisateur. Par défaut, montre des images de quelconque origine.

#### Encryptage de communications end-to-end avec SSL

Les communications externes avec le serveur de Linkurious peuvent être encryptées sans installer un logiciel tiers.

Dans la clé `server` :

* **listenPortHttps** - `3443`. Le port du serveur web si HTTPS est activé. Voir la section Installer pour apprendre pourquoi vous ne devriez pas directement paramétrer `443`.
* **useHttps** - `false`. Encrypter les communications via HTPPS si `true`. Exige un certificat SSL valide. 
* **forceHttps** - `false`. Force tout trafic à utiliser seulement HTTP si `true`. Le serveur rejetera toute requête HTTP.
* **certificateFile** (optionnel) - Le chemin relatif au certificat SSL.
* **certificateKeyFile** (optionnel) - Le chemin relatif à une clé publique du certificat SSL.

Si le serveur Linkurious, les sources de données, et le moteur de recherche sont installés sur des machines différentes, nous recommandons d'encrypter la communication entre elles. Celà protègera contre le reniflage de paquets de votre intranet ou sur une infrastructure cloud. Merci de vous référer à la documentation de Neo4j et d'ElasticSearch pour activer HTTPS. 

#### Droits d'accès des utilisateurs  

Le système d'accès des utilisateurs est configuré dans la clé `access`:

* **authRequired** - `false`. Rejeter les requêtes d'une session anonyme si `true`, sinon, toutes les requêtes seront liées à un compte "Unique User" . Paramétrez-le `false` pour lancer Linkurious pour la première fois, ou s'il y a un unique utilisateur. 
* **dataEdition** - `true`. Autorise la création, l'édition, et la suppression de noeuds et de liens dans toutes les sources de données. Les administrateurs peuvent régler les permissions des utilisateurs, voir le chapitre Administration. Si `false`, toutes les requêtes d'édition envoyées par Linkurious seront rejetées.
* **widget** - `true`. Active la publication en ligne de visualisations. Les visualisations publiées sont accessibles par les utilisateurs anonymes. Plus d'informations dans la section **Gérer > Publier** du manuel.
* **loginTimeout** - `3600`. Déconnecte l'utilisateur après une période d'inactivité (en secondes) 
* **ldap** - La connexion au service LDAP (voir ci-dessous).

##### Connexion au service LDAP

Dans Linkurious, les administrateurs gère les comptes des autres utilisateurs. Les comptes d'utilisateurs sont définis soit par un identifiant ou une adresse email. Si Linkurious est connecté à un service LDAP (de préférence OpenLDAP ou Active Directory), les utilisateurs sont authentifiés chaque fois qu'il se connectent. Si vous avez un service LDAP en route sur votre réseau, vous pouvez l'utiliser pour authentifier les utilisateurs de Linkurious. Notez que Linkurious stocke les mots de passe encryptés pour les utilisateurs non authentifiés par LDAP. 

Pour autoriser l'autentification LDAP dans Linkurious, paramétrez la configuration. 

Pour Microsoft Active Directory, ajoutez une section `msActiveDirectory` à l'intérieur de `access`:

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

Les administrateurs peuvent affinés les permissions des utilisateurs pour chaque source de données. Voir le chapitre Administration pour en savoir plus.

### Connexion

Linkurious peut enregistrer des événements du côté serveur et du côté client. 

#### Enregistrements serveurs

Le serveur Linkurious enregistre différents événements dans des fichiers à l'adresse `data/manager/logs/Linkurious-Server-*.log`. Ils sont utiles pour fixer des problèmes et vous devrier les inclure dans vos tickets d'incidents. Les événements du moteur incorporé ElasticSearch peut être trouvés dans `data/manager/logs/ElasticSearch-Server-*.log`.

#### Enregistrements clients

Le serveur Linkurious enregistre les actions d'utilisateurs en envoyant les événements à votre compte Google Analytics. Ils fournissent des informations sur la manière dont l'application est utilisée, quelles options sont les plus utiles, etc. Cette option est désactivée par défaut et aucun script externe n'est alors injecté. Elle se configure dans la clé `clientAnalytics`:

* **enabled** - `false`. 
* **code** - Code universels Analytics de forme "UA-XXXXX-xx".
* **domain** - `"none"`. Le domaine à partir duquel Linkurious est accessible par les utilisateurs, exemple: "www.example.com", ou "none".

#### Pistes d'audit

Les pistes d'audit vous permettent d'enregistrer des éveénements détaillés sur les opérations effectuées dans votre base de données de graphes par les utilisateurs de Linkurious Enterprise. Les fichiers d'événements contiennent des lignes JSON. Vous pouvez facilement utiliser un système de gestion d'événements comme [Logstash](https://www.elastic.co/products/logstash) pour les interpréter. Par défaut, cette option est désactivée. Les paramètres suivants sont disponibles dans la clé `auditTrail`:

* **enabled** - `false`. Activer l'enregistrement de pistes d'audit si `true`.
* **logFolder** - `"audit-trail"`. Où stocker les fichiers d'enregistrement. Ce chemin est relatif au répertoire`data` localisé à la racine de votre installation Linkurious.
* **fileSizeLimit** - `5242880`. Taille maximal en byte d'un fichier d'enregistrement (par défaut: 5MB). Un nouveau fichier est créé quand la limite est atteinte (rotation de fichiers) pour éviter de trop grand fichiers d'enregistrement.
* **strictMode** - `false`. S'assure que l'opération a été enregistrée avant de donner le résultat à l'utilisateur si `true`. Peut avoir un gros impact sur la capacité de réponse du serveur. 
* **mode** - `"rw"`. Enregistrera les actions de LECTURE (`"r"`), d'ECRITURE (`"w"`), ou les deux (`"rw"`).
