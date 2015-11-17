## Sizing the edges according to a property

Sizing the edges works exactly the same.

By default all the edges have the same size. It is possible though to choose to map the size of edges to certain properties. This way it will be possible to visualize that property.

![criteo](https://dl.dropboxusercontent.com/s/3vluq781j7yfw5d/46.png?dl=0)

In the picture above we see a start-up called [Criteo](http://www.criteo.com/). It is linked to four companies that has invested in it (IDInvest Partners, Softbank Capital, Index Ventures, Elaia Partners and Bessemer Venture Partners) and to a company it bought (AdQuantic).

If we zoom in on the relationship between Criteo and IDInvest Partners, we can see it has a ```raised_amount_usd``` property with the value ```6600000```.

![criteo and idinvest](https://dl.dropboxusercontent.com/s/85ugjya4kspvn6v/47.png?dl=0)

We can choose to size all the relationships in our visualization according to the ```raised_amount_usd``` property to quickly glimpse who invested the most money in Criteo.

In order to do that, we open the design panel on the right. Choose the ```Relationships``` tab.

![relationship tab](https://dl.dropboxusercontent.com/s/70c3duwrf5gkn1o/48.png?dl=0)

Now all the properties associated with the relationships in our graph are visible.

![relationship tab](https://dl.dropboxusercontent.com/s/el645at9kktrus4/49.png?dl=0)

We are going to scroll to go to ```raised_amount_usd```, the property we are interested in. We can use it to color the relationships but, because that property has numercial values, we can also use it to **size** the relationships.

![raised_amount_usd](https://dl.dropboxusercontent.com/s/3vsyxeee7jv4aiw/50.png?dl=0)

Simply click on ```Size```. A new menu appears. It makes it possible to set the ```Min/max size difference```, the difference in size between the relationship with the lowest value and the relationship with the highest value.

![the difference](https://dl.dropboxusercontent.com/s/8xerdpa26qktjos/51.png?dl=0)

If we want to view the difference in ```funding_total_usd``` we are going to set the ```Min/max size difference``` to ```3```.

![setting the size difference](https://dl.dropboxusercontent.com/s/m3z7hv2pgv1myue/52.png?dl=0)

Now we can see that SoftBank Capital appears to have contributed the most to the funding of Criteo because the relationship between these two companies is the largest.
