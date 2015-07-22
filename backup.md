
## Backup

### Linkurious

Follow these steps to perform a consistent backup:

1. Stop Linkurious.
2. Backup the folder `<linkurious-folder>/data`.
3. If you use mySQL or postreSQL instead of SQLite (default) as the internal data store of Linkurious, please backup these databases now.

Restart Linkurious once you have complete the backup of the Neo4j databases.

### Neo4j Enterprise

Please follow the [Neo4j documentation](http://neo4j.com/docs/stable/operations-backup.html) to perform a hot backup of the databases.

### Neo4j Community

1. Stop Neo4j Community edition.
2. Backup the folder `<neo4j-folder>/data` or any folder used to store the database.

You can restart Neo4j now.
