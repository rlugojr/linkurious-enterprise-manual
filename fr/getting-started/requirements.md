## Exigences

### Logiciel

Le serveur Linkurious peut-être déployé sur les plate-formes suivantes: 
* Windows 7, 8, 8.1, 10, et Server 2012.
* Mac OS X Lion et les versions plus récentes.
* Distributions Linux telles que Debian 6+, CentOS 6.5+, Ubuntu 12.10+, Gentoo, et Mint 14+.

Les utilisateurs accèderont à Linkurious via un navigateur web. Tous les navigateurs modernes peuvent être utilisés:  
* Chrome 23 ou plus (le plus rapide).
* Internet Explorer 10 ou plus.
* Firefox 17 ou plus.
* Safari 7.
* Opera 12 ou plus.

Le moteur de recherche incorporé ElasticSearch nécessite Java 8 pour fonctionner de manière adéquate.
**Les variables de l'environnement JAVA_HOME doivent être réglées**, voir [comment le faire sous Windows ici](http://docs.oracle.com/cd/E19182-01/820-7851/inst_cli_jdk_javahome_t/index.html).

#### SQLite et GLIBC 2.14

Linkurious utilise une base de données incorporée SQLite pour le système de gestion des données. Cette base de données nécessite GLIBC >= 2.14.
Des versions plus anciennes de Linux n'ont pas cette version de GLIBC disponible. Vous pouvez vérifier la version disponible pour votre système à l'adresse: http://distrowatch.com .

Si vous rencontrez un problème, une solution est d'utiliser un autre mécanisme de gestion de persistance des données pour Linkurious, comme [MySQL](https://www.mysql.fr/) ou [PostgreSQL](http://www.postgresql.org/).
Vous pouvez utiliser un serveur de base de données existant ou en installer un nouveau. Linkurious va sauvegarder son état dans une base de données spécifique nommée "linkurious".
Voir la section Configuration pour changer le mécanisme de persistance utilisé par Linkurious. Merci de vous référer à la documentation officielle de MySQL ou de PostgreSQL pour l'installation et la configuration de ces bases de données.

Alternativement, vous devriez pouvoir corriger le problème avec debian en mettant à jour GLIBC manuellement:

```Bash
echo 'deb http://ftp.fr.debian.org/debian/ testing main' > /etc/apt/sources.list
apt-get update
apt-get install -t testing libc6-dev=2.19-9
```

#### Source de données

La plateforme Linkurious se connecte à des sources de données à distance par HTTP ou HTTPS. Nous encourageons l'utilisation des serveurs Neo4j version 2.0 et plus. Neo4j de Neo Technology est le système leader de base de données de graphes sur le marché. Vous pouvez calculer les pré-requis matériel [ici](http://neo4j.com/developer/guide-sizing-and-hardware-calculator/).

### Hardware

Les pré-requis matériels de la plateforme dépendent de la taille de la base de données de graphes à laquelle Linkurious est connecté. Jusqu'à 2 millions de noeuds et liens, nous recommandons d'installer le serveur Linkurious  sur une machine avec 8 GB RAM, 4 CPU cores @ 2 Ghz, et 20 GB d'espace disque libre. 

Les pré-requis matériels du client internet de Linkurious varie également en fonction de la taille des graphes visualisés. Jusqu'à 500 noeuds et liens, nous recommandons l'utilisation d'une machine avec 4 GB RAM, et 2 CPU cores @ 1.6 Ghz. La résolution minimale d'écran est 1024x768 px.

