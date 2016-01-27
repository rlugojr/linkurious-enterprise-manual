## La sintaxis de búsqueda avanzada

Linkurious Enterprise utiliza Elastic. Por tanto usted puede utilizar la sintaxis de Elastic detallada en la [documentación de la cadena de búsqueda de Elastic](http://www.elasticsearch.org/guide/en/elasticsearch/reference/current/query-dsl-query-string-query.html#query-string-syntax).

Simplemente escriba los siguientes comandos en la barra de búsqueda de Linkurious Enterprise search.

### Nombre del campo

Donde el campo "status" contenga "active": ```status:active```

Donde el campo "title" contenga "quick" o "brown" (si usted omite el operador OR el operador por defecto será utilizado): ```title:(quick OR brown), title:(quick brown)```

Donde el campo "author" contenga la frase exacta "john smith": ```author:"John Smith"```

Donde cualquiera de los campos "book.title", "book.content" o "book.date" contenga "quick" o "brown" (preste atención a como necesitamos escapar el \* con una barra invertida): ```book.\*:(quick brown)```

Donde el campo "title" no tenga valor (o no exista): ```_missing_:title```

Donde el campo "title" tenga cualquier valor no nulo: ```_exists_:title```

### Rangos

Los rangos pueden especificarse en campos de tipo fecha, numéricos o cadenas de texto. Los rangos inclusivos se indican con corchetes [mín. TO máx.] y los rangos excluyentes con llaves {mín. TO máx.}.

Donde el campo "date" tenga valores incluidos en 2012: ```date:[2012-01-01 TO 2012-12-31]```

Donde el campo "count" tenga un número entre 1 y 5: ```count:[1 TO 5]```

Donde el campo "count" sea mayor o igual que 10: ```count:[10 TO *]```

Donde el campo "date" tenga un valor anterior a 2012: ```date:{* TO 2012-01-01}```

Donde el campo  "count" tenga un valor de 1 a 5 pero sin incluirlo: ```
count:[1..5}```

Los rangos con un extremo sin especificar también pueden indicarse con la siguiente sintaxis:
* age:>10 
* age:>=10 
* age:<10 
* age:<=10


### Operadores booleanos

Por defecto, todos los términos de búsqueda son opcionales, siempre que alguno de ellos coincida. Buscar ```foo bar baz``` encontrará cualquier documento que contenga uno  o más de los valores ```foo```, ```bar``` o ```baz```. Ya hemos explicado el operador por defecto anteriormente, que le permite forzar que todos los términos sean requeridos, pero también existen operadores booleanos que pueden ser utilizados en la cadena de búsqueda para proporcionar más control.

Los operadores preferidos son ```+``` (este término debe estar presente) y ```-``` (este término no puede estar presente). Todos los demás términos son opcionales. Por ejemplo, la búsqueda ```quick brown +fox -news``` indica que: 
* "fox" debe estar presente 
* "news" no puede estar presente 
* "quick" y "brown" son opcionales (su presencia incrementa la relevancia)

### Impulso

Utilice el operador de impulso ```^``` para hacer un término más relevante que otro. Por ejemplo, si queremos encontrar todos los documentos sobre zorros (foxes), pero estamos especialmente interesados en zorros rápidos (quick): ```quick^2 fox```

El impulso por defecto es 1, pero puede ser cualquier número real positivo. Un impulso entre 0 y 1 reduce la relevancia.

Los impulsos también pueden aplicarse a frases o grupos: ```"john smith"^2 (foo bar)^4```

### Agrupación

Múltiples términos y condiciones pueden agruparse con paréntesis, para formar sub-consultas: ```(quick OR brown) AND fox```

Los grupos pueden ser utilizados para afectar un campo en particular, o impulsar el resultado de una sub-consulta: ```status:(active OR pending) title:(full text search)^2```
