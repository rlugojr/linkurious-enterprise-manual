## Configuración

<div class="alert alert-info">
    Omita esta sección si utiliza Linkurious con la configuración predeterminada. Puede modificar la configuración en cualquier momento.
</div>

El archivo de configuración está en `linkurious/data/config/production.json`. Es un archivo JSON dividido en las siguientes secciones:

* **dataSources** - La lista de fuentes de datos a las que conectarse.
* **allSources** - Configuraciones aplicadas a todas las fuentes de datos.
    * Configurar caminos más cortos, indexación, expansión de nodos, límites de búsqueda y la longitud mínima de consultas de búsqueda.
* **db** - El almacén de datos interno de Linkurious.
* **server** - La configuración del servidor de Linkurious.
* **access** - Los permisos de acceso.
    * Activar autenticación, configurar autenticación LDAP, establecer modo de solo lectura de datos y activar la publicación online.
* **clientAnalytics**
    * Anotar acciones de los usuarios en el cliente mediante una cuenta de Google Analytics (desactivado por defecto).
* **sigma** - Preferencias de Sigma.js.
    * Usted solo debería editar los estilos y paletas.

### Gestión de datos

#### Fuentes de datos

Las fuentes de datos son servidores accesibles por red (local, intranet o internet) con URLs a las que conectarse. Nosotros asumimos que cada fuente de datos sirve una única base de datos de grafo, sin embargo puede ser utilizada para servir una base de datos diferente la próxima vez que Linkurious se conecte. Por ejemplo, usted podría cargar una base de datos en su servidor Neo4j, y luego reiniciar el servidor con otra base de datos. Linkurious utilizará el ID de almacén para identificar la base de datos, de forma que usted pueda cambiar la base de datos fácilmente.

Linkurious puede conectarse a muchas fuentes de datos al mismo tiempo. Los usuarios finales seleccionarán la base de datos con la que trabajar en la interfaz, y cambiarán entre ellas.

Las fuentes de datos se configuran en la sección **dataSources**, que es una lista de potenciales fuentes de datos. De forma predeterminada, una única fuente de datos está configurada para conectarse a un servidor local de Neo4j. Cada fuente de datos contiene los siguientes ajustes:

* **name** (opcional) - Nombre legible para personas.
* **graphdb** - Servidor de base de datos de grafos al que conectarse.
    * **vendor** - `"neo4j"`. Solo servidores Neo4j están soportados.
    * **url** - `"http://127.0.0.1:7474/"`. Linkurious se comunicará con la API REST de Neo4j en esta dirección.
    * **writeURL** (opcional) - Si es proporcionado, Linkurious enviará peticiones de ESCRITURA a la base de datos de grafos en este punto de acceso y peticiones de LECTURA al punto de acceso en **url**.
    * **user** (opcional) - El nombre de usuario si la autenticación está activada en el servidor de base de datos de grafos.
    * **password** (opcional) - La contraseña si la autenticación está activada en el servidor de base de datos de grafos.
* **index** - El motor de búsqueda.
    * **vendor** - `"elasticSearch"`. Solo servidores ElasticSearch están soportados.
    * **host** - `"127.0.0.1"` para utilizar el servidor ElasticSearch integrado. Usted puede especificar la dirección de su propio servidor ElasticSearch.
    * **port** - `9201` para utilizar el servidor ElasticSearch integrado. Usted puede especificar el puerto de su propio servidor ElasticSearch.
    * **forceReindex** - `false`. Linkurious siempre re-indexará la base de datos de grafos al iniciar si es `true`, de lo contrario los administradores tendrán que lanzar el proceso desde el panel de control de administración (ver capítulo de Administración).

Los siguientes ajustes aplican a todas las fuentes de datos. Están disponibles en la sección **allSources**.

Ajustes generales:

* **connectionRetries** - `10`. El número máximo de intentos de conexión a cada fuente de datos y motor de búsqueda antes de considerarlos desconectados.
* **pollInterval** - `10`. Comprobar si las fuentes de datos y motores de búsqueda están conectados en cada intervalo (en segundos).

Ajustes del motor de búsqueda:

* **indexationChunkSize** - `5000`. El número de nodos y relaciones extraídos durante el indexado de la base de datos.
* **searchAddAllThreshold** - `500`. El número máximo de resultados de búsqueda que el usuario puede añadir a una visualización a la vez.
* **searchThreshold** - `3000`. El número máximo de resultados de búsqueda que pueden ser devueltos.
* **minSearchQueryLength** - `3`. El número de caracteres necesarios para lanzar una consulta de búsqueda. Establecer `1` para proporcionar resultados en directo desde el primer carácter escrito por el usuario.

