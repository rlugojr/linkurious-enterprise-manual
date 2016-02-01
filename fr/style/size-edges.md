## Dimensionner les liens selon une propriété

Dimensionner les liens fonctionne exactement de la même manière que dimensionner les noeuds.

Par défaut, tous les liens ont la même taille. Il est possible cependant de dimensionner la taille des liens selon une certaine propriété. Il sera alors possible d'apprécier la valeur de cette propriété selon la taille du lien.

Cette technique s'applique seulement à des propriétés quantitatives.

Dimensionner les liens fonctionne de la même manière que la fonctionnalité Colorer un lien de Linkurious Enterprise. Les options Colorer et Dimensionner peuvent êtres combinées pour obtenir des visualisations plus pertinentes. 


![](https://github.com/Linkurious/linkurious-enterprise-manual/raw/master/en/style/PriceZoom.png)


Dans la figure ci-dessus, nous pouvons voir la compagnie Instagram et différentes compagnies ayant investi dans Instagram. 

Si nous zoomons sur la relation entre Instagram et Sequoia Capital, nous pouvons voir la propriété ```raised_amount_usd``` avec la valeur ```55 000 000```.

Nous allons dimensionner la taille des différentes compagnies en fonction de leur propriété ```raised amount``` afin de savoir rapidement qui a investi le plus d'argent dans Instagram.

Nous cliquons sur l'onglet en haut à droite pour ouvrir le designpanel et choisissons l'onglet Edges.

Nous déplaçons la souris sur ```raised_amount```. En plus de pouvoir colorer les liens selon cette propriété, il est également possible de les dimensionner. Linkurious Enterprise peut faire ça pour toutes les propriétés ayant des valeurs numériques.

Nous allons sélectionner l'icône taille (```Size```).

Un nouveau menu apparaît. Il permet de paramètrer la ```Min/max size difference```, la différence de taille entre le lien ayant la plus petite valeur et le lien ayant la plus grande valeur.

Si nous voulons voir la différence de ```raised_amount``` nous allons paramétrer  ```Min/max size difference``` à ```2```.

![](https://github.com/Linkurious/linkurious-enterprise-manual/raw/master/en/style/TailleEdges.png)

Maintenant nous pouvons voir que certains liens apparaissent plus large que d'autres.


