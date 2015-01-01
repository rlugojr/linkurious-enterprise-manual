# Coloring The Edges According To A Property

We have seen how to color the nodes according to the property of your choice. Coloring the edges works exactly the same.

By default the relationships are not colored.

![the criteo relationships](https://dl.dropboxusercontent.com/s/ituxoqm9kkyf6fh/40.png?dl=0)

If we want to be able to quickly distinguish betwene the different relationships in our dataset, colors can be helpful.

In order to color the edges according to a property of your choice, open the design panel.

![the design panel](https://dl.dropboxusercontent.com/s/rcjf06pghdub3kc/41.png?dl=0)

By default we can see the properties of the nodes. Select the ```Relationships``` tab.

![relationships tab](https://dl.dropboxusercontent.com/s/rse0rz97itwtlck/42.png?dl=0)

Now we can view the different properties associated with the edges.

![opened relationships tab](https://dl.dropboxusercontent.com/s/iz6jcaav9k87thk/43.png?dl=0)

We simply have to select the property we want to focus on. Here we want to distinguish the different types of relationships. Thus, we are going to select the ```type``` property.

It is as simple as going over ```type``` and selecting ```Colors```.

![selecting types](https://dl.dropboxusercontent.com/s/n2jy9vh73faxg2j/44.png?dl=0)

Immediately the edges in your visualization are colored according to their ```type```. In the design panel, we can see :
* the different values associated with the ```type``` property (HAS_ACQUIRED and HAS_INVESTED_IN);
* how many occurences of each value there is (there are 5 relationships with the value ```HAS_INVESTED_IN```);
* which color is associated to which value (```HAS_INVESTED_IN``` is blue).
