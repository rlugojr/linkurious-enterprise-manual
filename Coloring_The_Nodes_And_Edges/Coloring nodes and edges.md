# Coloring The Nodes According To A Property

If your nodes or edges all have the same color, it is difficult to distinguish difference between them without looking up their properties individually. A great way to circumvent that issue is to choose to color the nodes according to a certain property.

For example, your nodes may have a ```country``` property. Maybe you need that to analyse the data yor are looking at. Linkurious Enterprise enables you to color the nodes according to their ```country``` value. This way, a French and a German start-up will have different colors. It will be easy to distinguish them visually.

In the picture below, we see the start-ups and investors Twitter is connected to. At first glance we have no idea where they are coming from.

![the twitter network](https://github.com/Linkurious/linkurious-enterprise-manual/blob/master/screenshots/29.png)

First of all, let's open the design panel on the right side of the screen. To do this hit the ```+``` sign.

![open design panel](https://github.com/Linkurious/linkurious-enterprise-manual/blob/master/screenshots/30.png)

The design panel opens up.

Select the property you want to color the nodes according to. Here we want to use the ```country``` property. Click on the color symbol on the right.

![select country to color](https://github.com/Linkurious/linkurious-enterprise-manual/blob/master/screenshots/31.png)

![select country to color](screenshots/31.png)

![select country to color](screenshots/31.png?raw=true)

![select country to color](31.png)

![select country to color](31.png?raw=true)

Immediately the nodes in your visualization are colored according to their countries. In the design panel, we can see :
* the different values associated with the ```country``` property (CAN, GBR, JPN, RUS, USA);
* how many occurences of each value there is (there are 36 nodes with the value ```USA```);
* which color is associated to which value (```USA``` is velvet).

> The nodes that do not have a ```country``` property are not colored. They remain in black.
