## Recherche avancée

Vous êtes à la recherche d'un noeud ou d'une relation spécifique et la barre de recherche vous donne trop de résultats? Le texte que vous recherchez est trop commun! Vous souhaiteriez peut-être affiner votre recherche en cherchant à l'aide de plusieurs propriétés?

Si l'on recherche une Startup qui a le texte ```facebook``` dans une de ses propriétésn, nous obtenons 88 résultats. Essayons d'affiner notre recherche.

![](https://github.com/Linkurious/linkurious-enterprise-manual/raw/master/en/search/Facebook_Example.png)


Nous cliquons sur l'icône ```Advanced```, un nouveau menu apparaît: 

![](https://github.com/Linkurious/linkurious-enterprise-manual/raw/master/en/search/Advanced Search.png)

Nous pouvons voir le nom de différentes catégories (city, company, investor and market) dans notre base de données et nos occurences.

Nous cliquons sur ```Options``` pour voir le nom des différentes propriétés de notre graphe.

Dans notre graphe, Facebook est catégorisé comme une ```Compagnie```. Nous allons sélectionner ```Company``` pour restreindre notre recherche aux noeuds de compagnies. 

Nous pouvons voir les différents résultats.


![the company label](https://dl.dropboxusercontent.com/s/wtkhoy7drk1y7ri/72.png?dl=0)

Dans notre graphe, une ```Compagnie``` peut avoir des proprités telles que ```category ```,  ```country```, ```first_funding_at ``` or ```founded_at``` et plus encore. Tous les noeuds catégorisés comme Compagnie ne vont cependant pas avoir toutes ces propriétés. 

Afin d'affiner nos résultats de recherche, nous allons rechercher plusieurs propriétés à la fois. Pour trouver Facebook, nous allons rechercher une compagnie qui utilise Facebook comme url de site internet.

[](https://github.com/Linkurious/linkurious-enterprise-manual/raw/master/en/search/MProperties.png)

Maintenant si nous tapons ``facebook``, les résultats seront filtrés de manière à n'afficher que les noeuds ayant pour catégorie ```Company``` et la valeur ``facebook.com`` pour la propriété ```homepage_url```.


Nous pouvons voir les résultats filtrés et choisir celui qui nous intéresse.

La même approche peut-être utilisé pour la recherche de relations.


> Linkurious Enterprise recherchera une correspondance **exacte** pour la valeur que vous entrez dans le menu d'options de recherche. 
