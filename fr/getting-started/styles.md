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

Dans l'exemple suivant, les noeuds sont colorés selon la catégorie  "COMPANY", "CITY", "MARKET", "INVESTOR", et les liens selon le type  "HAS_CITY", "HAS_MARKED", "INVESTED_IN". Notez comment chaque palette est référencé par des formules (scheme) how each color palettes is referenced in schemes.

**Example for qualitative properties:**
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

Coloring by quantitative property follows the same logic. In the following example the nodes are colored by a numeric property. Values will be linearly grouped into 7 bins, ordered from small to large values (see an example below).

![color-scale](Color-scale.png)

**Example for quantitative properties:**
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

#### Color palette

Linkurious will always use 7 colors for quantitative properties of the nodes, and 3 colors only for edges. The human eye can distinguish a few colors only, so you should craft your palette carefully.

If you do not set styles for qualitative properties, Linkurious will assign colors from a randomly -but carefully- generated set of colors. This set can be modified at `palette.nodes.qualitative.linkurious_def` (edges respectively).

Be careful to never delete `linkurious_def` or `sequential` because they are used by Linkurious.

We recommend to pick colors from the [ColorBrewer palette](https://github.com/Linkurious/linkurious.js/blob/develop/plugins/sigma.plugins.colorbrewer/sigma.plugins.colorbrewer.js), which provides highly distinctive sets of colors (see below).

![color-brewer](Color-brewer.png)

You can also generate consistent color scales for qualitative data on http://gka.github.io/palettes/ .

#### Node icons

Linkurious provides more than 500 icons from the FontAwesome project. You can assign icons using their unicode characters such has "\uf219". Get the complete character map at http://fortawesome.github.io/Font-Awesome/icons/ (select an icon to display the unicode).

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
