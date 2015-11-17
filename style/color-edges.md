## Coloring the edges according to a property

Coloring the edges works exactly the same that coloring nodes like presented previously.

If all your nodes or edges have the same color, it is difficult to distinguish differences between them without looking at their individual properties. A great way to circumvent that issue is to choose to color the edges according to a certain property.

First of all, let's open the design panel on the right corner of the screen and hit the ```Design``` tab.By default we can see the properties of the nodes. We select the ```edges``` tab on the bottom.

![](TwitterPanel.png)




![](Colored.png)

If we look at the property ```country```, in the design panel we can see:
* the different values associated with the ```country``` property (CAN, GBR, JPN, RUS, USA);

And hitting the color button we also can see

* how many occurences of each value there is (there are 36 nodes with the value ```USA```);
* which color is associated to which value (```USA``` is velvet)



> We can see that the nodes that do not have a ```country``` property are not colored. They remain in grey.
By default the edges are not colored.





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
