
## Backup

For Neo4j Enterprise edition, please follow the [Neo4j documentation](http://neo4j.com/docs/stable/operations-backup.html) to perform a hot backup of the database.

Follow these steps to perform a consistent backup using Neo4j Community Edition:

1. Stop Neo4j Community edition
2. Stop Linkurious
3. Copy the folder `<neo4j-folder>/data`
4. Copy the folder `<linkurious-folder>/data`
5. If you use mySQL or postreSQL instead of SQLite as the internal data store of Linkurious