##Users & groups

###About users and groups
Linkurious Enterprise allows you to authenticate users and assign them to groups.

User groups provide permissions to read or write on nodes and relationships in the graph database. Each permission is defined at the level of node categories and edge types. Groups are defined for each data source.

Two user groups are available by default:

*  ```Admin ``` : The admin group has read and write access to graph data.

*  ```Default ``` : The default group has read-only access to graph data.

The ```Default``` group is assigned to new users by default.

### The users dashboard

To access the users dashboard, we click on ```Users``` in the Administration dashboard.

![opening the user management](https://dl.dropboxusercontent.com/s/sclu8e2gj8q4fk6/99.png?dl=0)

We access the users dashboard.

![opening the user management](https://dl.dropboxusercontent.com/s/rlgdsqsg44vogr3/103.png?dl=0)

From the dashboard, we can manage any user by clicking on ```Edit``` or ```Delete``` next to the user of our choice.

We can also manage the user groups.

### Create new users

Administrators can create new user accounts. In order to do that, we click on ```New user``` in the users dashboard.

![the user creation screen](https://dl.dropboxusercontent.com/s/pk1o1dzuzebpnf3/100.png?dl=0)

We fill in all fields in the form. Notice that you may assign user groups to the user.

![creating a user](https://dl.dropboxusercontent.com/s/smdlp7mjiytg7c7/101.png?dl=0)

We click on ```Create``` once it is done.

We have created our first user.

![first user created](https://dl.dropboxusercontent.com/s/5vlqz9hmrnpo59q/102.png?dl=0)

### Create and manage new user groups

Administrators can create groups and assign them to users from the users dashboard. In order to do that, we click on ```New group``` in the users dashboard.

You can set the access levels of different user groups from the users dashboard.

![first user created](https://dl.dropboxusercontent.com/s/fn05g4m2j7vjupb/120.png?dl=0)

In the picture above, we can see for example that the ```Analyst``` group has read-only right on the ```CITY```, ```MARKET```, ```STARTUP``` and ```INVESTOR``` in our dataset.

We click on ```Read+Write``` to allow the users of the ```Analyst``` group to modify the ```CITY``` nodes.

We click on ```None``` to hide the ```MARKET``` nodes from the ```Analyst``` users.

![first user created](https://dl.dropboxusercontent.com/s/pz53ahkzb413sc9/121.png?dl=0)
