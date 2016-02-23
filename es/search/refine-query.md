## Búsqueda avanzada

¿Está buscando un nodo o relación en particular y la búsqueda devuelve demasiados resultados? ¡El texto que está buscando es demasiado común! 
Usted podría querer reducir su búsqueda filtrando varias propiedades.

Si buscamos una startup que tenga el texto ```facebook``` en cualquiera de sus propiedades obtenemos 88 resultados. Intentemos reducirlos.

![](../../en/search/Facebook_Example.png)

Hacemos clic en el icono ```Advanced``` y aparece un nuevo menú:

![](../../en/search/Advanced_Search.png)

Podemos ver el nombre de las diferentes categorías (city: ciudad, company: empresa, investor: inversor y market: mercado) en nuestra base de datos y sus apariciones.
Hacemos clic en ```Options``` para ver el nombre de las diferentes propiedades en nuestro grafo.

En nuestro grafo, Facebook está categorizado como ```Company``` (empresa). Vamos a seleccionar ```Company``` para restringir nuestra búsqueda de nodos a empresas.

Podemos ver los resultados.

![la etiqueta company](72.png)

En nuestro grafo, una ```Company``` puede tener propiedades como  ```category ``` (categoría),  ```country``` (país), ```first_funding_at ``` (primera financiación en) o ```founded_at``` (fundado en) y otras más. No obstante, no todos los nodos categorizados como empresa tendrán **todas** las propiedades.

Para reducir nuestros resultados, vamos a buscar en múltiples propiedades al mismo tiempo. Para encontrar Facebook, vamos a buscar una empresa que utilice facebook.com como su URL principal.

![](../../en/search/MProperties.png)

Ahora cuando escribimos ``facebook``, los resultados están filtrados para mostrar solamente nodos que tienen la categoría ```Company``` y el valor ``facebook.com`` en su propiedad ```homepage_url```.

Podemos ver que ahora los resultados están filtrados y podemos seleccionar el resultado que nos interese.

Podemos aplicar la misma estrategia para buscar relaciones.

> Linkurious Enterprise buscará coincidencias **exactas** para los valores que usted introduzca en el menú de opciones de búsqueda.
