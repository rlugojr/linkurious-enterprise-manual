En este capítulo, aprenderemos el básico de como explorar y visualizar una base de datos orientadas a grafos con Linkurious.

###Sobre el dataset

Esta sección del manual y los siguientes capítulos se basan en un dataset proveniente de Crunchbase. Crunchbase es un sitio web popular que rastrea el ecosistema de start-up, sobre todo las empresas y los inversionistas.

Hemos utilizado Crunchbase para crear una base de datos orientadas a grafos de aproximadamente de 75000 nodos y 250000 relaciones. De esto hemos creado un subgrupo para enfocar sobre las empresas de Bahía de San Francisco únicamente. Esto contiene 14866 nodos y 47093 relaciones. Un grafo contiene 4 tipos de nodos:

- Ciudades
- Empresas
- Inversionistas
- Mercados 

Las empresas y los inversionistas están vinculados con las ciudades por la relación ```HAS_CITY``` Las empresas están vinculados unos con los otros por la relación ```ACQUIRED```. Los inversionistas y empresas son vinculados unos con los otros por la relación ```INVESTED_IN```. Las empresas están vinculados con los mercados por la relación ```HAS_MARKET```.

Para seguir este manual, le aconsejamos [descargar y instalar el datase.](http://linkurio.us/public/crunchbase-sfbay.db.zip) Extraiga el archivo y ponga su contenido en la carpeta ``[YOUR_NEO4J_FOLDER]/data/graph.db``

