## Data sources

Linkurious Enterprise se connecte à des sources de données locales ou à distance par HTTP et HTTPS. Les sources de données comme les serveurs de  Neo4j peuvent fournir un accès à différentes bases de données de graphes. Par exemple, il est commun de voir les utilisateurs de Neo4j passer d'une base de données à l'autre sur le même serveur  Neo4j. Linkurious Enterprise gère la configuration de plusieurs source de données et détecte quelle base de données est actuellement disponible derrière la source de données connectée. 

### Ajouter une nouvelle source de données

1. Ouvrir le dossier Linkurious dans votre ordinateur
- Ouvrez le fichier localisé à `linkurious/data/config/production.json` avec votre éditeur de texte favoris
- Cherchez la clé `dataSources`. Il s'agit d'une multitude de configuration de sources de données. Par défaut, une unique source de données est définie pour se connecter au serveur Neo4j localisé à l'adresse suivante: `http://localhost:7474/`.Copiez la configuration par défaut et éditez le distributeur `graphdb` et  `url` pour définir une seconde source de données.
- Redémarrez Linkurious pour prendre en compte les changements

### Editez une source de données à partir du tableau de bord de gestion

Pour accédez au tableau de bord de gestion de données, cliquez sur **Data** dans le tableau de bord de l'administrateur, ou selectionnez **Data** dans le menu **Admin** de la barre de navigation. Vous devriez voir l'écran suivant: 

![](admin-data-server.png)

We can edit here the data source configuration, set up and trigger data indexing. To edit the configuration of another data source, switch the data source from the navigation bar.

### Search server

The search feature uses [Elasticsearch](https://www.elastic.co/products/elasticsearch) for real-time full-text search in nodes and relationships. An embedded Elasticsearch server is shipped with Linkurious but you may set up your own. All data sources are indexed into the same Elasticsearch instance by default; you may configure different Elasticsearch instances for each data source. Please refer to the official documentation of Elasticsearch to set up your own cluster.
