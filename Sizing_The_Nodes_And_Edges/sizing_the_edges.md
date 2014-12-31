# Sizing The Edges According To A Property

We have seen how to size the nodes according to the property of your choice. Sizing the edges works exactly the same.

By default the relationships all have the same size. Using the size can be helpful to visualize a numerical value associated to the edges in your graph.

![criteo](https://github.com/Linkurious/linkurious-enterprise-manual/blob/master/screenshots/46.png)

In the picture aboce we see a start-up called [Criteo](http://www.criteo.com/). It is linked to four companies that has invested in it (IDInvest Partners, Softbank Capital, Index Ventures, Elaia Partners and Bessemer Venture Partners) and to a company it bought (AdQuantic).

If we zoom in on the relationship between Criteo and IDInvest Partners, we can see it has a ```raised_amount_usd``` property with the value ```6600000```.

![criteo and idinvest](https://github.com/Linkurious/linkurious-enterprise-manual/blob/master/screenshots/47.png)

We can choose to size all the edges in our visualization according to the ```raised_amount_usd``` property to quickly glimpse who invested the most money in Criteo.

In order to do that, open up the design panel on the right. Choose the ```Relationships``` tab.

![relationship tab](https://github.com/Linkurious/linkurious-enterprise-manual/blob/master/screenshots/48.png)

Now all the properties associated with the edges in your graph are visible.

![relationship tab](https://github.com/Linkurious/linkurious-enterprise-manual/blob/master/screenshots/49.png)

We are going to scroll to go to ```raised_amount_usd```, the property we are interested in. We can use it to color the edges but, because that property has numercial values, we can also use it to **size** the edges.

![raised_amount_usd](https://github.com/Linkurious/linkurious-enterprise-manual/blob/master/screenshots/50.png)

Simply click on ```Size```. A new menu appears. It makes it possible to set the ```Min/max size difference```, the difference in size between the node with the lowest value and the node with the highest value.

![the difference](https://github.com/Linkurious/linkurious-enterprise-manual/blob/master/screenshots/51.png)

If we want to view the difference in ```funding_total_usd``` we are going to set the ```Min/max size difference``` to ```3```.

![setting the size difference](https://github.com/Linkurious/linkurious-enterprise-manual/blob/master/screenshots/52.png)

Now we can see that SoftBank Capital appears to have contributed the most to the funding of Criteo because the edge between these two companies is the largest.
