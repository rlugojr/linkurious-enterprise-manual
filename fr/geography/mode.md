# Déployer un map géographique

Le bouton permettant de passer en mode géo est disponible dans le panneau de gauche de l'espace de travail.
Nous pouvons activer ou désactiver le mode afin de passer de la vue standard a la vue géographique. 


![](geo-mode-button.png)

Cliquer sur le bouton pour déployer le map géographique. Les noeuds sont positionnés sur le map selon leur coordonnées géographiques. Les autres noeuds sont cachés grâce au filtre "coordonnées géographiques".

![](geo-mode-enabled.png)

Nous pouvons zoomer et dezoomer, déplacer les noeuds sur le map afin d'améliorer la lisibilité, sélectionner des noeuds et des liens, etc. Il est toujours possible de repositionner les noeuds à leur location d'origine via le menu d'actions:

![](reset-geo-coordinates.png)

Hover the layer icon ![](layer-icon.png) on the bottom-right of the Workspace with your mouse. The list of available layers is displayed. We can pick another basemap and add overlays, depending on those available on your instance of Linkurious as seen below using the [Mapbox](https://www.mapbox.com/) provider:

![](geo-mode-alt.png)

Finally, we can publish an interactive widget from **Workspace menu > Publish** with the geographical layers. See the **Manage > Publish** chapter to know more.

![](geo-widget.png)
