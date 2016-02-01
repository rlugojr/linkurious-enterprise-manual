## Colorer les liens selon une propriété

Colorer les liens fonctionne exactement de la même manière que colorer les noeuds comme présenter précédemment.

Si tous les liens ont la même couleur, il est difficile de distinguer des différences entre eux sans se pencher sur leurs propriétés individuelles. Une bonne manière de contourner celà est de choisir de colorer les liens selon une propriété particulière. 


First of all, let's open the design panel on the right corner of the screen and hit the ```Design``` tab. We can see all edge properties. We click on the ```edges``` tab on the bottom.

![](NoColors.png)

We click on the ```color``` button along property ```type``` to color edges by this property.

![](Coloré.png)


We see:
* the different values associated with the ```type``` property (INVESTED_IN, ACQUiRED, HAS_CITY and HAS MARKET)
* how many occurences of each value there is (there are 39  nodes with the value ```INVESTED_IN```);
* which color is associated to which value (```ACQUIRED``` is blue)

To color the edges according to another property, we first unset colors by clicking on the same ```color``` button.

![](Change.png)

Then, we can click on the ```color``` button of another property.
