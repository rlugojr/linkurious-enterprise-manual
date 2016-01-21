Dans ce chapitre, nous allons apprendre les bases pour explorer et visualiser un graphique de base de données avec Linkurious.

###A propos du set de données

Cette section du manuel et les chapitres qui suivent sont basés sur un set de données provenant de Crunchbase. Crunchbase est un site internet populaire qui traque l'écosystème des start-up, plus spécifiquement des compagnies et investisseurs.

Nous avons utilisé Crunchbase pour créer une base de données  d'approximativement 75 000 nœuds et 250 000 relations. A partir de cela, nous avons crée un sous ensemble afin de nous concentrer sur les compagnies de la zone de San Francisco Bay. Ce sous ensemble contient 14 866 nœuds et 47 093 relations. Un graphique contient 4 types de nœuds

- Villes
- Compagnies
- Investisseurs
- Marchés
 
Les compagnies et les investisseurs sont reliés aux villes par la relation ```HAS_CITY```. Les compagnies sont reliées entre elles par la relation ```ACQUIRED```. Les investisseurs et les compagnies sont reliées les uns aux autres par la relation ```INVESTED_IN``` . Les compagnies sont reliées aux marchés par la relation ```HAS_MARKET```.

Afin de suivre ce manuel, nous vous suggérons [de télécharger et d'installer le set de données. ](http://linkurio.us/public/crunchbase-sfbay.db.zip) Vous devez extraire l'archive et la placer dans le dossier ```[YOUR_NEO4J_FOLDER]/data/graph.db```
