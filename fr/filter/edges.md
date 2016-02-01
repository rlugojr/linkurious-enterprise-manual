## Filtrer des relations selon une propriété

Nous avons vu qu'il est possible d'utiliser des filtres pour sélectionner ou supprimer des noeuds spécifiques dans notre visualisation selon une propriété. Il est possible de faire la même chose avec les relations.

![](https://github.com/Linkurious/linkurious-enterprise-manual/raw/master/en/filter/Example.png)

Dans le graphe ci-dessous, nous voyons les connections de Grabit. Chaque relation représente un investissement dans une start-up mais quel type d'investissement?

Nous pouvons ouvrir le design panel pour investiguer ce point. Sélectionnons ```Edges``` dans le coin en bas à droite.

Nous pouvons voir les différentes propriétés rattachées aux relations de notre set de données.

Nous allons nous concentrer sur la propriété ```funded_at```. Cliquons dessus.

![](https://github.com/Linkurious/linkurious-enterprise-manual/raw/master/en/filter/FundedAt.png)

Nous voulons seulement voir le funded_at avec le code ```03/06/2014```. Cochons la case pour seulement garder  ```03/06/2014``` et cliquons sur ```Filter ```.

![](https://github.com/Linkurious/linkurious-enterprise-manual/raw/master/en/filter/Final.png)

Les relations avec  ```03/06/2014``` et ```funded_at``` sont affichées. Les autres valeurs ```funded_at``` sont supprimées de la visualisation et le symbole du filtre ajouté apparait en bas de l'écran.


