## Colorer les noeuds en fonction d'une propriété

Si tous les noeuds ou liens ont la même couleur, il est difficile de distinguer des différences entre eux sans se pencher sur leurs propriétés individuelles. Une manière simple de contourner ce problème est de choisir de colorer les noeuds selon une propriété particulière.

Par exemple, nos noeuds peuvent avoir une propriété ```country``` que nous souhaiterions mettre en avant. Linkurious Enterprise nous permet donc de colorer les noeuds selon une certaine propriété, ici la propriété ```country```.

De cette manière, une start-up française et une start-up allemande auront deux couleurs différentes. Il sera alors plus simple de les distinguer.

Dans l'image ce-dessous, nous pouvons voir que la start-up Twitter est connectée à de nombreux investisseurs . A première vue, nous n'avons aucune idée d'où viennent ces investisseurs.

![](https://github.com/Linkurious/linkurious-enterprise-manual/raw/master/en/style/SinColor.png)


Premièrement, ouvrons le design panel dans le coin à droite de l'écran et sélectionnons l'onglet ```Design```. Nous pouvons alors voir toutes les propriétés des noeuds. Nous cliquons sur ```color```à côté d'une propriété pour colorer les noeuds selon cette propriété. 

![](https://github.com/Linkurious/linkurious-enterprise-manual/raw/master/en/style/Colors.png)

Nous pouvons voir:
* les différentes valeurs associées à la propriété ```country``` (JPN, RUS, USA);
* le nombre d'occurence de chacune des valeurs (il y a 20 noeuds ayant la valeur ```USA```);
* quelle couleur est associée à quelle valeur (```USA``` est en vert)

Notez que les noeuds n'ayant pas la propriété ```country``` restent en gris. 

Pour colorer les noeuds selon une autre propriété, nous devons d'abord désactiver les couleurs pour la propriété Country en cliquant à nouveau sur le bouton ```color``` :

![](https://github.com/Linkurious/linkurious-enterprise-manual/raw/master/en/style/Unset.png)

Puis nous cliquons sur le bouton ```color``` d'une autre propriété. 
