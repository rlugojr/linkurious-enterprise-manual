## Installer

### Systèmes Linux

1. Décompressez votre copie de Linkurious:
`>unzip linkurious-linux-v1.1.0.zip`.

2. Entrez dans le fichier Linkurious: `>cd linkurious-linux`.

3. Vérifiez la configuration et que l'URL de votre base de donnée Neo4j soit correctement mentionnée: `>head ./data/config/production.json`. Exemple de résultat:
```JavaScript
{
  "dataSources": [{
    "graphdb": {
      "vendor": "neo4j",
      "url": "http://localhost:7474",
      "user": null,
      "password": null
    }
```

4. Si vous avez besoin de changer l'URL de Neo4j ou de spécifier un nom d'utilisateur/mot de passe, éditez le fichier de configuration avec votre éditeur favoris. Lorsque vous ajoutez un utilisateur/mot de passe, rappelez-vous de mettre ces valeurs entre guillements (`"`).

5. Si la sécurité de votre déploiement est critique, assurez-vous que vous ne démarrez pas Linkurious avec un compte d'utilisateur de type `root`.

6. Assurez-vous que vous avez installé Java JDK en tapant `javac -version` dans le terminal. Si nécessaire, [install Java JDK for Linux](https://docs.oracle.com/javase/7/docs/webnotes/install/linux/linux-jdk.html).

7. Assurez vous que Neo4j tourne.

8. Démarrez `./linkurious-linux/start.sh` pour lancer Linkurious.

### Mac OSX systems

1. Décompressez votre copie de Linkurious:
`>unzip linkurious-osx-v1.1.0.zip`.

2. Entrez dans le fichier Linkurious:`>cd linkurious-osx`.

3. Vérifiez la configuration et assurez-vous que l'URL de votre base de donnée Neo4j est correctement spécifiéee: `>head ./data/config/production.json`. Exemple de sortie:
```JSON
{
  "dataSources": [{
    "graphdb": {
      "vendor": "neo4j",
      "url": "http://localhost:7474",
      "user": null,
      "password": null
    }
```

4. Si vous avez besoin de changer l'URL de Neo4j ou de spécifier un nom d'utilisateur et un mot de passe, éditez le fichier de configuration avec votre éditeur favoris. Lorsque vous ajoutez un utilisateur et un mot de passe, rappelez-vous de les mettre entre guillements (`"`).

5. Si votre processus de déploiement est critique, assurez vous de ne pas lancer Linkurious avec un compte racine (`root`).

6. Assurez-vous d'avoir Java JDK d'installé en tapant `javac -version` dans le terminal.si besoin, [installez Java JDK pour Mac OSX](http://docs.oracle.com/javase/7/docs/webnotes/install/mac/mac-jdk.html).

7. Assurez-vous que Neo4j est lancé.

8. Démarrez `./linkurious-osx/start.sh.command` pour lancer  Linkurious (vous pouvez double cliquer sur le fichier pour le lancer).

### Windows systems

1. [Décompressez](http://customize.org/help/How_To_Unzip_A_File) l'archive Linkurious (clic-droit sur `linkurious-windows-v0.10.0.zip`, puis sélectionnez "Tout extraire" (Extract all)).

2. Entrez dans le fichier Linkurious:`linkurious-windows`.

3. Ouvrez le fichier de configuration `linkurious-windows/data/config/production.json` avec WordPad ou Notepad++, et assurez-vous que l'URL de votre base de donnée Neo4j est correctement spécifiée. Si besoin, actualisez le nom d'utilisateur et le mot de passe. 
```JavaScript
{
  "dataSources": [{
    "graphdb": {
      "vendor": "neo4j",
      "url": "http://localhost:7474", // Neo4 URL
      "user": null, // if needed, replace with the Neo4j user (between " quotes) 
      "password": null // replace with the Neo4j password (between " quotes) 
    }
```

4. Assurez vous d'avoir [installé Java JDK ](https://www.java.com/en/download/help/version_manual.xml). (si besoin, [installer Java JDK](http://docs.oracle.com/cd/E19182-01/820-7851/inst_cli_jdk_javahome_t/index.html)).

5. Assurez vous que Neo4j est lancé.

6. Double-cliquez sur `linkurious-windows\start.bat` pour lancer Linkurious.


### Installer Linkurious en tant que logiciel de service 

Afin de démarrer Linkurious automatiquement quand le système démarre, il est possible d'installer Linkurious comme logiciel de service sur Linux et Max OSX.


#### Installer comme logiciel de service sous Linux 

1. Ouvrez le menu d'administration en lançant`menu.sh` dans le dossier Linkurious.
2. Vérifier si Linkurious est déjà installé comme logiciel service (mentionné en haut du menu).
3. Selectionnez `Install Linkurious as a service`.
4. Linkurious sera alors installé comme service de votre système d'exploitation.

#### Install er comme logiciel service sous Mac OSX

1. Ouvrez le menu d'administration en lançant `menu.sh.command` dans le dossier  Linkurious'.
2. Vérifier si Linkurious est déjà installé comme logiciel service (mentionné en haut du menu).
3. Selectionnez `Install Linkurious as a service`.
4. Linkurious sera alors installé comme service de votre système d'exploitation.

### Comment démarrer plusieurs instances Linkurious 

<div class="alert alert-info">
  Une instance unique de Linkurious peut se connecter à plusieurs bases de données de graphes. 
</div>

Linkurious est conçu pour lancer une seule instance par machine. Alors que ce n'est pas recommandé et que nous n'en garantissons pas le fonctionnement, vous pouvez lancer plusieurs instances Linkurious à la fois en suivant ce quit suit:

Copiez le répertoire entier de Linkurious directory (celui qui comprend ce fichier one including this file) to a new place, and edit the `data/config/production.json` file:
You will need to change ``listenPort`` to set a different port from the one used in the `production.json` file. You may also edit `graphdb` and `db.storage`.

This is an example of a second instance of Linkurious served on `http://localhost:3001`, that calls the Neo4j API on the port `7475`:

```JavaScript
{
  "dataSources": [{
    "graphdb": {
      "vendor": "neo4j",
      "url": "http://localhost:7475"
    },
    "index": {
      "vendor": "elasticSearch",
      "host": "localhost",
      "port": 9201
    }
  }],
  "db": {
    "username": null,
    "password": null,
    "logging": true,
    "options": {
      "dialect": "sqlite",
      "storage": "database_secondInstance.sqlite"
    }
  },
  "server": {
    "listenPort": 3001,
    "clientFolder": "/public",
    "cookieSecret": "zO6Yb7u5H907dfEcmjS8pXgWNEo3B9pNQF8mKjdzRR3I64o88GrGLWEjqNq1Yx5"
  }
}
```

If you use the ElasticSearch software bundled with Linkurious, you will also need to modify the configuration in `system/elasticsearch/config/elasticsearch.yml` to set an alternate port to the default of 9201.

Finally, note that it is not currently possible to install different versions of Linkurious as a system service, at the same time, on the same machine.
