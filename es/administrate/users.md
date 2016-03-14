## Usuarios y grupos

### Sobre los usuarios y grupos

Linkurious Enterprise le permite autenticar usuarios y asignarlos a grupos. Los grupos de usuarios proporcionan permisos para leer o escribir nodos y relaciones de la base de datos de grafos. Cada permiso es definido al nivel de categorías de nodos y tipos de relaciones. Los grupos son definidos para cada fuente de datos. Dos grupos están disponibles de forma predeterminada:

*  El grupo `admin` tiene permisos de LECTURA y ESCRITURA a los datos.
*  El grupo `default` tiene permisos de SOLO-LECTURA a los datos.

El grupo `default` es asignado a los usuarios nuevos de forma predeterminada.

Los usuarios pertenecen al menos a un grupo. Pueden ser asignados a múltiples grupos. Los permisos de acceso resultantes son combinados de la siguiente forma: *el permiso más permisivo gana*. Por ejemplo, un usuario pertenece a dos grupos. El primer grupo le permite LEER nodos de la categoría `CITY`, y el segundo grupo no permite nada sobre la categoría `CITY` de nodos. El usuario tendrá acceso de LECTURA a los nodos con categoría `CITY`.

### Panel de gestión de usuarios

Para acceder al panel de gestión de usuarios, haga clic en **Users** en el panel de administración, o seleccione el elemento **Users** en el menú **Admin** de la barra de navegación. 

Podemos gestionar cualquier usuario haciendo clic en **Edit** (editar) or **Delete** (eliminar) junto al usuario de nuestra elección. También podemos gestionar los grupos de usuarios. Si elimina el último grupo de un usuario se le asignará el grupo `default`.

![user-management](https://github.com/Linkurious/linkurious-enterprise-manual/raw/master/en/administrate/user-management.png)

### Crear nuevos usuarios

Los administradores y el *"Unique User"* (usuario único, utilizado cuando la autenticación está desactivada) pueden crear nuevas cuentas de usuario. Creemos un nuevo usuario. Haga clic en el botón **Add** (añadir) junto a "1 User", luego rellene todos los campos del formulario. Tenga en cuenta que puede asignar grupos al usuario. Haga clic en el botón **Save** (guardar) cuando haya terminado.

![new-user](https://github.com/Linkurious/linkurious-enterprise-manual/raw/master/en/administrate/new-user.png)

### Crear y gestionar grupos de usuarios

Los administradores y el usuario único pueden crear grupos de usuarios y asignarlos a los usuarios desde el panel de gestión de usuarios. Creemos un nuevo grupo de usuarios. Haga clic en el botón **Add** (añadir) en el panel de grupos de usuarios, luego elija un nombre (por ejemplo *Analyst*). Por defecto, los usuarios de este grupo tendrán permitida la LECTURA de todos los nodos y relaciones de la fuente de datos actual. Usted puede refinar los permisos después de crear el grupo.

![group-management](https://github.com/Linkurious/linkurious-enterprise-manual/raw/master/en/administrate/group-management.png)

En la imagen anterior, podemos ver que por ejemplo el grupo *Analyst* tiene permisos SOLO-LECTURA en las categorías `CITY`, `MARKET`, `STARTUP` e `INVESTOR` de nuestro conjunto de datos.

Haga clic en el botón **Read+Write** (Leer+Escribir) para permitir a los usuarios del grupo *Analyst* modificar los nodos de la categoría `CITY`. Haga clic en `None` (ninguno) para ocultar los nodos de  la categoría `MARKET` a los usuarios del grupo *Analyst*. Usted puede establecer varios permisos a la vez marcando el nombre del grupo y expandiendo el menú **Selection > Permissions**.

Finalmente, marque la opción **"Send cypher queries to the graph (read)"** (enviar consultas cypher al grafo (lectura)) para permitir a los usuarios de este grupo ejecutar consultas personalizadas de tipo Cypher a la base de datos de grafos. Cypher es el SQL de bases de datos de grafos, y está disponible en la base de datos Neo4j. Le proporciona una sintaxis potente para extraer patrones avanzados o editar la base de datos. Esta característica estará disponible a usuarios en el **Workspace** (espacio de trabajo) de la visualización bajo el menú **Find > Patterns** (Encontrar > Patrones). Usted puede aprender Cypher en [neo4j.com](http://neo4j.com/developer/cypher-query-language/).

<div class="alert alert-warning">
  Los usuarios podrían indagar en la estructura de la base de datos de grafos con consultas Cypher incluso aunque no tengan permisos de LECTURA sobre todos los nodos. Algunas consultas muy complejas también podrían dejar la base de datos de grafos en un estado inestable, así que sea cuidadoso al conceder permisos para ejecutar consultas personalizadas a sus usuarios.
</div>

<div class="alert alert-danger">
  Los usuarios podrían borrar datos por error cuando ejecuten consultas de ESCRITURA en la base de datos de grafo. Le recomendamos activar esta característica solamente en entornos de desarrollo, y desactivarlo para bases de datos de grafos en producción. Es una buena práctica crear un grupo de usuarios con el menor número de personas posible en él.
</div>