## Copia de seguridad

### Linkurious

Siga los siguientes pasos para crear una copia de seguridad consistente:

1. Pare Linkurious.
2. Haga una copia del directorio `<linkurious-folder>/data`.
3. Si usted utiliza MySQL o PostgreSQL en lugar de SQLite (predeterminado) como el almacén de datos interno de Linkurious, por favor haga una copia de seguridad de la base de datos ahora.

Reinicie Linkurious una vez que tenga la copia de seguridad completa de las bases de datos Neo4j.

### Neo4j Enterprise

Por favor consulte la [documentación de Neo4j](http://neo4j.com/docs/stable/operations-backup.html) para realizar copias de seguridad en caliente de la base de datos de grafos.

### Neo4j Community

1. Pare Neo4j Community edition.
2. Haga una copia del directorio `<neo4j-folder>/data` o cualquier otro directorio utilizado para almacenar la base de datos de grafos.

Usted puede reiniciar Neo4j ahora.
