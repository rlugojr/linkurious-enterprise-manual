## Utilisateurs et groupes

### A propos des utilisateurs et groupes 

Linkurious Enterprise vous permet d'authentifier des utilisateur et de les assigner à des groupes. Les groupes d'utilisateur fournissent l'autorisation de lire ou d'écrire des noeuds et liens dans la base de données de graphes. Chaque permission est définie selon le niveau de catégories de noeuds et le type de liens. Les groupes sont définis pour chaque donnée source. Deux groupes d'utilisateurs sont disponibles par défaut:

*  Le groupe `admin` a accès à la LECTURE et l'ECRITURE des données de graphes
*  Le groupe  `default` a un accès de has READ-ONLY access to graph data.

Le groupe `default` est le groupe assigné par défaut à tout nouvel utilisateur. 
Les utilisateurs appartiennent à au moins un groupe. Ils peuvent être assignés à plusieurs groupes. Les droits d'accès résultants sont combinés comme suit: *the most permissive right wins*. Prenons l'exemple d'un utilisateur appartenant à deux groupes. Le premier groupe permet de lire les noeuds `CITY` et le second groupe ne permet rien sur les noeuds `CITY`, l'utilisateur aura la permission de lire les noeuds `CITY`.

### Tableau de bord de gestion des utilisateurs

Pour accèder au tableau de bord de gestion des utilisateurs, cliquez sur **Users** dans le tableau de bord administrateur, ou sélectionnez **Users** dans le menu **Admin** de la barre de navigation. 

Nous pouvons gérer quelconque utilisateur en cliquant sur **Edit** ou **Delete** à côté de l'utilisateur de notre choix. Nous pouvons aussi gérer les groupes d'utilisateurs. si vous supprimez le dernier groupe d'un utilisateur, il sera assigné au groupe par défaut `défaut`. 

![user-management]](user-management.png)

### Créer de nouveaux utilisateurs

Les administrateur et l'utilisateur unique *"Unique User"* (utilisé quand l'identification d'utilisateurs n'est pas activée) peuvent créer des compte de nouveaux utilisateurs. Créons un nouvel utilisateur. Cliquez sur **Add** à côté de "1 User", puis remplissez tous les champs du formulaire. Notez qu'il est possible d'affecter un groupe à l'utilisateur. Cliquez sur **Save** une fois le formulaire rempli. 

![](https://github.com/Linkurious/linkurious-enterprise-manual/raw/master/en/manage/new-user.png)

![new-user]](new-user.png)

### Créer et gérer les groupes d'utilisateurs

Les administrateurs et l'utilisateur unique peuvent créer des groupes d'utilisateurs et les assigner aux différents utilisateurs à partir du tableau de bord de gestion. Créons un nouveau groupe d'utilisateurs. Cliquez sur **Add** dans le tableau de bord des utilisateurs puis donnez lui un nom (par exemple *Analyst*). Par défaut, les utilisateurs de ce groupe seront autorisés à lire tous les noeuds et liens de l'actuelle source de données. Vous pouvez modifier les autorisations après création du groupe.

![group-management]](group-management.png)

Dans l'image ci-dessus, nous pouvons voir par exemple que le groupe *Analyst* a seulement des droits de lecture (READ-ONLY) sur les villes, marchés, statrt up et investisseurs (`CITY`, `MARKET`, `STARTUP` et `INVESTOR`) de notre jeu de données.

Click on  the **Read+Write** button to allow the users of the *Analyst* group to modify the `CITY` nodes. Click on `None` to hide the `MARKET` nodes from the *Analyst* users. You can set permissions in bulk by checking the group name and expand the **Selection > Permissions** menu.

Finally, check the option **"Send cypher queries to the graph (read)"** to enable users of this group to run custom Cypher query the graph database. Cypher is the SQL for graph databases, and is available in the Neo4j graph database. It provides a powerful syntax to extract advanced patterns or to edit the database. This feature will be available to the users in the visualization **Workspace** under the menu **Find > Patterns**. You can learn Cypher on [neo4j.com](http://neo4j.com/developer/cypher-query-language/).

<div class="alert alert-warning">
  Users may probe the structure of the graph with Cypher queries even if they cannot have READ permissions on all nodes. Some very complex queries may also put the graph database in an unstable state, so be careful when granting your users the right to run custom queries.
</div>

<div class="alert alert-danger">
  Users may delete your data by mistake when they run WRITE queries on the graph database. We recommend to enable this feature in development environments only, and to disable it for graph databases in production. It is good practice to create a specific user group with the fewest people possible in it.
</div>
