## Sizing the nodes according to a property

By default all the nodes and edges have the same size. It is possible though to choose to map the size of nodes or edges to certain properties. This way it will be possible to visualize that property.

This technique only applies to numbers ie to the nodes or edges that have a property that is a number.

This works similarly to the coloring functionality of Linkurious Enterprise. Coloring and sizing can be combined to make powerful visualizations.

For example [Andreessen Horowitz](http://a16z.com/) is a leading VC firm with 327 relationships to different companies it has funded. Which companies have received the most funding? Hard to know by simply looking at the graph.

![the portfolio](https://dl.dropboxusercontent.com/s/euzn1glyj6h9i4y/34.png?dl=0)

We are going to size the different companies according to their ```funding_total``` property in order to visualize which are the most successful.

We click on the ```+``` symbol on the right to open up the design panel.

![open up the design panel](https://dl.dropboxusercontent.com/s/rockq8dqh0hyqwe/35.png?dl=0)

We move the mouse to ```funding_total```. In addition to being able to color the nodes according to that property, it is possible to size the nodes. Linkurious Enterprise can do that for any property that has numerical values.

We are going to select the ```Size``` icon.

![select size](https://dl.dropboxusercontent.com/s/s64sp6pzk7npbk1/36.png?dl=0)

A new menu appears. It makes it possible to set the ```Min/max size difference```, the difference in size between the node with the lowest value and the node with the highest value.

![size difference](https://dl.dropboxusercontent.com/s/0vcgwmtr0acgm7v/37.png?dl=0)

If we want to view the difference in ```funding_total``` we are going to set the ```Min/max size difference``` to ```5```.

![setting the size difference](https://dl.dropboxusercontent.com/s/hhwr85uv278unrw/38.png?dl=0)

Now we can see that a few outliers appear as nodes larger than the rest.

![the outliers](https://dl.dropboxusercontent.com/s/bfwom2cfa2q1win/39.png?dl=0)

The larger nodes represent companies like Airbnb, Groupon, Magic Leap or Pinterest. We can quickly identify them as the most successful investments of Andreessen Horowitz.
