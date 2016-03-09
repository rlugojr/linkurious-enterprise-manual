## Instalación

### Sistemas Linux

1. Descomprima su copia de Linkurious:
`>unzip linkurious-linux-v1.1.0.zip`.

2. Acceda al directorio de Linkurious: `>cd linkurious-linux`.

3. Compruebe la configuración y asegúrese de que la URL de su base de datos Neo4j esté correctamente especificada: `>head ./data/config/production.json`. Resultado de ejemplo:
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

4. Si necesita modificar la URL de Neo4j o especificar un usuario o contraseña, edite el archivo de configuración con su editor de texto favorito. Al añadir un usuario o contraseña, recuerde poner estos valores con comillas dobles (`"`).

5. Si la seguridad de su despliegue es crítica, por favor asegúrese de que no ejecuta Linkurious con una cuenta de usuario de tipo `root`.

6. Compruebe que tiene Java JDK instalado escribiendo `javac -version` en una terminal. Si lo necesita, [instale Java JDK para Linux](https://docs.oracle.com/javase/7/docs/webnotes/install/linux/linux-jdk.html).

7. Compruebe que Neo4j esté funcionando.

8. Ejecute `./linkurious-linux/start.sh` para arrancar Linkurious.

### Sistemas Mac OSX

1. Descomprima su copia de Linkurious:
`>unzip linkurious-osx-v1.1.0.zip`.

2. Acceda al directorio de Linkurious: `>cd linkurious-osx`.

3. Compruebe la configuración y asegúrese de que la URL de su base de datos Neo4j esté correctamente especificada: `>head ./data/config/production.json`. Resultado de ejemplo:
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

4. Si necesita modificar la URL de Neo4j o especificar un usuario o contraseña, edite el archivo de configuración con su editor de texto favorito. Al añadir un usuario o contraseña, recuerde poner estos valores con comillas dobles (`"`).

5. Si la seguridad de su despliegue es crítica, por favor asegúrese de que no ejecuta Linkurious con una cuenta de usuario de tipo `root`.

6. Compruebe que tiene Java JDK instalado escribiendo `javac -version` en una terminal. Si lo neceista, [instale Java JDK para Mac OSX](http://docs.oracle.com/javase/7/docs/webnotes/install/mac/mac-jdk.html).

7. Compruebe que Neo4j esté funcionando.

8. Ejecute `./linkurious-osx/start.sh.command` para arrancar Linkurious (puede hacer doble clic en este archivo para ejecutarlo).

### Sistemas Windows

1. [Descomprima](http://customize.org/help/How_To_Unzip_A_File) el archivo de Linkurious  (haga clic derecho en `linkurious-windows-v0.10.0.zip`, luego seleccione "Extraer todo").

2. Acceda al directorio de Linkurious `linkurious-windows`.

3. Abra el archivo de configuración `linkurious-windows/data/config/production.json` con WordPad o Notepad++, y asegúrese de que la URL de su base de datos Neo4j esté correctamente especificada. Si lo necesita, modifique el usuario o contraseña también.
```JavaScript
{
  "dataSources": [{
    "graphdb": {
      "vendor": "neo4j",
      "url": "http://localhost:7474", // Neo4 URL
      "user": null, // si es necesario, reemplazar con el usuario de Neo4j (entre comillas dobles ") 
      "password": null // reemplazar con la constraseña de Neo4j (entre comillas dobles ") 
    }
```

4. Compruebe [que tiene Java JDK instalado](https://www.java.com/en/download/help/version_manual.xml). Si es necesario, [instale Java JDK](http://docs.oracle.com/cd/E19182-01/820-7851/inst_cli_jdk_javahome_t/index.html).

5. Compruebe que Neo4j esté funcionando.

6. Haga doble click en `linkurious-windows\start.bat` para arrancar Linkurious.


### Instalar Linkurious como un servicio del sistema

Para ejecutar Linkurious automáticamente cuando el sistema operativo inicie, es posible instalar Linkurious como un servicio de sistema en las versiones de Linux y Mac OSX.

#### Instalar como servicio en sistemas Linux

1. Abra el menú de administración ejecutando `menu.sh` en el directorio de Linkurious.
2. Compruebe si Linkurious ya está instalado como servicio (aparece en la parte superior del menú).
3. Seleccione `Install Linkurious as a service`.
4. Linkurious se instalará como servicio de su sistema operativo.

#### Instalar como servicio en sistemas Mac OSX

1. Abra el menú de administración ejecutando `menu.sh.command` en el directorio de Linkurious.
2. Compruebe si Linkurious ya está instalado como servicio (aparece en la parte superior del menú).
3. Seleccione `Install Linkurious as a service`.
4. Linkurious se instalará como servicio de su sistema operativo.

### Cómo ejecutar múltiples instancias de Linkurious

<div class="alert alert-info">
  Una única instancia de Linkurious puede conectarse a varias bases de datos de grafos.
</div>

Linkurious ha sido diseñado para ejecutarse en una única instancia por máquina.
Aunque no está recomendado ni garantizado que funcione, usted podría ejecutar varias instancias de Linkurious haciendo lo siguiente:

Copie el directorio completo de linkurious (el que incluye este archivo) a un nuevo lugar, y edite el archivo `data/config/production.json`:
Necesitará modificar ``listenPort`` para establecer un puerto diferente al utilizado en el archivo `production.json`. Usted también podría editar `graphdb` y `db.storage`.

El siguiente es un ejemplo de una segunda instancia de Linkurious servida en `http://localhost:3001`, que se comunica con la API de Neo4j por el puerto `7475`:

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

Si utiliza el software ElasticSearch incluido con Linkurious, usted también podría necesitar modificar la configuración en `system/elasticsearch/config/elasticsearch.yml` para establecer un puerto alternativo al puerto por defecto 9201.

Finalmente, sea consciente de que no es posible instalar diferentes versiones de Linkurious como servicio de sistema, al mismo tiempo, en la misma máquina.
