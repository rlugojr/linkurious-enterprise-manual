## Dimensionner les noeuds selon une propriété

Par défaut, tous les noeuds ont la même taille. Il est possible cependant de dimensionner la taille des noeuds selon une certaine propriété. Il sera alors possible d'apprécier la valeur de cette propriété selon la taille du noeud.

Cette technique s'applique seulement à des propriétés quantitatives.

Dimensionner les noeuds fonctionne de la même manière que la fonctionnalité Colorer un noeud de Linkurious Enterprise. Les options Colorer et Dimensionner peuvent êtres combinées pour obtenir des visualisations plus pertinentes. 

Par exemple [Andreessen Horowitz](http://a16z.com/) est une entreprise leader avec 127 relations à différentes compagnies qu'elle a financé. Quelles compagnies ont reçues les fonds les plus importants? Il est difficile de le savoir en regardant simplement le graphe.

![](https://github.com/Linkurious/linkurious-enterprise-manual/raw/master/en/style/A.png)

Nous allons dimensionner les différentes compagnies selon leur propriété ```funding_total``` afin de savoir qui a le plus de succès. 

Nous cliquons dans le coin en haut à droite de l'écran pour ouvrir le design panel.


Nous déplaçons la souris sur ```funding_total```. En plus de pouvoir colorer les noeuds selon cette propriété, il est également possible de les dimensionner. Linkurious Enterprise peut faire ça pour toutes les propriétés ayant des valeurs numériques.

Nous allons sélectionner l'icône taille (```Size```).

![](https://github.com/Linkurious/linkurious-enterprise-manual/raw/master/en/style/B.png)


Un nouveau menu apparaît. Il permet de paramètrer la ```différence de taille min/max```(différence de taille entre le noeud ayant la plus petite valeur et le noeud ayant la plus grande valeur).

Si nous voulons voir la différence en ```funding_total``` nous paramétrons la  ```différence de taille min/max```à 12.

![](https://github.com/Linkurious/linkurious-enterprise-manual/raw/master/en/style/C.png)

Maintenant nous pouvons voir que certains noeuds apparaissent plus grands que d'autres.

Les noeuds les plus grands représentent les compagnies AirBnB, Box, Pinterest ou Zyga. Nous pouvons rapidement les identifier comme les meilleurs investissements de Andreessen Horowitz. 