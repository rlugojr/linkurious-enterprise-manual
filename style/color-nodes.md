## Coloring the nodes according to a property

If all your nodes or edges have the same color, it is difficult to distinguish differences between them without looking at their individual properties. A great way to circumvent that issue is to choose to color the nodes according to a certain property.

For example, our nodes may have a ```country``` property that we would like to highlight, thus Linkurious Enterprise enables us to color the nodes according to a particular property, here ```country```.

This way, a French and a German start-up will have different colors. It will be easier to distinguish them visually.

In the picture below, we see the start-ups and investors Twitter is connected to. At first glance we have no idea where they are coming from.

![](SinColor.png)

First of all, let's open the design panel on the right corner of the screen and hit the ```Design``` tab. We click on the ```color``` button along the property ```country``` to color nodes by this property.

![](Colors.png)

We see:
* the different values associated with the ```country``` property (CAN, GBR, JPN, RUS, USA);
* the number of occurences of each value there is (there are 20 nodes with the value ```USA```);
* which color is associated to which value (```USA``` is green)



Notice that the nodes that do not have a ```country``` property remain in grey.

To color another property, we unset colors by clicking on the same ```color``` button:

![](Unset.png)

Then, we can click on the ```color``` button of another property.
