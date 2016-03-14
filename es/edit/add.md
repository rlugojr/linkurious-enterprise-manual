## Crear nodos y relaciones

En el panel ```more options``` (más opciones), podemos elegir crear un nodo o relación.

![](https://github.com/Linkurious/linkurious-enterprise-manual/raw/master/en/edit/A1.png)

### Crear un nodo

Introducimos un valor para ```Categories``` (categorías), en este caso Investor (inversor) y pulsamos en add (añadir). 

![](https://github.com/Linkurious/linkurious-enterprise-manual/raw/master/en/edit/A2.png)

Después podemos rellenar el valor correspondiente para cada propiedad. Cuando hayamos acabado, hacemos clic en el botón ```Save``` (guardar).

![](https://github.com/Linkurious/linkurious-enterprise-manual/raw/master/en/edit/A3.png)

En este caso hemos introducido el valor ```Paris``` para la propiedad City (ciudad), el valor ```France``` para la propiedad Country (país) y el valor ```NewInvestor``` (nuevo inversor) para la propiedad Name (nombre).

![](https://github.com/Linkurious/linkurious-enterprise-manual/raw/master/en/edit/A5.png)

Podemos ver que el nodo creado ```NewInvestor``` es añadido a nuestro grafo.


### Crear una relación

Tenemos que proporcionar la siguiente información:

![](https://github.com/Linkurious/linkurious-enterprise-manual/raw/master/en/edit/A6.png)

* ```Type```: el tipo de relación
* ```Source```: el origen de la relación
* ```Target```: el destino de la relación

De la misma forma que para los nodos, podemos añadir cuantas propiedades queramos para la relación. Cuando hayamos acabado, hacemos clic en el botón ```Save``` (guardar).

En este caso hemos introducido el valor ```NewInvestor``` para el origen, el valor ```INVESTED_IN``` (invirtió en) para el tipo y el valor ```Twitter``` para el destino, y finalmente ```2015``` para la propiedad ```funded_year``` (año de financiación).

Finalmente, podemos ver en el grafo nuestro nuevo nodo y nuestra nueva relación:

![](https://github.com/Linkurious/linkurious-enterprise-manual/raw/master/en/edit/A8.png)

También es posible crear una nueva relación entre dos nodos seleccionando esos dos nodos, haciendo clic en el fondo de la visualización para mostrar el menú contextual y luego escogiendo la opción ```Create a new edge``` (crear una nueva relación). El origen y destino serán rellenados.
