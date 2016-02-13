## Technologie

![architecture](http://linkurio.us/images/lke-technical-diagram.svg)

Linkurious Enterprise est la somme de deux composantes:

* Le client Web, qui s'exécute dans un navigateur et fournit aux utilisateur une interface graphique pour explorer visuellement les graphes;
* la plateforme,  platform, qui est un serveur d'application middleware et fournit les services REST pour chercher et explorer les graphes, éditer les données des graphes, construire et partager les visualisations.

La plateforme contient:
* un module de graphe, qui permet d'accèder et d'étider les données de graphe;
* un module de recherche, qui permet une recherche avancée dans les données des noeuds et des liens;
* un module d'accès, qui permet de gérer et d'assigner l'accès et les droits d'éditions aux utilisateurs des différents groupes;
* un module de persistance, pour sauvegarder les visualisations et autres éléments.

La plateforme s'exécute sur tout système capable de supporter Java et Node.js, incluant Windows, Linux et Mac OS.

La plateforme Linkurious communique avec votre base de graphes Neo4j et votre indexe ElasticSearch (existant dans votre infrastructure, ou inclue dedans) au travers de HTTP APIs: chaque composant peut être exécuté sur votre réseau.

Linkurious Enterprise est basé sur une technologie Open Source:

* la plateforme est construite sur [Node.js](http://nodejs.org/) pour permettre une haute performance sur tout ordinateur récent Linux, Mac ou Windows;
* le module de recherche de la plateforme utilise  [ElasticSearch](http://www.elasticsearch.org/) pour des recherches full-text en temps réel dans les noeuds et les liens;
* le module depersistance de la plateforme utilise [Sequelize.js](http://docs.sequelizejs.com/en/latest/) pour permettre une persistance à [SQLite](https://sqlite.org/), [MySQL](https://www.mysql.com/) ou [PostgreSQL](http://www.postgresql.org/) avec une configuration minimale;
* le client est construit en utilisant [Angular.js](https://angularjs.org/) pour une expérience fluide avec différents navigateurs web;
* les visualisations interactives du clients sont exécutées par [Linkurious.js](https://github.com/Linkurious/linkurious.js) pour de hautes performances et des interactions avancées avec les graphes dans le navigateur.

