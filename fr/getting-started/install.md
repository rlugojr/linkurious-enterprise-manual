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

2. Enter the Linkurious folder: `>cd linkurious-osx`.

3. Check the configuration and make sure that the URL of you Neo4j database is correctly specified: `>head ./data/config/production.json`. Example output:
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

4. If you need to change the URL of Neo4j or specify a user/password, edit the configuration file with your favorite editor. When adding a user/password, remember to put these strings between quotes (`"`).

5. If your deployment is security critical, please make sure that you will not run Linkurious with a `root` account.

6. Make sure that you have Java JDK installed by typing `javac -version` in a terminal. If needed, [install Java JDK for Mac OSX](http://docs.oracle.com/javase/7/docs/webnotes/install/mac/mac-jdk.html).

7. Make sure that Neo4j is running.

8. Run `./linkurious-osx/start.sh.command` to launch Linkurious (you can double-click on the file to run it).

### Windows systems

1. [Unzip](http://customize.org/help/How_To_Unzip_A_File) Linkurious' archive (right-click on `linkurious-windows-v0.10.0.zip`, then select "Extract all").

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

### How to run multiple instances of Linkurious

<div class="alert alert-info">
  A single instance of Linkurious can connect to multiple graph databases.
</div>

Linkurious is designed to run a single instance per machine.
While it is not recommended and with no guarantee to work, you may run multiple instances of Linkurious by doing the following:

Copy the entire linkurious directory (the one including this file) to a new place, and edit the `data/config/production.json` file:
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
