### Style des visualisations

Vous pouvez configurer l'installation de Linkurious Enterprise pour personnaliser par défaut l'aspect visuel des noeuds et liens des nouvelles visualisations, ainsi les utilisateurs peuvent directement explorer les données. Par défaut, les noeuds et les liens sont gris et ont la même taille. Le style défini sera appliqué à **toutes** les sources de données sources.

Ouvrez le fichier de configuration `linkurious/data/config/production.json`. Les styles de visualisation sont définis dans la clé `sigma` par  `styles` et  `palette` de couleurs. Les styles sont définis par des variables visuelles comme les couleus ou la taille et les propriétés des données des noeuds et liens. Un seul type de variable visuelle peut être utilisé à la fois. Par exemple, nous pouvons paramètrer `nodes.color` et `nodes.icons`, mais nous ne pouvons pas paramètrer deux fois  `nodes.color`. Nous pouvons paramètrer `nodes.color` et `edges.color`.

Les palettes peuvent contenir des couleurs pour des propriétés qualitatives et quantitatives, ainsi que des modèles pour les icônes. Dans le cas des propriétés qualitatives, une valeur de propriété est associée à une couleur. Dans le cas de propriétés quantitatives, les valeurs numériques d'une propriété sont associées à une séquence de couleurs.   may contain color schemes for both quantitative and qualitative properties, as well as schemes for icons. Schemes for qualitative properties bind property values to colors. Schemes for quantitative properties bind the number of property values to lists of sequential colors. Ces schémas peuvent être imbriqués et référencés à l'aide d'une notation par point par les styles. 

Valeurs disponibles `styles.nodes.by` :
- "data.categories"
- "data.properties.X", with "X" the property name.

Valeurs disponibles `styles.edges.by` :
- "data.type"
- "data.properties.X", with "X" the property name.

#### Attribution des couleurs 

Dans l'exemple suivant, les noeuds sont colorés selon la catégorie  "COMPANY", "CITY", "MARKET", "INVESTOR", et les liens selon le type  "HAS_CITY", "HAS_MARKED", "INVESTED_IN". Notez comment chaque palette est référencé par des formules (scheme).

**Exemple pour des propriétés qualitatives:**
```json
"styles": {
  "nodes": {
    "color": {
      "by": "data.categories",
      "scheme": "nodes.qualitative.categories"
    }
  },
  "edges": {
    "color": {
      "by": "data.type",
      "scheme": "edges.qualitative.type"
    }
  }
},
"palette": {
  "nodes": {
    "qualitative": {
      "categories": {
        "INVESTOR": "#5FDAA2",
        "COMPANY": "#DE6FBC",
        "MARKET": "#4EA4D4",
        "CITY": "#D4742C"
      }
    }
  },
  "edges": {
    "qualitative": {
      "type": {
        "INVESTED_IN": "#5FDAA2",
        "HAS_CITY": "#DE6FBC",
        "HAS_MARKET": "#4EA4D4"
      }
    }
  }
}
```

Colorer selon des propriétés quantitatives suit la même logique. Dans l'exemple suivant, les noeuds sont colorés selon une propriété numérique. Les valeurs peuvent être groupés en 7 compartiments, ordonnés des plus petites aux plus larges valeurs. 

![Echelle de couleur](Color-scale.png)

**Exemple pour des propriétés quantitatives :**
```json
"styles": {
  "nodes": {
    "color": {
      "by": "data.properties.my_score",
      "scheme": "nodes.quantitative"
    }
  }
},
"palette": {
  "nodes": {
    "quantitative": {
      7: ['#161344','#3f1c4c','#632654','#86315b','#a93c63','#cd476a','#f35371']
    }
  }
}
```

#### Palette de couleurs

Linkurious utilisera toujours 7 couleurs pour despropriétés quantitatives des noeuds et 3 pour celles des liens. L'oeil humain peut seulement distinguer quelques couleurs donc soyez vigilants lorsque vous définissez votre palette.  

Si vous ne paramètrez pas de styles pour les propriétés quantitatives, Linkurious assignera de manière aléatoire-mais avec soin- un set de couleurs. Ce set peut être modifiè à  `palette.nodes.qualitative.linkurious_def` (de même pour les liens).

Soyez vigilants à ne jamais supprimer `linkurious_def` ou `sequential` car ils sont utilisés par Linkurious.

Nous recommandons de choisir des couleurs de  [la palette ColorBrewer ](https://github.com/Linkurious/linkurious.js/blob/develop/plugins/sigma.plugins.colorbrewer/sigma.plugins.colorbrewer.js), qui fournit des sets de couleurs bien distinctes (voir ci dessous) 

![color-brewer](Color-brewer.png)

Vous pouvez également créer une échelle de couleur pertinente pour des données qualitative à l'adresse   http://gka.github.io/palettes/ .

#### Icônes des noeuds

Linkurious fournit plus de  500 icônes issus du projet FontAwesome. Vous pouvez attribuer des icônes en utilisant leur unicode tel que "\uf219". L'e the complete character map at http://fortawesome.github.io/Font-Awesome/icons/ (select an icon to display the unicode).

The following example set icons to node categories "COMPANY", "CITY", "MARKET", "INVESTOR".

**Example;**
```json
"styles": {
  "nodes": {
    "icon": {
      "by": "data.categories",
      "scheme": "nodes.icons.categories"
    }
  }
},
"palette": {
  "nodes": {
    "icons": {
      "categories": {
        "INVESTOR": {"font": "FontAwesome", "scale": 1, "color": "#fff", "content": "\uf19c"},
        "CITY": {"font": "FontAwesome", "scale": 1, "color": "#fff", "content": "\uf015"},
        "COMPANY": {"font": "FontAwesome", "scale": 1, "color": "#fff", "content": "\uf135"},
        "MARKET": {"font": "FontAwesome", "scale": 1, "color": "#fff", "content": "\uf219"}
      }
    }
  }
}
```

#### Node images

*This feature is experimental and not yet available from the user interface.*

Nodes can be filled with an image if one of their property is an URL to an image. Available image formats are PNG, JPG, GIF, or TIFF. The following example set images to node categories "COMPANY", "CITY", "MARKET".


**Example;**
```json
"styles": {
  "nodes": {
    "image": {
      "by": "data.categories",
      "scheme": "nodes.images"
    }
  }
},
"palette": {
  "nodes": {
    "images": {
      'COMPANY': {
        url: 'http://example.com/img/company.png', scale: 1.3, clip: 0.85
      },
      'CITY': {
        url: 'http://example.com/img/city.png', scale: 1.3, clip: 0.85
      },
      'MARKET': {
        url: 'http://example.com/img/market.png', scale: 1.3, clip: 0.85
      }
    }
  }
}
```
