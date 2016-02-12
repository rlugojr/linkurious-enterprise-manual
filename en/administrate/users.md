## Users & groups

### About users and groups

Linkurious Enterprise allows you to authenticate users and assign them to groups. User groups provide permissions to read or write on nodes and edges in the graph database. Each permission is defined at the level of node categories and edge types. Groups are defined for each data source. Two user groups are available by default:

*  The `admin` group has READ and WRITE access to graph data.
*  The `default` group has READ-ONLY access to graph data.

The `default` group is assigned to new users by default.

Users belong to at least one group. They can be assigned to multiple groups. The resulting access rights are combined as follows: *the most permissive right wins*. For instance, let a user belongs to two groups. The first group allows to READ `CITY` nodes, and the second group allows nothing on `CITY` nodes. The user will then have the permission to READ `CITY` nodes.

### User management dashboard

To access the user management dashboard, click on **Users** in the administrator dashboard, or select the **Users** item in the **Admin** menu of the navigation bar. 

We can manage any user by clicking on **Edit** or **Delete** next to the user of our choice. We can also manage the user groups. Remove the last group of an user and they will be assigned to the `default` group.

![user-management](user-management.png)

### Create new users

Administrators and the *"Unique User"* (used when user authentication is disabled) can create new user accounts. Let's create a new user. Click on the **Add** button next to "1 User", then fill in all fields in the form. Notice that you may assign user groups to the user. Click on the **Save** button once it is done.

![new-user](new-user.png)

### Create and manage user groups

Administrators and the Unique User can create user groups and assign them to users from the user management dashboard. Let's create a new user group. Click on the **Add** button in the users dashboard, then give it a name (e.g. *Analyst*). By default, the users of this group will be allowed to READ all nodes and edges of the current data source. You can refine the permissions after the creation of the group.

![group-management](group-management.png)

In the picture above, we can see for example that the *Analyst* group has READ-ONLY right on the `CITY`, `MARKET`, `STARTUP` and `INVESTOR` in our dataset.

Click on  the **Read+Write** button to allow the users of the *Analyst* group to modify the `CITY` nodes. Click on `None` to hide the `MARKET` nodes from the *Analyst* users. You can set permissions in bulk by checking the group name and expand the **Selection > Permissions** menu.

Finally, check the option **"Send cypher queries to the graph (read)"** to enable users of this group to run custom Cypher query the graph database. Cypher is the SQL for graph databases, and is available in the Neo4j graph database. It provides a powerful syntax to extract advanced patterns or to edit the database. This feature will be available to the users in the visualization **Workspace** under the menu **Find > Patterns**. You can learn Cypher on [neo4j.com](http://neo4j.com/developer/cypher-query-language/).

<div class="alert alert-warning">
  Users may probe the structure of the graph with Cypher queries even if they cannot have READ permissions on all nodes. Some very complex queries may also put the graph database in an unstable state, so be careful when granting your users the right to run custom queries.
</div>

<div class="alert alert-danger">
  Users may delete your data by mistake when they run WRITE queries on the graph database. We recommend to enable this feature in development environments only, and to disable it for graph databases in production. It is good practice to create a specific user group with the fewest people possible in it.
</div>
