## Placements

### Commandes de visualisation

Dans l'espace de travail, plusieurs commandes sont disponibles sur le boutton en bas à droite de l'écran; 

![](https://github.com/Linkurious/linkurious-enterprise-manual/raw/master/en/manipulate/Menu.png)


- Le bouton ```shortcuts``` : ![](https://github.com/Linkurious/linkurious-enterprise-manual/raw/master/en/manipulate/Shortcuts.png), donne accès à la liste des raccourcis existants pour explorer et interagir avec le graphe. 
- Le bouton ```Locate```: ![](https://github.com/Linkurious/linkurious-enterprise-manual/raw/master/en/manipulate/Locate.png) centre le graphe sur l'écran
- Le bouton ```Zoom In/Zoom Out``` ![](https://github.com/Linkurious/linkurious-enterprise-manual/raw/master/en/manipulate/ZoomIO.png)  permet de zoomer ou dézoomer sur le graphe
- Le bouton ```Layout``` nous donne plusieurs options d'organisation du graphe 
- 
Un clic sur le bouton ```layout``` appliquera un agencement spécifique, qui, par défaut, est un agencement ```fast force-directed```. Deux catégories d'agencements sont disponibles: dirigés par force ou hiérarchique. Il viennent avec des formes prédéfinies


![](https://github.com/Linkurious/linkurious-enterprise-manual/raw/master/en/manipulate/FastLayout.png)

### Placements basé sur les forces 

Ces arrangements disposent les noeuds selon leurs connections: des noeuds connectés sont habituellement près les uns des autres alors que des noeuds non connectés seront plus éloignés.


**Best Mode:**
prend un temps plus long pour calculer la nouvelle position des noeuds mais offre de meilleurs résultats que le **fast mode** 

![](https://github.com/Linkurious/linkurious-enterprise-manual/raw/master/en/manipulate/FM.png)


**Fast Mode (par défaut):**
trouve rapidement la nouvelle les position des noeuds mais des superpositions peuvent exister

**Random Mode:**
Les noeuds sont placés aléatoirement avant de recalculer leur positions.

### Hierarchical layout

Ce algorithme place automatiquement les noeuds en différentes couches en alignant les noeuds de chaque couche soit verticalement soit horizontalement. Les noeuds racine sont déterminés automatiquement. 

**Top to bottom Mode:**
positionnera les noeuds racine en haut de l'écran

![](https://github.com/Linkurious/linkurious-enterprise-manual/raw/master/en/manipulate/TtB.png)

**Left to Right Mode:**
positionnera les noeuds racine sur le côté gauche de l'écran

![](https://github.com/Linkurious/linkurious-enterprise-manual/raw/master/en/manipulate/LtR.png)


**Bottom to top Mode:**
positionnera les noeuds racine en bas de l'écran

**Right to left Mode:**
positionnera les noeuds racine sur le côté droit de l'écran