# Coloring The Edges According To A Property

We have seen how to color the nodes according to the property of your choice. Coloring the edges works exactly the same.

By default the relationships are not colored.

![the criteo relationships](https://github.com/Linkurious/linkurious-enterprise-manual/blob/master/screenshots/40.png)

If we want to be able to quickly distinguish betwene the different relationships in our dataset, colors can be helpful.

In order to color the edges according to a property of your choice, open the design panel.

![the design panel](https://github.com/Linkurious/linkurious-enterprise-manual/blob/master/screenshots/41.png)

By default we can see the properties of the nodes. Select the ```Relationships``` tab.

![relationships tab](https://github.com/Linkurious/linkurious-enterprise-manual/blob/master/screenshots/42.png)

Now we can view the different properties associated with the edges.

![opened relationships tab](https://github.com/Linkurious/linkurious-enterprise-manual/blob/master/screenshots/43.png)

We simply have to select the property we want to focus on. Here we want to distinguish the different types of relationships. Thus, we are going to select the ```type``` property.

It is as simple as going over ```type``` and selecting ```Colors```.

![selecting types](https://github.com/Linkurious/linkurious-enterprise-manual/blob/master/screenshots/44.png)

Immediately the edges in your visualization are colored according to their ```type```. In the design panel, we can see :
* the different values associated with the ```type``` property (HAS_ACQUIRED and HAS_INVESTED_IN);
* how many occurences of each value there is (there are 5 relationships with the value ```HAS_INVESTED_IN```);
* which color is associated to which value (```HAS_INVESTED_IN``` is blue).
