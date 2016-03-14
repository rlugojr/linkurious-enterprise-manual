## Monitorización

### Monitorización de procesos

Linkurious inicia 3 procesos independientes cuando es arrancado:
1. `node` (o `node.exe`): El gestor de procesos interno (un [PM2](https://github.com/Unitech/pm2) manager)  
2. `node` (o `node.exe`): El proceso del servidor de Linkurious
3. `java` (o `java.exe`): El servidor integrado de [ElasticSearch](https://www.elastic.co/)

Compruebe si estos procesos están funcionando abriendo el menú desde el directorio de Linkurious (ver cómo en cada sistema operativo en la siguiente sección). El menú tiene el aspecto de la siguiente imagen:


![menu](https://github.com/Linkurious/linkurious-enterprise-manual/raw/master/en/administrate/Menu.png)


#### Sistemas Linux
 
Ejecute `menu.sh` (el estado aparece encima del menú). Alternativamente, ejecute `menu.sh status`.

#### Sistemas Mac OS X

Ejecute `menu.sh.command` (el estado aparece encima del menú). Alternativamente, ejecute `menu.sh.command status`.

#### Sistemas Windows

Ejecute `menu.bat` (el estado aparece encima del menú). Alternativamente, ejecute `menu.bat status`.

### Estado

#### Aplicación

El estado de la aplicación puede obtenerse consultando al servidor web de la siguiente forma:

> curl http://127.0.0.1:3000/api/status

**Respuesta exitosa:**

```
HTTP/1.1 200 OK
{
  "status": {
    "code": 200,
    "name": 'initialized',
    "message": 'Linkurious ready to go :)'
  }
}
```
Donde "code" es el código de estado del servidor (100: iniciando, 200: OK, >400: problema), "name" es el nombre del estado actual del servidor, y "message" describe el estado actual del servidor.

#### Fuentes de datos

El estado de todas las fuentes de datos puede obtenerse consultando al servidor web de la siguiente forma:

> curl http://127.0.0.1:3000/api/dataSources

**Respuesta exitosa:**

```
HTTP/1.1 200 OK
{
  "sources": [
    {"name":"Database #0","configIndex":0, "key":"a2e3c50f", "connected":true},
    {"name":"Database #1","configIndex":1, "key":null, "connected":false},
    {"name":"Database #2","configIndex":2, "key":null, "connected":false}
  ]
}
```

Donde "configIndex" es el índice de la fuente de datos en la sección 'dataSources' de la lista de configuración (ver sección Configuración), "key" es la clave única que identifica la fuente de datos (null cuando no está conectada), y "connected" es `true` si la fuente está disponible actualmente.
