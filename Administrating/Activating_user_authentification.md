# Enable user authentication

By default, user authentication is disabled. The unique user can do everything we wants and everybody can access the platform, which is not so great to provide Linkurious Enterprise to your organization. We will thus enable user authentication to handle multiple user accounts.

We must create an administrator account before enabling authentication, otherwise we will not be able to log in.

To do that, click on ```Users``` in the administrator dashboard to enter the Users panel.

![opening the user management](https://dl.dropboxusercontent.com/s/sclu8e2gj8q4fk6/99.png?dl=0)

Click on ```New user``` on the right.

![the user creation screen](https://dl.dropboxusercontent.com/s/pk1o1dzuzebpnf3/100.png?dl=0)

Fill in all fields of the user creation form, and especially remove the ```default``` group and add the ```admin``` group in the groups field to grant administration rights to the new user.

![creating a user](https://dl.dropboxusercontent.com/s/85w4sm4fkh86t8d/109.png?dl=0)

Once done, click on ```Create```.

We have created our first administrator. Now it is time to enable user authentication. 

Go to  ```\linkurious\config``` in your Linkurious Enterprise directory.

Open the ```production.json``` file. Look for ```auth_required```. Change its value from ```false``` to ```true```. Restart Linkurious Enterprise.

User authentication is now enabled. Reload the user interface to get the login screen.

![admin login](https://dl.dropboxusercontent.com/s/ymsb2l06egytrte/110.png?dl=0)

Enter the login and password of the administrator to access Linkurious Enterprise.

In the following section we see how to create more user accounts and to assign them to user groups with permissions on graph data.
