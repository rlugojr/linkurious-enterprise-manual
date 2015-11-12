## Coloring the edges according to a property

Coloring the edges works exactly the same that coloring nodes like presented previously.


By default the edges are not colored.

![the criteo edges](https://dl.dropboxusercontent.com/s/ituxoqm9kkyf6fh/40.png?dl=0)

If we want to be able to quickly distinguish between the different edges in our dataset, colors can be helpful.

In order to color the edges according to a property of our choice, we open the design panel.

![the design panel](https://dl.dropboxusercontent.com/s/rcjf06pghdub3kc/41.png?dl=0)

By default we can see the properties of the nodes. We elect the ```edges``` tab.

![edges tab](https://dl.dropboxusercontent.com/s/rse0rz97itwtlck/42.png?dl=0)

Now we can view the different properties associated with the edges.

![opened edges tab](https://dl.dropboxusercontent.com/s/iz6jcaav9k87thk/43.png?dl=0)

We simply have to select the property we want to focus on. Here we want to distinguish the different types of edges. Thus, we are going to select the ```type``` property.

It is as simple as going over ```type``` and selecting ```Colors```.

![selecting types](https://dl.dropboxusercontent.com/s/n2jy9vh73faxg2j/44.png?dl=0)

Immediately the edges in our visualization are colored according to their ```type```.

![the colors are applied](https://dl.dropboxusercontent.com/s/isb4ghghxw4fvbr/45.png?dl=0)

In the design panel, we can see :
* the different values associated with the ```type``` property (HAS_ACQUIRED and HAS_INVESTED_IN);
* how many occurences of each value there is (there are 5 edges with the value ```HAS_INVESTED_IN```);
* which color is associated to which value (```HAS_INVESTED_IN``` is blue).
