## Filtering the edges according to a property

We have seen it is possible to use filters to select or remove specific nodes in our visualization according to a property. It is possible to do the same thing with edges.

![the relationships of Banexi Ventures](https://dl.dropboxusercontent.com/s/t1djwb2fausqjg9/78.png?dl=0)

In the graph below we see the relationships of [Banexi Ventures](http://www.banexiventures.com/) with other companies. Each relationship represents an investment in a start-up. But what kind of investment?

We can open up the design panel to investigate. Let's select ```Relationships``` on the bottom right corner.

![the relationships in the design panel](https://dl.dropboxusercontent.com/s/ean15t4etw6yxn4/79.png?dl=0)

We can see the different properties attached to the relationships in our dataset.

![the properties of relationships](https://dl.dropboxusercontent.com/s/7zrbb50bg5k46i9/80.png?dl=0)

We are going to focus on the ```funding_round_code```. Let's click on it.

![the different investments code](https://dl.dropboxusercontent.com/s/ofd68ngk0cs0cgz/81.png?dl=0)

We want to view only the funding round with the ```A``` code. These are the [Series A investments](http://en.wikipedia.org/wiki/Series_A_round) of Banexi Ventures. Let's uncheck the checkboxes to keep only ```A```.

![uncheck boxes](https://dl.dropboxusercontent.com/s/kkquxnkm9gmvqci/82.png?dl=0)

Now let's click on  ```Filter ```.

![applying filter](https://dl.dropboxusercontent.com/s/ovsi1nxyluy0itv/83.png?dl=0)

The relationships with the ```A``` ```funding_round_code``` are displayed. The other ```funding_round_code``` values removed from the visualization and a filter symbol is added on the bottom right corner.

![filtered visualization](https://dl.dropboxusercontent.com/s/xtbsb9cvke7fpi1/84.png?dl=0)

