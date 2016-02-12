## Fuentes de datos

Linkurious Enterprise se conecta a fuentes de datos locales o remotas a través de HTTP y HTTPS. Las fuentes de datos tales como servidores Neo4j podrían proporcionar acceso a diferentes bases de datos de grafos. Por ejemplo, es común ver usuarios de Neo4j cambiar entre diferentes bases de datos en el mismo servidor Neo4j. Linkurious Enterprise maneja múltiples configuraciones de fuentes de datos y detecta qué bases de datos están disponibles actualmente desde de las fuentes de datos conectadas.

### Añadir una nueva fuente de datos

1. Abra el directorio de linkurious en su sistema.
- Abra el archivo `linkurious/data/config/production.json` con su editor de texto favorito.
- Busque la clave `dataSources`. Es una lista de configuraciones de fuentes de datos. Por defecto, una única fuente de datos está definida para conectarse a un servidor Neo4j situado en `http://localhost:7474/`. Duplique la configuración por defecto y edite `graphdb` y `url` para definir una segunda fuente de datos.
- Reinicie Linkurious para aplicar los cambios.

### Editar una fuente de datos desde el panel de gestión de datos

Para acceder al panel de gestión de datos, haga clic en **Data** en el panel de administración, o seleccione el elemento **Data** en el menú **Admin** de la barra de navegación. Usted debería ver la siguiente pantalla.

![](../../en/administrate/admin-data-server.png)

Aquí podemos editar la configuración de la fuente de datos, configurar y activar la indexación de datos. Para editar la configuración de otra fuente de datos, cambie la fuente de datos desde la barra de navegación.

### Servidor de búsqueda

La característica de búsqueda utiliza [Elasticsearch](https://www.elastic.co/products/elasticsearch) para realizar búsquedas full-text en tiempo real sobre nodos y relaciones. Un servidor integrado de Elasticsearch es incluido con Linkurious pero usted podría configurar su propio servidor. Todas las fuentes de datos son indexadas en la misma instancia de Elasticsearch por defecto; usted podría configurar diferentes instancias de Elasticsearch para cada fuente de datos. Por favor consulte la documentación oficial de Elasticsearch para configurar su propio clúster.
