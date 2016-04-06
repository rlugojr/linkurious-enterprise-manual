Dans ce chapitre, nous allons apprendre les bases pour explorer et visualiser une base de données de graphe avec Linkurious.

###A propos du jeu de données

Cette section du manuel et les chapitres qui suivent sont basés sur un jeu de données provenant de Crunchbase. Crunchbase est un site internet populaire qui traque l'écosystème des start-ups, plus spécifiquement des entreprises et investisseurs.

Nous avons utilisé Crunchbase pour créer une base de données  d'approximativement 75 000 nœuds et 250 000 liens. A partir de cela, nous avons créé un sous ensemble afin de nous concentrer sur les entreprises de la zone de San Francisco Bay. Ce sous ensemble contient 14 866 nœuds et 47 093 liens. Un graphe contient 4 types de nœuds

- Villes
- Entreprises
- Investisseurs
- Marchés
 
Les entreprises et les investisseurs sont reliés aux villes par le lien ```HAS_CITY```. Les entreprises sont reliées entre elles par le lien ```ACQUIRED```. Les investisseurs et les entreprises sont reliées les uns aux autres par le lien ```INVESTED_IN``` . Les entreprises sont reliées aux marchés par le lien ```HAS_MARKET```.

Afin de suivre ce manuel, nous vous suggérons [de télécharger et d'installer le jeu de données. ](http://linkurio.us/public/crunchbase-sfbay.db.zip) Vous devez extraire l'archive et la placer dans le dossier ```[YOUR_NEO4J_FOLDER]/data/graph.db```