Ajustes de exploración de grafos:

* **maxPathLength** - `20`. La longitud máxima de camino más corto devuelta por Linkurious. Encontrar el camino más corto es una operación costosa. Establecer un número pequeño limitará los recursos utilizados por la fuente de datos para realizar esta operación, y devolverá resultados más rápido.
* **shortestPathsMaxResults** - `10`. El número máximo de caminos más cortos devueltos.
* **rawQueryTimeout** - `60000`. Abandonar una consulta a la base de datos si el tiempo de respuesta es sobrepasado (en segundos).
* **defaultFuzziness** - `0.9`. Valor predeterminado para la aproximación de búsqueda entre 0 y 1. Un valor de `1` significa coincidencia exacta de la consulta de búsqueda.
* **expandThreshold** - `50`. Cuando el usuario expande un nodo con demasiados vecinos, Linkurious pedirá refinar la consulta de forma que menos vecinos sean obtenidos.

#### Conexión a un servidor Neo4j

Si es la primera vez que ejecuta un servidor Neo4j y usa Neo4j v2.2 o una versión más reciente, necesitará configurar las credenciales:

1. Lance el servidor Neo4j
- Abra el navegador web en la dirección http://127.0.0.1:7474
- Establezca un nuevo usuario y contraseña, y recuérdelos para configurar Linkurious.

Configurar Linkurious:

- Abra el archivo de configuración.
- Busque los ajustes `graphdb` de la fuente de datos.
- Establezca la URL del servidor Neo4j.
- Establezca el usuario y contraseña del servidor Neo4j.

Linkurious se conectará al servidor la próxima vez que lo inicie.

#### Gestión de instancias de Neo4j

Linkurious puede gestionar (iniciar y detener a la vez que Linkurious se inicia y detiene) su servidor Neo4j por usted para simplificar los scripts de administración. Para activar esta característica (disponible solamente en Linux y Max OSX), simplemente establezca el valor **neo4jPath** en **allSources** a la ruta absoluta del directorio raíz de Neo4j. Usted podrá ver una nueva entrada "Neo4j server" en el informe de estado del menú de consola de Linkurious (ver capítulo Administración > Monitorización).

#### Conexión al motor de búsqueda

El motor ElasticSearch integrado puede ser reemplazado por su propio clúster de ElasticSearch. Edite el archivo de configuración para establecer los ajustes `index` de la fuente de datos con la URL y credenciales de su clúster ElasticSearch. Linkurious creará un índice para cada base de datos de grafos, con nombres prefijados por `linkurious_`.

#### Almacén de datos interno

Linkurious almacena información como visualizaciones, usuarios y permisos en un almacén de datos separado de las bases de datos de grafos. Por defecto, Linkurious utiliza una base de datos SQLite. MySQL y PostgreSQL también pueden utilizarse pero deben ser instalados manualmente.

El almacén de datos interno se configura en la sección `db`:

* **name** - `"linkurious"`. El nombre de la base de datos.
* **username** (opcional) - El nombre de usuario administrador de la base de datos.
* **password** (opcional) - La contraseña del usuario administrador de la base de datos.
* **options** - 
    * **dialect** - `"sqlite"`. Valores disponibles: `"mysql"`, `"postgres"`.
    * **storage** (opcional) - `"server/database.sqlite"`. La ruta al archivo de base de datos, relativo al directorio `data`. Requerido para SQLite.
    * **host** (opcional) - Requerido para MySQL y PostgreSQL.
    * **port** (opcional) - Requerido para MySQL y PostgreSQL.


<div class="alert alert-warning">
    GLIBC >= v1.14 debe estar instalado en el servidor para poder utilizar SQLite. Usted puede comprobar las versiones disponibles para su sistema en <a href="http://distrowatch.com/search.php?ostype=All&category=All&origin=All&basedon=All&notbasedon=None&desktop=All&architecture=All&package=All&status=Active">http://distrowatch.com</a>.
</div>

### Servidor web

El servidor web de Linkurious proporciona la aplicación a usuarios finales mediante HTTP/S. Se configura en la sección `server`:

