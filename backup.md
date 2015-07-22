
## Backup


### Neo4j Enterprise

Please follow the [Neo4j documentation](http://neo4j.com/docs/stable/operations-backup.html) to perform a hot backup of the database.

### Neo4j Community

1. Stop Neo4j Community edition.
2. Copy the folder `<neo4j-folder>/data`.

### Linkurious

Follow these steps to perform a consistent backup:

1. Stop Linkurious.
2. Copy the folder `<linkurious-folder>/data`.
3. If you use mySQL or postreSQL instead of SQLite (default) as the internal data store of Linkurious, please backup these databases now.


You can now restart Neo4j and Linkurious.