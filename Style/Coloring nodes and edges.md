## Coloring the nodes according to a property

If your nodes or edges all have the same color, it is difficult to distinguish differences between them without looking up their properties individually. A great way to circumvent that issue is to choose to color the nodes according to a certain property.

For example, our nodes may have a ```country``` property. Maybe we need to consider that property when we look at our graph. Linkurious Enterprise enables you to color the nodes according to their ```country``` value. This way, a French and a German start-up will have different colors. It will be easy to distinguish them visually.

In the picture below, we see the start-ups and investors Twitter is connected to. At first glance we have no idea where they are coming from.

![the twitter network](https://dl.dropboxusercontent.com/s/dax3g40yu1sansd/29.png?dl=0)

First of all, let's open the design panel on the right side of the screen. To do this we hit the ```+``` sign.

![open design panel](https://dl.dropboxusercontent.com/s/ic4usvd9feckvl2/30.png?dl=0)

The design panel opens up.

We select the property we want to color the nodes according to. Here we want to use the ```country``` property. We click on the color symbol on the right.

![select country to color](https://dl.dropboxusercontent.com/s/u4b5i7t6nbe5mgo/32.png?dl=0)

Immediately the nodes in our visualization are colored according to their countries.

![the colors are applied](https://dl.dropboxusercontent.com/s/rztgatl6cr663fy/33.png?dl=0)

In the design panel, we can see :
* the different values associated with the ```country``` property (CAN, GBR, JPN, RUS, USA);
* how many occurences of each value there is (there are 36 nodes with the value ```USA```);
* which color is associated to which value (```USA``` is velvet).

> The nodes that do not have a ```country``` property are not colored. They remain in black.
