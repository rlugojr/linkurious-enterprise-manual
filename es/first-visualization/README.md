En este capítulo, aprenderemos lo básico sobre como explorar y visualizar una base de datos de grafos con Linkurious.

###Sobre el conjunto de datos

Esta sección del manual y los siguientes capítulos están basados en un conjunto de datos procedente de [Crunchbase](http://www.crunchbase.com/). Crunchbase es un popular sitio web que rastrea el ecosistema de start-ups, especialmente empresas e inversores.

Hemos utilizado Crunchbase para crear una base de datos de grafos de aproximadamente 75,000 nodos y 250,000 relaciones. A partir de esto hemos creado un subconjunto centralizado solamente en las empresas del área de la bahía de San Francisco. Este subconjunto contiene 14,866 nodos y 47,093 relaciones. Un grafo contiene 4 tipos de nodos:
* Ciudades
* Empresas
* Inversores
* Mercados

Las empresas e inversores están enlazados a ciudades mediante la relación `HAS_CITY`. Las empresas están relacionadas con otras empresas mediante la relación `ACQUIRED`. Los inversores y empresas están enlazados mediante la relación `INVESTED_IN`. Las empresas están enlazadas a mercados mediante la relación `HAS_MARKET`.

Para seguir este manual, le aconsejamos [descargar y instalar conjunto de datos](http://linkurio.us/public/crunchbase-sfbay.db.zip). Extraiga el archivo y ponga su contenido en la carpeta `[YOUR_NEO4J_FOLDER]/data/graph.db`.