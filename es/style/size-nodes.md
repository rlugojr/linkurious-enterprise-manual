## Dar tamaño a los nodos de acuerdo a una propiedad

Por defecto todos los nodos tienen el mismo tamaño. Sin embargo es posible escoger asociar el tamaño de los nodos a ciertas propiedades. De esta forma será posible visualizar esa propiedad.

Esta técnica solamente puede aplicarse a propiedades cuantitativas.

Esto funciona de forma similar a la funcionalidad de colorear de Linkurious Enterprise. Colorear y dar tamaño pueden ser combinados para obtener visualizaciones potentes.

Por ejemplo [Andreessen Horowitz](http://a16z.com/) es una agencia de capital riesgo líder con 127 relaciones con diferentes empresas que ha financiado. ¿Qué empresas han recibido las mayores financiaciones? Es difícil saberlo simplemente observando este grafo.

![](https://github.com/Linkurious/linkurious-enterprise-manual/raw/master/en/style/A.png)

Vamos a dar tamaño a las diferentes empresas de acuerdo a su propiedad ```funding_total``` (financiación total) para visualizar cuáles son las más exitosas.

Hacemos clic en la esquina superior derecha para abrir el panel de diseño.

Movemos el ratón a ```funding_total```. Además de poder colorear los nodos de acuerdo a esta propiedad, también es posible dar tamaño a los nodos. Linkurious Enterprise puede hacer esto por usted para cualquier propiedad que tenga valores numéricos.

Vamos a seleccionar el icono ```Size``` (dar tamaño).

![](https://github.com/Linkurious/linkurious-enterprise-manual/raw/master/en/style/B.png)

Aparece un nuevo menú. Hace posible establecer ```Min/max size difference```, la diferencia en tamaño entre el nodo con el menor valor y el nodo con el mayor valor.

Si queremos ver la diferencia en ```funding_total``` establecemos ```Min/max size difference``` a ```12```.

![](https://github.com/Linkurious/linkurious-enterprise-manual/raw/master/en/style/C.png)

Ahora podemos ver que algunos nodos aparecen más grandes que otros nodos.

Los nodos más grandes representan empresas como Airbnb, Box, Pinterest o Zynga. Podemos identificarlas rápidamente como las inversiones más exitosas de Andreessen Horowitz.
