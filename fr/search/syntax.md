## La syntaxe de recherche avancée

Linkurious Enterprise utilise Elastic. Vous pouvez donc utiliser la syntaxe Elastic détaillée dans la documentation suivante[Elastic query_string documentation](http://www.elasticsearch.org/guide/en/elasticsearch/reference/current/query-dsl-query-string-query.html#query-string-syntax).

Entrez simplement les commandes dans la barre de recherche de Linkurious Enterprise

### Nom

Où le champ "status" contient  "active": ```status:active```

Où le champ "title" contient "quick" ou "brown" (Si vous oubliez le OU, l'opérateur par défaut sera utilisé): ```title:(quick OR brown), title:(quick brown)```

Où le champ "author" contient la phrase exacte "john smith": author:```"John Smith"```

Où un des champs "book.title", "book.content" ou "book.date" contient "quick" ou "brown" (notez qu'il est nécessaire d'esquiver le \* avec la barre oblique inversée): ```book.\*:(quick brown)```

Où le champ "title" n'a pas de valeur (ou valeur manquante) ```_missing_:title```

Où le champ "title" a quelconque valeur nulle: ```_exists_:title```

### Rangs

Des rangs peuvent être spécifiés pour des dates ou des champs numériques et/ou vides. Les rangs inclusifs sont spécifiés avec des crochets [min TO max] et les rangs exclusifs avec des accolades {min TO max}.

Où le champ  "date"  a une valeur en 2012: ```date:[2012-01-01 TO 2012-12-31]```

Où le champ "count" est un chiffre entre 1 et 5: ```count:[1 TO 5]```

Où le champ "count" est une valeur supérieure à 10: ```count:[10 TO *]```

Où le champ "date" a une valeur avant 2012: ```date:{* TO 2012-01-01}```

Où le champ "count" a une valeur de 1 à 5 mais n'incluant pas 5: [1..5}```

Les rangs avec une extrémité non limitée peuvent utiliser la syntaxe suivante:* age:>10 * age:>=10 * age:<10 * age:<=10


### Opérateurs booléens 

Par défaut, tous les termes sont optionnels tant qu'un terme au moins correspond. Une recherche pour 
```foo bar baz``` trouvera tout document qui contient un terme ou plus sur les trois soit ```foo``` ou ```bar``` ou ```baz```. Nous avons déjà discuté plus haut le default_operator qui vous permet de rechercher uniquement les documents contenant tous les termes, mais il est également possible d'utiliser des opérateurs booléens dans la requête pour un meilleur contrôle. 

Les opérateurs préférés sont  ```+``` (ce terme doit être présent) et ```-``` (ce terme n'est pas obligatoirement présent). Tous les autres termes sont optionnels. Par exemple, la requête ```quick brown +fox -news``` signifie que: * "fox" doit être présent * "news" ne doit pas être présent * "quick" et "brown" sont optionnels — leur présence augmente la pertinence.

### Boosting

Utilisez l'opérateur boost ```^``` pour rendre un terme plus pertinent que l'autre. Par exemple, si nous voulons trouver tous les documents sur les renards mais que nous sommes plus particulièrement intéressés par les renards rapides: ```quick^2 fox```

La valeur par défaut du boost est 1 mais ce peut-être toute valeur flottante positive. Les boots entre 0 et 1 réduisent la pertinence.

Les Boosts peuvent aussi être apppliqués à des phrases ou à des groupes: ```"john smith"^2 (foo bar)^4```

### Grouper

Les termes multiples ou clauses peuvent êtres groupés avec des parenthèses, pour former des sous-requêtes: ```(quick OR brown) AND fox```

Les groupes peuvent être utilisés pour cibler un champ particulier, ou pour booster le résultat d'une sous-requête: ```status:(active OR pending) title:(full text search)^2```
