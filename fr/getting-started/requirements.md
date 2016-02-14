## Requirements

### Logiciel

Le serveur Linkurious peut-être déployé sur les plateformes suivantes: 
* Windows 7, 8, 8.1, 10, et Server 2012.
* Mac OS X Lion et les versions plus récentes.
* Distribution Linux comme Debian 6+, CentOS 6.5+, Ubuntu 12.10+, Gentoo, et Mint 14+.

Les utilisateurs accèderont à Linkurious par un navigateur web. Tous les navigateurs modernes peuvent être utilisés:  
* Chrome 23 ou plus(le plus rapide).
* Internet Explorer 10 ou plus.
* Firefox 17 ou plus.
* Safari 7.
* Opera 12 ou plus.

Le moteur de recherche incorporé ElasticSearch nécessite Java 8 pour fonctionner de manière adéquate.
**Les variables de l'environnement JAVA_HOME peuvent être réglées**, voir [comment le faire sous Windows ici](http://docs.oracle.com/cd/E19182-01/820-7851/inst_cli_jdk_javahome_t/index.html).

#### SQLite et GLIBC 2.14

Linkurious utilise une base de donnéée incorporée SQLite pour la persistence. Cette base de données nécessite GLIBC >= 2.14.
Des versions plus anciennes de Linux n'ont pas cette version de GLIBC disponible. vous pouvez vérifier la version disponible pour votre système à l'addresse: http://distrowatch.com .

Si vous rencontrez un problème, une solution est d'utiliser un autre mécanisme de persistance de données pour Linkurious, comme [MySQL](https://www.mysql.fr/) ou [PostgreSQL](http://www.postgresql.org/).
Vous pouvez utilisé un serveur de base de données existant ou en installer un nouveau. Linkurious va garder son état dans une base de donnée spécifique "linkurious".
Voir la section Configuration pour changer le mécanisme de persistance utilisé par Linkurious. Merci de vous référer à la documentation officielle de MySQL ou de PostgreSQL pour l'installation et la configuration de ces bases de données.

Alternativement, vous devriez pouvoir arranger le problème avec debian en mettant à jour GLIBC manuellement:

```Bash
echo 'deb http://ftp.fr.debian.org/debian/ testing main' > /etc/apt/sources.list
apt-get update
apt-get install -t testing libc6-dev=2.19-9
```

#### Source de donnée

La plateforme Linkurious se connecte à des sources de données à distance par HTTP ou HTTPS. Nous encourageons l'utilisation des serveurs Neo4j version 2.0 et plus. Neo4j de Neo Technology est le système leader de base de données de graphes sur le marché. Vous pouvez calculer les exigences de matériel [ici](http://neo4j.com/developer/guide-sizing-and-hardware-calculator/).

### Hardware

Les exigences matérielles de la plateforme dépendent de la taille de la base de données de graphes à laquelle Linkurious est connecté. Jusqu'à 2 millions de noeuds et liens, nous recommendons d'installer le serveur Likurious  sur une machine avec 8 GB RAM, 4 CPU cores @ 2 Ghz, et 20 GB d'espace disque libre. 

Hardware requirements of the Linkurious web client varies also with the size of the visualized graphs. For up to 500 nodes and edges, we recommend to use a machine with 4 GB RAM, and 2 CPU cores @ 1.6 Ghz. The minimal screen resolution is 1024x768 px.