* **domain** - `localhost`. El dominio o subdominio utilizado para acceder al servidor web. Es obligatorio editarlo para publicar visualizaciones online. También es utilizado para restringir la validez de cookies a un dominio o subdominio.
* **listenPort** - `3000`. El puerto del servidor web. Algunos cortafuegos bloquean el tráfico de red en puertos diferentes al 80 (HTTP). Dado que solamente usuarios `root` pueden escuchar en puertos < 1024, usted puede necesitar re direccionar tráfico desde el puerto 80 al 3000 de la siguiente forma.

```
>sudo iptables -t nat -A PREROUTING -p tcp --dport 80 -j REDIRECT --to-port 3000
```

### Seguridad

Múltiples características de seguridad pueden ser activadas de acuerdo a sus necesidades. El valor `cookieSecret` en `server` es establecido aleatoriamente durante el primer inicio de Linkurious.

#### Cookies

Dentro de `server`:

* **cookieSecret** - La clave secreta utilizada para cifrar la cookie de sesión. Generada aleatoriamente durante el primer inicio.

#### Cross-origin resource sharing (CORS)

Dentro de `server`:

* **allowOrigin** - `"*"`. Definir la política de cross-origin resource sharing (CORS). Aceptar peticiones HTTP/S entre diferentes sitios por defecto (comodín).

#### Imágenes cross-origin (lado del cliente)

Dentro de `sigma`:

* **imgCrossOrigin** - `"anonymous"`. Restringir el origin de imágenes mostradas en visualizaciones para prevenir la ejecución de código malicioso en la tarjeta gráfica de los usuarios. Mostrar imágenes de cualquier origen por defecto.

#### Comunicaciones cifradas con SSL

Las comunicaciones externas con el servidor de Linkurious pueden ser cifradas con SSL sin necesidad de instalar software de terceros.

Dentro de `server`:

* **listenPortHttps** - `3443`. El puerto del servidor web si HTTPS está activo. Vea la sección de Instalación para entender por qué no debería establecer `443` directamente.
* **useHttps** - `false`. Cifrar comunicaciones con HTTPS si es `true`. Requiere un certificado SSL valido.
* **forceHttps** - `false`. Forzar que todo el tráfico utilice HTTPS si es `true`. El servidor rechazará todas las peticiones HTTP.
* **certificateFile** (opcional) - La ruta relativa al certificado SSL.
* **certificateKeyFile** (opcional) - La ruta relativa a la clave pública del certificado SSL.

Si el servidor Linkurious, fuentes de datos y motor de búsqueda están instalados en máquinas diferentes, recomendamos cifrar la comunicación interna entre ellos. Esto le protegerá ante la captura de paquetes en su intranet o una infraestructura de tipo cloud. Por favor consulte la documentación de Neo4j y ElasticSearch para activar HTTPS.

#### Permisos de acceso de usuarios

El sistema de permisos de acceso de usuarios es configurado en la sección `access`:

* **authRequired** - `false`. Rechazar peticiones de sesiones anónimas si es `true`, de lo contrario todas las peticiones serán enlazadas a una cuenta de usuario llamada "Unique User". Establecer a `false` para lanzar Linkurious por primera vez, o si solamente hay un usuario.
* **dataEdition** - `true`. Activa la creación, edición y borrado de nodos y relaciones en todas las fuentes de datos. Los administradores pueden ajustar los permisos de los usuarios, ver el capítulo de Administración. Si es `false`, todas las peticiones de edición de fuentes de datos a Linkurious serán rechazadas.
* **widget** - `true`. Activar para publicar visualizaciones online. Las visualizaciones publicadas son accesibles por usuarios anónimos. Más información en la sección **Gestión > Publicación** del manual.
* **loginTimeout** - `3600`. Terminar la sesión del usuario tras un periodo de inactividad (en segundos).
* **ldap** - La conexión al servicio LDAP (ver debajo).

##### Conexión al servicio LDAP

En Linkurious, los administradores gestionan las cuentas de otros usuarios. Las cuentas de usuario se identifican por un nombre de usuario o dirección de correo electrónico. Si Linkurious está conectado a un servicio LDAP (preferiblemente OpenLDAP o Active Directory), los usuarios son autenticados cada vez que acceden. Si usted tiene un servicio LDAP funcionando en su red, puede utilizarlo para autenticar a los usuarios en Linkurious. Sea consciente de que Linkurious guarda contraseñas cifradas para los usuarios que no son autenticados mediante LDAP.

Para activar la autenticación con LDAP en Linkurious, edite la configuración.

