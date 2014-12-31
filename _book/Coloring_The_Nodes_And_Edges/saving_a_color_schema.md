# Saving A Color Scheme

In the current beta version of Linkurious Enterprise, it is not possible within the interface to map specific colors to specific property values.

You can do it though by editing the file ```production.js``` in ```nameofyourlinkuriousfolder/linkurious/config```.

At the end of the file, you should see :

```
palette: {
    nodes: {
      qualitative: {
        linkurious_def: {
          // generated with http://tools.medialab.sciences-po.fr/iwanthue/
          12: ['#701E30','#00D745','#FA5AE3','#EB9104','#25623B','#3C4382','#E885A2','#9391ED','#2F9539','#C9B528','#8B2E0B','#7BA273'],
          20: ['#D094FD','#41D321','#F0712F','#1D4427','#1EC0F2','#A52851','#B6AE4F','#EFA6B8','#E231CA','#54368D','#64290F','#1F7216','#D3920B','#85B719','#486AAE','#8357DB','#FC7591','#2AA7B3','#A7AAF9','#0B8807'],
          40: ['#DD45F5','#317999','#FC4B1E','#AE3D6A','#5DC187','#3961DA','#F0946C','#36A82C','#28A4FC','#D292FE','#CE8212','#4C7126','#AC3924','#865F91','#EE4CC5','#158074','#735E0B','#7B45A4','#456AAF','#F385B1','#BC6E72','#A83186','#0EB4AB','#72C766','#9EC47C','#8E9FE7','#F67033','#F80BDD','#649D73','#A9323E','#687386','#974C2A','#CE2E22','#CAB439','#C147DA','#547506','#BDB30E','#2EA67D','#E98E2F','#98A00E']
        }
      },
      sequential: {
        //colorbrewer.YlGnBu
        7: ['#ffffcc','#c7e9b4','#7fcdbb','#41b6c4','#1d91c0','#225ea8','#0c2c84']
      }
    },
    edges: {
      qualitative: {
        linkurious_def: {
          // generated with http://tools.medialab.sciences-po.fr/iwanthue/
          12: ['#701E30','#00D745','#FA5AE3','#EB9104','#25623B','#3C4382','#E885A2','#9391ED','#2F9539','#C9B528','#8B2E0B','#7BA273'],
          20: ['#D094FD','#41D321','#F0712F','#1D4427','#1EC0F2','#A52851','#B6AE4F','#EFA6B8','#E231CA','#54368D','#64290F','#1F7216','#D3920B','#85B719','#486AAE','#8357DB','#FC7591','#2AA7B3','#A7AAF9','#0B8807'],
          40: ['#DD45F5','#317999','#FC4B1E','#AE3D6A','#5DC187','#3961DA','#F0946C','#36A82C','#28A4FC','#D292FE','#CE8212','#4C7126','#AC3924','#865F91','#EE4CC5','#158074','#735E0B','#7B45A4','#456AAF','#F385B1','#BC6E72','#A83186','#0EB4AB','#72C766','#9EC47C','#8E9FE7','#F67033','#F80BDD','#649D73','#A9323E','#687386','#974C2A','#CE2E22','#CAB439','#C147DA','#547506','#BDB30E','#2EA67D','#E98E2F','#98A00E']
        }
      },
      sequential: {
        //colorbrewer.YlGnBu
        7: ['#ffffcc','#c7e9b4','#7fcdbb','#41b6c4','#1d91c0','#225ea8','#0c2c84']
      }
    }
  }
};```

You can edit it to attribute specific colors to the nodes according to specific properties.

The example below shows how to do it for a graph where there is a property called ```__type__``` that has two values : ```org.neo4j.cineasts.domain.Person``` or ```org.neo4j.cineasts.domain.Movie```.

```
styles: {
    nodes: {
      //TODO smart truncate of the label
      color: {
        by: 'data.data.__type__',
        scheme: 'qualitative.__type__'
      }
    },
    edges: {}
  },
  palette: {
    qualitative: {
      '__type__': { //colorbrewer.Set1.8
        'org.neo4j.cineasts.domain.Person': '#e41a1c',
        'org.neo4j.cineasts.domain.Movie': '#377eb8'
      }
    },
    //colorbrewer.YlGnBu
    sequential: ['#ffffcc','#c7e9b4','#7fcdbb','#41b6c4','#1d91c0','#225ea8','#0c2c84']
  }
};```


# Changing the Color Palette
