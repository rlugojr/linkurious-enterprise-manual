## Mise à jour

<div class="alert alert-danger">
    Sauvegardez Linkurious avant d'effectuer toute mise à jour.
</div>

### Mise à jour automatiques 

Si vous avez installé Linkurious v0.10.0 ou plus, vous pouvez le mettre à jour en utilisant le script de mise à jour automatique:


1. Téléchargez la dernière version de Linkurious sur notre site internet (par exemple `linkurious-linux-v1.0.0.zip`) et sauvegardez le dans le dossier Linkurious.
2. Arrêtez Linkurious en utilisant le script `stop` 
3. Sauvegardez le dossier `data`. Si vous utilisez une base de données externe (e.g. MySQL or PostgreSQL), sauvegardez également cette base de données `linkurious` 
4. Démarrez le script de mise à jour (Linux: `update.sh`, OSX: `update.sh.command`, Windows: `update.bat`).
5. Démarrez Linkurious normalement

### Mise à jour du manuel 

Pour des versions antérieures à v0.10, aucune mise à jour n'est disponible. Pour mettre à jour Linkurious, vous devez installer une nouvelle version et supprimer la précédente. Toutes les visualisations, utilisateurs, groupes et droits d'accès seront perdus.

Dans certains cas, copier le fichier `database.db` de l'ancien dossier Linkurious vers le nouveau dossier peut fonctionner. Ceci n'est cependant pas garanti et dépend des versions.
