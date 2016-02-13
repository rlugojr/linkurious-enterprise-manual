# Audit trail

## Configuration

Linkurious Enterprise est fournit avec une option de piste d'audit. Cette option vous permet d'avoir un registre détaillé sur les opérations effectués dans la base de données de graphes par les utilisateurs de Linkurious Enterprise. 

Pour configurer le system de piste d'audit, éditez le fichier `linkurious/data/config/production.json`. Ajoutez ce qui suit:

```json
"auditTrail": {
  "enabled": true,
  "logFolder": "audit-trail",
  "fileSizeLimit": 5242880,
  "strictMode": false,
  "mode": "rw"
}
```

* **enabled** - `false`. Permet la piste d'audit si `true`.
* **logFolder** - `"audit-trail"`. Où stocker le registre. Ce chemin est relatif au répertoire  `data` localisé à la racine de votre installation Linkurious.
* **fileSizeLimit** - `5242880`. Taille maximum en bite d'une archive de registre (par défaut: 5MB). Un nouveau fichier est créé lorque la limite est atteinte (rotations des fichiers) pour éviter des archives de registres trop énorme.
* **strictMode** - `false`. Assure que l'opération a été archivée avant de renvoyer le résultat à l'utilisateur si `true`. Peut avoir un gros impact sur la capacité de réponse du serveur.
* **mode** - `"rw"`. Enregistrera les actions de LECTURE (`"r"`), d'ECRITURE (`"w"`), ou les deux (`"rw"`).


## Format des registres

Les registres sont des lignes JSON. Vous pouvez facilement les reliés à un système de gestion come Log Stash pour les interpréter. Echantillon: 

```json
{"mode":"READ","date":"2015-10-11T11:05:21.888Z","user":"seb@linkurio.us","sourceKey":"2c08a4d9","action":"getEdge","params":{"edgeId":23}}
{"mode":"READ","date":"2015-10-11T11:05:21.889Z","user":"jean@linkurio.us","sourceKey":"2c08a4d9","action":"getNode","params":{"id":157}}
{"mode":"READ","date":"2015-10-11T11:05:21.910Z","user":"seb@linkurio.us","sourceKey":"2c08a4d9","action":"getNode","params":{"id":832}}
```