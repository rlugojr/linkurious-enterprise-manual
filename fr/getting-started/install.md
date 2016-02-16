## Installer

### Systèmes Linux

1. Décompressez votre copie de Linkurious:
`>unzip linkurious-linux-v1.1.0.zip`.

2. Entrez dans le fichier Linkurious: `>cd linkurious-linux`.

3. Vérifiez la configuration et assurez-vous que l'URL de votre base de donnée Neo4j soit correctement mentionnée: `>head ./data/config/production.json`. Exemple de résultat:
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

4. Si vous avez besoin de changer l'URL de Neo4j ou de spécifier un nom d'utilisateur/mot de passe, éditez le fichier de configuration avec votre éditeur favori. Lorsque vous ajoutez un utilisateur/mot de passe, rappelez-vous de mettre ces valeurs entre guillements (`"`).

5. Si votre déploiement informatique est critique, assurez-vous que vous ne démarrez pas Linkurious avec un compte utilisateur racine.

6. Assurez-vous que vous avez installé Java JDK en tapant `javac -version` dans le terminal. Si nécessaire, [install Java JDK for Linux](https://docs.oracle.com/javase/7/docs/webnotes/install/linux/linux-jdk.html).

7. Assurez vous que Neo4j tourne.

8. Démarrez `./linkurious-linux/start.sh` pour lancer Linkurious.

### Mac OSX systems

1. Décompressez votre copie de Linkurious:
`>unzip linkurious-osx-v1.1.0.zip`.

2. Entrez dans le fichier Linkurious:`>cd linkurious-osx`.

3. Vérifiez la configuration et assurez-vous que l'URL de votre base de données Neo4j soit correctement spécifiéee: `>head ./data/config/production.json`. Exemple de sortie:
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

4. Si vous avez besoin de changer l'URL de Neo4j ou de spécifier un nom d'utilisateur et un mot de passe, éditez le fichier de configuration avec votre éditeur favori. Lorsque vous ajoutez un utilisateur et un mot de passe, rappelez-vous de les mettre entre guillements (`"`).

5. Si votre déploiement informatque est critique, assurez vous de ne pas lancer Linkurious avec un compte racine .

6. Assurez-vous que vous avez installé Java JDK en tapant `javac -version` dans le terminal. Si nécessaire, [install Java JDK for Linux](https://docs.oracle.com/javase/7/docs/webnotes/install/linux/linux-jdk.html).

7. Assurez-vous que Neo4j est lancé.

8. Démarrez `./linkurious-osx/start.sh.command` pour lancer  Linkurious (vous pouvez double cliquer sur le fichier pour le lancer).

### Windows systems

1. [Décompressez](http://customize.org/help/How_To_Unzip_A_File) l'archive Linkurious (clic-droit sur `linkurious-windows-v0.10.0.zip`, puis sélectionnez "Tout extraire".

2. Entrez dans le fichier Linkurious:`linkurious-windows`.

3. Ouvrez le fichier de configuration `linkurious-windows/data/config/production.json` avec WordPad ou Notepad++, et assurez-vous que l'URL de votre base de données Neo4j soit correctement spécifiée. Si besoin, actualisez le nom d'utilisateur et le mot de passe. 
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


### Installer Linkurious en tant que logiciel service 

Afin de démarrer Linkurious automatiquement quand le système démarre, il est possible d'installer Linkurious comme logiciel service sur Linux et Max OSX.


#### Installer comme logiciel service sous Linux 

1. Ouvrez le menu d'administration en lançant `menu.sh` dans le dossier Linkurious.
2. Vérifiez si Linkurious est déjà installé comme logiciel service (mentionné en haut du menu).
3. Selectionnez `Install Linkurious as a service`.
4. Linkurious sera alors installé comme service de votre système d'exploitation.

#### Installer comme logiciel service sous Mac OSX

1. Ouvrez le menu d'administration en lançant `menu.sh.command` dans le dossier  Linkurious'.
2. Vérifier si Linkurious est déjà installé comme logiciel service (mentionné en haut du menu).
3. Selectionnez `Install Linkurious as a service`.
4. Linkurious sera alors installé comme service de votre système d'exploitation.

### Comment démarrer plusieurs instances Linkurious 

<div class="alert alert-info">
  Une instance unique de Linkurious peut se connecter à plusieurs bases de données de graphes. 
</div>

Linkurious est conçu pour lancer une seule instance par machine. Alors que ce n'est pas recommandé et que nous n'en garantissons pas le fonctionnement, vous pouvez lancer plusieurs instances Linkurious à la fois en suivant ce quit suit:

Copiez le répertoire entier de Linkurious (celui qui comprend le répertoire (directory)) à un nouvel emplacement, et éditez le fichier `data/config/production.json` :
Vous aurez besoin de changer ``listenPort`` pour paramètrer un port différent de celui utilisé dans le fichier `production.json`. Vous devez aussi éditer  `graphdb` et `db.storage`.

Ceci est un exemple d'une seconde instance de Linkurious sur`http://localhost:3001`, qui appelle l'API Neo4j sur le port `7475`:

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

Si vous utilisez le logiciel Elasticsearch associé à Linkurious, vous aurez aussi besoin de modifier la configuration dans `system/elasticsearch/config/elasticsearch.yml` pour paramétrer un autre port que le port par défaut 9201. 

Enfin, notez qu'il n'est pas possible d'installer différentes versions de Linkurious comme logiciel service en même temps sur une même machine.


