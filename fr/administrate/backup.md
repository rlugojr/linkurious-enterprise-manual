## Backup

### Linkurious

Suivez ces étapes pour effectuer un backup consistant:

1. Arrêtez Linkurious.
2. Faites une sauvegarde du fichier `<linkurious-folder>/data`.
3. Si vous utilisé MySQL ou PostgreSQL au lieu de SQLite (par défaut) pour conserver les données internes de Linkurious, sauvegardez cette base de données maintenant. 

Redémarrez Linkurious une fois que vous avez terminé la sauvegarde de la base de données de graphes Neo4j graph databases.

### Neo4j Enterprise

Merci de suivre la documentation [Neo4j documentation](http://neo4j.com/docs/stable/operations-backup.html) pour effectuer la sauvegarde de la base de données de graphes. 

### Neo4j Community

1. Arrêtez Neo4j Community 
2. Sauvegardez le dossier `<neo4j-folder>/data` ou tout autre dossier utilisé pour garder les graphes de la base de données. 

Maintenant vous pouvez redémarrer Neo4j.
