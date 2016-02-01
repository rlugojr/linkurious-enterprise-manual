## Dimensionner les liens selon une propriété

Par exemple [Andreessen Horowitz](http://a16z.com/) est une entreprise leader avec 127 relations à différentes compagnies qu'elle a financé. Quelles compagnies ont reçues les fonds les plus importants? Il est difficile de le savoir en regardant simplement le graphe.


Dimensionner les liens fonctionne exactement de la même manière que dimensionner les noeuds.

Par défaut, tous les liens ont la même taille. Il est possible cependant de dimensionner la taille des liens selon une certaine propriété. Il sera alors possible d'apprécier la valeur de cette propriété selon la taille du lien.

Cette technique s'applique seulement à des propriétés qualitatives.

Dimensionner les liens fonctionne de la même manière que la fonctionnalité Colorer un lien de Linkurious Enterprise. Les options Colorer et Dimensionner peuvent êtres combinées pour obtenir des visualisations plus pertinentes. 

![](https://github.com/Linkurious/linkurious-enterprise-manual/raw/master/en/style/ProceZoom.png)

Dans la figure ci-dessous, nous pouvons voir la compagnie Instagram et différentes compagnies ayant investi dans Instagram. 

Si nous zoomons sur la relation entre Instagram et Sequoia Capital, nous pouvons voir la propriété ```raised_amount_usd``` avec la valeur ```55 000 000```.

Nous allons dimensionner la taille des différentes compagnies en fonction de leur propriété ```raised amount``` afin de savoir rapidement qui a investi le plus d'argent dans Instagram.

Nous cloquons sur l'onglet en haut à droite pour ouvrir le designpanel et choisissons l'onglet Edges.

Nous déplaçons la souris sur ```raised_amount```. En plus de pouvoir colorer les liens selon cette propriété, il est également possible de les dimensionner. Linkurious Enterprise peut faire ça pour toutes les propriétés ayant des valeurs numériques.

Nous allons sélectionner l'icône taille (```Size```).

Un nouveau menu apparaît. Il rend possible de paramétrer 

A new menu appears. It makes it possible to set the ```Min/max size difference```, the difference in size between the node with the lowest value and the node with the highest value.

If we want to view the difference in ```raised amount``` we are going to set the ```Min/max size difference``` to ```2```.

![](TailleEdges.png)

Now we can see that few outliers appear thicker than the other edges.