Para Microsoft Active Directory, añada una sección `msActiveDirectory` dentro de `access`:

```JavaScript
"access": {
  // [...]
  "msActiveDirectory": {
    "enabled": true,
    // URL del servidor Active Directory al que conectar
    "url": "ldap://ldap.lks.com",
    // 'Domain Name' base en el que buscar usuarios
    "baseDN": "dc=ldap,dc=lks,dc=com",
    // Dominio de su servidor Active Directory
    "domain": "ldap.lks.com"
  }
}
```

Para OpenLDAP, añada una sección `ldap` dentro de `access`:

```JavaScript
"access": {
  // [...]
  "ldap": {
    // Si es true, Linkurious intentará conectar al servidor LDAP al iniciar
    // utilizando 'bindDN' y 'bindPassword'
    "enabled": true,
    // URL del servidor LDAP al que conectar
    "url": "ldap://ldap.forumsys.com:389",
    // 'Domain Name' de la cuenta LDAP utilizada para autenticar
    "bindDN": "cn=read-only-admin,dc=example,dc=com",
    // contraseña de la cuenta LDAP usada para autenticar
    "bindPassword": "password",
    // 'Domain Name' base en el que buscar usuarios
    "baseDN": "dc=example,dc=com'",
    // nombre del atributo LDAP que contiene el USERNAME de un usuario
    "usernameField": "uid",
    // nombre del atributo LDAP que contiene el PASSWORD de un usuario
    "passwordField": "userPassword",
    // nombre del atributo LDAP que contiene el EMAIL de un usuario
    "emailField": "mail"
  }
}
```

Por favor consulte la documentación de su proveedor LDAP.

<div class="alert alert-warning">
    Contacte a su administrador de redes para asegurar que la máquina en la que Linkurious está instalado pueda conectar al servicio LDAP.
</div>

#### Permisos de usuarios para las fuentes de datos

Los administradores pueden establecer permisos detallados a los usuarios finales para cada fuente de datos. Vea el capítulo de Administración para más información.

### Registro

Linkurious puede registrar eventos del lado del servidor y del lado del cliente.

#### Registros del servidor

El servidor de Linkurious registra varios eventos en los archivos `data/manager/logs/Linkurious-Server-*.log`. Son útiles para arreglar problemas y usted debería incluirlos en sus tickets de soporte.
Los registros del servidor integrado ElasticSearch pueden encontrarse en `data/manager/logs/ElasticSearch-Server-*.log`.

#### Registros del cliente

El cliente de Linkurious puede registrar las acciones del usuario enviando eventos a su cuenta de Google Analytics. Estos registros proporcionan información sobre cómo se utiliza la aplicación, qué características son las más útiles, etc. Esta característica está desactivada de forma predeterminada y ningún script externo es inyectado en este caso. Puede ser configurado en la sección  `clientAnalytics`:

* **enabled** - `false`. 
* **code** - Código universal de Google Analytics tipo "UA-XXXXX-xx".
* **domain** - `"none"`. El dominio desde el que Linkurious es accesible a los usuarios, por ejemplo "www.example.com", o "none".

#### Trazas de auditoría

Las trazas de auditoría le permiten guardar registros detallados de las operaciones realizadas en su base de datos de grafos por los usuarios de Linkurious Enterprise. Los archivos de registro contienen líneas en formato JSON. Usted puede enlazarlas con un sistema de gestión de registros como [Logstash](https://www.elastic.co/products/logstash) para interpretarlas. Esta característica está desactivada de forma predeterminada. Los siguientes ajustes están disponibles en la sección `auditTrail`:

* **enabled** - `false`. Activa las trazas de auditoría si es `true`.
* **logFolder** - `"audit-trail"`. Dónde almacenar los archivos de registro. Esta ruta es relativa al directorio `data` en la raíz de su instalación de Linkurious.
* **fileSizeLimit** - `5242880`. Tamaño máximo en bytes de cada archivo (predeterminado: 5MB). Un nuevo archivo es creado cuando el límite es alcanzado (rotación de archivos) para evitar archivos de registro enormes.
* **strictMode** - `false`. Asegura que se ha registrado la operación antes de devlover el resultado al usuario si es `true`. Podría tener un gran impacto en la velocidad de respuesta del servidor.
* **mode** - `"rw"`. Guardar acciones de LECTURA (`"r"`), ESCRITURA (`"w"`), o ambas (`"rw"`).
