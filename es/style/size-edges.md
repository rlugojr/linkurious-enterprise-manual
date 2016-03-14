## Dar tamaño a las relaciones de acuerdo a una propiedad

Dar tamaño a las relaciones funciona de la misma forma.

Por defecto todas las relaciones tienen el mismo tamaño. Sin embargo es posible escoger asociar el tamaño de las relaciones a ciertas propiedades. De esta forma será posible visualizar esa propiedad.

Esta técnica solamente puede aplicarse a propiedades cuantitativas.

Esto funciona de forma similar a la funcionalidad de colorear de Linkurious Enterprise. Colorear y dar tamaño pueden ser combinados para obtener visualizaciones potentes.

![](https://github.com/Linkurious/linkurious-enterprise-manual/raw/master/en/style/PriceZoom.png)

En la imagen anterior vemos la empresa Instagram con varias empresas que han invertido en ella.

Si hacemos zoom en la relación entre Instagram y Sequoia Capital, podemos ver que tiene la propiedad ```raised_amount_usd``` (cantidad recaudada en dólares) con el valor ```55 000 000```.

Vamos a dar tamaño a las relaciones entre las diferentes empresas de acuerdo a su propiedad ```raised amount``` para ver rápidamente quien invirtió más dinero en Instagram.

Hacemos clic en la esquina superior derecha para abrir el panel de diseño y escogemos la pestaña ```Edges``` (relaciones).

Movemos el ratón a ```raised amount```. Además de poder colorear las relaciones nodos de acuerdo a esta propiedad, también es posible dar tamaño a los a las relaciones. Linkurious Enterprise puede hacer esto por usted para cualquier propiedad que tenga valores numéricos.

Hacemos clic en el icono ```Size``` (dar tamaño).

Aparece un nuevo menú. Hace posible establecer ```Min/max size difference```, la diferencia en tamaño entre la relación con el menor valor y la relación con el mayor valor.

Si queremos ver la diferencia en ```raised amount``` establecemos ```Min/max size difference``` a ```2```.

![](https://github.com/Linkurious/linkurious-enterprise-manual/raw/master/en/style/TailleEdges.png)

Ahora podemos ver que algunas relaciones son más gruesas que las otras.


