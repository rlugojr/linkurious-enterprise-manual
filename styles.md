### Visualization style

You can customize the default visual aspect of nodes and edges in new visualizations, so that your users will jump head first into the exploration of data. Nodes and edges are grey and have the same size by default, but we can define rules that will apply to all data sources.

Visualization style is defined within the `sigma` key by the `styles` and color `palette`. Styles are mapping between visual variables such as colors or size, and data properties on nodes and edges.

Palettes may contain color schemes for both quantitative and qualitative properties, as well as schemes for icons. Schemes for qualitative properties bind property values to colors. Schemes for quantitative properties bind the number of property values to lists of sequential colors. Schemes may be nested and be referenced in dot notation by the styles.

Available `styles.nodes.by` values:
- "data.categories"
- "data.properties"

Available `styles.edges.by` values:
- "data.type"
- "data.properties"

The following example set colors and icons to node categories COMPANY, CITY, MARKET, INVESTOR, and edge types HAS_CITY, HAS_MARKED, INVESTED_IN.

**Example;**
```json
"styles": {
  "nodes": {
    "color": {
      "by": "data.categories",
      "scheme": "nodes.qualitative.my_scheme"
    },
    "icon": {
      "by": "data.categories",
      "scheme": "nodes.icons.my_scheme"
    }
  },
  "edges": {
    "color": {
      "by": "data.type",
      "scheme": "edges.qualitative.my_scheme"
    }
  }
},

"palette": {
  "nodes": {
    "qualitative": {
      "my_scheme": {
        "INVESTOR": "#5FDAA2",
        "COMPANY": "#DE6FBC",
        "MARKET": "#4EA4D4",
        "CITY": "#D4742C"
      }
    },
    "icons": {
      "my_scheme": {
        "INVESTOR": {"font": "FontAwesome", "scale": 1, "color": "#fff", "content": "\uf19c"},
        "CITY": {"font": "FontAwesome", "scale": 1, "color": "#fff", "content": "\uf015"},
        "COMPANY": {"font": "FontAwesome", "scale": 1, "color": "#fff", "content": "\uf135"},
        "MARKET": {"font": "FontAwesome", "scale": 1, "color": "#fff", "content": "\uf219"}
      }
    }
  },

  "edges": {
    "qualitative": {
      "my_scheme": {
        "INVESTED_IN": "#5FDAA2",
        "HAS_CITY": "#DE6FBC",
        "HAS_MARKET": "#4EA4D4"
      }
    }
  }
}
```

Notice the codes for icons such has "\uf219"; they are unicode characters in the font FontAwesome, which contain more than 500 icons available in Linkurious. Get the complete character map at http://fortawesome.github.io/Font-Awesome/icons/ (select an icon to display the unicode).

#### Color mapping



#### Color palette

Linkurious will always use 7 colors for quantitative properties of the nodes.

TODO color generation